---
title: Report and analyze your mobile app data with Customer Journey Analytics
description: Learn how to report ana analyze the interactions with your mobile app using Customer Journey Analytics.
solution: Data Collection,Experience Platform,Analytics
---
# Report and analyze using Customer Journey Analytics

Learn how to report and analyze your mobile app interactions with Customer Jouney Analytics.

The event data which you collected and sent to Platform Edge Network in earlier lessons is forwarded to the services configured in your datastream. If you followed the [Send data to Experience Platform](platform.md) lesson, that data is now available in Experience Platform for Customer Journey Analytics to use for reporting and analysis.

Contrary to Adobe Analytics, Customer Journey Analytics is an application that *uses* data from datasets you have created in Experience Platform. Using the Adobe Experience Platform Mobile SDK, you do not send data to Customer Journey Analytics. Instead, Customer Journey Analytics uses the data from the datasets in Experience Platform.

This lesson in the tutorial will only focus on reporting on and analyzing the data captured from the Luma tutorial app. One of the unique capabilities of Customer Journey Analytics is to combine data from multiple sources (CRM, point-of-sale, loyalty application, call-center) and channels (web, mobile, offline) to provide deep insights into customer journeys. That capability is beyond the scope of this lesson. See [Customer Journey Analytics overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) for more information.


## Prerequisites

Your organization must be provisioned and permission granted for Customer Journey Analytics. You must have administration access to Customer Journey Analytics.


## Learning objectives

In this lesson, you will:

- Create a connection to define the datasets from Experience Platform you want to use in Customer Journey Analytics.
- Create a dataview to prepare the data from the datasets for your reporting and analysis
- Create a project to build reports, visualizations and analyze the data from your mobile app.


## Create a connection

A connection in Customer Journey Analytics defines the datasets (and the data within these datasets) from Experience Platform you want to use for reporting and analysis.

1. Navigate to the Customer Journey Analytics interface by selecting it from the Apps ![Apps](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg) menu in the top right.

1. Select **[!UICONTROL Connections]** from the top menu bar.

1. Ensure you select the **[!UICONTROL List]** tab in the Connections interface. You will see a list of existing connections.

1. Select Create new connection.

1. In Connection settings, provide
   1. **[!UICONTROL Connection name]**, for example `Luma - AEP Mobile SDK Tutorial Connection`.
   1. **[!UICONTROL Connection description]**, for example `Connection for the Luma app used in the AEP Mobile SDK tutorial`.
   1. Select the sandbox you have used to collect your mobile app data, for example **[!UICONTROL Mobile and Web SDK Courses]**.
   1. Select **[!UICONTROL less than 1 million]** from the **[!UICONTROL Average number of daily events]**.
   1. Select **[!UICONTROL Add datasets]**. This allows you to select the datasets from Experience Platform you want to use in Customer Journey Analytics.

      1. In the **[!UICONTROL Add datasets]** wizard, **[!UICONTROL Select datasets]** step, select the following datasets:

         - **[!UICONTROL Luma Mobile App Event Dataset]**, the dataset you created as part of the [Create a dataset](platform.md#create-a-dataset) section in the Experience Platform lesson.
         - **[!UICONTROL ODE DecisionEvents - *sandbox name*] decisioning**
         - **[!UICONTROL Journey Step Events]**
         - **[!UICONTROL AJO Push Tracking Event Datasets]**
         - **[!UICONTROL AJO Entity Dataset]**

      1. In the **[!UICONTROL Add datasets]** wizard, **[!UICONTROL Datasets settings]** step, you need to define the Person ID (for event datasets) or Key and Matching (for lookup datasets). See the following tables for the proper setup:

         - For event datasets:

           | Dataset | Person ID | Timestamp | Data source type | Import all new data | Backfill all existing data |
           |---|---|---|---|---|---|
           | Journey Step Events | identityMap  | timestamp | Mobile App Data | enable | enable |
           | ODE DecisionEvents - *sandbox name* decisioning | identityMap  | timestamp | Mobile App Data | enable | enable |
           | Luma Mobile App Event Dataset | identityMap  | timestamp | Mobile App Data | enable | enable |
           | AJO Push Tracking Experience Event Dataset | identityMap  | timestamp | Mobile App Data | enable | enable |



         - For lookup dataset:

           | Dataset | Key | Matching key | Data source type | Import all new data | Backfill all existing data |
           |---|---|---|---|---|---|

      1. Select Add datasets.





## Create a dataview




## Create a project


