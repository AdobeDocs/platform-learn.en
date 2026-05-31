---
title: Collect lifecycle data with Platform Mobile SDK
description: Learn how to collect lifecycle data in a mobile app.
jira: KT-14630
exl-id: 75b2dbaa-2f84-4b95-83f6-2f38a4f1d438
TQID: https://experienceleague.adobe.com/V-BNVuYq5G07Fp-W3uRAvn6lqg3VXDBXgBpNvWBn5JI
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: acc16deb-1d7f-4ec9-9ce3-6cdf355afde6
    internal-label: XDM
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: c1f1ac67-ccab-4be9-a93a-b7faba1192c4
    internal-label: Assurance
  - id: d9830f6f-ceb6-4faa-9744-f281fe4439f9
    internal-label: Tags
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# Collect lifecycle data

Learn how to collect lifecycle data in a mobile app.

The Adobe Experience Platform Mobile SDK Lifecycle extension enables the collection of lifecycle data from your mobile app. The Adobe Experience Platform Edge Network extension sends this lifecycle data to the Platform Edge Network where it is then  forwarded to other applications and services according to your datastream configuration. Learn more about the [Lifecycle extension](https://developer.adobe.com/client-sdks/documentation/lifecycle-for-edge-network/) in the product documentation.


## Prerequisites

* Successfully built and run app with SDKs installed and configured. As part of this lesson, you started lifecycle monitoring already. See [Install SDKs - Update AppDelegate](install-sdks.md#update-appdelegate) to review.
* Registered the Assurance extension as described in the [previous lesson](install-sdks.md).

## Learning objectives

In this lesson, you will:

<!--
* Add lifecycle field group to the schema.
* 
-->
* Enable accurate lifecycle metrics by correctly starting/pausing as the app moves between foreground and background.
* Send data from the app to Platform Edge Network.
* Validate in Assurance.

<!--
## Add lifecycle field group to schema

The Consumer Experience Event field group you added in the [previous lesson](create-schema.md) already contains the lifecycle fields, so you can skip this step. If you don't use Consumer Experience Event field group in your own app, you can add the lifecycle fields by doing the following:

1. Navigate to the schema interface as described in the [previous lesson](create-schema.md).
1. Open the **Luma Mobile App Event Schema** schema and select **[!UICONTROL Add]** next to Field groups.
    ![select add](assets/lifecycle-add.png){zoomable="yes"}
1. In the search bar, enter "lifecycle".
1. Select the checkbox next to **[!UICONTROL AEP Mobile Lifecycle Details]**.
1. Select **[!UICONTROL Add field groups]**.
    ![add field group](assets/lifecycle-lifecycle-field-group.png){zoomable="yes"}
1. Select **[!UICONTROL Save]**.
    ![save](assets/lifecycle-lifecycle-save.png){zoomable="yes"}
-->

## Implementation changes

Now, you can update your project to register the lifecycle events.

>[!BEGINTABS]

>[!TAB iOS]

1. Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!UICONTROL SceneDelegate]** in the Xcode Project navigator.

1. When launched, if your app is resuming from a background state, iOS might call your `sceneWillEnterForeground:` delegate method and this method is where you want to trigger a lifecycle start event. Add this code to `func sceneWillEnterForeground(_ scene: UIScene)`:
 
   ```swift
   // When in foreground start lifecycle data collection
   MobileCore.lifecycleStart(additionalContextData: nil)
   ```

1. When the app enters the background, you want to pause lifecycle data collection from your app's `sceneDidEnterBackground:` delegate method. Add this code to  `func sceneDidEnterBackground(_ scene: UIScene)`:

   ```swift
   // When in background pause lifecycle data collection
   MobileCore.lifecyclePause()
   ```

>[!TAB Android]

1. Navigate to **[!UICONTROL app]** > **[!UICONTROL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL LumaApplication]** in the Android Studio navigator.

1. When launched, if your app is resuming from a background state, Android might call your override `fun onActivityResumed function` and this function is where you want to trigger a lifecycle start event. Add this code to `override fun onActivityResumed(activity: Activity)`:
 
   ```kotlin
   // When in foreground start lifecycle data collection
   MobileCore.lifecycleStart(null)
   ```

1. When the app enters the background, you want to pause lifecycle data collection from your app's `override fun onActivityPaused` function. Add this code to  `override fun onActivityPaused(activity: Activity)`:

   ```kotlin
   // When in background pause lifecycle data collection
   MobileCore.lifecyclePause()
   ```

>[!ENDTABS]


## Validate with Assurance

1. Review the [setup instructions](assurance.md#connecting-to-a-session) section to connect your simulator or device to Assurance.
1. Send the app to the background. Check for **[!UICONTROL LifecyclePause]** events in the Assurance UI.
1. Bring the app to the foreground. Check for **[!UICONTROL LifecycleResume]** events in the Assurance UI.
![validate lifecycle](assets/lifecycle-lifecycle-assurance.png){zoomable="yes"}


## Forward data to Platform Edge Network

The previous exercise dispatches the foreground and background events to Adobe Experience Platform Mobile SDK. To forward these events to Platform Edge Network:

1. Select **[!UICONTROL Rules]** in the Tags property.
   ![Create Rule](assets/rule-create.png){zoomable="yes"}
1. Select **[!UICONTROL Initial Build]** as the library to use.
1. Select **[!UICONTROL Create New Rule]**.
   ![Create New Rule](assets/rules-create-new.png){zoomable="yes"}
1. In the **[!UICONTROL Create Rule]** screen, enter `Application Status` for **[!UICONTROL Name]**.
1. Select ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Add]** below **[!UICONTROL EVENTS]**.
   ![Create Rule dialog](assets/rule-create-name.png){zoomable="yes"} 
1. In the **[!UICONTROL Event Configuration]** step:
   1. Select **[!UICONTROL Mobile Core]** as the **[!UICONTROL Extension]**.
   1. Select **[!UICONTROL Foreground]** as the **[!UICONTROL Event Type]**.
   1. Select **[!UICONTROL Keep Changes]**.
      ![Rule Event Configuration](assets/rule-event-configuration.png){zoomable="yes"}
1. Back in the **[!UICONTROL Create Rule]** screen, select ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Add]** next to **[!UICONTROL Mobile Core - Foreground]**.
   ![Next event configuration](assets/rule-event-configuration-next.png){zoomable="yes"}
