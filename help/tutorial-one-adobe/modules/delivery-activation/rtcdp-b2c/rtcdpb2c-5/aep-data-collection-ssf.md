---
title: Adobe Experience Platform Data Collection & Real-time Server Side Forwarding
description: In this module, you'll use the previously configured datasets, schemas and Adobe Experience Platform Data Collection Server property to collect data, and then forward that data server-side to an endpoint of choice.
kt: 5342
doc-type: tutorial
exl-id: dbf5e995-9c2e-4f72-b336-e942cb22cde5
TQID: https://experienceleague.adobe.com/4hqUmZrVY-JugsGJv2zeaNmTXqF-B9NRkBgqLMRd6Vw
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: acc16deb-1d7f-4ec9-9ce3-6cdf355afde6
    internal-label: XDM
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: dc6ebdf7-9a94-43eb-9184-759cfdd0cf1c
    internal-label: Event forwarding
  - id: de9975b2-c43a-4287-9698-4f4cad92b83f
    internal-label: Schemas
  - id: f6ff4d13-7b5c-4533-8556-95e76673d4cb
    internal-label: Properties
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# 2.5 Real-Time CDP Connections: Event Forwarding

In this module, you'll use the previously configured datasets, schemas and Adobe Experience Platform Data Collection Client property to collect data, and then forward that data server-side to an endpoint of choice.

In this module, you'll:

- Create an Adobe Experience Platform Data Collection Server property
- Install and use the Adobe Cloud Connector extension in Adobe Experience Platform Data Collection
- Create a Google Function endpoint and stream data to it
- Create an AWS endpoint and stream data to it

## Learning Objectives

- Become familiar with Adobe Experience Platform Data Collection Server properties and the new Adobe Cloud Connector extension 
- Understand how to reuse Adobe Experience Platform Web SDK data in 3rd party solutions like Google and AWS
- Understand the architecture behind Adobe Experience Platform Data Collection and Server Side Forwarding.

## Prerequisites

- Access to Adobe Experience Platform and Adobe Experience Platform Data Collection
- Understanding of Adobe Experience Platform datasets and XDM

>[!NOTE]
>
>Don't forget to install, configure and use the Chrome Extension as referenced in [Install the Chrome extension for the Experience League documentation](../../../getting-started/gettingstarted/ex1.md)

## Exercises

[2.5.1 Create a Data Collection Event Forwarding property](./ex1.md)

In this exercise, you'll create your Adobe Experience Platform Data Collection Event Forwarding property.

[2.5.2 Update your Datastream to make data available to your Data Collection Event Forwarding property](./ex2.md)

In this exercise, you'll update your existing Datastream to make data that is collected by your Adobe Experience Platform Data Collection Client property available to your Adobe Experience Platform Data Collection Server property.

[2.5.3 Create and configure a custom webhook](./ex3.md)

In this exercise, you'll create and configure a custom webhook and you'll start forwarding data that is collected by Web SDK to that custom webhook.

[2.5.4 Forward events to GCP Pub/Sub](./ex4.md)

In this exercise, you'll create and configure a Google Cloud Function and you'll start forwarding data that is collected by Web SDK to Google.

[2.5.5 Forward events to AWS Kinesis & AWS S3](./ex5.md)

In this exercise, you'll configure your AWS environment using AWS IAM, AWS Kinesis, AWS Firehose and AWS S3 after which you'll start forwarding event data that is collected by Web SDK.

![Tech Insiders](./../../../../assets/images/techinsiders.png){width="50px"}

>[!NOTE]
>
>Thank you for investing your time in learning all there is to know about Adobe Experience Platform and its applications. If you have questions, want to share general feedback of have suggestions on future content, please contact Tech Insiders directly, by sending an email to **techinsiders@adobe.com**.

[Go Back to All Modules](./../../../../overview.md)
