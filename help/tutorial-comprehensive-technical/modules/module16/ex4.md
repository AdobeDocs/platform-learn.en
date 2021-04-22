---
title: Ingest & Analyze Google Analytics data in Adobe Experience Platform with the BigQuery Source Connector - Load data from BigQuery into Adobe Experience Platform
description: Ingest & Analyze Google Analytics data in Adobe Experience Platform with the BigQuery Source Connector - Load data from BigQuery into Adobe Experience Platform
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 94ee64a1-4e80-48e1-9442-ff30f6285045
---
# 16.4 Load data from BigQuery into Adobe Experience Platform

## Objectives

- Map BigQuery data to an XDM schema
- Load BigQuery data into Adobe Experience Platform
- Become familiar with the BigQuery Source Connector UI

## Before you start

After exercise 16.3, you should have this page open in Adobe Experience Platform:

![demo](./images/ex2/datasets.png)

**If you have it open, continue with exercise 16.4.1.**

**If you don't have it open, go to [Adobe Experience Platform](https://experience.adobe.com/platform/home).**

In the left menu, go to Sources. You'll then see the **Sources** homepage. In the **Sources** menu, click on **Databases**.

![demo](./images/ex4/0-a.png)

Select the **Google BigQuery** Source Connector and click on **+ Connect source**.

![demo](./images/ex4/0-b.png)

You'll then see the Google BigQuery Account selection screen.

![demo](./images/ex4/0-c.png)

Select your account and click **Next**.

![demo](./images/ex4/0-d.png)

You'll then see the **Add data** view.

![demo](./images/ex2/datasets.png)

## 16.4.1 BigQuery Table Selection

In the **Add data** view, select your BigQuery dataset. 

![demo](./images/ex4/1.png)

You can now see a sample data preview of the Google Analytics data in BigQuery.

Click **Next**.

![demo](./images/ex4/3.png)



## 16.4.2 XDM mapping

You'll now see the Mapping screen:

![demo](./images/ex4/4a.png)

You now have to either create a new dataset or select an existing dataset to load the Google Analytics data into. For this exercise, a dataset and schema have already been created. You do not need to create a new schema or dataset.

Select **Use existing dataset**.

![demo](./images/ex4/4.png)

Click the dataset icon to select an existing dataset:

![demo](./images/ex4/5.png)

Search for the dataset named `AEP Demo - BigQuery Website Interactions` and select it.

![demo](./images/ex4/6.png)

Next, click **Confirm**.

![demo](./images/ex4/7.png)

You now need to map every **Source Field** from Google Analytics/BigQuery to an XDM **Target Field**, field by field.

![demo](./images/ex4/8.png)

Use the below mapping table for this exercise.

| Source Field        | Target Field |   
| ----------------- |-------------| 
| **_id** | _id | 
| timeStamp | timestamp | 
| GA_ID | ``--aepTenantId--``.identification.gaid | 
| customerID | ``--aepTenantId--``.identification.crmId | 
| Page | ``--aepTenantId--``.gabqdata.page.pagetitle | 
| Landing_Page | ``--aepTenantId--``.gabqdata.page.landingpage | 
| Exit_Page | ``--aepTenantId--``.gabqdata.page.exitpage | 
| Device | ``--aepTenantId--``.gabqdata.useragent.device | 
| Browser | ``--aepTenantId--``.gabqdata.useragent.browser | 
| MarketingChannel | ``--aepTenantId--``.gabqdata.traffic.marketingchannel | 
| TrafficSource | ``--aepTenantId--``.gabqdata.traffic.trafficsource | 
| TrafficMedium | ``--aepTenantId--``.gabqdata.traffic.trafficmedium | 
| TransactionID | ``--aepTenantId--``.gabqdata.commerce.transactionid | 
| Ecommerce_Action_Type | ``--aepTenantId--``.gabqdata.commerce.actiontype | 
| Entries | ``--aepTenantId--``.gabqdata.behaviourevents.entries | 
| Pageviews | ``--aepTenantId--``.gabqdata.behaviourevents.pageviews | 
| Exits | ``--aepTenantId--``.gabqdata.behaviourevents.exits | 
| Bounces | ``--aepTenantId--``.gabqdata.behaviourevents.bounces | 
| Unique_Purchases | ``--aepTenantId--``.gabqdata.commerce.commerceevents.purchase | 
| Product_Detail_Views | ``--aepTenantId--``.gabqdata.commerce.commerceevents.productdetail | 
| Adds_To_Cart | ``--aepTenantId--``.gabqdata.commerce.commerceevents.addtocart | 
| Product_Removes_From_Cart | ``--aepTenantId--``.gabqdata.commerce.commerceevents.removeproduct | 
| Product_Checkouts | ``--aepTenantId--``.gabqdata.commerce.commerceevents.checkout | 
| Product_Refunds | ``--aepTenantId--``.gabqdata.commerce.commerceevents.refund | 

