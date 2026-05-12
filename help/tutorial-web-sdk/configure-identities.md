---
title: Configure an identity namespace
description: Learn how to configure identity namespaces to use with Adobe Experience Platform Web SDK. This lesson is part of the Implement Adobe Experience Cloud with Web SDK tutorial.
feature: Web SDK,Identities
jira: KT-15400
exl-id: 7719dff4-6b30-4fa0-acae-7491c3208f15
TQID: https://experienceleague.adobe.com/Uy6tmS-z6-JTiqHwT0bQMgM-sw7dEdIMmri955fL9p8
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
    internal-label: Journey Optimizer
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: df80eeb1-8d72-467e-b0df-9d51c7d3a0a1
    internal-label: Audience Manager
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
  - id: a8b0238e-1d43-4679-a3b4-5ba1bad83baa
    internal-label: Implementation
  - id: b82b475d-1e7d-46c6-9172-1f9c73004b11
    internal-label: Integrations
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
    internal-label: Implementation
  - id: d556b755-390a-43f0-be32-a08cf6236126
    internal-label: Configuration
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
  - id: e75a4a9c-d354-4ca4-9b02-1afeca73fa5e
    internal-label: Integrations
  - id: eb9732ab-8232-4b21-bc4c-89de86dbe4d7
    internal-label: Integrations
  - id: ed0d8d0e-04b9-4326-be72-a0fbca265377
    internal-label: Integrations
  - id: f7c7de77-382f-4f48-8b36-61a170f06d3d
    internal-label: Integrations
  - id: fc7979f3-56c3-43ca-9784-f1ea3dc69c4b
    internal-label: Integrations
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
  - id: fe96aceb-8194-4a8a-a6b0-75302d02804d
    internal-label: Integrations
subfeature_v2:
  - id: abc02dd6-664f-446a-9aaa-675bc0f2fe4a
    internal-label: Sources
  - id: acc16deb-1d7f-4ec9-9ce3-6cdf355afde6
    internal-label: XDM
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: d9830f6f-ceb6-4faa-9744-f281fe4439f9
    internal-label: Tags
  - id: de9975b2-c43a-4287-9698-4f4cad92b83f
    internal-label: Schemas
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
  - id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
    internal-label: Customer profiles
---
# Configure an identity namespace

Learn how to configure identity namespaces to use with Adobe Experience Platform Web SDK. 

The [Adobe Experience Cloud Identity Service](https://experienceleague.adobe.com/en/docs/id-service/using/home) sets a common visitor ID (the ECID) across SDK-based Adobe applications to power Experience Cloud capabilities such as audience-sharing between applications. You can also send your own customer IDs to the Service to enable cross-device targeting and integrations with other systems, such as your Customer Relationship Management (CRM) system.

The [Adobe Experience Platform Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) (yes, there are two!) uses the ECIDs and customer IDs to generate identity graphs, allowing you to merge attributes and behaviors into Real-Time Customer Profiles.


>[!NOTE]
>
>A custom identity namespace is _not required_ to implement Adobe Analytics, Adobe Target, or Adobe Audience Manager with Web SDK (authenticated identities can be passed in the `data` object instead of the `xdm` object as you will see later). Identity namespaces are required for Platform-native applications like Journey Optimizer, Real-Time Customer Data Platform, Customer Journey Analytics. While you may decide not to use an identity namespace in your own implementation, you are expected to do so as part of this tutorial.

## Learning objectives

At the end of this lesson, you will be able to:

* Understand identity namespaces
* Create a custom identity namespace to capture an internal CRM Id


## Prerequisites

You must have already completed the previous lessons:

* [Configure Schemas](configure-schemas.md)

>[!IMPORTANT]
>
>The [Experience Cloud ID Extension](https://exchange.adobe.com/apps/ec/100160/adobe-experience-cloud-id-launch-extension) is not needed when implementing Adobe Experience Platform Web SDK, as the Web SDK JavaScript library contains the Visitor ID service functionality.
>
> If your website is already using the Experience Cloud ID Service on your website&mdash;either through Visitor API or the Experience Cloud ID Service tag extension&mdash;and you would like to continue using it while migrating to Adobe Experience Platform Web SDK, you must use the latest version of Visitor API or the Experience Cloud ID Service tag extension. See [ID Migration](https://experienceleague.adobe.com/en/docs/experience-platform/edge/identity/overview) for more information.

## Create an identity namespace

In this exercise, you create an identity namespace for Luma's custom identity field, `lumaCrmId`. Identity namespaces play a critical role in building real-time customer profiles, as two matching values in the same namespace allow two data sources to form an identity graph.

Before you begin the exercises, watch this short video to learn more about identity in Adobe Experience Platform:

>[!VIDEO](https://video.tv.adobe.com/v/27841?learn=on&enablevpops)

Now, create a namespace for the Luma CRM ID:

1. Open the [Data Collection interface](https://experience.adobe.com/data-collection/){target="_blank"}
1. Select the sandbox that you are using for the tutorial

   >[!NOTE]
   >
   >If you are the customer of a Platform-based application like Real-Time CDP or Journey Optimizer, we recommend using a development sandbox for this tutorial. If you are not, use the **[!UICONTROL Prod]** sandbox.
   
1. Select **[!UICONTROL Identities]** in the left navigation
1. Select **[!UICONTROL Namespaces]**

   A list of identity namespaces appears in the main interface of the page, showing their names, identity symbols, last updated date, and whether they are standard or custom namespaces. The right rail contains information on [!UICONTROL Identity graph strength].

1. Select **[!UICONTROL Create identity namespace]**

   ![View identities](assets/configure-identities-screen.png)

1. Provide details as follows and select **[!UICONTROL Create]**.
   
   | Field         |  Value    |
   |---------------|-----------|
   | Display name  | Luma CRM ID   |
   | Identity symbol| lumaCrmId    |
   | Type           | Individual cross-device ID |


   ![Create Namespaces](assets/identities-create-namespace.png)


   The new identity namespace should appear in the **[!UICONTROL Namespaces]** screen.

   ![Created Namespace](assets/configure-identities-namespace-lumaCrmId.png)


>[!NOTE]
>
> In the [Capture identities](create-identities.md) lesson, you will learn how to use this namespace when sending identities to Platform Edge Network. 

Now that identities are in place, the datastream can be configured.

>[!NOTE]
>
>Thank you for investing your time in learning about Adobe Experience Platform Web SDK. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/adobe-experience-platform-18/tutorial-discussion-implement-adobe-experience-cloud-with-web-sdk-tutorial-248848)
