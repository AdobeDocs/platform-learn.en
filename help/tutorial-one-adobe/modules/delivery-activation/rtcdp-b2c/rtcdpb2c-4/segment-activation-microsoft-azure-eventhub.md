---
title: Audience Activation to Microsoft Azure Event Hub
description: Audience Activation to Microsoft Azure Event Hub
kt: 5342
doc-type: tutorial
---
# 2.4 Real-Time CDP: Audience Activation to Microsoft Azure Event Hub

In this module, you'll setup a Microsoft Azure EventHub destination as a real-time destination for Adobe Experience Platform Real-time CDP. You will also setup and deploy an Azure function that will be triggered in real-time whenever Adobe Experience Platform delivers an audience payload to your Azure EventHub destination. The Azure Function that you'll trigger will show the mechanism of Adobe Experience Platform Real-time CDP's activation capabilities.

As part of this module you will also get an understanding of what triggers Real-time CDP to actually deliver a payload to a specified destination. We will also discuss the status of an audience qualification and how it relates to activation.

Adobe Experience Platform Real-time CDP supports data activation to streaming cloud storage destinations, allowing you to export audience data and events in real-time to these destinations in JSON format. You can then describe business logic on top of these events in your destinations

Microsoft Azure Event Hubs is a fully managed, real-time data ingestion service that’s simple, trusted, and scalable. Stream millions of events per second from any source to build dynamic data pipelines and immediately respond to business challenges.

## Learning Objectives

- Become familiar with the Microsoft Azure Event Hubs
- Setup an RTCDP destination to your Microsoft Azure Event Hub
- Understand when Real-time CDP activates and what the activation payload looks like
- Setup Visual Studio Code to develop, test and deploy your Azure project
- Create and deploy an Azure function that consumes audience qualifications delivered in real-time by RTCDP

## Prerequisites

- Access to [Adobe Experience Platform](https://experience.adobe.com/platform)
- Understand how to define, use and activate audiences in Adobe Experience Platform

>[!NOTE]
>
>Don't forget to install, configure and use the Chrome Extension as referenced in [Install the Chrome extension for the Experience League documentation](../../gettingstarted/gettingstarted/ex1.md)

## Exercises

[2.4.1 Configure your environment](./ex1.md)

In this exercise, you'll setup your Microsoft Azure environment.

[2.4.2 Configure your Microsoft Azure EventHub environment](./ex2.md)

In this exercise you'll setup your Microsoft Azure EventHub environment.

[2.4.3 Configure your Azure Event Hub Destination in Adobe Experience Platform](./ex3.md)

In this exercise you'll setup your Real-time CDP destination connection that will deliver audiences in real-time to the Event Hub instance that you've configured in the previous exercise.

[2.4.4 Create an audience](./ex4.md)

In this exercise you will create an audience in Adobe Experience Platform

[2.4.5 Activate your audience](./ex5.md)

In this exercise you'll activate your audience to your  EventHub destination.

[2.4.6 Create your Microsoft Azure Project](./ex6.md)

In this exercise you will create an Azure function that will be triggered in real-time when Adobe Experience platform delivers audience qualifications to the corresponding Azure Event Hub destination.

[2.4.7 End-to-end scenario](./ex7.md)

At this point, everything is setup. You can now do some browsing on your demo website and get audience qualifications delivered to your Microsoft Azure Event Hub Trigger function.  

[Summary and benefits](./summary.md)

Summary of this module and overview of the benefits.

![Tech Insiders](./../../../../assets/images/techinsiders.png){width="50px" align="left"}

>[!NOTE]
>
>Thank you for investing your time in learning all there is to know about Adobe Experience Platform and its applications. If you have questions, want to share general feedback of have suggestions on future content, please contact Tech Insiders directly, by sending an email to **techinsiders@adobe.com**.

[Go Back to All Modules](./../../../../overview.md)
