---
title: Configure a datastream for Platform Web SDK
description: Learn how to enable a datastream and configure Experience Cloud solutions. This lesson is part of the Implement Adobe Experience Cloud with Web SDK tutorial.
feature: Web SDK,Datastreams
jira: KT-15399
exl-id: 20f770d1-eb0f-41a9-b451-4069a0a91fc4
TQID: https://experienceleague.adobe.com/ptsTKfn6SLbYSuQJlA9SKuUZUf80jbIstW-h1MAo3k4
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
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
    internal-label: Real-Time Customer Data Platform
feature_v2:
  - id: d556b755-390a-43f0-be32-a08cf6236126
    internal-label: Configuration
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: aff8c1fa-1be7-48bd-92b8-4b12a668ca13
    internal-label: Data prep
  - id: ca3d6bf4-a4af-4944-936b-8de1eb09f149
    internal-label: Datastreams
  - id: d2e8a157-b3b0-4143-9ff3-809bf400be56
    internal-label: Sandboxes
  - id: d9830f6f-ceb6-4faa-9744-f281fe4439f9
    internal-label: Tags
  - id: dc6ebdf7-9a94-43eb-9184-759cfdd0cf1c
    internal-label: Event forwarding
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
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# Configure a datastream

Learn how to configure a datastream for Adobe Experience Platform Web SDK.

[Datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overview) tell Adobe Experience Platform Edge Network where to send data collected by Platform Web SDK. In the datastreams configuration, you enable your Experience Cloud applications, your Experience Platform account, and event forwarding. 


![Web SDK, datastreams, and Edge Network diagram](assets/dc-websdk-datastreams.png)

## Learning objectives

At the end of this lesson, you will be able to:

* Create a datastream
* Get started with datastream overrides

## Prerequisites

Before you configure your datastream, you must have already completed the following lessons:

* [Configure a schema](configure-schemas.md)
* [Configure an identity namespace](configure-identities.md)

## Create a datastream

Now, you can create a datastream to tell Platform Edge Network where to send data collected by Web SDK.

**To create a datastream:**

1. Open the [Data Collection interface](https://experience.adobe.com/data-collection/){target="_blank"}
1. Make sure you are in the correct sandbox 

   >[!NOTE]
   >
   >If you are the customer of a Platform-based application like Real-Time CDP or Journey Optimizer, we recommend using a development sandbox for this tutorial. If you are not, use the **[!UICONTROL Prod]** sandbox.

1. Go to **[!UICONTROL Datastreams]** in the left navigation
1. Select **[!UICONTROL New Datastream]**
1. Enter `Luma Web SDK: Development Environment` as the **[!UICONTROL Name]**. This name is referenced later when you configure the Web SDK extension in your tag property.
1. Select **[!UICONTROL Save]**

   ![Create the datastream](assets/datastream-create-new-datastream.png)

   >[!NOTE]
   >
   >You don't need to select a schema. A schema selection is only required if you are using the [Data Prep for Data Collection](/help/data-collection/edge/data-prep.md) feature.

On the next screen, you are able to add services such as Adobe applications to the datastream, however you will not add any services at this point. You will do so later in the lessons [Set up Experience Platform](setup-experience-platform.md), [Set up Analytics](setup-analytics.md), [Set up Audience Manager](setup-audience-manager.md), [Setup Target](setup-target.md), or [Event Forwarding](setup-event-forwarding.md).

>[!NOTE]
>
>When implementing Platform Web SDK on your own website, you should create three datastreams to map to your three tag environments (development, stage, and production). If you are using Platform Web SDK with Platform-based applications such as Adobe Real-Time Customer Data Platform or Adobe Journey Optimizer, you should be sure to create those datastreams in the appropriate Platform sandboxes.

## Override a datastream

[Datastream overrides](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overrides) allow you to define additional configurations for your datastream and then override your default configuration under certain conditions. 

Datastream configuration override is a two-step process:

1. First, you define datastream overrides in the datastream service configuration. For example, you might define alternate Analytics report suites, Target workspaces, or Platform datasets to use as overrides.
1. Then, you send the overrides to the Edge Network either with a Web SDK send event action, or by a configuration in the Web SDK tag extension.

In the [Set up Adobe Analytics](setup-analytics.md) lesson, you override the report suite for a page using the Platform Web SDK Send Event Action.

You are now ready to install the Platform Web SDK extension in your tag property!

>[!NOTE]
>
>Thank you for investing your time in learning about Adobe Experience Platform Web SDK. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/adobe-experience-platform-18/tutorial-discussion-implement-adobe-experience-cloud-with-web-sdk-tutorial-248848)
