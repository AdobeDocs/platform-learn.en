---
title: Configure a datastream
description: Learn how to create a datastream in Experience Platform.
feature: Mobile SDK,Datastreams

---
# Create a datastream

Learn how to create a datastream in Experience Platform.

A datastream is a server-side configuration on Platform Edge Network. The datastream ensures that incoming data to the Platform Edge Network is routed to Adobe Experience Cloud applications and services appropriately. For more information, see the [documentation](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html) or this [video](https://experienceleague.adobe.com/docs/platform-learn/data-collection/edge-network/configure-datastreams.html).

## Prerequisites

To create a datastream, your organization must be provisioned for this feature in the Data Collection interface (formerly [!UICONTROL Launch]) and you must have user permissions for [!UICONTROL Experience Platform] > [!UICONTROL Data Collection] > **[!UICONTROL Manage Datastreams]** and **[!UICONTROL View Datastreams]**.

## Learning objectives

In this lesson, you will:

* Know when to use a datastream.
* Create a datastream.
* Configure a datastream.

## Create a datastream

Datastreams can be created in the [!UICONTROL Data Collection] interface using the [!UICONTROL Datastream] configuration tool. To create a datastream:

1. Make sure you are in the correct Experience Platform sandbox, as Datastreams are defined on a sandbox level.
1. Select **[!UICONTROL Datastreams]** in the left rail.
1. Select **[!UICONTROL New Datastream]**. 

    ![datastreams home](assets/datastream-new.png)

1. Provide a **[!UICONTROL Name]**, for example `Luma Mobile App` and a **[!UICONTROL Description]**, for example `Datastream for Luma Mobile App`.
1. Select the schema that you created in the previous lesson from the **Event Schem**a list.
1. Select **[!UICONTROL Save]**.

    ![new datastreams](assets/datastream-name.png)


## Add services

Next, you connect your Experience Cloud services to your datastream. When Platform Mobile SDK sends data to Edge Network, the datastream sends the data to these services:

1. Select **[!UICONTROL Add Service]**.

1. Add **[!UICONTROL Adobe Analytics]** from the [!UICONTROL Service] list, 

1. Enter the name of the report site that you want to use in **[!UICONTROL Report Suite ID]**.

1. Enable the service by switching **[!UICONTROL Enabled]** on.

1. Select **[!UICONTROL Save]**.

   ![Add Adobe Analytics as Datastream service](assets/datastream-service-aa.png)

You might also want to enable the Adobe Experience Platform service. 

>[!IMPORTANT]
>
>You can only enable the Adobe Experience Platform service when having created an event dataset. If you don't already have an event dataset created, follow the instructions [here](platform.md).

1. Click ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Add Service]** to add another service.

1. Select **[!UICONTROL Adobe Experience Platform]** from the [!UICONTROL Service] list.

1. Enable the service by switching **[!UICONTROL Enabled]** on.

1. Select the **[!UICONTROL Event Dataset]** that you created as part of the [Create a dataset](platform.md#create-a-dataset) instruction, for example **Luma Mobile App Event Dataset**

1. Select **[!UICONTROL Save]**.

   ![Add Adobe Experience Platform as a Datastream service](assets/datastream-service-aep.png)
1. The final configuration should look something like this.
   
   ![datastream settings](assets/datastream-settings.png)


>[!NOTE]
>
>Enabling each of the services that your organization uses ensures data collected in the mobile app can be used everywhere. For more information about datastream settings, review the documentation [here](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html#adobe-experience-platform-settings).

When implementing Platform Mobile SDK on your own website, you should create three datastreams to map to your three tag environments (development, stage, and production). If you are using Platform Mobile SDK with Platform-based applications such as Adobe Real-Time Customer Data Platform or Adobe Journey Optimizer, you should be sure to create those datastreams in the appropriate Platform sandboxes.

>[!SUCCESS]
>
>You have now a datastream to use for the remainder of the tutorial.<br/>Thank you for investing your time in learning about Adobe Experience Platform Mobile SDK. If you have questions, want to share general feedback, or have suggestions on future content, share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Next: **[Configure tags](configure-tags.md)**
