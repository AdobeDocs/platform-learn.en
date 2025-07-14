---
title: Install Adobe Experience Platform Mobile SDKs
description: Learn how to implement the Adobe Experience Platform Mobile SDK in a mobile app.
jira: KT-14627
exl-id: 98d6f59e-b8a3-4c63-ae7c-8aa11e948f59
---
# Install Adobe Experience Platform Mobile SDKs {#tutorial_install_mobile_sdks}

>[!CONTEXTUALHELP]
>
>id="platform_mobile_sdk_tutorial_install"
>title="Install Adobe Experience Platform Mobile SDKs"
>abstract="Learn how to implement the Adobe Experience Platform Mobile SDK in a mobile app."

Learn how to implement the Adobe Experience Platform Mobile SDK in a mobile app.

## Prerequisites

* Successfully built a tag library with the extensions described in the [previous lesson](configure-tags.md).
* Development Environment File ID from the [Mobile Install Instructions](configure-tags.md#generate-sdk-install-instructions).
* Downloaded the [sample app for iOS](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App) or [sample app for Android](https://github.com/adobe/Luma-Android).
* Experience with [Xcode](https://developer.apple.com/xcode/) (iOS) or [Android Studio](https://developer.android.com/studio/intro?utm_source=android-studio) (Android)

## Learning objectives

In this lesson, you will:

* Add the required SDKs to your project.
* Register the extensions.

>[!NOTE]
>
>In a mobile app implementation, the terms "extensions" and "SDKs" are nearly interchangeable.

>[!BEGINTABS]

>[!TAB iOS]

## Swift Package Manager

Instead of using CocoaPods and a Pod file (as outlined in [Generate SDK install instructions](./configure-tags.md#generate-sdk-install-instructions)), you add individual packages using Xcode's native Swift Package Manager. The Xcode project already has all packages dependencies added for you. The Xcode **[!UICONTROL Package Dependencies]** screen should look like:

![Xcode Package Dependencies](assets/xcode-package-dependencies.png){zoomable="yes"}


In Xcode, you can use **[!UICONTROL File]** > **[!UICONTROL Add Packages...]** to add packages. The table below provides links to the URLs you would use to add packages. The links also direct you to more information about each specific package.  

| Package | Description | 
|---|---|
| [AEP Core](https://github.com/adobe/aepsdk-core-ios) | The `AEPCore`, `AEPServices`, and `AEPIdentity` extensions represent the foundation of the Adobe Experience Platform SDK - every app using the SDK must include them. These modules contain a common set of functionality and services which are required by all SDK extensions.<br/><ul><li>`AEPCore` contains implementation of the Event Hub. The Event Hub is the mechanism used for delivering events between the app and the SDK. The Event Hub is also used for sharing data between extensions.</li><li>`AEPServices` provides several reusable implementations needed for platform support, including networking, disk access, and database management.</li><li>`AEPIdentity` implements the integration with Adobe Experience Platform Identity services.</li><li>`AEPSignal` represents the Adobe Experience Platform SDKs Signal extension that allows marketers to send a "signal" to their apps to send data to external destinations or to open URLs.</li><li>`AEPLifecycle` represents the Adobe Experience Platform SDKs Lifecycle extension that helps collect application lifecycle metrics such as application install or upgrade information, application launch and session information, device information, and any additional context data provided by the application developer.</li></ul> |
| [AEP Edge](https://github.com/adobe/aepsdk-edge-ios) | The Adobe Experience Platform Edge Network mobile extension (`AEPEdge`) allows you to send data to the Adobe Edge Network from a mobile application. This extension allows you to implement Adobe Experience Cloud capabilities in a more robust way, serve multiple Adobe solutions though one network call, and simultaneously forward this information to the Adobe Experience Platform.<br/>The Edge Network mobile extension is an extension for the Adobe Experience Platform SDK and requires the `AEPCore` and `AEPServices` extensions for event handling, as well as the `AEPEdgeIdentity` extension for retrieving the identities, such as ECID.|
| [AEP Edge Identity](https://github.com/adobe/aepsdk-edgeidentity-ios) | The Adobe Experience Platform Edge Identity mobile extension (`AEPEdgeIdentity`) enables handling of user identity data from a mobile application when using the Adobe Experience Platform SDK and the Edge Network extension. |
| [AEP Edge Consent](https://github.com/adobe/aepsdk-edgeconsent-ios) | The Adobe Experience Platform Consent Collection mobile extension (`AEPConsent`) enables consent preferences collection from the mobile application when using the Adobe Experience Platform SDK and the Edge Network extension. |
| [AEP User Profile](https://github.com/adobe/aepsdk-userprofile-ios) | The Adobe Experience Platform User Profile Mobile extension (`AEPUserProfile`) is an extension to manage user profiles for the Adobe Experience Platform SDK.|
| [AEP Places](https://github.com/adobe/aepsdk-places-ios) | The Adobe Experience Platform Places extension (`AEPPlaces`) allows you to track geolocation events as defined in the Adobe Places interface and in Adobe Data Collection Tag rules. |
| [AEP Messaging](https://github.com/adobe/aepsdk-messaging-ios) | The Adobe Experience Platform Messaging extension (`AEPMessaging`) allows you to send push notification tokens and push notification click-through feedback to the Adobe Experience Platform.|
| [AEP Optimize](https://github.com/adobe/aepsdk-optimize-ios) | The Adobe Experience Platform Optimize extension (`AEPOptimize`) provides APIs to enable real-time personalization workflows in the Adobe Experience Platform Mobile SDKs using Adobe Target or Adobe Journey Optimizer Offer Decisioning. It requires `AEPCore` and `AEPEdge` extensions to send personalization query events to the Experience Edge network. |
| [AEP Assurance](https://github.com/adobe/aepsdk-assurance-ios) | Adobe Experience Platform Assurance is product from Adobe Experience Cloud to help you inspect, proof, simulate, and validate how you collect data or serve experiences in your mobile app.|


## Import extensions

Open in Xcode the project in the **[!UICONTROL Start]** folder of the sample app.

In Xcode, navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!UICONTROL AppDelegate]** and ensure the following imports are part of this source file.

```swift
// import AEP MobileSDK libraries
import AEPCore
import AEPServices
import AEPIdentity
import AEPSignal
import AEPLifecycle
import AEPEdge
import AEPEdgeIdentity
import AEPEdgeConsent
import AEPUserProfile
import AEPPlaces
import AEPMessaging
import AEPOptimize
import AEPAssurance
```

Do the same for **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]**.

## Update AppDelegate

Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **AppDelegate** in the Xcode Project navigator. 

1. Replace the `@AppStorage` value `YOUR_ENVIRONMENT_ID_GOES_HERE` for `environmentFileId` with the Environment File ID value that you retrieved from tags in [Generate SDK install instructions](configure-tags.md#generate-sdk-install-instructions). 

   ```swift
   @AppStorage("environmentFileId") private var environmentFileId = "YOUR_ENVIRONMENT_ID_GOES_HERE"
   ```

1. Add the following code to the `application(_, didFinishLaunchingWithOptions)` function.

    ```swift
    // Define extensions
    let extensions = [
        AEPIdentity.Identity.self,
        Lifecycle.self,
        Signal.self,
        Edge.self,
        AEPEdgeIdentity.Identity.self,
        Consent.self,
        UserProfile.self,
        Places.self,
        Messaging.self,
        Optimize.self,
        Assurance.self
    ]
    
    // Register extensions
    MobileCore.registerExtensions(extensions, {
        // Use the environment file id assigned to this application via Adobe Experience Platform Data Collection
        Logger.aepMobileSDK.info("Luma - using mobile config: \(self.environmentFileId)")
        MobileCore.configureWith(appId: self.environmentFileId)
        
        // set this to false or comment it when deploying to TestFlight (default is false),
        // set this to true when testing on your device.
        MobileCore.updateConfigurationWith(configDict: ["messaging.useSandbox": true])
        if appState != .background {
            // only start lifecycle if the application is not in the background
            MobileCore.lifecycleStart(additionalContextData: nil)
        }
        
        // assume unknown, adapt to your needs.
        MobileCore.setPrivacyStatus(.unknown)
    })
    ```

The above code does the following:

1. Registers the required extensions.
1. Configures MobileCore and other extensions to use your tag property configuration.
1. Enables debug logging. More details and options can be found in the [Adobe Experience Platform Mobile SDK documentation](https://developer.adobe.com/client-sdks/documentation/getting-started/enable-debug-logging/).
1. Starts lifecycle monitoring. See [Lifecycle](lifecycle-data.md) step in the tutorial for more details.
1. Sets the default consent to unknown. See [Consent](consent.md) step in the tutorial for more details.

Ensure you update `MobileCore.configureWith(appId: self.environmentFileId)` with the `appId` based on the `environmentFileId` from the tag environment you are building for (development, staging, or production).

>[!TAB Android]

## Gradle

You use the dependencies from the [Generate SDK install instructions](./configure-tags.md#generate-sdk-install-instructions) to add individual packages using Gradle's integration with Android Studio, The Android Studio project already has all packages dependencies added for you. 

Select **[!UICONTROL build.gradle.kts (Module app)]** from the left pane and in the right pane, scroll until you see `dependencies`.

![Android Gradle Dependencies](assets/androidstudio-package-dependencies.png){zoomable="yes"}

In Anroid Studio, you can use **[!UICONTROL File]** > **[!UICONTROL Project Structure...]** to add module dependencies. Select **[!UICONTROL Dependencies]** and then use **[!UICONTROL Modules]** ![Add](/help/assets/icons/Add.svg) to add modules. The table below provides links to the URLs you would use to add dependency modules. The links also direct you to more information about each specific module.  

| Package<br/>com.adobe.<br/>marketing.mobile: | Description | 
|---|---|
| [core](https://github.com/adobe/aepsdk-core-android) | The `MobileCore` and `Identity` extensions represent the foundation of the Adobe Experience Platform SDK. Every app using the SDK must include them. These modules contain a common set of functionality and services which are required by all SDK extensions<ul><li>`MobileCore` contains the implementation of the Event Hub. The Event Hub is the mechanism used for delivering events between the app and the SDK. The Event Hub is also used for sharing data between extensions and provides several reusable implementations needed for platform support, including networking, disk access, and database management.</li><li>`Identity` implements the integration with Adobe Experience Platform Identity services.</li><li>`Signal` represents the Adobe Experience Platform SDK's Signal extension that allows marketers to send a "signal" to their apps to send data to external destinations or to open URLs.</li><li>`Lifecycle` represents the Adobe Experience Platform SDK's Lifecycle extension that helps collect application Lifecycle metrics, such as application install or upgrade information, application launch and session information, device information, and any additional context data provided by the application developer.</li></ul> |
| [edge](https://github.com/adobe/aepsdk-edge-android) | The Adobe Experience Platform Edge Network mobile extension (`AEPEdge`) allows you to send data to the Adobe Edge Network from a mobile application. This extension allows you to implement Adobe Experience Cloud capabilities in a more robust way, serve multiple Adobe solutions though one network call, and simultaneously forward this information to the Adobe Experience Platform.<br/>The Edge Network mobile extension is an extension for the Adobe Experience Platform SDK and requires the `Mobile Core` and `Services` extensions for event handling, as well as Identity for Edge Network extension for retrieving the identities, such as ECID.|
| [edgeidentity](https://github.com/adobe/aepsdk-edgeidentity-android) | The Adobe Experience Platform Edge Identity mobile extension enables handling of user identity data from a mobile application when using the Adobe Experience Platform SDK and the Edge Network extension. |
| [edgeconsent](https://github.com/adobe/aepsdk-edgeconsent-android) | The Adobe Experience Platform Consent Collection mobile extension enables consent preferences collection from the mobile application when using the Adobe Experience Platform SDK and the Edge Network extension. |
| [userprofile](https://github.com/adobe/aepsdk-userprofile-android) | The Adobe Experience Platform User Profile Mobile extension is an extension to manage user profiles for the Adobe Experience Platform SDK.|
| [aepplaces](https://github.com/adobe/aepsdk-places-android) | Adobe Places Service is a geo-location service that enables mobile apps with location awareness to understand the location context by using rich and easy-to-use SDK interfaces accompanied by a flexible database of points of interests (POIs). For more information, see the Places Service Documentation.<br/>This service the Places mobile extension for the Android 2.x Adobe Experience Platform SDK and requires the Core extension for event handling. |
| [messaging](https://github.com/adobe/aepsdk-messaging-android) | The Adobe Experience Platform Messaging extension  powers push notifications, in-app messages, and code-based experiences for your mobile apps. This extension also helps you to collect user push tokens and manages interaction measurement with Adobe Experience Platform services. |
| [optimize](https://github.com/adobe/aepsdk-optimize-android) | The Adobe Experience Platform Optimize extension provides APIs to enable real-time personalization workflows in the Adobe Experience Platform SDKs using Adobe Target or Adobe Journey Optimizer Offer Decisioning. It depends on the Mobile Core and requires Edge Extension to send personalization query events to the Experience Edge network. |
| [assurance](https://github.com/adobe/aepsdk-assurance-android) | Assurance (a.k.a. project Griffon) is a mobile extension for Adobe Experience Platform that allows integrating with Adobe Experience Platform Assurance to help inspect, proof, simulate, and validate how you collect data or serve experiences in your mobile app. This extension requires MobileCore. |

## Import extensions

In Android Studio, navigate to **[!UICONTROL app]** > **[!UICONTROL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL LumaApplication]** and ensure the following imports are part of the source file.

```kotlin
import com.adobe.marketing.mobile.Assurance
import com.adobe.marketing.mobile.Edge
import com.adobe.marketing.mobile.Lifecycle
import com.adobe.marketing.mobile.LoggingMode
import com.adobe.marketing.mobile.Messaging
import com.adobe.marketing.mobile.MobileCore
import com.adobe.marketing.mobile.MobilePrivacyStatus
import com.adobe.marketing.mobile.Places
import com.adobe.marketing.mobile.Signal
import com.adobe.marketing.mobile.UserProfile
import com.adobe.marketing.mobile.edge.consent.Consent
import com.adobe.marketing.mobile.edge.identity.Identity
import com.adobe.marketing.mobile.optimize.Optimize
```

Do the same for **[!UICONTROL app]** > **[!UICONTROL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL models]** > **[!UICONTROL MobileSDK]**.


## Update LumaApplication

Navigate to **[!UICONTROL app]** > **[!UICONTROL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL LumaApplication]** in Android Studio.

1. Replace `"YOUR_ENVIRONMENT_FILE_ID"` in `private var environmentFileId = "YOUR_ENVIRONMENT_ID_GOES_HERE"` with the Environment File ID value that you retrieved from tags in [Generate SDK install instructions](configure-tags.md#generate-sdk-install-instructions).

   ```kotlin
   private var environmentFileId = "YOUR_ENVIRONMENT_ID_GOES_HERE"
   ```

1. Add the following code to `override fun onCreate()` function in `class LumaApplication : Application()`.

   ```kotlin
   // Define extensions
   val extensions = listOf(
      Identity.EXTENSION,
      Lifecycle.EXTENSION,
      Signal.EXTENSION,
      Edge.EXTENSION,
      Consent.EXTENSION,
      UserProfile.EXTENSION,
      Places.EXTENSION,
      Messaging.EXTENSION,
      Optimize.EXTENSION,
      Assurance.EXTENSION
   )

   // Register extensions
   MobileCore.registerExtensions(extensions) {
   // Use the environment file id assigned to this application via Adobe Experience Platform Data Collection
     Log.i("Luma", "Using mobile config: $environmentFileId")
     MobileCore.configureWithAppID(environmentFileId)

     // set this to true when testing on your device, default is false.
     //MobileCore.updateConfiguration(mapOf("messaging.useSandbox" to true))

     // assume unknown, adapt to your needs.
     MobileCore.setPrivacyStatus(MobilePrivacyStatus.UNKNOWN)
   }
   ```

   The above code does the following:

   1. Registers the required extensions.
   1. Configures MobileCore and other extensions to use your tag property configuration.
   1. Enables debug logging. More details and options can be found in the [Adobe Experience Platform Mobile SDK documentation](https://developer.adobe.com/client-sdks/documentation/getting-started/enable-debug-logging/).
   1. Starts lifecycle monitoring. See [Lifecycle](lifecycle-data.md) step in the tutorial for more details.
   1. Sets the default consent to unknown. See [Consent](consent.md) step in the tutorial for more details.

Ensure you update `MobileCore.configureWith(environmentFileId)` with the `environmentFileId` based on the Environment File ID from the tag environment you are building for (development, staging, or production).


>[!ENDTABS]

>[!SUCCESS]
>
>You have now installed the necessary packages and updated your project to properly register the required  Adobe Experience Platform Mobile SDK extensions you are going to use for the remainder of the tutorial.
>
>Thank you for investing your time in learning about Adobe Experience Platform Mobile SDK. If you have questions, want to share general feedback, or have suggestions on future content, share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Next: **[Set up Assurance](assurance.md)**
