---
title: Configure an identity namespace
description: Learn how to configure identity namespaces to use with Adobe Experience Platform Web SDK. This lesson is part of the Implement Adobe Experience Cloud with Web SDK tutorial.
feature: Identities
exl-id: 7719dff4-6b30-4fa0-acae-7491c3208f15
---
# Configure an identity namespace

Learn how to configure identity namespaces to use with Adobe Experience Platform Web SDK. 

The [Adobe Experience Platform Identity Service](https://experienceleague.adobe.com/docs/id-service/using/home.html) sets a common visitor ID across all Adobe solutions in order to power Experience Cloud capabilities such as audience-sharing between solutions. You can also send your own customer IDs to the Service to enable cross-device targeting and integrations with other systems, such as your Customer Relationship Management (CRM) system.

If your website is already using the Experience Cloud ID Service on your website&mdash;either through Visitor API or the Experience Cloud ID Service tag extension&mdash;and you would like to continue using it while migrating to Adobe Experience Platform Web SDK, you must be using the latest version of Visitor API or the Experience Cloud ID Service tag extension. See [ID Migration](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/overview.html?lang=en) for more information.

>[!NOTE]
>
> For demonstration purposes, the exercises in this lesson have you capture the identity details of a fictional customer logged into the [Luma Demo Site](https://luma.enablementadobe.com/content/luma/us/en.html) using the credentials, **user: test@adobe.com / password: test**. While you can use these steps to create a different identity for your own purposes, to learn the capabilities of the Identity Map in the Data Collection interface it is recommended that you first follow along to capture the example identity.

## Learning objectives

At the end of this lesson, you will be able to:

* Understand identity namespaces
* Create a custom identity namespace to capture an internal CRM Id


## Prerequisites

You must have already completed the previous lessons:

* [Configure Permissions](configure-permissions.md)
* [Configure Schemas](configure-schemas.md)

>[!IMPORTANT]
>
>The [Experience Cloud ID Extension](https://exchange.adobe.com/experiencecloud.details.100160.adobe-experience-cloud-id-launch-extension.html) is not needed when implementing Adobe Experience Platform Web SDK, as the Web SDK JavaScript library contains the Visitor ID service functionality.

## Create an identity namespace

In this exercise, you create an identity namespace for Luma's custom identity field, `lumaCrmId`. Identity namespaces play a critical role in building real-time customer profiles, as two matching values in the same namespace allow two data sources to form an identity graph.

Before you begin the exercises, watch this short video to learn more about identity in Adobe Experience Platform:
>[!VIDEO](https://video.tv.adobe.com/v/27841?quality=12&learn=on)

Now, create a namespace for the Luma CRM ID:

1. Open the [Data Collection interface](https://launch.adobe.com/){target="_blank"}
1. Select the sandbox you are using for the tutorial

   >[!NOTE]
   >
   >If you are the customer of a Platform-based application like Real-time CDP, we recommend using a development sandbox for this tutorial. If you are not, use the **[!UICONTROL Prod]** sandbox.
   
1. Select **[!UICONTROL Identities]** in the left navigation
1. Select **[!UICONTROL Browse]**

   A list of identity namespaces appears in the main interface of the page, showing their names, identity symbols, last updated date, and whether they are standard or custom namespaces. The right rail contains information on Identity graph strength.

1. Select **[!UICONTROL Create identity namespace]**

   ![View identities](assets/configure-identities-screen.png)

1. Provide details as following and select **[!UICONTROL Create]**.
   
   | Field         |  Value    |  
   |---------------|-----------|
   | Display name  | Luma CRM ID   | 
   | Identity symbol| lumaCrmId    |  
   | Type           | Cross-Device ID|  


   ![Create Namespaces](assets/identities-create-namespace.png)


   The Identity namespace populates in the **[!UICONTROL Identities]** screen.

   ![Create Namespaces](assets/configure-identities-namespace-lumaCrmId.png)


>[!INFO]
>
> In the [Create Data Elements](create-data-elements.md) lesson, you will learn how to use this namespace when sending identities to Platform Edge Network. 

## Create the identity namespace in your production sandbox

Due to a current limitation in the Web SDK extension, identity namespaces must also be created in the production sandbox in order to use the namespace to send data to a development sandbox. So, if you have been using a development sandbox for this tutorial, please also create the `Luma CRM ID` namespace in your production sandbox.

## Additional Resources

* [Identity Service documentation](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html)
* [Identity Service API](https://www.adobe.io/experience-platform-apis/references/identity-service/)

Now that identities are in place, the datastream can be configured.

[Next: **Configure a datastream**](configure-datastream.md)

>[!NOTE]
>
>Thank you for investing your time in learning about Adobe Experience Platform Web SDK. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
