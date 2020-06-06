---
title: Foundation - Data Ingestion
description: Foundation - Data Ingestion
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: 
---

# 2. Foundation - Data Ingestion

**Author: [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In this foundational exercise, the goal is to learn all about data ingestion. You'll learn about data ingestion in Streaming and Batch. You'll implement Streaming Data Ingestion by using Launch, so that the customer behavior on the Hands-On Lab website is streamed to Adobe Experience Platform in real-time. You'll learn about Batch Data Ingestion by using an Adobe Experience Platform Workflow to take a CSV-file, map it against an XDM-schema and then ingest it into Adobe Experience Platform. 

## Learning Objectives

- Learn how to create an XDM Schema in Adobe Experience Platform
- Learn how to create Datasets in Adobe Experience Platform
- Learn how to create a streaming endpoint and configure the Adobe Experience Platform extension in Launch
- Learn how to create Rules in Launch to stream data to Adobe Experience Platform
- Learn how to integrate Adobe Experience Platform Launch onto a webpage
- Learn how to use an Adobe Experience Platform Workflow to ingest a CSV-file into Adobe Experience Platform

## Prerequisites

- Access to Adobe Experience Platform: [https://platform.adobe.com](https://platform.adobe.com)
- Access to Adobe Experience Platform Launch: [https://launch.adobe.com](https://launch.adobe.com)
- Access to an AEP demo website
- Access Postman
- This documentation has been created to facilitate hands-on, technical enablement around Adobe Experience Platform. In order to complete some of the modules, you'll need to change some variables and replace them by your specific **Environment Variables**. Please contact your Adobe contact who will provide you with the required **Environment Variables** of your specific Adobe Experience Platform instance.

>[!NOTE]
>
>If you don't have access to your own Adobe Experience Platform instance, don't let it stop you! You'll still learn a lot by reading through these very detailed tutorials.

## Exercises

### 2.1 Explore the website

In this exercise, you'll explore the website that you'll use as part of this enablement.

Go to [2.1 Explore the website](./ex1.md)

### 2.2 Configure Schema's and Set Identifiers

In this exercise, you'll configure the required XDM schema's to capture profile information and customer behavior. In every XDM schema, you'll also have to configure a primary identifier to link all the information to.

Go to [2.2 Configure Schema's and Set Identifiers](./ex2.md)

### 2.3 Configure Datasets

In this exercise, you'll retrieve the required datasets to capture and store profile information and customer behavior.

Go to [2.3 Configure Datasets](./ex3.md)

### 2.4 Use Launch and the Adobe Experience Platform Extension

In this exercise, you'll learn how to use the Adobe Experience Platform extension in Launch to stream data to Adobe Experience Platform.

Go to [2.4 Use Launch and the Adobe Experience Platform Extension](./ex4.md)

### 2.5 Data Ingestion from Offline Sources

In this exercise, you'll go on the website and mobile app and behave like a customer, streaming data to Platform.

Go to [2.5 Data Ingestion from Offline Sources](./ex5.md)

>[!NOTE]
>
>Thank you for investing your time in learning all there is to know about Adobe Experience Platform. If you have questions, want to share general feedback of have suggestions on future content, please contact Wouter Van Geluwe directly, by sending an email to **vangeluw@adobe.com**.

[Go Back to All Modules](../../overview.md)
