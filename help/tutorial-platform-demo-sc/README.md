# Adobe Experience Platform - Technical Enablement

![Platform](./platformlogo.png)

## Overview

This training course is the perfect starting point for Data Engineers, Data Analysts, Data Architects, Data Scientists, Orchestration Engineers and Marketers to gain a full understanding of the business value of Adobe Experience Platform and all of its Application Services. Each lesson focuses on a real challenge businesses face in today's complex ecosystem of personalization, and breaks down the solution to that challenge in various hands-on instructions.

This training course is very diverse and offers clear insights in the following applications:

- Adobe Experience Platform
- Adobe Experience Platform Launch
- Real-time CDP
- Journey Orchestration
- Customer Journey Analytics
- Offer Decisioning

This training course doesn't just focus on Adobe applications, but takes into account the broader ecosystem in which brands operate. This means that in several of these lessons, there's a lot of focus on how non-Adobe applications integrate with Adobe Experience Platform. As such, you'll gain a deep understanding in how the following applications will work together with Adobe Experience Platform:

- Postman
- Informatica
- AWS Lambda
- Amazon Alexa
- AWS Kinesis
- Google Tag Manager
- Google Analytics
- Google Cloud Platform
- Google BigQuery
- Twilio
- Apache Kafka
- Microsoft Azure EventHub
- ...

After completing this tutorial, you will be able to:

- Configure Schemas, Mixins, Datasets, Identifiers
- Configure a Launch property and setup the new WebSDK extension in Launch
- Stream data into Adobe Experience Platform in real-time using Launch, Google Tag Manager or Amazon Alexa
- Batch ingest data into Adobe Experience Platform using a workflow or by using an ETL application
- Visualize and use the Real-time Customer Profile in Adobe Experience Platform
- Create segments
- Consume several Adobe Experience Platform APIs
- Use SQL to query your data in Adobe Experience Platform
- Configure, Train and Score Machine Learning Models in Adobe Experience Platform
- Use Journey Orchestration to configure real-time, trigger-based journeys
- Use Real-time CDP to take action by activating a segment to various destinations
- Use Customer Journey Analytics to report on omnichannel customer data from various sources, including Google BigQuery

>[!IMPORTANT]
>
>Your Adobe Experience Platform instance
>
>This documentation has been created to facilitate hands-on, technical enablement around Adobe Experience Platform. In order to execute these tutorials in a hands-on way, you will need access to an Adobe Experience Platform instance.
>
>In order to complete some of the modules, you'll need to change some variables and replace them by your specific **Environment Variables**. 
>
>Please contact your Adobe contact who will provide you with the required **Environment Variables** of your specific Adobe Experience Platform instance.
>
>If you don't have access to your own Adobe Experience Platform instance, don't let it stop you! You'll still learn a lot by reading through these very detailed tutorials.

## Content

### 1. Foundation - Setup of Adobe Experience Platform Launch and the WebSDK extension

- **Audience:** Data Engineer, Data Architect
- **Dependencies:** Access to Adobe Experience Platform and Adobe Experience Platform Launch
- **Description:** In this foundational module the focus is configuring Launch by making use of the new WebSDK extension.

Go to [1. Foundation - Setup of Launch & WebSDK](./modules/module1/data-ingestion-launch-websdk.md).

### 2. Foundation - Data Ingestion

- **Audience:** Data Engineer, Data Architect
- **Dependencies:** Access to Adobe Experience Platform and Adobe Experience Platform Launch
- **Description:** In this foundational module the focus is on data ingestion by making use of the website

Go to [2. Foundation - Data Ingestion](./modules/module2/data-ingestion.md).

### 3. Foundation - Real-time Customer Profile

- **Audience:** Data Engineer, Data Architect, Marketer
- **Dependencies:** Access to Adobe Experience Platform and for some exercises, Postman
- **Description:** In this foundational module you'll be exploring the Real-time Customer Profile in Adobe Experience Platform by making use of the UI and API.

Go to [3. Foundation - Real-time Customer Profile](./modules/module3/real-time-customer-profile.md).

### 4. Voice Assistant - Amazon Alexa

- **Audience:** Developer
- **Dependencies:** Access to Adobe Experience Platform, AWS Lambda and Amazon Alexa
- **Description:** In this module you'll add an Amazon Alexa Skill to your live demo environment.

Go to [4. Voice Assistant - Amazon Alexa](./modules/module4/data-ingestion-amazon-alexa.md).

### 5. Extract, Transform, Load data using a 3rd party ETL-tool

- **Audience:** Data Engineer, Data Architect
- **Dependencies:** Access to Adobe Experience Platform, Informatica ETL
- **Description:** In this module you'll use an ETL-tool to extract, transform and load data in Adobe Experience Platform.

Go to [5. Extract, Transform, Load data using a 3rd party ETL-tool](./modules/module5/data-ingestion-informatica-etl.md).

### 6. Journey Orchestration

- **Audience:** Data Engineer, Data Architect, Orchestration Engineer
- **Dependencies:** Access to Adobe Experience Platform, Journey Orchestration and Adobe Campaign with Platform (on Azure)
- **Description:** In this module you'll use Journey Orchestration to build out a trigger-based journey.

Go to [6. Journey Orchestration](./modules/module6/journey-orchestration-create-account.md).

### 7. Query Service

- **Audience:** Data Engineer, Data Architect, Data Analyst, BI Expert
- **Dependencies:** Access to Adobe Experience Platform, Query Service, Power BI or Tableau
- **Description:** In this module you'll learn how to use Adobe Experience Platform Query Service.

