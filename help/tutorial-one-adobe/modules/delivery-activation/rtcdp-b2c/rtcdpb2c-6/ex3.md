---
title: Configure HTTP API endpoint in Adobe Experience Platform
description: Configure HTTP API endpoint in Adobe Experience Platform
kt: 5342
doc-type: tutorial
exl-id: 621a4db7-0aff-42bf-ad42-daec6e924451
---
# 2.6.3 Configure HTTP API Streaming endpoint in Adobe Experience Platform

Before you can set up the Adobe Experience Platform Sink Connector in Kafka, you need to create an HTTP API Source Connector in Adobe Experience Platform. The HTTP API Streaming endpoint URL is required to set up the Adobe Experience Platform Sink Connector.

To create an HTTP API Source Connector, log in to Adobe Experience Platform by going to this URL: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./../../../../modules/delivery-activation/datacollection/dc1.2/images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxName--``. After selecting the appropriate sandbox, you'll see the screen change and now you're in your dedicated sandbox.

![Data Ingestion](./../../../../modules/delivery-activation/datacollection/dc1.2/images/sb1.png)

In the left menu, go to **Sources** and scroll down in the **Sources Catalog** until you see **HTTP API**. Click **Setup**.

![Data Ingestion](./images/kaep1.png)

Click **New account**. Use `--aepUserLdap-- - Kafka` as the name for your HTTP API connection, in this case **vangeluw - Kafka**. Enable the checkbox for **XDM Compatible**. Click **Connect to source**.

![Data Ingestion](./images/kaep2.png)

You'll then see this, click **Next**.

![Data Ingestion](./images/kaep3.png)

Select **Existing dataset**, open the dropdown menu. Search and select the dataset **Demo System - Event Dataset for Call Center (Global v1.1)**.

Click **Next**.

![Data Ingestion](./images/kaep4.png)

Click **Finish**.

![Data Ingestion](./images/kaep8.png)

You'll then see an overview of the HTTP API Source Connector you just created.

You'll need to copy the **Streaming endpoint** URL, which looks like the one below, as you'll need it in the next exercise.

`https://dcs.adobedc.net/collection/63751d0f299eeb7aa48a2f22acb284ed64de575f8640986d8e5a935741be9067`

![Data Ingestion](./images/kaep9.png)

You have finished this exercise.

## Next Steps

Go to [2.6.4 Install and configure Kafka Connect and the Adobe Experience Platform Sink Connector](./ex4.md){target="_blank"}

Go back to [Stream data from Apache Kafka into Adobe Experience Platform](./aep-apache-kafka.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
