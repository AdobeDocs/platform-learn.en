---
title: Overview
description: Starting point for Data Engineers, Data Analysts, Data Architects, Data Scientists, Orchestration Engineers and Marketers to gain a full understanding of the business value of Adobe Experience Platform and all of its Application Services.
doc-type: multipage-overview
hide: no
exl-id: 88c19383-c185-40f0-b118-6cb82db0ce0e
---
# Comprehensive Technical Tutorial for Adobe Experience Platform

## Overview

This tutorial is the perfect starting point for Data Engineers, Data Analysts, Data Architects, Data Scientists, Orchestration Engineers and Marketers to gain a full understanding of the business value of Adobe Experience Platform and all of its application services. Each lesson focuses on a real challenge businesses face in today's complex ecosystem of personalization and breaks down how Experience Platform solves that challenge in various hands-on exercises. 

This tutorial is very diverse and offers clear insights in the following applications:

- Adobe Experience Platform
- Adobe Experience Platform Data Collection
- Real-time CDP
- Adobe Journey Optimizer
- Customer Journey Analytics

This tutorial doesn't just focus on Adobe applications, but takes into account the broader ecosystem in which brands operate. In order to do that, in some lessons there is a focus on how _non-Adobe_ applications integrate with Adobe Experience Platform. As such, you'll gain a deep understanding in how the following applications will work together with Adobe Experience Platform:

- Amazon: AWS Lambda, AWS S3, AWS Kinesis
- Google: Google Cloud Platform, Google BigQuery, Google Display&Video 360, Google AdWords
- Microsoft: Power BI, Azure EventHub, Azure Blob Storage
- Salesforce: Tableau
- Apache Kafka
- Postman
- ...

After completing the exercises in this tutorial, you will be able to:

- Configure Schemas, Field Groups, Datasets, and Identities
- Configure an Adobe Experience Platform Data Collection property and setup the new Web SDK extension in Adobe Experience Platform Data Collection
- Stream data into Adobe Experience Platform in real-time using Adobe Experience Platform Data Collection
- Batch ingest data into Adobe Experience Platform using a workflow or by using an extract, transform, load (ETL) application
- Visualize and use the Real-time Customer Profile in Adobe Experience Platform
- Create segments
- Consume several Adobe Experience Platform APIs
- Use SQL to query your data in Adobe Experience Platform
- Configure and run real-time, trigger-based journeys
- Use Real-time CDP to take action by activating a segment to various destinations
- Use Customer Journey Analytics to report on omnichannel customer data from various sources, including Google BigQuery

## Prerequisites

