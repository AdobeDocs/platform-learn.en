---
title: Implement Adobe Experience Cloud in mobile apps tutorial
description: Learn how to implement the Adobe Experience Cloud mobile applications. This tutorial guides you through an implementation of Experience Cloud applications in a sample Swift or Android app.
recommendations: noDisplay,catalog
last-substantial-update: 2023-11-29T00:00:00.000Z
exl-id: daff4214-d515-4fad-a224-f7589b685b55
TQID: https://experienceleague.adobe.com/FtRtGFh6VmUM2LRD6RBNWdTsTv54bokfVGpj4cuW674
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
    internal-label: Journey Optimizer
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
    internal-label: Acrobat Sign
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
    internal-label: Target
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
  - id: e98b7246-966c-4318-9e95-cad2f7a17dc7
    internal-label: Customer Journey Analytics
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
  - id: f002a92a-b99f-47a4-90c8-65e0e415bc7a
    internal-label: Pass
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
    internal-label: Real-Time Customer Data Platform
feature_v2:
  - id: b3538224-471e-4c63-a444-9b19d89ae29c
    internal-label: Activities
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
    internal-label: Implementation
  - id: d556b755-390a-43f0-be32-a08cf6236126
    internal-label: Configuration
  - id: d833d0ef-8ed5-4cff-a5e7-9f12abd02a31
    internal-label: SDKs
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
  - id: ca3d6bf4-a4af-4944-936b-8de1eb09f149
    internal-label: Datastreams
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
    internal-label: Places
  - id: d9830f6f-ceb6-4faa-9744-f281fe4439f9
    internal-label: Tags
  - id: de9975b2-c43a-4287-9698-4f4cad92b83f
    internal-label: Schemas
  - id: e0c8953a-a203-4291-bef3-3560160d3041
    internal-label: Get started
  - id: f12fb58f-577d-4dbe-85f9-c8194b075f20
    internal-label: Cloud Mobile
  - id: f5efb499-54f9-432b-ac5c-599dbac103af
    internal-label: Data management
  - id: f6ff4d13-7b5c-4533-8556-95e76673d4cb
    internal-label: Properties
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: b23e006f-0a29-4f1d-8fd0-77aa56f3d12b
    internal-label: Data modeling
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
    internal-label: Data management
---
# Implement Adobe Experience Cloud in mobile apps tutorial

Learn how to implement Adobe Experience Cloud applications in your mobile app using the Adobe Experience Platform Mobile SDK.

