---
title: Adobe Experience Platform Data Collection & Real-time Event Forwarding Side Forwarding - Create an Adobe Experience Platform Data Collection Event Forwarding property
description: Create an Adobe Experience Platform Data Collection Event Forwarding property
kt: 5342
doc-type: tutorial
exl-id: ac6d09dd-ae8f-4b8a-b543-e4b96aed2c38
---
# 2.5.1 Create an Adobe Experience Platform Data Collection Event Forwarding property

## What is an Adobe Experience Platform Data Collection Event Forwarding property?

Typically, when data is collected using Adobe Experience Platform Data Collection, it is collected on the **client side**. The **client side** is an environment such as a website or a mobile application. In Getting Started and Data Collection, the configuration of a Adobe Experience Platform Data Collection Client property was discussed in depth and you implemented that Adobe Experience Platform Data Collection Client property onto your website and mobile application, so that data could be collected there when a customer was interacting with the website and mobile application.

When that interaction data is collected by the Adobe Experience Platform Data Collection Client property, a request is sent by the website or mobile app to Adobe's Edge. The Edge is Adobe's Data Collection environment and is the entry-point for clickstream data into the Adobe ecosystem. From the Edge, that collected data is then sent to applications like Adobe Experience Platform, Adobe Analytics, Adobe Audience Manager or Adobe Target. 

With the addition of an Adobe Experience Platform Data Collection Event Forwarding property, it's now possible to configure a Adobe Experience Platform Data Collection property that listens to incoming data on the Edge. When the Adobe Experience Platform Data Collection Event Forwarding property that is running on the Edge sees incoming data, it has the ability to use that data and forward it to somewhere else. That somewhere else can now also be a non-Adobe external webhook, which makes it possible to send that data to for instance, your data lake of choice, a decisioning application, or any other application that has the ability to open up a webhook.

The configuration of a Adobe Experience Platform Data Collection Event Forwarding property looks familiar to a client side property, with the ability to configure data elements and rules just like in the past with Adobe Experience Platform Data Collection Client properties. However, the way that data will be accessed and used will be slightly different, depending on your use case.

Let's start by creating the Adobe Experience Platform Data Collection Event Forwarding property.

## Create a Adobe Experience Platform Data Collection Event Forwarding property

Go to [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). In the left menu, click **Event Forwarding**. You'll then see an overview of all available Adobe Experience Platform Data Collection Event Forwarding properties. Click the **Create Property** button.

![Adobe Experience Platform Data Collection SSF](./images/launchhome.png)

Alternatively, if other Event Forwarding properties have already been created, the UI will look a bit different. In that case, click **New Property**.

![Adobe Experience Platform Data Collection SSF](./images/launchhomea.png)

You now need to enter a name for your Adobe Experience Platform Data Collection Event Forwarding property. As a naming convention, use `--aepUserLdap-- - Demo System (DD/MM/YYYY) (Edge)`. For instance, in this example, the name is **vangeluw - Demo System (22/02/2022) (Edge)**. Click **Save**.

![Adobe Experience Platform Data Collection SSF](./images/ssf1.png)

You'll then be back in the list of Adobe Experience Platform Data Collection Event Forwarding properties. Click to open the property you just created.

![Adobe Experience Platform Data Collection SSF](./images/ssf2.png)

## Configure the Adobe Cloud Connector extension

In the left menu, go to **Extensions**. You'll see that the **Core** extension is already configured.

![Adobe Experience Platform Data Collection SSF](./images/ssf3.png)

Go to **Catalog**. You'll see the **Adobe Cloud Connector** extension, along many others. Click **Install** to install it.

![Adobe Experience Platform Data Collection SSF](./images/ssf4.png)

The extension will then be added. There's no configuration to do at this step. You'll be sent back to the overview of installed extensions.

![Adobe Experience Platform Data Collection SSF](./images/ssf5.png)

## Deploy your Adobe Experience Platform Data Collection Event Forwarding property

In the left menu, go to **Publishing Flow**. Click **Add Library**.

![Adobe Experience Platform Data Collection SSF](./images/ssf6.png)

Enter the name **Main**, select the environment **Development (development)** and click **+ Add All Changed Resources**. 

![Adobe Experience Platform Data Collection SSF](./images/ssf7.png)

You'll then see this. Click **Save & Build for Development**.

![Adobe Experience Platform Data Collection SSF](./images/ssf8.png)

Your library will then be built, which might take a 1-2 minutes.

![Adobe Experience Platform Data Collection SSF](./images/ssf10.png)

## Next Steps

Go to [2.5.2 Update your Datastream to make data available to your Data Collection Event Forwarding property](./ex2.md){target="_blank"}

Go back to [Real-Time CDP Connections: Event Forwarding](./aep-data-collection-ssf.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