Go to [7. Query Service](./modules/module7/query-service.md).

### 8. Data Science Workspace - Popularity Based Recommendations

- **Audience:** Data Engineer, Data Architect, Data Scientist
- **Dependencies:** Access to Adobe Experience Platform and Data Science Workspace
- **Description:** In this module you'll learn how to use Adobe Experience Platform Data Science Workspace to build a Popularity Based Recommendations Recipe.

Go to [8. Data Science Workspace - Popularity Based Recommendations](./modules/module8/data-science-workspace-popularity-based-recommendations.md).

### 9. Data Ingestion using Google Tag Manager and Google Analytics

- **Audience:** Data Engineer, Data Architect
- **Dependencies:** Access to Adobe Experience Platform, Google Tag Manager and Google Analytics
- **Description:** In this module you'll learn how to use Google Tag Manager to ingest clickstream data in real-time into Adobe Experience Platform.

Go to [9. Data Ingestion using Google Tag Manager and Google Analytics](./modules/module9/data-ingestion-using-google-tag-manager-and-google-analytics.md).

### 10. Data Science Workspace - Churn Prediction Model

- **Audience:** Data Engineer, Data Architect, Data Scientist
- **Dependencies:** Access to Adobe Experience Platform, Data Science Workspace
- **Description:** In this module you'll learn basic Data Science concepts, and also, how to use Adobe Experience Platform Data Science Workspace to build a Churn Prediction Model.

Go to [10. Data Science Workspace - Churn Prediction Model](./modules/module10/data-science-workspace-churn-prediction-model.md).

### 11. RTCDP - Build a segment and take action

- **Audience:** Data Architect, Orchestration Engineer, Marketer
- **Dependencies:** Access to Adobe Experience Platform, Real-time CDP, Adobe Audience Manager, Adobe Target, AWS S3
- **Description:** In this module you'll configure a segment, enable it for Streaming Segmentation and activate the segment to several destinations, including Google DV360, Google AdWords, Adobe Audience Manager, Adobe Target and S3-destinations like Salesforce Marketing Cloud.

Go to [11. RTCDP - Build a segment and take action](./modules/module11/real-time-cdp-build-a-segment-take-action.md).

### 12. Journey Orchestration - External Weather API, SMS Action & more

- **Audience:** Data Engineer, Data Architect, Orchestration Engineer, Marketer
- **Dependencies:** Access to Adobe Experience Platform, Journey Orchestration, Open Weather API, Twilio
- **Description:** In this module you'll use Journey Orchestration to listen to customer behavior, both online and offline, and respond to it in an intelligent, contextual and real-time way over various channels.

Go to [12. Journey Orchestration - External Weather API, SMS Action & more](./modules/module12/journey-orchestration-external-weather-api-sms.md).

### 13. Customer Journey Analytics - Build a dashboard using Analysis Workspace on top of Adobe Experience Platform

- **Audience:** Data Engineer, Data Architect, Data Analyst
- **Dependencies:** Access to Adobe Experience Platform and Customer Journey Analytics
- **Description:** In this module you'll get Online to Offline insights by configuring a dashboard containing omni-channel data like Website Interactions, Mobile App Interactions, Call Center Interactions, In-Store Interactions and much more.

Go to [13. Customer Journey Analytics (CJA) - Build a dashboard using Analysis Workspace on top of Adobe Experience Platform](./modules/module13/customer-journey-analytics-build-a-dashboard.md).

### 14. Offer Decisioning

- **Audience:** Data Engineer, Data Architect, Orchestration Engineer, Marketer
- **Dependencies:** Access to Adobe Experience Platform and Offer Decisioning
- **Description:** **This module is not available yet.** In this module you'll get a hands-on preview of the Adobe Experience Platform - Offers/Decisioning Service.

Go to [14. Offer Decisioning](./modules/module14/offer-decisioning.md)

### 15. Data Science Workspace - Car Insurance Sales Propensity

- **Audience:** Data Engineer, Data Architect, Data Scientist
- **Dependencies:** Access to Adobe Experience Platform, Data Science Workspace, Anaconda
- **Description:** In this module you'll learn basic Data Science concepts, and also, how to use Adobe Experience Platform Data Science Workspace to build a Car Insurance Sales Propensity Model, schedule the model to re-train, and prepare the model for Real-time Scoring.

Go to [15. Data Science Workspace - Car Insurance Sales Propensity](./modules/module15/data-science-workspace-car-insurance-sales-propensity.md)

### 16. Ingest & Analyze Google Analytics data in Adobe Experience Platform with the BigQuery Source Connector

- **Audience:** Data Engineer, Data Architect, Data Analyst
- **Dependencies:** Access to Adobe Experience Platform, Customer Journey Analytics, Google Cloud Platform, Google BigQuery
- **Description:** In this module you'll setup your own instance of Google Cloud Platform, load demo data in Google Cloud Platform and you'll then use the BigQuery Source Connector to ingest that data from Google Cloud Platform into Adobe Experience Platform. Finally, you'll use Customer Journey Analytics to visualize that data.

Go to [16. Ingest & Analyze Google Analytics data in Adobe Experience Platform with the BigQuery Source Connector](./modules/module16/customer-journey-analytics-bigquery-gcp.md)

>[!NOTE]
>
>Thank you for investing your time in learning all there is to know about Adobe Experience Platform. If you have questions, want to share general feedback of have suggestions on future content, please contact Wouter Van Geluwe directly, by sending an email to **vangeluw@adobe.com**.
