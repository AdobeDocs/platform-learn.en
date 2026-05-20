---
title: Install and configure the Adobe Experience Platform Web SDK tag extension
description: Learn how to install and configure the Platform Web SDK tag extension in the Data Collection interface. This lesson is part of the Implement Adobe Experience Cloud with Web SDK tutorial.
feature: Web SDK, Tags
jira: KT-15404
exl-id: f30a44bb-99d7-476e-873a-b7802a0fe6aa
TQID: https://experienceleague.adobe.com/-c6-3UNo4yJ82YRgGricXJNzHAWhylvLpisQmlPNIqs
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
  - id: a8b0238e-1d43-4679-a3b4-5ba1bad83baa
    internal-label: Implementation
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
    internal-label: Implementation
  - id: d556b755-390a-43f0-be32-a08cf6236126
    internal-label: Configuration
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: acc16deb-1d7f-4ec9-9ce3-6cdf355afde6
    internal-label: XDM
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: ca3d6bf4-a4af-4944-936b-8de1eb09f149
    internal-label: Datastreams
  - id: d9830f6f-ceb6-4faa-9744-f281fe4439f9
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
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# Install Adobe Experience Platform Web SDK tag extension

Learn how to install and configure the Adobe Experience Platform Web SDK tag extension. The easiest way to implement Web SDK is using Adobe's tag manager, tags (formerly known as Launch). The Platform Web SDK tag extension is the _only tag extension_ required to send data to _all Adobe Experience Cloud applications_, including [Analytics](setup-analytics.md), [Target](setup-target.md), [Audience Manager](setup-audience-manager.md), Real-Time Customer Data Platform, and [Journey Optimizer](setup-web-channel.md)!



## Learning objectives

At the end of this lesson, you will be able to:

* Create a tag property in the Data Collection interface
* Install the Platform Web SDK tag extension
* Map your previously created datastream to the extension

## Prerequisites

You must have completed the previous lessons in this tutorial:

* [Configure a datastream](configure-datastream.md)

### Add a tag property

A tag property is a container for all the JavaScript, rules, and other features required to collect details from a web page and send it to various locations.

Create a new tag property for the tutorial:

1. Open the [Data Collection interface](https://experience.adobe.com/data-collection/){target="_blank"}
1. Select **[!UICONTROL Tags]** in the left navigation
1. Select the **[!UICONTROL New Property]** button
    ![Add a new property](assets/websdk-property-addNewProperty.png)
1. As the **[!UICONTROL Name]**, enter `Luma Web SDK Tutorial` (add your name to the end, if multiple people from your company are taking this tutorial)
1. As the **[!UICONTROL Domains]**, enter `enablementadobe.com` (explained later)
1. Select **[!UICONTROL Save]**
    ![Property details](assets/websdk-property-propertyDetails.png)

## Add the Web SDK extension

With your XDM schema, datastream, and tag property now created, you are ready to install the Platform Web SDK extension:

1. Open your new tag property
1. Go to **[!UICONTROL Extensions]** > **[!UICONTROL Catalog]**
1. Search for `Adobe Experience Platform Web SDK`
1. Select the `Adobe Experience Platform Web SDK` extension so the sidebar opens
1. Select **[!UICONTROL Install]**

    ![Install Web SDK Extension](assets/extension-platform-web-sdk.png)


## Link the extension to your datastream 

Leave most of the default settings and update them later, as needed. The only thing that you must do now is link the extension to your datastream. This adds the correct datastream/config id to the network calls made from the browser, so the calls are routed to the correct datastream when they arrive in the Platform Edge Network:

1. Under **[!UICONTROL Datastreams]**, select the **[!UICONTROL Choose from list]** input method
1. Configure the **[!UICONTROL Production Environment]**. (The other tag environments in the property will inherit the production settings): 
    1. Select the sandbox in which you created the schema, identity namespace and datastream
    1. Select the datastream that you created earlier, `Luma Web SDK: Development Environment`
1. Select **[!UICONTROL Save]**

    ![Datastream selection](assets/extension-luma-web-sdk-datastream-extension.png)

For more information on each section of the extension, see [Configure the Adobe Experience Platform Web SDK extension](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/client/web-sdk/web-sdk-extension-configuration).

>[!NOTE]
>
>While you did not configure a CNAME in the [!UICONTROL Edge domain] setting in this lesson, Adobe recommends you use a CNAME when you implement Platform Web SDK on your own website. While a CNAME implementation does not provide any benefits in terms of cookie lifetime, there may be some other benefits. These benefits include ad blockers and less-common browsers preventing data from being sent to domains that they classify as trackers. In these cases, using a CNAME can prevent your data collection from being disrupted for users employing these tools.

>[!NOTE]
>
>During this tutorial, you configure just one datastream and associate it with all tag environments (development, stage, and production). When you implement Platform Web SDK on your own website, you should configure a separate datastream for each environment and map them accordingly in the extension configuration. 

Now that you have installed Platform Web SDK and associated it with the datastream, you are ready to start collecting data.

>[!NOTE]
>
>Thank you for investing your time in learning about Adobe Experience Platform Web SDK. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/adobe-experience-platform-18/tutorial-discussion-implement-adobe-experience-cloud-with-web-sdk-tutorial-248848)
