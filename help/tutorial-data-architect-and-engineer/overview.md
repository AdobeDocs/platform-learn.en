---
title: Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
description: Get started with Adobe Experience Platform for Data Architects and Data Engineers.
breadcrumb-title: Overview
role: Developer
jira: KT-4348
thumbnail: 4348-overview.jpg
recommendations: catalog, noDisplay
last-substantial-update: 2023-06-21T00:00:00.000Z
exl-id: fabbc591-840b-40dc-89af-305626a16338
TQID: https://experienceleague.adobe.com/c7kjzg6YbnanyIJrk2SSQiz---KYOuA8JlbJYWp69ww
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: a230274e-7e6e-49eb-b817-514495a710ac
    internal-label: query service
  - id: d1a87129-ba05-4f15-98b1-233618f1774a
    internal-label: Data ingestion
  - id: de9975b2-c43a-4287-9698-4f4cad92b83f
    internal-label: Schemas
  - id: e0c8953a-a203-4291-bef3-3560160d3041
    internal-label: Get started
  - id: ee602049-8a18-43df-9299-a689a025a371
    internal-label: Use cases
  - id: f5efb499-54f9-432b-ac5c-599dbac103af
    internal-label: Data management
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c7d04a2c-412a-4c9d-9d7a-4456eaa5adeb
    internal-label: Governance
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
    internal-label: Data management
  - id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
    internal-label: Customer profiles
---
# Getting Started with Adobe Experience Platform for Data Architects and Data Engineers

<!--5min-->

_Getting Started with Adobe Experience Platform for Data Architects and Data Engineers_ is the perfect starting point to get hands-on with Experience Platform.


<!--How do we address ETL-->

## Learning Objectives

Data Architects and Data Engineers must closely collaborate for a successful Experience Platform deployment. This hands-on tutorial teaches you the key tasks executed by _both roles_ so you know how to start implementing Platform for your own business. You will be guided through exercises that will introduce you to the key terminology, features, interface, and APIs of Experience Platform. Customers of Adobe Experience Cloud applications like Real-Time Customer Data Platform, Customer Journey Analytics, and Journey Optimizer will also find this content useful, as Platform services are critical foundations of those applications.

![Adobe Experience Cloud marketecture highlighting the Platform services covered in this tutorial--Identity, Profile, Segmentation, Ingestion, Query, and Governance](assets/marketecture.png)

Topics include: 

* Configuring user permissions
* Creating sandboxes
* Setting up a Developer Console project and using the Platform API
* Data management&mdash;including creating schemas, datasets, identities, merge policies, and data governance
* Data ingestion using batch and streaming modes
* Capturing web data with Adobe Experience Platform Web SDK
* Building Real-Time Customer Profiles
* Using Query Service to validate data and extract data
* Building segments

## Business Scenario

Adobe Experience Platform is a technical platform designed to help you achieve marketing objectives. The business use cases should drive how you design and implement the technology. This tutorial focuses on a fictional retail brand called Luma. Luma operates brick-and-mortar stores in multiple countries and also has an online presence with a website and mobile apps. They are investing in Adobe Experience Platform to combine loyalty, CRM, web, and offline purchase data into real-time customer profiles and activate these profiles to take their marketing to the next level. The business objectives of Luma may or may not align with the objectives of your company, but you should be able to relate the hands-on steps in this tutorial to your own business objectives.

## Pre-requisites

* You have watched the [Introduction to Adobe Experience Platform playlist](https://experienceleague.adobe.com/en/playlists/experience-platform-introduction) on Experience League and are familiar with Platform capabilities
* You have access to an account provisioned with Adobe Experience Platform (or a Platform-based application such as Real-Time CDP or Journey Optimizer) and Data Collection (formerly Launch).  
* You are a System Administrator of that account or can have one [configure user permissions](configure-permissions.md) for you.

## Using this tutorial

This tutorial combines tasks for both Data Engineers and Data Architects. Since it's an introductory-level tutorial, you should be able to complete the tasks for both roles. Because many of the lessons build on what was implemented in earlier lessons, you should move through the lessons in order. I will call out which lessons can be skipped.

As you create various Platform elements during this tutorial, try to stick to the names I recommend as much as possible. However, there are a few high-level element names that you may want to customize in case there are multiple people at your organization taking this tutorial simultaneously. For example, you may want to name the Platform sandbox "Luma Tutorial Platform - Ignatius J Reilly" instead of just "Luma Tutorial Platform."

If you get stuck, try re-reading the instructions first, and then use the ![Log an issue](https://experienceleague.adobe.com/assets/img/feedback.svg) link on the sidebar of each page to contact me. 

## Technical notes

### Sandbox environments

In the tutorial, you will create a sandbox environment and use it to complete the exercises. The sandbox environment makes it safe for you to complete the exercises and experiment without being concerned about compromising your production data.

### API

Platform is built API-first. While interface workflows exist for all major Platform workflows and will be used primarily, the tutorial contains some API-oriented exercises. I will guide you through the basic project setup in the Adobe Developer Console and provide you with [!DNL Postman] environments and collections to get started with the Platform API. After completing the tutorial, you may find it valuable to be familiar with the Platform API and use it in your own deployment.

### Third-party technologies

Although you will use multiple technologies in this tutorial, you will remain almost entirely within the Adobe ecosystem. In your own Platform implementation, you will likely integrate Platform with specific third-party technologies. To keep this tutorial relevant for all customers, we will use a more generic implementation. 

## Tutorial updates

* June 2023: Updated to include new Permission workflow and to use OAuth Server-to-Server API credential


Now let's move on to the first lesson&mdash;[configure permissions](configure-permissions.md).
