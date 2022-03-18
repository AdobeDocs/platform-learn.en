---
title: Configure a datastream
description: Learn how to enable a datastream and configure Experience Cloud solutions. This lesson is part of the Implement Adobe Experience Cloud with Web SDK tutorial.
feature: Datastreams
exl-id: ca28374a-9fe0-44de-a7ac-0aa046712515
---
# Configure a datastream

Learn how to enable a datastream and configure Experience Cloud solutions.

Datastreams tell Adobe Experience Platform Edge Network where to send data collected by Platform Web SDK. In the datastreams configuration, you enable your Experience Cloud applications, your Experience Platform account, and event forwarding. See the [Fundamentals of Configuring a Datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=en) for more detailed information.

## Learning objectives

At the end of this lesson, you will be able to:

* Create a datastream
* Enable your Experience Cloud applications
* Enable Experience Platform

## Prerequisites

Before you configure your datastream, you must have already completed the following lessons:

* [Configure permissions](configure-permissions.md)
* [Configure a schema](configure-schemas.md)
* [Configure an identity namespace](configure-identities.md)

## Create a datastream

Now you can create a datastream to tell Platform Edge Network where to send data collected by Web SDK.

**To create a datastream:**

1. Open the [Data Collection interface](https://launch.adobe.com/){target="_blank"}
1. Select the development sandbox you are using for the tutorial 

   >[!IMPORTANT]
   >
   >Make sure you are no longer in your Production sandbox

1. Go to **[!UICONTROL Datastreams]** in the left navigation
1. Select **[!UICONTROL New Datastream]** on the right hand-side of the screen.
1. Enter `Luma Web SDK` as the **[!UICONTROL Name]**. This name is referenced later when you configure the Web SDK extension in your tag property.
1. Select your `Luma Web Event Data` as the **[!UICONTROL Event Schema]** 
1. Select **[!UICONTROL Save]**

   ![Create the datastream](assets/datastream-create-datastream.png)

   >[!AVAILABILITY]
   >
   >The mapping feature will be incorporated into this tutorial at a later date.

   


On the next screen, you are able to add services such as Adobe applications to the datastream, however you will not add any services at this point in the tutorial. You will do so later in the lessons [Set up Experience Platform](setup-experience-platform.md), [Set up Analytics](setup-analytics.md), [Set up Audience Manager](setup-audience-manager.md), [Setup Target](setup-target.md), or [Event Forwarding](setup-event-forwarding.md).

>[!NOTE]
>
>When implementing Platform Web SDK on your own website, you should create three datastreams to map to your three tag environments (development, stage, and production). If you are using Platform Web SDK with Platform-based applications such as Adobe Real-time Customer Data Platform or Adobe Journey Optimizer, you should be sure to create those datastreams in the appropriate Platform sandboxes.

You are now ready to install the Platform Web SDK extension in your tag property!

[Next: **Install Platform Web SDK extension in tags**](install-web-sdk.md)

>[!NOTE]
>
>Thank you for investing your time in learning about Adobe Experience Platform Web SDK. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)