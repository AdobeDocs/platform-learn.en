---
title: Create and send in-app messages with Platform Mobile SDK
description: Learn how to create and send in-app messages to a mobile app with Platform Mobile SDK and Adobe Journey Optimizer.
solution: Data Collection,Journey Optimizer
feature-set: Journey Optimizer
feature: In App
exl-id: 6cb4d031-6172-4a84-b717-e3a1f5dc7d5d
---
# Create and send in-app messages

Learn how to create in-app messages for mobile apps with Experience Platform Mobile SDK and Journey Optimizer.

Journey Optimizer allows you to create campaigns to send in-app messages to targeted audiences. Campaigns in Journey Optimizer are used to deliver one-time content to a specific audience using various channels. With campaigns, actions are performed simultaneously, either immediately, or based on a specified schedule. When using journeys (see the [Journey Optimizer push notifications](journey-optimizer-push.md) lesson), actions are executed in sequence. 

![Architecture](assets/architecture-ajo.png)

Before you send in-app messages with Journey Optimizer, you must ensure that the proper configurations and integrations are in place. To understand the in-app messaging data flow in Journey Optimizer, refer to [the documentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/in-app/inapp-configuration.html?lang=en).

>[!NOTE]
>
>This lesson is optional and only applies to Journey Optimizer users looking to send in-app messages. 


## Prerequisites

