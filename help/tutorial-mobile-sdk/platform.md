---
title: Send data to Experience Platform with Platform Mobile SDK
description: Learn how to send data to Experience Platform.
solution: Data Collection,Experience Platform
feature: Mobile SDK,Data Ingestion
jira: KT-14637
exl-id: fdd2c90e-8246-4d75-a6db-df3ef31946c4
---
# Send data to Experience Platform

Learn how to send mobile app data to Adobe Experience Platform.

This optional lesson is relevant to all customers of Real-Time Customer Data Platform (Real-Time CDP), Journey Optimizer, and Customer Journey Analytics. Experience Platform, the foundation of Experience Cloud products, is an open system that transforms all your data (Adobe and non-Adobe) into robust customer profiles. These customer profiles update in real time and uses AI-driven insights to help you to deliver the right experiences across every channel.

The [event](events.md), [lifecycle](lifecycle-data.md), and [identity](identity.md) data which you collected and sent to Platform Edge Network in earlier lessons is forwarded to the services configured in your datastream, including Adobe Experience Platform.

![Architecture](assets/architecture-aep.png){zoomable="yes"}


## Prerequisites

Your organization must be provisioned and permissions granted for Adobe Experience Platform.

If you don't have access, you can [skip this lesson](install-sdks.md).

## Learning objectives

In this lesson, you will:

* Create an Experience Platform dataset.
* Configure your datastream to forward data to Experience Platform.
* Validate data in the dataset.
* Enable your schema and dataset for Real-Time Customer Profile.
* Validate data in Real-Time Customer Profile.
* Validate data in the identity graph.


## Create a dataset

All data that is successfully ingested into Adobe Experience Platform is persisted within the data lake as datasets. A dataset is a storage and management construct for a collection of data (typically a table) that contains a schema (columns) and fields (rows). Datasets also contain metadata that describes various aspects of the data they store. See the [documentation](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/overview) for more information.

1. Navigate to the Experience Platform UI. Select **[!UICONTROL Experience Platform]** from the Apps ![Apps](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg) menu in the top right.


1. Select **[!UICONTROL Datasets]** from the left navigation menu.

1. Select ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Create dataset]**.

1. Select **[!UICONTROL Create dataset from schema]**.
![dataset home](assets/dataset-create.png){zoomable="yes"}

1. Search for your schema. for example using `Luma Mobile` in the search field.
1. Select your schema, for example **[!DNL Luma Mobile App Event Schema]**.

1. Select **[!UICONTROL Next]**.
   ![dataset configure](assets/dataset-configure.png){zoomable="yes"}

1. Provide a **[!UICONTROL Name]**, for example `Luma Mobile App Events Dataset` and a **[!UICONTROL Description]**.

1. Select **[!UICONTROL Finish]**.
   ![dataset finish](assets/dataset-finish.png){zoomable="yes"}


## Add Adobe Experience Platform datastream service

To send your XDM data from the Edge Network to Adobe Experience Platform, add the Adobe Experience Platform service to the datastream you set up as part of [Create a datastream](create-datastream.md).

>[!IMPORTANT]
>
>You can only enable the Adobe Experience Platform service when having created an event dataset.

1. In the Data Collection UI, select **[!UICONTROL Datastreams]** and your datastream. 
   
1. Then select ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Add Service]**.

1. Select **[!UICONTROL Adobe Experience Platform]** from the [!UICONTROL Service] list.

1. Enable the service by switching **[!UICONTROL Enabled]** on.

1. Select the **[!UICONTROL Event Dataset]** that you created earlier , for example **[!DNL Luma Mobile App Event Dataset]**.

1. Select **[!UICONTROL Save]**.

   ![Add Adobe Experience Platform as a datastream service](assets/datastream-service-aep.png){zoomable="yes"}
1. The final configuration should look something like this.
   
   ![datastream settings](assets/datastream-settings.png){zoomable="yes"}


## Validate data in the dataset

Now that you have created a dataset and updated your datastream to send data to Experience Platform, all XDM data send to Platform Edge Network is forwarded to Platform and lands in the dataset.