1. In the **[!UICONTROL Event Configuration]** step:
   1. Select **[!UICONTROL Mobile Core]** as the **[!UICONTROL Extension]**.
   1. Select **[!UICONTROL Background]** as the **[!UICONTROL Event Type]**.
   1. Select **[!UICONTROL Keep Changes]**.
      ![Rule Event Configuration](assets/rule-event-configuration-background.png){zoomable="yes"}
1. Back in the **[!UICONTROL Create Rule]** screen, select ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Add]** underneath **[!UICONTROL ACTIONS]**.
   
   ![Rule Add Action](assets/rule-action-button.png){zoomable="yes"}

1. In the **[!UICONTROL Action Configuration]** step:
   1. Select **[!UICONTROL Adobe Experience Edge Network]** as the **[!UICONTROL Extension]**.
   1. Select **[!UICONTROL Forward event to Edge Network]** as the **[!UICONTROL Action Type]**.
   1. Select **[!UICONTROL Keep Changes]**.
      ![Rule Action Configuration](assets/rule-action-configuration.png){zoomable="yes"}
1. Select **[!UICONTROL Save to Library]**.
   ![Rule - Save to Library](assets/rule-save-to-library.png){zoomable="yes"}
1. Select **[!UICONTROL Build]** to rebuild the library.
   ![Rule - Build](assets/rule-build.png){zoomable="yes"}

Once you have successfully built the property, the events are sent to Platform Edge Network, and the events are forwarded to other applications and services according to your datastream configuration.

You should see **[!UICONTROL Application Close (Background)]** and **[!UICONTROL Application Launch (Foreground)]** events containing XDM data in Assurance.

![validate lifecycle sent to Platform Edge](assets/lifecycle-edge-assurance.png){zoomable="yes"}

>[!SUCCESS]
>
>You have now set up your app to send application state (foreground, background) events to the Adobe Experience Platform Edge Network and all services you have defined in your datastream.
>
> Thank you for investing your time in learning about Adobe Experience Platform Mobile SDK. If you have questions, want to share general feedback, or have suggestions on future content, share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Next: **[Track event data](events.md)**
