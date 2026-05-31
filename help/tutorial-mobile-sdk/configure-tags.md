---
title: Configure a tag property for Platform Mobile SDK implementations
description: Learn how to configure a tag property in the [!UICONTROL Data Collection] interface.
feature: Mobile SDK,Tags
jira: KT-14626
exl-id: 0c4b00cc-34e3-4d08-945e-3fd2bc1b6ccf
TQID: https://experienceleague.adobe.com/5PadqhaPYjbdIdx1gtQFXX-6VbTfPCwVKworOAWrGMg
product_v2:
  - id: a829a185-511f-4bf8-8dcf-9e684f8011cf
    internal-label: Advertising
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
subfeature_v2:
  - id: abc02dd6-664f-446a-9aaa-675bc0f2fe4a
    internal-label: Sources
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: c1f1ac67-ccab-4be9-a93a-b7faba1192c4
    internal-label: Assurance
  - id: c77ba355-6681-41fe-b719-563d3f507fdb
    internal-label: Mobile SDK
  - id: ca3d6bf4-a4af-4944-936b-8de1eb09f149
    internal-label: Datastreams
  - id: d9830f6f-ceb6-4faa-9744-f281fe4439f9
    internal-label: Tags
  - id: df312454-73c4-43f6-a90e-18f5043f074c
    internal-label: Tags
  - id: f9a2105e-7a47-4e85-9193-31a519a2cb83
    internal-label: Data elements
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
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
    internal-label: Customer experience
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
---
# Configure a tag property

Learn how to configure a tag property in the [!UICONTROL Data Collection] interface.

Tags in Adobe Experience Platform are the next generation of tag management capabilities from Adobe. Tags give customers a simple way to deploy and manage analytics, marketing, and advertising tags necessary to power relevant customer experiences. Learn more about [Tags](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home) in the product documentation.

## Prerequisites

To complete the lesson, you must have permission to create a tag property. It's also helpful to have a baseline understanding of tags. 

>[!NOTE]
>
> Platform Launch (Client Side) is now [Tags](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)

## Learning objectives

In this lesson, you will:

* Install and configure the mobile tag extensions.
* Generate the SDK install instructions.

## Initial setup

