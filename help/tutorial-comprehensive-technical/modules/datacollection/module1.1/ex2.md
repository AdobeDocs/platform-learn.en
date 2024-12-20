---
title: Foundation - Setup of Adobe Experience Platform Data Collection and the Web SDK extension - Edge Network, Datastreams and Server Side Data Collection
description: Foundation - Setup of Adobe Experience Platform Data Collection and the Web SDK extension - Edge Network, Datastreams and Server Side Data Collection
kt: 5342
doc-type: tutorial
exl-id: e97d40b5-616d-439c-9d6b-eaa4ebf5acb0
---
# 1.1.2 Edge Network, Datastreams and Server Side Data Collection

## Context

In this exercise you'll create a **Datastream**. A **datastream** tells the Adobe Edge servers where to send the data after it is collected by Web SDK. For example, do you want to send the data to Adobe Experience Platform? Adobe Analytics? Adobe Audience Manager? Adobe Target? 

Datastreams are always managed in the Adobe Experience Platform Data Collection user interface and are critical to Adobe Experience Platform data collection with Web SDK. Even when you implement Web SDK with a non-Adobe tag management solution, you'll still need to create your Datastream in the Adobe Experience Platform Data Collection user interface.

You'll be implementing the Web SDK on the browser in the next exercise. It will then be more clear to you what the data that is being collected looks like. For now, we are just telling the Datastream where to forward the data.

## Create a Datastream

In [Getting Started](./../../../modules/gettingstarted/gettingstarted/ex2.md) you already created a datastream, but we didn't discuss the background and reason for being of the Datastream. 

A satastream tells the Adobe Edge servers where to send the data after it is collected by the Web SDK. For example, do you want to send the data to Adobe Experience Platform? Adobe Analytics? Adobe Audience Manager? Adobe Target? Datastreams are managed in the Adobe Experience Platform Data Collection user interface and are critical to data collection with Web SDK, regardless of whether or not you are implementing Web SDK via Adobe Experience Platform Data Collection.

Let's review your **[!UICONTROL Datastream]**:

Go to [https://experience.adobe.com/launch/](https://experience.adobe.com/launch/).

Click **[!UICONTROL Datastreams]** in the left menu.

![Click Datastream icon in the left navigation](./images/edgeconfig1.png)

Open your datastream, which is named `--aepUserLdap-- - Demo System Datastream`.

![Name the Datastream and save](./images/edgeconfig2.png)

You'll then see the details of your datastream. 

![Name the Datastream and save](./images/edgecfg1.png)

Click **...** next to **Adobe Experience Platform** and click **Edit**.

![Name the Datastream and save](./images/edgecfg1a.png)

You'll then see this. At this moment, you've only enabled Adobe Experience Platform. Your configuration will look similar to the configuration below. (Depending on your environment and Adobe Experience Platform instance, the Sandbox Name might be different)

![Name the Datastream and save](./images/edgecfg2.png)

You should interpret the below fields like this:

For this datastream...

- All data that is collected will be stored in the `--aepSandboxName--` sandbox in Adobe Experience Platform
- All Experience Event data is collected by default into the dataset **Demo System - Event Dataset for Website (Global v1.1)**
- All Profile data will be collected by default into the dataset **Demo System - Profile Dataset for Website (Global v1.1)** (ingesting profile data natively with Web SDK currently isn't supported yet by Web SDK)
- If you want to use the **Offer Decisioning** application service for this datastream, you need to check the box for Offer Decisioning. (This will be part of [Module 3.3](./../../../modules/ajo-b2c/module3.3/offer-decisioning.md))
- **Edge Segmentation** is enabled by default, which means that qualifying audiences will be evaluated at the edge, upon ingestion of incoming traffic
- If you want to use the **Personalization Destinations**, you need to check the box for Personalization Destinations.
- - If you want to use **Adobe Journey Optimizer**'s capabilities in this datastream, you need to check the box for Adobe Journey Optimizer.


For now, no other configuration is needed for your datastream.

Next Step: [1.1.3 Introduction to Adobe Experience Platform Data Collection](./ex3.md)

[Go Back to Module 1.1](./data-ingestion-launch-web-sdk.md)

[Go Back to All Modules](./../../../overview.md)
