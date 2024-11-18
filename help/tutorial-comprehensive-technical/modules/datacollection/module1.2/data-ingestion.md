---
title: Foundation - Data Ingestion
description: Foundation - Data Ingestion
kt: 5342
doc-type: tutorial
exl-id: 976d801a-3dcb-4cd9-8b9f-b1c964fe7c25
---
# 1.2 Foundation - Data Ingestion

In this module, the goal is to learn all about data ingestion. You'll learn about data ingestion in Streaming and Batch. You'll implement Streaming Data Ingestion by using Launch, so that the customer behavior on the Hands-On Lab website is streamed to Adobe Experience Platform in real-time. You'll learn about Batch Data Ingestion by using an Adobe Experience Platform Workflow to take a CSV-file, map it against an XDM-schema and then ingest it into Adobe Experience Platform. 

## Learning Objectives

- Learn how to create an XDM Schema in Adobe Experience Platform
- Learn how to create Datasets in Adobe Experience Platform
- Learn how to create a streaming endpoint and configure the Adobe Experience Platform extension in Launch
- Learn how to create Rules in Launch to stream data to Adobe Experience Platform
- Learn how to integrate Adobe Experience Platform Launch onto a webpage
- Learn how to use an Adobe Experience Platform Workflow to ingest a CSV-file into Adobe Experience Platform

## Prerequisites

- Access to Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Access to Adobe Experience Platform Launch: [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/)
- Access to Postman

>[!NOTE]
>
>Don't forget to install, configure and use the Chrome Extension as referenced in [Install the Chrome extension for the Experience League documentation](../../gettingstarted/gettingstarted/ex1.md)

## Exercises

[1.2.1 Explore the website](./ex1.md)

In this exercise, you'll explore the website that you'll use as part of this enablement.

[1.2.2 Configure Schemas and Set Identifiers](./ex2.md)

In this exercise, you'll configure the required XDM schema's to capture profile information and customer behavior. In every XDM schema, you'll also have to configure a primary identifier to link all the information to.

[1.2.3 Configure Datasets](./ex3.md)

In this exercise, you'll retrieve the required datasets to capture and store profile information and customer behavior.

[1.2.4 Data Ingestion from Offline Sources](./ex4.md)

In this exercise, you'll go on the website and mobile app and behave like a customer, streaming data to Platform.

[1.2.5 Data Landing Zone](./ex5.md)

Setup your Data Landing Zone Source connector with Azure Blob storage.

[Summary and benefits](./summary.md)

Summary of this module and overview of the benefits.

>[!NOTE]
>
>Thank you for investing your time in learning all there is to know about Adobe Experience Platform and its applications. If you have questions, want to share general feedback of have suggestions on future content, please contact Tech Insiders directly, by sending an email to **techinsiders@adobe.com**.

[Go Back to All Modules](../../../overview.md)
