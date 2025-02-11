---
title: Replace the SDK - Migrate from the Adobe Target to the Adobe Journey Optimizer - Decisioning Mobile extension
description: Learn how to replace the SDK when migrating from the Adobe Target to the Adobe Journey Optimizer - Decisioning Mobile extension.
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
> * **Optimize SDK** implements the **Adobe Journey Optimizer - Decisioning extension**

## Update dependencies

+++Android exanple

>[!BEGINTABS]

>[!TAB Optimize SDK] 

`build.gradle` dependencies after migrating

```Java
implementation platform('com.adobe.marketing.mobile:sdk-bom:3.+')
implementation 'com.adobe.marketing.mobile:edgeconsent'
implementation 'com.adobe.marketing.mobile:edgeidentity'
implementation 'com.adobe.marketing.mobile:edge'
implementation 'com.adobe.marketing.mobile:assurance'
implementation 'com.adobe.marketing.mobile:core'
implementation 'com.adobe.marketing.mobile:identity'
implementation 'com.adobe.marketing.mobile:lifecycle'
implementation 'com.adobe.marketing.mobile:signal'
implementation 'com.adobe.marketing.mobile:userprofile'
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
pod 'AEPAnalytics', '~> 5.0'
pod 'AEPTarget', '~> 5.0'
pod 'AEPCore', '~> 5.0'
pod 'AEPIdentity', '~> 5.0'
pod 'AEPSignal', '~>5.0'
pod 'AEPLifecycle', '~>5.0'
pod 'AEPUserProfile', '~> 5.0'
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
import com.adobe.marketing.mobile.AdobeCallback;
import com.adobe.marketing.mobile.Assurance;
import com.adobe.marketing.mobile.Edge;
import com.adobe.marketing.mobile.Extension;
import com.adobe.marketing.mobile.Identity;
import com.adobe.marketing.mobile.Lifecycle;
import com.adobe.marketing.mobile.LoggingMode;
import com.adobe.marketing.mobile.MobileCore;
import com.adobe.marketing.mobile.Signal;
import com.adobe.marketing.mobile.UserProfile;
import com.adobe.marketing.mobile.edge.consent.Consent;
import com.adobe.marketing.mobile.edge.identity.Identity;
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
            Consent.EXTENSION,
            com.adobe.marketing.mobile.edge.identity.Identity.EXTENSION,
            com.adobe.marketing.mobile.Identity.EXTENSION,
            Edge.EXTENSION,
            Assurance.EXTENSION,
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
            Consent.self,
            AEPEdgeIdentity.Identity.self,
            AEPIdentity.Identity.self,
            Edge.self,
            Assurance.self,
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

## Function comparison

Many Target extension functions have an equivalent approach using the Decisioning extension outlined in the table below. For more details about the [functions](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/atjs-functions/), refer to the Adobe Target Developer Guide.

| Target extension | Decisioning extension | Notes |
| --- | --- | --- | 
| `prefetchContent` | `updatePropositions` |  | 
| `retrieveLocationContent` | `getPropositions` | When using `getPropositions` API, no remote call is made to fetch non-cached scopes in the SDK.  | 
| `displayedLocations` | Offer -> `displayed()` |     In addition, `generateDisplayInteractionXdm` Offer method can be used to generate the XDM for item display. Subsequently, Edge network SDK's sendEvent API can be used to attach additional XDM, free-form data and send an Experience Event to the remote. | 
| `clickedLocation` | Offer -> `tapped()` | In addition, `generateTapInteractionXdm` Offer method can be used to generate the XDM for item tap. Subsequently, Edge network SDK's sendEvent API can be used to attach additional XDM, free-form data and send an Experience Event to the remote. | 
| `clearPrefetchCache` | `clearCachedPropositions` |  | 
| `resetExperience` | n/a | Use `removeIdentity` API from Identity for Edge Network extension for the SDK to stop sending the visitor identifier to the Edge network. For more details, see [the removeIdentity API documentation](https://developer.adobe.com/client-sdks/edge/identity-for-edge-network/api-reference/#removeidentity). <br><br>Note: Mobile Core's `resetIdentities` API clears all stored identities in the SDK, including the Experience Cloud ID (ECID) and it should be sparingly used! | 
| `getSessionId` | n/a | `state:store` response handle carries session-related information. Edge network extension helps manage it by attaching non-expired state store items to subsequent requests. | 
| `setSessionId` | n/a | `state:store` response handle carries session-related information. Edge network extension helps manage it by attaching non-expired state store items to subsequent requests. | 
| `getThirdPartyId`  |  n/a | Use updateIdentities API from Identity for Edge Network extension to supply the third party ID value. Then, configure the third party ID namespace in the datastream. For more details, see [the Target Third Party Id mobile documentation](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id).  |
| `setThirdPartyId` | n/a | Use updateIdentities API from Identity for Edge Network extension to supply the third party ID value. Then, configure the third party ID namespace in the datastream. For more details, see [the Target Third Party Id mobile documentation](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id). | 
| `getTntId` | n/a | `locationHint:result` response handle carries the Target location hint information. It is assumed Target edge will be co-located with Experience Edge. <br> <br>Edge network extension uses the EdgeNetwork location hint to determine the Edge network cluster to send requests to. To share Edge network location hint across SDKs (hybrid apps), use `getLocationHint` and `setLocationHint` APIs from Edge Network extension. For more details, see [the `getLocationHint` API documentation](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#getlocationhint). | 
| `setTntId` | n/a | `locationHint:result` response handle carries the Target location hint information. It is assumed Target edge will be co-located with Experience Edge. <br> <br>Edge network extension uses the EdgeNetwork location hint to determine the Edge network cluster to send requests to. To share Edge network location hint across SDKs (hybrid apps), use `getLocationHint` and `setLocationHint` APIs from Edge Network extension. For more details, see [the `getLocationHint` API documentation](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#getlocationhint).  | 


Next, learn how to [request and render activities](render-activities.md) to the page.

>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Decisioning extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
