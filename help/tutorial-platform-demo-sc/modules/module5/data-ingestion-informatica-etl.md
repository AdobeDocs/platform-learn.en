---
title: Extract, Transform, Load data using a 3rd party ETL-tool
description: Extract, Transform, Load data using a 3rd party ETL-tool
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: 
---

# 5. Extract, Transform, Load data using a 3rd party ETL-tool

**Authors: [Marius Shehati](https://www.linkedin.com/in/mshehati/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In **Module 5**, the following topics will be addressed:

- ETL Overview
- How to set up Adobe Experience Platform - ETL integration
- Upload data in an ETL-tool, join the data, enrich the data and push it to Platform.

## Learning Objectives

- Learn how to setup an AWS S3 bucket
- Learn how to use Informatica ETL
- Learn how to setup a connector from Informatica to your AWS S3 bucket
- Learn how to build a mapper workflow to extract data, transform data and eventually, load that data into a dataset in Adobe Experience Platform

## Prerequisites

- Access to Adobe Experience Platform: [https://platform.adobe.com](https://platform.adobe.com)
- Access to Informatica ETL
- Access to AWS S3
- This documentation has been created to facilitate hands-on, technical enablement around Adobe Experience Platform. In order to complete some of the modules, you'll need to change some variables and replace them by your specific **Environment Variables**. Please contact your Adobe contact who will provide you with the required **Environment Variables** of your specific Adobe Experience Platform instance.

>[!NOTE]
>
>If you don't have access to your own Adobe Experience Platform instance, don't let it stop you! You'll still learn a lot by reading through these very detailed tutorials.

## Business Context

Luma Retail is a fashion brand and in addition to its online presence, has brick and mortar stores all over the world. So far the marketing team has struggled to make use of the offline orders data to optimize their online experience. Recently, they introduced a new loyalty program that allows customers to collect points when purchasing in store using their loyalty card. The marketing team receives regularly a flat file with all the offline orders as well and has a record of all customers who have joined the loyalty program. With the help of Informatica, we will join the two data sources, enrich the result so that it can be ingested into Adobe Experience Platform, then hydrate the profile with the offline order events.

Luma Retail also has a partnership with Survey corp which has agreed to share their latest survey results on people preferences on designers, colors, and brands. Luma Retail has also decided to buy some demographics data from a marketplace from Money Corp, providing details on people income and credit score. By combining these two data sets Luma Retail is aiming to target their customer with more meaningful experiences based on their their preferences as well as income.

## Exercises

### 5.1 Setup an AWS S3 bucket

In this exercise, you'll learn how to setup an AWS S3 bucket in your own AWS environment and how to upload data in that S3 bucket.

Go to [5.1 Setup an AWS S3 bucket](./ex1.md)

### 5.2 Connect Informatica to your AWS S3 bucket

In this exercise, you'll create a connection in Informatica to read data from your AWS S3 bucket.

Go to [5.2 Connect Informatica to your AWS S3 bucket](./ex2.md)

### 5.3 Ingest Offline Order Events into Adobe Experience Platform

In this exercise, you'll learn how to import order data into Informatica, join datasets and ingest transformed data into Adobe Experience Platform as Experience Events.

Go to [5.3 Ingest Offline Order Events into Adobe Experience Platform](./ex3.md)

### 5.4 Ingest 2nd and 3rd party data into Adobe Experience Platform

In this exercise, you'll learn how to import 2nd and 3rd party data into Informatica, join datasets and ingest transformed data into Adobe Experience Platform as Experience Events.

Go to [5.4 Ingest 2nd and 3rd party data into Adobe Experience Platform](./ex4.md)

>[!NOTE]
>
>Thank you for investing your time in learning all there is to know about Adobe Experience Platform. If you have questions, want to share general feedback of have suggestions on future content, please contact Wouter Van Geluwe directly, by sending an email to **vangeluw@adobe.com**.

[Go Back to All Modules](../../overview.md)
