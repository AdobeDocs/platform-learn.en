---
title: Ingest & Analyze Google Analytics data in Adobe Experience Platform with the BigQuery Source Connector
description: Ingest & Analyze Google Analytics data in Adobe Experience Platform with the BigQuery Source Connector
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: 
---

# 16. Ingest & Analyze Google Analytics data in Adobe Experience Platform with the BigQuery Source Connector

**Authors: [Victor de la Iglesia](https://www.linkedin.com/in/victordelaiglesia/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

**In Module 16**, you'll setup your own instance of Google Cloud Platform, load demo data in Google Cloud Platform and you'll then use the BigQuery Source Connector to ingest that data from Google Cloud Platform into Adobe Experience Platform. Finally, you'll use Customer Journey Analytics to visualize that data.

Source Connectors in Adobe Experience Platform make the process of getting data into Adobe Experience Platform easy. Google BigQuery is one of the already available connectors. 

Google Analytics is one of the most used web analytics solutions in the world, however is not the most powerful one. We all know Adobe Analytics and its capabilities. Thanks to Adobe Experience Platform and the BigQuery Source Connector we can now bring Google Analytics data into Analysis Workspace in Customer Journey Analytics. 
In addition, we can enrich that Google Analytics data by joining it with other data sources such as CRM, Call Center or Loyalty data within Customer Journey Analytics.

## Learning Objectives

- Become familiar with the Google Cloud Platform and BigQuery User Interface
- Ingest Google Analytics data into Adobe Experience Platform
- Use Customer Journey Analytics to perform analysis of Google Analytics data
- Enrich Google Analytics data with offline data

## Prerequisites

- Some familiarity with Customer Journey Analytics is preferred, but not required
- Access to Adobe Experience Platform: [https://platform.adobe.com](https://platform.adobe.com) 
- Access to Customer Journey Analytics
- Access to Google Cloud Platform and Google BigQuery
- This documentation has been created to facilitate hands-on, technical enablement around Adobe Experience Platform. In order to complete some of the modules, you'll need to change some variables and replace them by your specific **Environment Variables**. Please contact your Adobe contact who will provide you with the required **Environment Variables** of your specific Adobe Experience Platform instance.

>[!NOTE]
>
>If you don't have access to your own Adobe Experience Platform instance, don't let it stop you! You'll still learn a lot by reading through these very detailed tutorials.

## Exercises

[16.1 Create your Google Cloud Platform Account](./ex1.md)

In this exercise, you'll create your Google Cloud Platform account.

[16.2 Create your first query in BigQuery](./ex2.md)

In this exercise, you'll learn how to use BigQuery to prepare the data for loading into AEP.

[16.3 Connect GCP & BigQuery to Adobe Experience Platform](./ex3.md)

In this exercise, you'll learn how to setup the Source Connector in Adobe Experience Platform.

[16.4 Load data from BigQuery into Adobe Experience Platform](./ex4.md)

In this exercise, you'll learn how to configure the BigQuery Source Connector in Adobe Experience Platform to ingest your Google Analytics Data.

[16.5 Analyze Google Analytics Data using Customer Journey Analytics](./ex5.md)

In this exercise, you'll learn how to analyze Google Analytics data in Customer Journey Analytics and combine it with Loyalty data.

>[!NOTE]
>
>Thank you for investing your time in learning all there is to know about Adobe Experience Platform. If you have questions, want to share general feedback of have suggestions on future content, please contact Wouter Van Geluwe directly, by sending an email to **vangeluw@adobe.com**.

[Go Back to All Modules](../../overview.md)