- Access to Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Access to Adobe Experience Platform Data Collection: [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/)
- Access to Demo System: [https://dashboard.adobedemo.com/](https://dashboard.adobedemo.com/)

## Videos

You can find a lot of interesting videos from our Tech Academy events, from Bootcamps and more on our [Experience Makers Community YouTube channel](https://www.youtube.com/channel/UCUKG2dkZ9pYuZUPebQ21jUw).

## Content

[0. Getting started](./modules/gettingstarted/getting-started.md)

- **Audience:** All participants of the Comprehensive Technical Tutorial for Adobe Experience Platform
- **Prerequisites:** Access to Demo System Next, Adobe Experience Platform and Adobe Experience Platform Data Collection. 
- **Description:** In this foundational module, you will setup everything so that you can access and use the demo environment.
- **Time Investment:** 30 minutes

### 1. Data Collection

[1.1 Foundation - Setup of Adobe Experience Platform Data Collection & Web SDK](./modules/datacollection/module1.1/data-ingestion-launch-web-sdk.md)

- **Audience:** Data Engineer, Data Architect
- **Prerequisites:** Access to Adobe Experience Platform and Adobe Experience Platform Data Collection.
- **Description:** In this foundational module, you will learn about Adobe Experience Platform Data Collection and the new Web SDK extension.
- **Time Investment:** 30 minutes

[1.2 Foundation - Data Ingestion](./modules/datacollection/module1.2/data-ingestion.md)

- **Audience:** Data Engineer, Data Architect
- **Prerequisites:** Access to Adobe Experience Platform and Adobe Experience Platform Data Collection.
- **Description:** In this foundational module, you will ingest data from the website into Platform
- **Time Investment:** 120 minutes

[1.3 Federated Audience Composiiton](./modules/datacollection/module1.3/fac.md)

- **Audience:** Data Analyst, Data Engineer, Data Architect
- **Prerequisites:** Access to Adobe Experience Platform
- **Description:** In this module, you'll learn how to setup your own Apache Kafka cluster, define topics, producers and consumers and stream data into Adobe Experience Platform using the Adobe Experience Platform Sink Connector for Kafka Connect.
- **Time Investment:** 90 minutes

### 2. Real-Time CDP B2C

[2.1 Foundation - Real-time Customer Profile](./modules/rtcdp-b2c/module2.1/real-time-customer-profile.md)

- **Audience:** Data Engineer, Data Architect, Marketer
- **Prerequisites:** Access to Adobe Experience Platform and Postman
- **Description:** In this foundational module, you will explore the Real-time Customer Profile in Adobe Experience Platform by making use of the UI and API.
- **Time Investment:** 90 minutes
- **Download these assets**: 
  - [Postman collections](./assets/postman/postman_profile.zip)

[2.2 Intelligent Services](./modules/rtcdp-b2c/module2.2/intelligent-services.md)

- **Audience:** Data Engineer, Data Architect, Data Scientist
- **Prerequisites:** Access to Adobe Experience Platform, Intelligent Services
- **Description:** In this module, you'll learn how to setup, configure and use Adobe Experience Platform Intelligent Services.
- **Time Investment:** 60 minutes

[2.3 Real-Time CDP - Build a segment and take action](./modules/rtcdp-b2c/module2.3/real-time-cdp-build-a-segment-take-action.md)

- **Audience:** Data Architect, Orchestration Engineer, Marketer
- **Prerequisites:** Access to Adobe Experience Platform, Real-time CDP, Adobe Audience Manager, Adobe Target, AWS S3
- **Description:** In this module, you'll configure a segment, enable it for Streaming Segmentation and activate the segment to several destinations, including Google DV360, Google AdWords, Adobe Audience Manager, Adobe Target and S3-destinations like Salesforce Marketing Cloud.
- **Time Investment:** 90 minutes

[2.4 Real-Time CDP: Segment Activation to Microsoft Azure Event Hub](./modules/rtcdp-b2c/module2.4/segment-activation-microsoft-azure-eventhub.md)

- **Audience:** Data Engineer, Data Architect, Data Analyst
- **Prerequisites:** Access to Adobe Experience Platform, Real-time CDP and Microsoft Azure
- **Description:** In this module, you'll setup a Microsoft Azure EventHub destination as a real-time destination for Adobe Experience Platform Real-time CDP. You will also setup and deploy an Azure function that will be triggered in real-time whenever Adobe Experience Platform delivers a segment payload to your Azure EventHub destination. The Azure Function that you'll trigger will show the mechanism of Adobe Experience Platform Real-time CDP's activation capabilities.
As part of this module you will also get an understanding of what triggers Real-time CDP to actually deliver a payload to a specified destination. We will also discuss the status of a segment qualification and how it relates to activation.
- **Time Investment:** 90 minutes

[2.5 Real-Time CDP Connections: Event Forwarding](./modules/rtcdp-b2c/module2.5/aep-data-collection-ssf.md)

- **Audience:** Data Engineer, Data Architect, Data Analyst
- **Prerequisites:** Access to Real-Time CDP Connections, Tags and Event Forwarding properties
- **Description:** In this module, you'll use the previously configured datasets, schemas and Adobe Experience Platform Data Collection property to collect data, and then forward that data server-side to an endpoint of choice.
- **Time Investment:** 90 minutes

[2.6 Stream data from Apache Kafka into Real-Time CDP](./modules/rtcdp-b2c/module2.6/aep-apache-kafka.md)

- **Audience:** Data Analyst, Data Engineer, Data Architect
- **Prerequisites:** Access to Adobe Experience Platform
- **Description:** In this module, you'll learn how to setup your own Apache Kafka cluster, define topics, producers and consumers and stream data into Adobe Experience Platform using the Adobe Experience Platform Sink Connector for Kafka Connect.
- **Time Investment:** 90 minutes

### 3. Adobe Journey Optimizer B2C

[3.1 Adobe Journey Optimizer: Orchestration](./modules/ajo-b2c/module3.1/journey-orchestration-create-account.md)

- **Audience:** Data Engineer, Data Architect, Orchestration Engineer
- **Prerequisites:** Access to Adobe Experience Platform and Adobe Journey Optimizer
- **Description:** In this module, you'll use Adobe Journey Optimizer to build out a trigger-based journey.
- **Time Investment:** 60 minutes

[3.2 Adobe Journey Optimizer: External data sources and custom actions](./modules/ajo-b2c/module3.2/journey-orchestration-external-weather-api-sms.md)

- **Audience:** Data Engineer, Data Architect, Orchestration Engineer, Marketer
- **Prerequisites:** Access to Adobe Experience Platform, Adobe Journey Optimizer, Open Weather API, Twilio
- **Description:** In this module, you'll use Adobe Journey Optimizer to listen to customer behavior, both online and offline, and respond to it in an intelligent, contextual and real-time way over various channels.
- **Time Investment:** 90 minutes

[3.3 Adobe Journey Optimizer: Offer Decisioning](./modules/ajo-b2c/module3.3/offer-decisioning.md)

- **Audience:** Data Engineer, Data Architect, Orchestration Engineer, Marketer
- **Prerequisites:** Access to Adobe Experience Platform and Offer Decisioning
- **Description:** In this module, you'll use the Adobe Experience Platform - Offers/Decisioning application service in a hands-on way to configure Personalized Offers and your own Offer Activity.
- **Time Investment:** 120 minutes

[3.4 Adobe Journey Optimizer: Event-based Journeys](./modules/ajo-b2c/module3.4/journeyoptimizer.md)

- **Audience:** Email Marketer, Orchestration Specialist, Data Engineer, Data Architect, Data Analyst
- **Prerequisites:** Access to Adobe Experience Platform and Journey Optimizer
- **Description:** In this module, you'll learn everything there is to know about Journey Optimizer, which helps companies design and deliver connected, contextual, and personalized experiences to their customers.
- **Time Investment:** 120 minutes

### 4. Adobe Customer Journey Analytics

[4.1 Customer Journey Analytics: Build a dashboard using Analysis Workspace on top of Adobe Experience Platform](./modules/cja-b2c/module4.1/customer-journey-analytics-build-a-dashboard.md)

- **Audience:** Data Engineer, Data Architect, Data Analyst
- **Prerequisites:** Access to Adobe Experience Platform and Customer Journey Analytics
- **Description:** In this module, you'll get Online to Offline insights by configuring a dashboard containing omni-channel data like Website Interactions, Mobile App Interactions, Call Center Interactions, In-Store Interactions and much more.
- **Time Investment:** 120 minutes

[4.2 Customer Journey Analytics: Ingest & Analyze Google Analytics data in Adobe Experience Platform with the BigQuery Source Connector](./modules/cja-b2c/module4.2/customer-journey-analytics-bigquery-gcp.md)

- **Audience:** Data Engineer, Data Architect, Data Analyst
- **Prerequisites:** Access to Adobe Experience Platform, Customer Journey Analytics, Google Cloud Platform, Google BigQuery
- **Description:** In this module, you'll set up your own instance of Google Cloud Platform, load demo data in Google Cloud Platform and you'll then use the BigQuery Source Connector to ingest that data from Google Cloud Platform into Adobe Experience Platform. Finally, you'll use Customer Journey Analytics to visualize that data.
- **Time Investment:** 120 minutes
- **Download these assets**: 
  - [JSON - Sample Data: Demo - Loyalty Data](./assets/json/bqLoyalty.json)

### 5. Data Distiller

[5.1 Query Service](./modules/datadistiller/module5.1/query-service.md)

- **Audience:** Data Engineer, Data Architect, Data Analyst, BI Expert
- **Prerequisites:** Access to Adobe Experience Platform, Query Service, Power BI or Tableau
- **Description:** In this module, you'll learn how to use Adobe Experience Platform Query Service.
- **Time Investment:** 90 minutes
- **Download these assets**: 
  - [JSON - Sample Data: Demo System - Event Dataset for Website](./assets/json/ee.json)
  - [JSON - Sample Data: Demo System - Event Dataset for Call Center](./assets/json/callcenter.json)
  - [JSON - Sample Data: Demo System - Profile Dataset for Loyalty](./assets/json/loyalty.json)





