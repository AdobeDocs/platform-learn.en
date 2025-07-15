---
title: Replace the SDK - Migrate the Adobe Target implementation in your mobile app to the Offer Decisioning and Target extension
description: Learn how to replace the SDK when migrating from the Adobe Target to the Offer Decisioning and Target Mobile extension.
exl-id: f1b77cad-792b-4a80-acff-e1a2f29250e1
---
# Replace the Target SDK with the Optimize SDK

Learn how to replace the Adobe Target SDKs with the Optimize SDKs in your mobile implementation. A basic replacement consists of the following steps:

* Update dependencies in your Podfile or `build.gradle` file
* Update imports
* Update application code


>[!INFO]
>
>Within the Adobe Experience Platform Mobile SDK ecosystem, extensions are implemented by SDKs imported into your applications which may have different names:
>
> * **Target SDK** implements the **Adobe Target extension**
> * **Optimize SDK** implements the **Offer Decisioning and Target extension**

## Update dependencies

+++Android exanple

>[!BEGINTABS]

>[!TAB Optimize SDK] 

`build.gradle` dependencies after migrating

```Java
implementation platform('com.adobe.marketing.mobile:sdk-bom:3.+')
implementation 'com.adobe.marketing.mobile:core'
implementation 'com.adobe.marketing.mobile:edgeidentity'
implementation 'com.adobe.marketing.mobile:edge'
implementation 'com.adobe.marketing.mobile:optimize'
```


>[!TAB Target SDK] 

`build.gradle` dependencies before migrating

```Java
implementation platform('com.adobe.marketing.mobile:sdk-bom:3.+')
implementation 'com.adobe.marketing.mobile:analytics'
implementation 'com.adobe.marketing.mobile:target'
implementation 'com.adobe.marketing.mobile:core'
implementation 'com.adobe.marketing.mobile:identity'
implementation 'com.adobe.marketing.mobile:lifecycle'
implementation 'com.adobe.marketing.mobile:signal'
implementation 'com.adobe.marketing.mobile:userprofile'

```


>[!ENDTABS]

+++ 

+++ iOS example

>[!BEGINTABS]


>[!TAB Optimize SDK]

`Podfile` dependencies after migrating

```Swift
use_frameworks!
target 'YourAppTarget' do
    pod 'AEPCore', '~> 5.0'
    pod 'AEPEdge', '~> 5.0'
    pod 'AEPEdgeIdentity', '~> 5.0'
    pod 'AEPOptimize', '~> 5.0'
end
```

>[!TAB Target SDK]

`Podfile` dependencies before migrating

```Swift
use_frameworks!
pod 'AEPAnalytics', '~> 5.0'
pod 'AEPTarget', '~> 5.0'
pod 'AEPCore', '~> 5.0'
pod 'AEPIdentity', '~> 5.0'
pod 'AEPSignal', '~>5.0'
pod 'AEPLifecycle', '~>5.0'
pod 'AEPUserProfile', '~> 5.0'
```

>[!ENDTABS]

+++

## Update imports and code

+++ Android example

>[!BEGINTABS]

>[!TAB Optimize SDK] 

Java initialization code after migrating

```Java
import com.adobe.marketing.mobile.MobileCore;
import com.adobe.marketing.mobile.Edge;
import com.adobe.marketing.mobile.edge.identity.Identity;
import com.adobe.marketing.mobile.optimize.Optimize;
import com.adobe.marketing.mobile.AdobeCallback;
 
public class MainApp extends Application {
 
  private final String ENVIRONMENT_FILE_ID = "YOUR_APP_ENVIRONMENT_ID";
 
    @Override
    public void onCreate() {
        super.onCreate();
 
        MobileCore.setApplication(this);
        MobileCore.configureWithAppID(ENVIRONMENT_FILE_ID);
 
        MobileCore.registerExtensions(
            Arrays.asList(Edge.EXTENSION, Identity.EXTENSION, Optimize.EXTENSION),
            o -> Log.d("MainApp", "Offer Decisioning and Target Mobile SDK was initialized.")
        );
    }
}
```

>[!TAB Target SDK] 

Java initialization code before migrating

```Java
import com.adobe.marketing.mobile.AdobeCallback;
import com.adobe.marketing.mobile.Analytics;
import com.adobe.marketing.mobile.Extension;
import com.adobe.marketing.mobile.Identity;
import com.adobe.marketing.mobile.Lifecycle;
import com.adobe.marketing.mobile.LoggingMode;
import com.adobe.marketing.mobile.MobileCore;
import com.adobe.marketing.mobile.Signal;
import com.adobe.marketing.mobile.Target;
import com.adobe.marketing.mobile.UserProfile;
import java.util.Arrays;
import java.util.List;
...
import android.app.Application;
...
public class MainApp extends Application {
...
    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);
        MobileCore.setLogLevel(LoggingMode.DEBUG);
        ...
        List<Class<? extends Extension>> extensions = Arrays.asList(
            Analytics.EXTENSION,
            Target.EXTENSION,
            Identity.EXTENSION,
            Lifecycle.EXTENSION,
            Signal.EXTENSION,
            UserProfile.EXTENSION
        );
 
 
        MobileCore.registerExtensions(extensions, new AdobeCallback () {
            @Override
            public void call(Object o) {
                MobileCore.configureWithAppID(<Environment File ID>);
            }
        });
    }
}

```

>[!ENDTABS]

+++

+++ iOS

>[!BEGINTABS]

>[!TAB Optimize SDK]

Swift initialization code after migrating

