---
title: Overview | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
description: 
feature:
topics: 
kt: 4348
audience: data architect,data engineer
doc-type: tutorial
activity: implement
---

# Overview

_Getting Started with Adobe Experience Platform for Data Architects and Data Engineers_ is the perfect starting point for Data Architects and Data Engineers to get hands-on with Experience Platform.


<!--How do we address ETL-->

## Learning Objectives

Data Architects and Data Engineers need to collaborate closely for a successful Experience Platform deployment. This tutorial takes you through the key tasks executed by both roles so you can see how the efforts come together, including: 

* Configuring user permissions
* Creating sandboxes
* Setting up an Adobe IO project and using the Platform API
* Data management, including creating schemas, datasets, identities, merge policies, and data governance
* Data ingestion using batch and streaming modes
* Capturing web data with Adobe Experience Platform Launch and the Web SDK
* Combining data sources into Real-time Customer Profiles
* Using Query Service to validate data and extract data
* Building segments

## Business Scenario

Adobe Experience Platform is a technical platform designed to help you achieve marketing objectives. The business use cases should always be driving how you design and implement the technology. This tutorial focuses on a fictional retail brand called Luma. Luma operates brick-and-mortar stores in multiple countries and also has an online presence with a website and mobile apps. They are investing in Adobe Experience Platform to take their marketing to the next level by combining loyalty, CRM, web, and offline purchase data into real-time customer profiles and activating these profiles to accomplish business objectives. The business objectives of Luma may or may not align exactly with those of your own company, but we encourage you to take note of any ideas that may be sparked as you implement for Luma's objectives.

## Pre-requisites

* You have completed the [Introduction to Adobe Experience Platform course](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-U-1-2020.1) on Experience League and are familiar with Platform capabilities
* You have access to an Adobe Experience Cloud account with Adobe Experience Platform provisioned.  If you are not a System Administrator of that account, you will need one to help get you started by completing some of the steps in the [Configure Permissions](configure-permissions.md) lesson.

## Technical notes

### Sandbox environments

In the tutorial, you will create a sandbox environment and use it to complete the exercises. The sandbox environment makes it safe for you to complete the exercises and experiment with Platform without being concerned about compromising your Production environment.

### API

Platform is built API-first. While interface methods exist for all major Platform tasks and will be used in the majority of the exercises, this tutorial contains some exercises that use the API. We will guide you through the basic project setup in the Adobe Developer Console and provide you with a Postman Collection to make the necessary API calls. After completing the tutorial, you will find it valuable to be familiar with the Platform API and use it in your own deployment.

### Third-party technologies

Although you will use multiple technologies in this tutorial, we will remain almost entirely within the Adobe ecosystem. In your own Platform implementation you will likely integrate Platform with specific third-party technologies. In order to keep this tutorial relevant for all customers, we will stick to a more generic implementation. There are however, other enablement materials which may address the details of specific third-party tools and we will link to those where relevant.

