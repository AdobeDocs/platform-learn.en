---
title: Overview | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Overview
description: 
feature:
topics: 
kt: 4348
audience: data architect,data engineer
doc-type: tutorial
activity: implement
thumbnail: 4348-overview.jpg
---

# Getting Started with Adobe Experience Platform for Data Architects and Data Engineers

<!--5min-->

_Getting Started with Adobe Experience Platform for Data Architects and Data Engineers_ is the perfect starting point for Data Architects and Data Engineers to get hands-on with Experience Platform.


<!--How do we address ETL-->

## Learning Objectives

Data Architects and Data Engineers must closely collaborate for a successful Experience Platform deployment. This hands-on tutorial will teach you the key tasks executed by _both roles_ so you know how to get started implementing Experience Platform for your own business.  

Topics include: 

* Configuring user permissions
* Creating sandboxes
* Setting up a Developer Console project and using the Platform API
* Data management, including creating schemas, datasets, identities, merge policies, and data governance
* Data ingestion using batch and streaming modes
* Capturing web data with Adobe Experience Platform Launch and the Web SDK
* Combining data sources into Real-time Customer Profiles via identity stitching
* Using Query Service to validate data and extract data
* Building segments

## Business Scenario

Adobe Experience Platform is a technical platform designed to help you achieve marketing objectives. The business use cases should always be driving how you design and implement the technology. This tutorial focuses on a fictional retail brand called Luma. Luma operates brick-and-mortar stores in multiple countries and also has an online presence with a website and mobile apps. They are investing in Adobe Experience Platform to take their marketing to the next level by combining loyalty, CRM, web, and offline purchase data into real-time customer profiles and activating these profiles to accomplish business objectives. The business objectives of Luma may or may not align exactly with those of your own company, but we encourage you to take note of any ideas that may be sparked as you implement for Luma's objectives.

## Pre-requisites

* You have completed the [Introduction to Adobe Experience Platform course](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-U-1-2020.1) on Experience League and are familiar with Platform capabilities
* You have access to an account provisioned with Adobe Experience Platform and Adobe Experience Platform Launch.  
* You are a System Administrator of that account or can have one complete several tasks in the [Configure Permissions](configure-permissions.md) lesson.

## Using this tutorial

This tutorial combines tasks for both Data Engineers and Data Architects. Since this is an introductory-level tutorial, you should easily be able to complete the tasks for both roles. In each lesson, I call out the primary audience&mdash;Data Architects, Data Engineers, or both roles.  Because many of the lessons build on what was implemented in earlier lessons, you should move through the lessons in order. I will call out which lessons can be skipped. Of course, if you want to, you could also tag team the tutorial with a colleague in the other role.

Try to stick to the names assigned to various elements in the tutorial, as they are constantly referred to by these names. However, there are a few high level containers that you may want to customize the names in case there are multiple people at your organization taking this tutorial. For example, you may want to name the product profile "Luma Tutorial Platform - Fred Bean" instead of just "Luma Tutorial Platform."

If you get stuck, try re-reading the instructions first, and then use the "Log an Issue" link on the top right of each page to contact me. 

## Technical notes

### Sandbox environments

In the tutorial, you will create a sandbox environment and use it to complete the exercises. The sandbox environment makes it safe for you to complete the exercises and experiment without being concerned about compromising your production Experience Platform environment.

### API

Platform is built API-first. While interface workflows exist for all major Platform tasks and will be used in the majority of the exercises, this tutorial contains some API-oriented exercises. I will guide you through the basic project setup in the Adobe Developer Console and provide you with [!DNL Postman] environments and collections to get started with the API. After completing the tutorial, you may find it valuable to be familiar with the Platform API and use it in your own deployment.

### Third-party technologies

Although you will use multiple technologies in this tutorial, we will remain almost entirely within the Adobe ecosystem. In your own Platform implementation you will likely integrate Platform with specific third-party technologies. In order to keep this tutorial relevant for all customers, we will stick to a more generic implementation. 