Experience Platform Mobile SDK is a client-side SDK that allows customers of Adobe Experience Cloud to interact with both Adobe applications and third-party services through the Adobe Experience Platform Edge Network. See the [Adobe Experience Platform Mobile SDK documentation](https://developer.adobe.com/client-sdks/home/) for more detailed information.

![Architecture](assets/architecture.png){zoomable="yes"}


This tutorial guides you through the implementation of the Platform Mobile SDK in a sample app called Luma. The Luma app has functionality that lets you build a realistic implementation. After you have completed this tutorial, you should be ready to start implementing all of your marketing solutions through Experience Platform Mobile SDK in your own mobile apps.

The lessons are designed for:

* iOS, using the Swift programming language and the SwiftUI framework.
* Android, using the Kotlin and Java programming language and the JetPack Compose framework.

After completing this tutorial, you will be able to:

* Create a schema using standard and custom field groups.
* Set up a datastream.
* Configure a mobile tag property.
* Set up an Experience Platform dataset (optional).
* Install and implement tag extensions in an app.
* Correctly pass Experience Cloud parameters to a [webview](web-views.md).
* Validate the implementation using [Adobe Experience Platform Assurance](assurance.md).
* Add the following Adobe Experience Cloud applications or extensions:
  * [Adobe Experience Platform Edge (XDM)](events.md)
  * [Lifecycle data collection](lifecycle-data.md)
  * [Consent](consent.md)
  * [Identity](identity.md)
  * [Profile](profile.md)
  * [Places](places.md)
  * [Analytics](analytics.md)
  * [Experience Platform](platform.md)
  * [Push messaging with Journey Optimizer](journey-optimizer-push.md)
  * [In-app messaging with Journey Optimizer](journey-optimizer-inapp.md)
  * [Decision management with Journey Optimizer](journey-optimizer-offers.md)
  * [Target](target.md)


>[!NOTE]
>
>A similar multi-solution tutorial is available for [Web SDK](../tutorial-web-sdk/overview.md).

## Permissions

In these lessons, it is assumed that you have an Adobe Id and the required user-level permissions to complete the exercises. If not, you should reach out to your Adobe Administrator to request access.

* In Data Collection, you must have:
  * **[!UICONTROL Platforms]**&mdash;permission item **[!UICONTROL Mobile]**
  * **[!UICONTROL Property Rights]**&mdash;permission items to **[!UICONTROL Develop]**, **[!UICONTROL Approve]**, **[!UICONTROL Publish]**, **[!UICONTROL Manage Extensions]**, and **[!UICONTROL Manage Environments]**.
  * **[!UICONTROL Company Rights]**&mdash;permission items to **[!UICONTROL Manage Properties]**
  
    For more information on tag permissions, see [User permissions for tags](https://experienceleague.adobe.com/en/docs/experience-platform/tags/admin/user-permissions){target="_blank"} in the product documentation.
* In Experience Platform, you must have:
  * **[!UICONTROL Data Modeling]**&mdash;permission items to manage and view schemas.
  * **[!UICONTROL Identity Management]**&mdash;permission items to manage and view identity namespaces.
  * **[!UICONTROL Data Collection]**&mdash;permission items to manage and view datastreams.

  * If you are the customer of a Platform-based application like Real-Time CDP, Journey Optimizer, or Customer Journey Analytics, and plan to do the related lessons you should also have:
    * **[!UICONTROL Data Management]**&mdash;permission items to manage and view datasets.
    * A development **sandbox** which you can use for this tutorial.
  
  * For the Journey Optimizer lessons, you need permissions to configure the **push notification service** and to create an **app surface**, a **journey**, a **message**, and **message presets**. Additionally, for Decision Management, you need the proper permissions to **manage offers** and **decisions**, as described in [Permission levels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/access-control/high-low-permissions).

* For Adobe Analytics, you must know which **report suites** you can use to complete this tutorial.

* For Adobe Target, you must have permission to create and activate activities.


>[!NOTE]
>
>As part of this tutorial, you create schemas, datasets, identities, and so on. If multiple people are going through this tutorial in a single sandbox, consider appending or prepending an identification as part of your naming conventions when creating these objects. For example, add ` - <your name or initials>` to the name of the object you are instructed to create.

## Version history

* September 9, 2025: 
  * Android version of the app with accompanying instructions.
  * Updates for changes in app surface and campaign functionality in Journey Optimizer.
* Nov. 29, 2023: Major overhaul with new sample app and new lessons for in-app messaging, decision management, and Adobe Target.
* Mar. 9, 2022: First publish

## Download the Luma app

>[!BEGINTABS]

>[!TAB iOS]

Two versions of the sample app are available for download. Both versions can be downloaded / cloned from [GitHub](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App). You find two folders:

1. [Start](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"}: a project without code or with placeholder code for most of the Experience Platform Mobile SDK code you need to use to complete the hands-on exercises in this tutorial.
1. [Finish](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"}: a version with the full implementation for reference.

You use iOS as the platform, [!DNL Swift] as the programming language, [!DNL SwiftUI] as the UI framework and [!DNL Xcode] as the integrated development environment (IDE). However, many of the implementation concepts explained are similar for other development platforms. Many have already successfully completed this tutorial with little to no previous iOS and Swift(UI) development experience. You do not need to be an expert to complete the lessons, but you get more out of the lessons if you can comfortably read and understand code.

You can download the final productized version of the app from the App Store.

[![Download](assets/download-app.svg)](https://apps.apple.com/us/app/luma-app/id6466588487)

>[!TAB Android]

Two versions of the sample app are available for download. Both versions can be downloaded or cloned from [GitHub](https://github.com/adobe/Luma-Android). You find two folders:

1. [Start](https://github.com/adobe/Luma-Android){target="_blank"}: a project without code or with placeholder code for most of the Experience Platform Mobile SDK code you need to use to complete the hands-on exercises in this tutorial.
1. [Finish](https://github.com/adobe/Luma-Android){target="_blank"}: a version with the full implementation for reference.

You use Android as the platform, [!DNL Kotlin]+[!DNL Java] as the programming language, [!DNL JetPack Compose] as the UI framework and [!DNL Android Studio] as the integrated development environment (IDE). However, many of the implementation concepts explained are similar for other development platforms. Many have already successfully completed this tutorial with little to no previous Android / Kotlin+Java / JetPack Compose experience. You do not need to be an expert to complete the lessons, but you get more out of the lessons if you can comfortably read and understand code.

If you prefer, you can [join a test for a productized version](https://play.google.com/apps/internaltest/4700642199234438150) of the app from Google Play.


>[!ENDTABS]

Let's get started!

>[!SUCCESS]
>
>Thank you for investing your time in learning about Adobe Experience Platform Mobile SDK. If you have questions, want to share general feedback, or have suggestions on future content, share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Next: **[Create an XDM schema](create-schema.md)**
