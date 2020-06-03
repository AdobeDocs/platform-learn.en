---
title: Module 16, Exercise
description: 
kt: 5342
audience: 
doc-type: tutorial
activity: 
---

# Module 16: Ingest & Analyze Google Analytics data in Adobe Experience Platform with the BigQuery Source Connector

**Authors: [Victor de la Iglesia](https://www.linkedin.com/in/victordelaiglesia/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

**In Module 16**, you'll setup your own instance of Google Cloud Platform, load demo data in Google Cloud Platfrom and you'll then use the BigQuery Source Connector to ingest that data from Google Cloud Platfrom into Adobe Experience Platform. Finally, you'll use Customer Journey Analytics to visualize that data.

Source Connectors in Adobe Experience Platform make the process of getting data into Adobe Experience Platform easy. Google BigQuery is one of the already available connectors. 

Google Analytics is one of the most used web analytics solutions in the world, however is not the most powerful one. We all know Adobe Analytics and its capabilities. Thanks to Adobe Experience Platform and the BigQuery Source Connector we can now bring Google Analytics data into Analysis Workspace in Customer Journey Analytics. 
In addition, we can enrich that Google Analytics data by joining it with other data sources such as CRM, Call Center or Loyalty data within Customer Journey Analytics.

## Key Takeaways

* Become familiar with the Google Cloud Platform and BigQuery User Interface
* Ingest Google Analytics data into Adobe Experience Platform
* Use Customer Journey Analytics to perform analysis of Google Analytics data
* Enrich Google Analytics data with offline data

## Prerequisites

* Some familiarity with Customer Journey Analytics is preferred, but not required
* Access to Adobe Experience Platform, Customer Journey Analytics
* Understanding of Adobe Experience Platform data sets and XDM

## Your Environment Variables

This documentation has been created to be reused across multiple Adobe Experience Platform instances for enablement purposes.
In order to complete some of the modules, you'll need to change some variables and replace them by your specific ``Environment Variables``.

You can view these variables [here](../../environment.md).

## Content

### [Exercise 16.1 - Create your Google Cloud Platform Account](./ex1.md)

In this exercise, you'll create your Google Cloud Platform account.

### [Exercise 16.2 - Create your first query in BigQuery](./ex2.md)

In this exercise, you'll learn how to use BigQuery to prepare the data for loading into AEP.

### [Exercise 16.3 - Connect GCP & BigQuery to Adobe Experience Platform](./ex3.md)

In this exercise, you'll learn how to setup the Source Connector in Adobe Experience Platform.

### [Exercise 16.4 - Load data from BigQuery into Adobe Experience Platform](./ex4.md)

In this exercise, you'll learn how to configure the BigQuery Source Connector in Adobe Experience Platform to ingest your Google Analytics Data.

### [Exercise 16.5 - Analyze Google Analytics Data using Customer Journey Analytics](./ex5.md)

In this exercise, you'll learn how to analyze Google Analytics data in Customer Journey Analytics and combine it with Loyalty data.

[Go Back to All Modules](../../README.md)