* Successfully built and run app with SDKs installed and configured.
* Set up the app for Adobe Experience Platform.
* Access to Journey Optimizer and sufficient permissions as described [here](https://experienceleague.adobe.com/docs/journey-optimizer/using/push/push-config/push-configuration.html). Also you need sufficient permission to the following Journey Optimizer features.
  * Manage campaigns.
* Physical iOS device or simulator for testing.


## Learning objectives

In this lesson, you will

* Create an App Surface in AJO.
* Install & configure the Journey Optimizer tag extension.
* Update your app to register the Journey Optimizer tag extension.
* Validate setup in Assurance.
* Define your own campaign and in-app message experience in Journey Optimizer.
* Send your own in-app message from within the app.

## Setup

>[!TIP]
>
>If you have setup your environment already as part of the [Journey Optimizer push messaging](journey-optimizer-push.md) lesson, you might already have performed some of the steps in this setup section.


### Add an app surface in Data Collection

1. From the [Data Collection interface](https://experience.adobe.com/data-collection/), select **[!UICONTROL App Surfaces]** in the left-hand panel.
1. To create a configuration, select **[!UICONTROL Create App Surface]**.
![app surface home](assets/push-app-surface.png)
1. Enter a **[!UICONTROL Name]** for the configuration, for example `Luma App Tutorial`  .
1. From **[!UICONTROL Mobile Application Configuration]**, select **[!UICONTROL Apple iOS]**.
1. Enter the mobile app Bundle Id in the **[!UICONTROL App ID (iOS Bundle ID)]** field. For example,  `com.adobe.luma.tutorial.swiftui`. 
1. Select **[!UICONTROL Save]**.

   ![app surface configuration](assets/push-app-surface-config-inapp.png)

### Update datastream configuration

To ensure data send from your mobile app to the Edge Network is forwarded to Journey Optimizer, update your Experience Edge configuration.



1. In the Data Collection UI, select **[!UICONTROL Datastreams]**, and select your datastream, for example **[!DNL Luma Mobile App]**.
1. Select ![More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_MoreSmallList_18_N.svg) for **[!UICONTROL Experience Platform]** and select ![Edit](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) **[!UICONTROL Edit]** from the context menu.
1. In the **[!UICONTROL Datastreams]** > ![Folder](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) >  **[!UICONTROL Adobe Experience Platform]** screen, ensure **[!UICONTROL Adobe Journey Optimizer]** is selected. See [Adobe Experience Platform settings](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html?lang=en#aep) for more information.
1. To save your datastream configuration, select **[!UICONTROL Save]**.


   ![AEP datastream configuration](assets/datastream-aep-configuration.png)


### Install Journey Optimizer tags extension

For your app to work with Journey Optimizer, you must update your tag property.

1. Navigate to **[!UICONTROL Tags]** > **[!UICONTROL Extensions]** > **[!UICONTROL Catalog]**. 
1. Open your property, for example **[!DNL Luma Mobile App Tutorial]**.
1. Select **[!UICONTROL Catalog]**.
1. Search for the **[!UICONTROL Adobe Journey Optimizer]** extension.
1. Install the extension.
1. In the **[!UICONTROL Install Extension]** dialog
   1. Select an environment, for example **[!UICONTROL Development]**.
   1. Select the **[!UICONTROL AJO Push Tracking Experience Event Dataset]** dataset from the **[!UICONTROL Event Dataset]** list.
   1. Select **[!UICONTROL Save to Library and Build]**.
       ![AJO extension settings](assets/push-tags-ajo.png)

>[!NOTE]
>
>If you don't see `AJO Push Tracking Experience Event Dataset` as an option, contact customer care.
>

### Implement Journey Optimizer in the app

As discussed in previous lessons, installing a mobile tag extension only provides the configuration. Next you must install and register the Messaging SDK. If these steps aren't clear, review the [Install SDKs](install-sdks.md) section.

>[!NOTE]
>
>If you completed the [Install SDKs](install-sdks.md) section, then the SDK is already installed and you can skip this step.
>

1. In Xcode, ensure that [AEP Messaging](https://github.com/adobe/aepsdk-messaging-ios) is added to the list of packages in Package Dependencies. See [Swift Package Manager](install-sdks.md#swift-package-manager).
1. Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!UICONTROL AppDelegate]** in the Xcode Project navigator.
1. Ensure `AEPMessaging` is part of your list of imports.

    `import AEPMessaging`

1. Ensure `Messaging.self` is part of the array of extensions that you are registering.

    ```swift
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
    ```


## Validate setup with Assurance

1. Review the [setup instructions](assurance.md#connecting-to-a-session) section to connect your simulator or device to Assurance.
1. In the Assurance UI, select **[!UICONTROL Configure]**.
    ![configure click](assets/push-validate-config.png)
1. Select the ![Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) button next to **[!UICONTROL In-App Messaging]**.
1. Select **[!UICONTROL Save]**.
    ![save](assets/assurance-in-app-config.png)
1. Select **[!UICONTROL In-App Messaging]** from the left navigation.
1. Select the **[!UICONTROL Validation]** tab. Confirm that you aren't getting any errors.
   
   ![In-App Validation](assets/assurance-in-app-validate.png)


## Create your own in-app message

To create your own in-app message, you must define a campaign in Journey Optimizer that triggers an in-app message based on events that occur. These events can be:

* data sent to Adobe Experience Platform,
* core tracking events, like action, or state or collection of PII data, through the Mobile Core generic APIs,
* application lifecycle events, such as launch, install, upgrade, close, or crash,
* geolocation events, like entering or exiting a point of interest.

In this tutorial, you are going to use the Mobile Core generic and extension-independent APIs (see [Mobile Core generic APIs](https://developer.adobe.com/client-sdks/documentation/mobile-core/#mobile-core-generic-apis)) to facilitate the event tracking of user screens, actions, and PII data. Events generated by these APIs are published to the SDK event hub and are available for use by extensions. The SDK event hub provides the core data structure tied to all Mobile Platform SDK extensions, maintaining a list of registered extensions and internal modules, a list of registered event listeners, and a shared state database.

The SDK event hub publishes and receives event data from registered extensions to simplify integrations with Adobe and third-party solutions. For instance, when the Optimize extension is installed, all requests and interactions with the Journey Optimizer - Decision Management offer engine are handled by the event hub. 

1. In the Journey Optimizer UI, select **[!UICONTROL Campaigns]** from the left rail.
1. Select **[!UICONTROL Create Campaign]**.
1. In the **[!UICONTROL Create Campaign]** screen: 
   1. Select **[!UICONTROL In-app message]** and select an app surface from the **[!UICONTROL App surface]** list, for example **[!DNL Luma Mobile App]**.
   1. Select **[!UICONTROL Create]**
      ![Campaign Properties](assets/ajo-campaign-properties.png)
1. In the Campaign definition screen, at **[!UICONTROL Properties]**, enter a **[!UICONTROL Name]** for the campaign, for example `Luma - In-App Messaging Campaign`, and a **[!UICONTROL Description]**, for example `In-app messaging campaign for Luma app`.
   ![Campaign name](assets/ajo-campaign-properties-name.png)
1. Scroll down to **[!UICONTROL Action]**, and select **[!UICONTROL Edit Content]**.
1. In the **[!UICONTROL In-App Message]** screen:
   1. Select **[!UICONTROL Modal]** as the **[!UICONTROL Message Layout]**.
   2. Enter `https://luma.enablementadobe.com/content/dam/luma/en/logos/Luma_Logo.png` for the **[!UICONTROL Media URL]**.
   3. Enter a **[!UICONTROL Header]**, for example `Welcome to this Luma In-App Message` and enter a **[!UICONTROL Body]**, for example `Triggered by pushing that button in the app...`.
   4. Enter **[!UICONTROL Dismiss]** as the **[!UICONTROL Button #1 text (primary)]**.
   5. Note how the preview is updated.
   6. Select **[!UICONTROL Review to activate]**.
      ![In-app editor](assets/ajo-in-app-editor.png)
1. In the **[!UICONTROL Review to activate (Luma - In-App Messaging Campaign)]** screen, select ![Edit](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) in the **[!UICONTROL Schedule]** tile.
   ![Review schedule select Schedule](assets/ajo-review-select-schedule.png)
1. Back in the **[!DNL Luma - In-App Messaging Campaign]** screen, select ![Edit](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) **[!UICONTROL Edit triggers]**.
1. In the **[!UICONTROL In-app message trigger]** dialog, you configure the details of the track action that triggers the in-app message:
   1. To remove **[!UICONTROL Application launch event]**, select ![Close](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Close_18_N.svg) .
   1. Use ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Add condition]** repeatedly to build the following logic for **[!UICONTROL Show message if]**.
   1. Click **[!UICONTROL Done]**.
      ![Trigger logic](assets/ajo-trigger-logic.png)
    
   You have defined a track action, where the **[!UICONTROL Action]** equals `in-app` and the **[!UICONTROL Context data]** with the action is a key value pair of `"showMessage" : "true"`.

1. Back in the **[!DNL Luma - In-App Messaging Campaign]** screen, select **[!UICONTROL Review to activate]**.
1. In the **[!UICONTROL Review to activate (Luma - In-App Messaging Campaign)]** screen, select **[!UICONTROL Activate]**.
1. You see your **[!DNL Luma - In-App Messaging Campaign]** with status **[!UICONTROL Live]** in the **[!UICONTROL Campaigns]** list.
   ![Campaign list](assets/ajo-campaign-list.png)


## Trigger the in-app message

You have all the ingredients in place to send an in-app message. What remains is how to trigger this in-app message in your app.

1. Go to **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** in the Xcode Project navigator. Find the `func sendTrackAction(action: String, data: [String: Any]?)` function, and add the following code, which calls the [`MobileCore.track`](https://developer.adobe.com/client-sdks/documentation/mobile-core/api-reference/#trackaction) function, based on the parameters `action` and `data`.

    
    ```swift
    // Send trackAction event
    MobileCore.track(action: action, data: data)
    ```  

1. Go to **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL ConfigView]** in the Xcode Project Navigator. Find the code for the In-App Message button and add the following code:

    ```swift
    // Setting parameters and calling function to send in-app message
    Task {
        MobileSDK.shared.sendTrackAction(action: "in-app", data: ["showMessage": "true"])
    }
    ```

## Validate using your app

1. Rebuild and run the app in the simulator or on a physical device from Xcode, using ![Play](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Play_18_N.svg).

1. Go to the **[!UICONTROL Settings]** tab.

1. Tap **[!UICONTROL In-App Message]**. You see the in-app message appear in your app.

   <img src="assets/ajo-in-app-message.png" width=300/>


## Validate implementation in Assurance

You can validate your in-app messages in the Assurance UI.
 
1. Review the [setup instructions](assurance.md#connecting-to-a-session) section to connect your simulator or device to Assurance.
1. Select **[!UICONTROL In-App Messaging]**.
1. Select **[!UICONTROL Event List]**.
1. Select a **[!UICONTROL Display message]** entry.
1. Inspect the raw event, especially the `html`, which contains the complete layout and content of the in-app message.
    ![Assurance In-App Message](assets/assurance-in-app-display-message.png)
   

## Next steps

You should now have all the tools to start adding in-app messages, where relevant and applicable. For example, promoting products based on specific interactions you are tracking in your app.

>[!SUCCESS]
>
>You have enabled the app for in-app messaging and added an in-app messaging campaign using Journey Optimizer and the Journey Optimizer extension for the Experience Platform Mobile SDK.
>
>Thank you for investing your time in learning about Adobe Experience Platform Mobile SDK. If you have questions, want to share general feedback, or have suggestions on future content, share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Next: **[Create and display offers](journey-optimizer-offers.md)**
