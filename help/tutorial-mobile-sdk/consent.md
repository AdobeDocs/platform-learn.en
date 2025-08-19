---
title: Implement consent for Platform Mobile SDK implementations
description: Learn how to implement consent in a mobile app.
feature: Mobile SDK,Consent
jira: KT-14629
exl-id: 08042569-e16e-4ed9-9b5a-864d8b7f0216
---
# Implement consent

Learn how to implement consent in a mobile app.

The Adobe Experience Platform Consent mobile extension enables consent preferences collection from your mobile app when using the Adobe Experience Platform Mobile SDK and the Edge Network extension. Learn more about the [Consent extension](https://developer.adobe.com/client-sdks/documentation/consent-for-edge-network/) in the documentation.

## Prerequisites

* Successfully built and run app with SDKs installed and configured.

## Learning objectives

In this lesson, you will:

* Prompt the user for consent.
* Update the extension based on the user response.
* Learn how to get the current consent state.

## Ask for consent

If you followed the tutorial from the beginning, you might remember that you have set the default consent in the Consent extension to **[!UICONTROL Pending - Queue events that occur before the user provides consent preferences.]** 

To begin collecting data, you must get consent from the user. In a real-world app, you would want to consult consent best practices for your region. In this tutorial, you get consent from the user by simply asking for it with an alert:

>[!BEGINTABS]

>[!TAB iOS]

1. You only want to ask the user once for consent. You can do this by combining the Mobile SDK consent with the required authorization for tracking using Apple's [App Tracking Transparency framework](https://developer.apple.com/documentation/apptrackingtransparency). In this app, you assume that when the user authorizes tracking they consent to collecting events.
 
1. Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** in the Xcode Project navigator.
  
   Add this code to the `updateConsent` function.

   ```swift
   // Update consent
   let collectConsent = ["collect": ["val": value]]
   let currentConsents = ["consents": collectConsent]
   Consent.update(with: currentConsents)
   MobileCore.updateConfigurationWith(configDict: currentConsents)
   ```

1. Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL DisclaimerView]** in Xcode's Project navigator, which is the view that is shown after installing or reinstalling the application and starting the app for the first time. The user is prompted to authorize tracking per Apple's [App Tracking Transparency framework](https://developer.apple.com/documentation/apptrackingtransparency). If the user authorizes, you also update the consent.

   Add the following code to the `ATTrackingManager.requestTrackingAuthorization { status in` closure.

   ```swift 
   // Add consent based on authorization
   if status == .authorized {
      // Set consent to yes
      MobileSDK.shared.updateConsent(value: "y")
   }
   else {
      // Set consent to yes
      MobileSDK.shared.updateConsent(value: "n")
   }
   ```

>[!TAB Android]

1. You only want to ask the user once for consent. In this app, you assume that when the user authorizes tracking they consent to collecting events.
 
1. Navigate to **[!UICONTROL app]** > **[!UICONTROL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL models]** > **[!UICONTROL MobileSDK]** in the Android Studio navigator.
  
   Add this code to the `updateConsent(value: String)` function.

   ```kotlin
   // Update consent
   val collectConsent = mapOf("collect" to mapOf("val" to value))
   val currentConsents = mapOf("consents" to collectConsent)
   Consent.update(currentConsents)
   MobileCore.updateConfiguration(currentConsents)
   ```

1. Navigate to **[!UICONTROL app]** > **[!UICONTROL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL views]** > **[!UICONTROL DisclaimerView.kt]** in the Android Studio navigator.

   Add the following code to the `DisclaimerView(navController: NavController)` function underneath `// Set content to yes`, and `// Set content to no`.

   ```kotlin 
   // Add consent based on authorization
   if (status) {
      showPersonalizationWarning = false

      // Set consent to yes
      MobileSDK.shared.updateTrackingStatus(TrackingStatus.AUTHORIZED)
      MobileSDK.shared.updateConsent("y")
   } else {
      Toast.makeText(
            context,
            "You will not receive offers and location tracking will be disabled.",
            Toast.LENGTH_LONG
      ).show()
      showPersonalizationWarning = true
      
      // Set consent to no
      MobileSDK.shared.updateTrackingStatus(TrackingStatus.DENIED)
      MobileSDK.shared.updateConsent("n")
   }
   ```

>[!ENDTABS]

## Get current consent state

The Consent mobile extension automatically suppresses / pends / allows tracking based on the current consent value. You can also access the current consent state yourself:

>[!BEGINTABS]

>[!TAB iOS]

1. Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** in Xcode's Project navigator.

   Add the following code to the `getConsents` function:

   ```swift
   // Get consents
   Consent.getConsents { consents, error in
      guard error == nil, let consents = consents else { return }
      guard let jsonData = try? JSONSerialization.data(withJSONObject: consents, options: .prettyPrinted) else { return }
      guard let jsonStr = String(data: jsonData, encoding: .utf8) else { return }
      Logger.aepMobileSDK.info("Consent getConsents: \(jsonStr)")
   }
   ```

2. Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL HomeView]** in Xcode's Project navigator.

   Add the following  code to the `.task` modifier:

   ```swift
   // Ask status of consents
   MobileSDK.shared.getConsents()   
   ```

In the above example, you are simply logging the consent status to the console in Xcode. In a real-world scenario, you might use it to modify what menus or options are shown to the user.

>[!TAB Android]

1. Navigate to **[!UICONTROL app]** > **[!UICONTROL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL models]** > **[!UICONTROL MobileSDK]** in the Android Studio navigator.

   Add the following code to the `getConsents()` function:

   ```kotlin
   // Get consents
   Consent.getConsents { callback ->
      if (callback != null) {
            val jsonStr = JSONObject(callback).toString(4)
            Log.i("MobileSDK", "Consent getConsents: $jsonStr")
      }
   }
   ```

1. Navigate to **[!UICONTROL app]** > **[!UICONTROL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL views]** > **[!UICONTROL HomeView.kt]** in the Android Studio navigator.

   Add the following  code to `LaunchedEffect(unit)`:

   ```kotlin
   // Ask status of consents
   MobileSDK.shared.getConsents()   
   ```

In the above example, you are simply logging the consent status to the console in Android Studio. In a real-world scenario, you might use it to modify what menus or options are shown to the user.

>[!ENDTABS]

## Validate with Assurance

1. Delete the application from your device or simulator to properly reset and initialize the tracking and consent.
1. To connect your simulator or device to Assurance, review the [setup instructions](assurance.md#connecting-to-a-session) section.
1. When moving in the app from **[!UICONTROL Home]** screen to **[!UICONTROL Products]** screen and back to **[!UICONTROL Home]** screen, you should see a **[!UICONTROL Get Consents Response]** event in the Assurance UI.
    ![validate consent](assets/consent-update.png){zoomable="yes"}


>[!SUCCESS]
>
>You have now enabled your app to prompt the user at its initial start after installation (or reinstallation) to consent using the Adobe Experience Platform Mobile SDK.
>
>Thank you for investing your time in learning about Adobe Experience Platform Mobile SDK. If you have questions, want to share general feedback, or have suggestions on future content, share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Next: **[Collect lifecycle data](lifecycle-data.md)**
