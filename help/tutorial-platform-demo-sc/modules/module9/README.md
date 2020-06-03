---
title: Module 9, Exercise - 
description: 
kt: 5342
audience: 
doc-type: tutorial
activity: 
---

# Module 9: Data Ingestion using Google Tag Manager and Google Analytics

**Author: [Gerard Lindeboom](https://www.linkedin.com/in/gerardlindeboom/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In **Module 9**, the following topics will be addressed:
  
* Configuration of Google Tag Manager
* Basic setup of Google Analytics
* Stream GA/GTM-data to Adobe Experience Platform in real-time

In this module, the goal is to install and configure Google Tag Manager and Google Analytics and connect them to Platform by capturing data from our SYTYCD-environment client-side and streaming it in real-time to Adobe Experience Platform.
This is to show that customers with an existing Google Analytics and Google Tag Manager implementation can also benefit from the power of Adobe Experience Platform, without limitations or latencies.

## Prerequisites

* You must have a working version of the AEP Demo - environment on your local machine to complete this module.

## Resources

* You will need a Google account. You can apply for one at [https://accounts.google.com/signup](https://accounts.google.com/signup).
* Using that Google account you can get access to Google Analytics
* You will setup and use Google Analytics on the AEP Demo website using Google Tag Manager [https://tagmanager.google.com](https://tagmanager.google.com)

## Story

After setting up our website, we now want to make sure that new Profile data (from sign-ups) and behavioral ExperienceEvent data (browsing habits, actionable triggers, etc) are recorded and updated in near real-time. We can do this by utilizing Google Tag Manager on our website. For this exercise, we will step into the shoes of the owners of Luma Retail, a fashion retail website, and see how we can bring in behavioral and profile data from website interactions into Experience Platform.

## Your Environment Variables

This documentation has been created to be reused across multiple Adobe Experience Platform instances for enablement purposes.
In order to complete some of the modules, you'll need to change some variables and replace them by your specific ``Environment Variables``.

You can view these variables [here](../../environment.md).

## Content

### [Exercise 9.0 - Create a Google Account](./ex0.md)

In this exercise, you'll set up a Google User Account. If you already have a Google User Account, you can skip this step.

### [Exercise 9.1 - Create a Google Tag Manager Property](./ex1.md)

In this exercise, you'll set up a Google Tag Manager property. You will use this on the AEP Demo website to manage the Google Analytics code and to send data to platform.

### [Exercise 9.2 - Setup Google Analytics & link it to GTM](./ex2.md)

In this exercise, you'll set up a Google Analytics property which will be used on your AEP Demo website.

### [Exercise 9.3 - Configure GTM Variables](./ex3.md)

In this exercise, you'll be configuring Data Elements so you can send data to Google Analytics and to Adobe Experience Platform.

### [Exercise 9.4 - Retrieve Data Sets in Platform](./ex4.md)

In this exercise, you'll retrieve data sets in Adobe Experience Platform.

### [Exercise 9.5 - Configure GTM Tags & Triggers](./ex5.md)

After the configuration of variables in your Google Tag Manager property and retrieving the configuration of your datasets in the Adobe Experience Platform UI, you're now ready to configure your Google Tag Manager Tags to send real data into Adobe Experience Platform.

### [Exercise 9.6 - Publish your GTM Property](./ex6.md)

With all GTM configuration done now, let's publish your Google Tag Manager property.

### [Exercise 9.7 - Implement GTM Tag on SYTYCD website](./ex7.md)

After publishing your Google Tag Manager property, you can now implement it on your SYTCD-website.

### [Exercise 9.8 - Activate GTM-tag in SYTYCD Admin](./ex8.md)

While creating your custom demo brand using SYTYCD, you can now activate the GTM Tag so that the GT Tag is loaded and sends calls to Adobe Experience Platform.

### [Exercise 9.9 - Verify Data Ingestion from website into Platform](./ex9.md)

With the implementation done now, you'll learn how you can verify your full implementation.

[Go Back to All Modules](../../README.md)