```Swift
import AEPCore
import AEPEdge
import AEPEdgeIdentity
import AEPOptimize
 
@UIApplicationMain
final class AppDelegate: UIResponder, UIApplicationDelegate {
  var window: UIWindow?
 
  func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]? = nil) -> Bool {
 
      // register the extensions
      MobileCore.registerExtensions([Edge.self, AEPEdgeIdentity.Identity.self, Optimize.self]) {
        MobileCore.configureWith(appId: <YOUR_ENVIRONMENT_FILE_ID>) // Replace <YOUR_ENVIRONMENT_FILE_ID> with a String containing your own ID.
      }
 
      return true
  }
}
```

>[!TAB Target SDK]

Swift initialization code before migrating

```Swift
import AEPCore
import AEPAnalytics
import AEPTarget
import AEPIdentity
import AEPLifecycle
import AEPSignal
import AEPServices
import AEPUserProfile
...
@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {
    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        MobileCore.setLogLevel(.debug)
        let appState = application.applicationState
        ...
        let extensions = [
            Analytics.self,
            Target.self,
            Identity.self,
            Lifecycle.self,
            Signal.self,
            UserProfile.self
        ]
        MobileCore.registerExtensions(extensions, {
        MobileCore.configureWith(<Environment File ID>)
        if appState != .background {
            MobileCore.lifecycleStart(additionalContextData: ["contextDataKey": "contextDataVal"])
            }
        })
        ...
        return true
    }
}
```

>[!ENDTABS]

+++

## API comparison

Many Target extension APIs have an equivalent approach using the Offer Decisioning and Target extension outlined in the table below. For more details about the [functions](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/api-reference/), refer to the API reference.

| Target extension | Offer Decisioning and Target extension | Notes |
| --- | --- | --- | 
| [prefetchContent](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#prefetchcontent){target=_blank} | [updatePropositions](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/api-reference/#updatepropositionswithcompletionhandlerandtimeout){target=_blank} |  | 
| [retrieveLocationContent](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#retrievelocationcontent){target=_blank} | [getPropositions](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/api-reference/#getpropositionswithtimeout){target=_blank} | When using `getPropositions` API, no remote call is made to fetch non-cached scopes in the SDK.  | 
| [displayedLocations](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#retrievelocationcontent){target=_blank} | [Offer -> displayed()](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-direct-offer-class-methods){target=_blank} |     In addition, `generateDisplayInteractionXdm` Offer method can be used to generate the XDM for item display. Subsequently, Edge network SDK's sendEvent API can be used to attach additional XDM, free-form data and send an Experience Event to the remote. | 
| [clickedLocation](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#clickedlocation){target=_blank} | [Offer -> tapped()](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-direct-offer-class-methods){target=_blank} | In addition, `generateTapInteractionXdm` Offer method can be used to generate the XDM for item tap. Subsequently, Edge network SDK's sendEvent API can be used to attach additional XDM, free-form data and send an Experience Event to the remote. | 
| [clearPrefetchCache](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#clickedlocation){target=_blank} | [clearCachedPropositions](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-direct-offer-class-methods){target=_blank} |  | 
| [resetExperience](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#resetexperience){target=_blank} | n/a | Use [removeIdentity](https://developer.adobe.com/client-sdks/edge/identity-for-edge-network/api-reference/#removeidentity){target=_blank} API from Identity for Edge Network extension for the SDK to stop sending the visitor identifier to the Edge network. For more details, see [the removeIdentity API documentation](https://developer.adobe.com/client-sdks/edge/identity-for-edge-network/api-reference/#removeidentity). <br><br>Note: Mobile Core's `resetIdentities` API clears all stored identities in the SDK, including the Experience Cloud ID (ECID) and it should be sparingly used! | 
| [getSessionId](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#getsessionid){target=_blank} | n/a | `state:store` response handle carries session-related information. Edge network extension helps manage it by attaching non-expired state store items to subsequent requests. | 
| [setSessionId](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#setsessionid){target=_blank} | n/a | `state:store` response handle carries session-related information. Edge network extension helps manage it by attaching non-expired state store items to subsequent requests. | 
| [getThirdPartyId](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#getthirdpartyid){target=_blank}  |  n/a | Use updateIdentities API from Identity for Edge Network extension to supply the third party ID value. Then, configure the third party ID namespace in the datastream. For more details, see [the Target Third Party Id mobile documentation](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id).  |
| [setThirdPartyId](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#setthirdpartyid){target=_blank} | n/a | Use updateIdentities API from Identity for Edge Network extension to supply the third party ID value. Then, configure the third party ID namespace in the datastream. For more details, see [the Target Third Party Id mobile documentation](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id). | 
| [getTntId](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#gettntid){target=_blank} | n/a | `locationHint:result` response handle carries the Target location hint information. It is assumed Target edge will be co-located with Experience Edge. <br> <br>Edge network extension uses the EdgeNetwork location hint to determine the Edge network cluster to send requests to. To share Edge network location hint across SDKs (hybrid apps), use `getLocationHint` and `setLocationHint` APIs from Edge Network extension. For more details, see [the `getLocationHint` API documentation](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#getlocationhint). | 
| [setTntId](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#gettntid){target=_blank} | n/a | [locationHint:result](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#setlocationhint){target=_blank} response handle carries the Target location hint information. It is assumed Target edge will be co-located with Experience Edge. <br> <br>Edge network extension uses the EdgeNetwork location hint to determine the Edge network cluster to send requests to. To share Edge network location hint across SDKs (hybrid apps), use `getLocationHint` and `setLocationHint` APIs from Edge Network extension. For more details, see [the `getLocationHint` API documentation](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#getlocationhint).  | 


Next, learn how to [request and render activities](retrieve-activities.md) to the page.

>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Offer Decisioning and Target extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-adobe-target-to-mobile-sdk-on-edge/m-p/747484#M625).