After copying and pasting the above mapping into the Adobe Experience Platform UI, please verify if you don't see any errors due to typos or leading/trailing spaces.

You now have a **Mapping** like this one:

![demo](./images/ex4/34.png)

The source fields **GA_ID** and **customerID** are mapped to an Identifier in this XDM Schema. This will allow you to enrich Google Analytics data (web/app behavior data) with other datasets such as Loyalty or Call Center-data.

Click **Next**.

![demo](./images/ex4/38.png)

## 16.4.3 Connection and the data ingestion scheduling

You'll now see the **Scheduling** tab:

![demo](./images/ex4/38a.png)

In the **Scheduling** tab, you are able to define a frequency for the data ingestion process for this **Mapping** and data. 

![demo](./images/ex4/40.png)

As you're using demo data in Google BigQuery that won't be refreshed, there's no real need for setting a schedule in this exercise. You do have to select something, and to avoid too many useless data ingestion processes, you need to set the frequency like this:

- Frequency: **Week**
- Interval: **200**

![demo](./images/ex4/39.png)

**Important**: be sure you activate the **Backfill** switch.

![demo](./images/ex4/39a.png)

Last but not least, you must define a **delta** field. 

![demo](./images/ex4/36.png)

The **delta** field is used to schedule the connection and upload only new rows that come into your BigQuery dataset. A delta field is typically always a timestamp column. So for future scheduled data ingestions, only the rows with a new, more recent timestamp will be ingested.

Select **timeStamp** as the delta field.

![demo](./images/ex4/37.png)

Click **Next**.

![demo](./images/ex4/42.png)

## 16.4.4 Review and launch connection

In the **Dataset flow detail** view. you need to name your connection, which will help you to find it later. 

Please use this naming convention:

| Field         | Naming| Example|   
| ----------------- |-------------| -------------|
| Dataset flow name| DataFlow - ldap - BigQuery Website Interaction | DataFlow - vangeluw - BigQuery Website Interaction  |
| Description | DataFlow - ldap - BigQuery Website Interaction | DataFlow - vangeluw - BigQuery Website Interaction|

![demo](./images/ex4/44.png)

Click **Next**.

![demo](./images/ex4/45.png)

You now see a detailed overview of your connection. Make sure everything is correct before you continue, as some settings can't be changed anymore afterwards, like for instance the XDM mapping.

![demo](./images/ex4/46.png)

Click **Finish**.

![demo](./images/ex4/finish.png)

Setting up the connection may take some time, so don't worry if you see this:

![demo](./images/ex4/47.png)

Once the connection has been created, you'll see this:

![demo](./images/ex4/48.png)

You're now ready to continue with the next exercise, in which you'll use Customer Journey Analytics to build powerful visualizations on top of Google Analytics data.

Next Step: [16.5 Analyze Google Analytics Data using Customer Journey Analytics](./ex5.md)

[Go Back to Module 16](./customer-journey-analytics-bigquery-gcp.md)

[Go Back to All Modules](./../../overview.md)