Open the app and navigate to screens where you are tracking events. You can also trigger lifecycle metrics.

Open your dataset in the Platform interface. You should see the data arriving in batches to the dataset. The data typically arrives in microbatches every 15 minutes, so you might not see your data immediately.

![validate data landing Platform dataset batches](assets/platform-dataset-batches.png){zoomable="yes"}

You should also see example records and fields using the **[!UICONTROL Preview dataset]** feature:
![validate lifecycle sent to Platform dataset](assets/lifecycle-platform-dataset.png){zoomable="yes"}

A more robust tool for validating data is Platform's [query service](https://experienceleague.adobe.com/en/docs/platform-learn/tutorials/queries/explore-data).

## Enable Real-Time Customer Profile

Experience Platform's Real-Time Customer Profile allows you to build a holistic view of each individual customer that combines data from multiple channels, including online, offline, CRM, and third-party data. Profile allows you to consolidate your disparate customer data into a unified view offering an actionable, timestamped account of every customer interaction.

### Enable the schema

1. Open your schema, for example **[!DNL Luma Mobile App Event Schema]**.
1. Enable **[!UICONTROL Profile]**.
1. Select **[!UICONTROL Data for this schema contains a primary identity in the identityMap field.]** in the  dialog.
1. **[!UICONTROL Save]** the schema.

    ![enable the schema for profile](assets/platform-profile-schema.png){zoomable="yes"}

### Enable the dataset

1. Open your dataset, for example **[!DNL Luma Mobile App Event Dataset]**.
1. Enable **[!UICONTROL Profile]**.

    ![enable the dataset for profile](assets/platform-profile-dataset.png){zoomable="yes"}

### Validate data in Profile

Open the app and navigate to screens where you are tracking events, for example: log in to the Luma app and make a purchase.

Use Assurance to find one of the identities passed in the identityMap (Email, lumaCrmId, or ECID), for example the CRM Id.

![grab an identity value](assets/platform-identity.png){zoomable="yes"}

In the Platform interface, 

1. Navigate to **[!UICONTROL Profiles]**, and select **[!UICONTROL Browse]** from the top bar. 
1. Specify the identity details you just grabbed, for example `Luma CRM ID` for **[!UICONTROL Identity namespace]** and the value you copied for **[!UICONTROL Identity value]**. Then select **[!UICONTROL View]**.
1. To view details, select the profile.

![look up an identity value](assets/platform-profile-lookup.png){zoomable="yes"}

On the **[!UICONTROL Detail]** screen, you can see basic info about the user, including the **[!UICONTROL **linked identities**]**:
![profile details](assets/platform-profile-details.png){zoomable="yes"}

On the **[!UICONTROL Events]**, you can see the events collected from your mobile app implementation for this user:

![profile events](assets/platform-profile-events.png){zoomable="yes"}


From the profile detail screen:

1. To view the identity graph, click the link or navigate to **[!UICONTROL Identities]**, then select **[!UICONTROL Identity Graph]** from the top bar.
1. To look up the identity value, specify `Luma CRM ID` as the **[!UICONTROL Identity namespace]** and the copied value as the **[!UICONTROL Identity value]**. Then select **[!UICONTROL View]**.
   
   This visualization shows you the identities that are linked together in a profile and their origin. Here is an example of an identity graph constructed of data collected from completing both this Mobile SDK tutorial (Data Source 2) and the [Web SDK tutorial](https://experienceleague.adobe.com/en/docs/platform-learn/implement-web-sdk/overview) (Data Source 1):

   ![grab an identity value](assets/platform-profile-identitygraph.png){zoomable="yes"}


## Next steps

There is a lot more that marketers and analytics can do with data captured in Experience Platform, including analyzing it in Customer Journey Analytics and building segments in Real-Time Customer Data Platform. You are off to a good start!


>[!SUCCESS]
>
>You have now set up your app to send data not only to the Edge Network but also to Adobe Experience Platform.<br>Thank you for investing your time in learning about Adobe Experience Platform Mobile SDK. If you have questions, want to share general feedback, or have suggestions on future content, share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).
>

Next: **[Create and send push notifications](journey-optimizer-push.md)**