1. Create a new mobile tag property in the Data Collection Interface:
    1. Select **[!UICONTROL Tags]** in the left navigation.
    1. Select **[!UICONTROL New Property]**
       ![create a tag property](assets/tags-new-property.png){zoomable="yes"}.
    1. For the **[!UICONTROL Name]**, enter `Luma Mobile App Tutorial`.
    1. For the **[!UICONTROL Platform]**, select **[!UICONTROL Mobile]**.
    1. Select  **[!UICONTROL Save]**. 
     
        ![configure the tag property](assets/tags-property-config.png){zoomable="yes"}

        >[!NOTE]
        >
        > Default consent settings for the edge-based Mobile SDK implementations, such as the one you are doing in this lesson, come from the [!UICONTROL Consent extension] and not the [!UICONTROL Privacy] setting in the tag property configuration. You add and configure the Consent extension later in this lesson. For more info, see [the documentation](https://developer.adobe.com/client-sdks/edge/consent-for-edge-network/).


1. Open the new property.    
1. Create a library:

    1. Go to **[!UICONTROL Publishing Flow]** in the left navigation.
    1. Select **[!UICONTROL Add Library]**.

        ![Select Add Library](assets/tags-create-library.png){zoomable="yes"}

    1. For the **[!UICONTROL Name]**, enter `Initial Build`.
    1. For the **[!UICONTROL Environment]**, select **[!UICONTROL Development (development)]**.
    1. Select  ![Add button](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Add All Changed Resources]**. 
    1. Select **[!UICONTROL Save and Build to Development]**. 

        ![Build the Library](assets/tags-save-library.png){zoomable="yes"}
        
    1. Finally, select **[!UICONTROL Initial Build]** as your working library from the **[!UICONTROL Select a working library]** menu. 
        ![Select as the working library](assets/tags-working-library.png){zoomable="yes"}
1. Check extensions:

    1. Ensure that **[!UICONTROL Initial Build]** is selected as the default library. 
   
    1. Select **[!UICONTROL Extensions]** in the left rail.

    1. Select the **[!UICONTROL Installed]** tab.
    
       The [!UICONTROL Mobile Core] and [!UICONTROL Profile] extensions should be pre-installed.

       ![Tags installed](assets/tags-installed.png){zoomable="yes"}

## Extension configuration

1. Ensure you are in **[!UICONTROL Extensions]** within your mobile app property.

1. Select **[!UICONTROL Catalog]**.

    ![initial setup](assets/tags-starting.png){zoomable="yes"}

1. Use the ![Search](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Search_18_N.svg) **[!UICONTROL Search]** field the find the **Identity** extension.

    1. Search for `Identity`.

    2. Select the **[!UICONTROL Identity]** extension.

    3. Select **[!UICONTROL Install]**.

       ![Identity Install](assets/tags-identity-install.png){zoomable="yes"}

    This extension does not require any further configuration.

1. Use the ![Search](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Search_18_N.svg) **[!UICONTROL Search]** field to find and install the **AEP Assurance** extension.
    
   This extension does not require any further configuration.

1. Use the ![Search](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Search_18_N.svg) **[!UICONTROL Search]** field to find and install the **Consent** extension. In the configuration screen:

    1. Select **[!UICONTROL Pending]**. In this tutorial, you manage consent further in the application. Learn more about the Consent extension in [the documentation](https://developer.adobe.com/client-sdks/documentation/consent-for-edge-network/).
    1. Select **[!UICONTROL Save to Library]**.
    
       ![consent settings](assets/tags-extension-consent.png){zoomable="yes"}

1. Use the ![Search](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Search_18_N.svg) **[!UICONTROL Search]** field to find and install the **Adobe Experience Platform Edge Network** extension. 
    
    1. In **[!UICONTROL Datastreams]** select the **[!UICONTROL Datastream]** that you created in the [previous step](create-datastream.md) for each of the environments, for example **[!DNL Luma Mobile App]**.

    1. If not already populated, specify the **[!UICONTROL Edge Network domain]** within **[!UICONTROL Domain Configuration]**. The Edge Network domain is the name of your organization, followed by `data.adobedc.net`, for example `techmarketingdemos.data.adobedc.net`.

    1. From the **[!UICONTROL Save to Library]** menu, select **[!UICONTROL Save to Library and Build]**.

       ![edge network settings](assets/tags-extension-edge.png){zoomable="yes"}

Your library is built for the new extensions and configurations. A <span style="color:green">●</span> in the **[!UICONTROL Initial Build]** button indicated a successful build.


## Generate SDK install instructions

Tags provide you with instructions and code snippets to install the Adobe Experience Platform Mobile SDK in your app.

>[!BEGINTABS]

>[!TAB iOS]

1. Select **[!UICONTROL Environments]** from the left rail.

1. Select the **[!UICONTROL Development]** install icon ![Box](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) .

   ![environments home screen](assets/tags-environments.png){zoomable="yes"}

1. In the **[!UICONTROL Mobile Install Instructions]** dialog, select the **[!UICONTROL iOS]** tab.

1. You can copy ![Copy](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) the instructions to set up your project using CocoaPods. CocoaPods are used to manage SDK versions and downloads. To learn more, please review the [CocoaPods documentation](https://cocoapods.org/).
 
   The [install instructions](https://developer.adobe.com/client-sdks/documentation/getting-started/get-the-sdk/) provide you a good starting point for implementation.

   For the remainder of this tutorial, you are **not** using the CocoaPods instructions. Instead, you use the native Swift Package Manager (SPM) based setup.

1. Select the **[!UICONTROL Swift]** tab below **[!UICONTROL Add Initialization Code]**. This block of code shows how to import the required SDKs and register the extensions at launch. This import and registration is covered in more detail in [Install SDKs](install-sdks.md).

1. Copy ![Copy](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) the **[!UICONTROL Environment File ID]** and store it in a place as you need it later. This unique ID points to your development environment. Each environment (Production, Staging, Development) does have its own unique ID value.

   ![install instructions](assets/tags-install-instructions.png){zoomable="yes"}

>[!TAB Android]

1. Select **[!UICONTROL Environments]** from the left rail.
1. Select the **[!UICONTROL Development]** install icon ![Box](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) .

   ![environments home screen](assets/tags-environments.png){zoomable="yes"}

1. In the **[!UICONTROL Mobile Install Instructions]** dialog, select the **[!UICONTROL Android]** tab.
1. You can copy ![Copy](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) the instructions to set up your project using Gradle. Gradle is used to manage SDK versions and downloads. To learn more, please review the [Gradle documentation](https://gradle.org/)
 
   The [install instructions](https://developer.adobe.com/client-sdks/documentation/getting-started/get-the-sdk/) provide you a good starting point for implementation.

1. This block of code shows how to import the required SDKs and register the extensions at launch. This import and registration is covered in more detail in [Install SDKs](install-sdks.md).

1. Copy ![Copy](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) the **[!UICONTROL Environment File ID]** and store it in a place as you need it later. This unique ID points to your development environment. Each environment (Production, Staging, Development) does have its own unique ID value.

   ![install instructions](assets/tags-install-instructions-android.png){zoomable="yes"}

>[!ENDTABS]

>[!NOTE]
>
>The install instructions should be considered a starting point and not definitive documentation. The latest SDK versions and code samples can be found in the official [documentation](https://developer.adobe.com/client-sdks/home/).

## Mobile tags architecture

If you are familiar with the web version of Tags, formerly Launch, it's important to understand the differences on mobile. 

* On the web, a tag property is rendered into JavaScript which is then (usually) hosted in the cloud. That JavaScript file is referenced directly in the website.

* In a mobile tag property, rules and configurations are rendered into JSON files which are hosted in the cloud. The JSON files are downloaded and read by the Mobile Core extension in the mobile app. Extensions are separate SDKs that work together. If you add an extension to your tag property, you must also update the app. If you change an extension setting or create a rule, those changes are reflected in the app once you publish the updated tag library. That flexibility allows you to modify settings (like Adobe Analytics report suite id). Or even change your app's behavior (using data elements and rules, as you see in later lessons) without having to change code in your app and resubmit to the app store.

>[!SUCCESS]
>
>You have now a mobile tag property to use in the remainder of this tutorial.
>
>Thank you for investing your time in learning about Adobe Experience Platform Mobile SDK. If you have questions, want to share general feedback, or have suggestions on future content, share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Next: **[Install SDKs](install-sdks.md)**
