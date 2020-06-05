---
title: Data Science Workspace - Car Insurance Sales Propensity
description: Data Science Workspace - Car Insurance Sales Propensity
kt: 5342
audience: Data Engineer, Data Architect, Data Scientist
doc-type: tutorial
activity: 
---

# 15. Data Science Workspace - Car Insurance Sales Propensity

**In Module 15**, you'll learn basic Data Science concepts, and also, how to use Adobe Experience Platform Data Science Workspace to build a Car Insurance Sales Propensity Model, schedule the model to re-train, and prepare the model for Real-time Scoring.

Please watch this video to understand the value, demo storyline and process: [Luma Insurance](http://bit.ly/lumainsurance)

## Learning Objectives

In this module, you'll...

- Understand the **Luma Insurance** Real-Time Machine Learning use-case
- Learn how to use Anaconda and a local JupyterLab instance to interact with data in Adobe Experience Platform for building an ML Model
- Learn how to operationalize a ML Model by creating a Recipe to then train and score that Recipe.
- Learn how to publish a Recipe as a Service for recurring, automated training.

## Resources

- Access to Adobe Experience Platform: [https://platform.adobe.com](https://platform.adobe.com) 
- Access to Anaconda
- Access to the zip-file containing the 2 required notebooks

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

## Business Context

Luma Insurance is a typical Insurance Company with a big offline dealer-network and a website with lots of traffic.
Luma Insurance has been trying to personalize their digital communication for years, but it’s very hard to personalize anything if you don’t know who you’re speaking to. As most of the traffic on the website is from unknown, anonymous users who only visit the website once or twice, it’s difficult for Luma Insurance to build out a deep customer profile.

Most of these unknown, anonymous visitors only come to the website with one goal: get a quick indication of the cost of an insurance, by filling out a form which then gives them an idea of the insurance cost.

Because of this limited amount of information, Luma Insurance has a hard time optimizing any kind of digital campaign which leads to prospects being bombarded with irrelevant and inconsistent messaging.

As a consequence, Luma Insurance can’t understand which customer are interesting targets and which customers aren’t, they’re unable to optimize their ad spend and they’re unable to understand which channels are best used to interact with any given customer.

## Exercises

### 15.1 Introduction to Luma Insurance

In this exercise, you'll learn how to use the Luma Insurance Demo Brand and how to demo the Real-time ML Use-Case.

Go to [15.1 Introduction to Luma Insurance](./ex1.md)

### 15.2 Interact with data in Adobe Experience Platform from a local JupyterLab environment

In this exercise, you'll install Anaconda on your local machine so you can run Jupyter Notebooks on your local machine, to then interact with the data in Adobe Experience Platform through the Query Service.

Go to [15.2 Interact with data in Adobe Experience Platform from a local JupyterLab environment](./ex2.md)

### 15.3 Operationalize your model using a Recipe

In this exercise, you'll take your model and operationalize it in Adobe Experience Platform by creating a Recipe.

Go to [15.3 Operationalize your model using a Recipe](./ex3.md)

### 15.4 Train and Score your Recipe

After creating a Recipe, you can now Train and Score your Recipe without having to touch code again.

Go to [15.4 Train and Score your Recipe](./ex4.md)

### 15.5 Publish your Recipe as a Scheduled Service

Finally, you can select your best experiment and Publish it as a Scheduled Service which will score customers and their propensity to buy on a recurring basis.

Go to [15.5 Publish your Recipe as a Scheduled Service](./ex5.md)

### FAQ

Go to [FAQ](./qa.md)

>[!NOTE]
>
>Thank you for investing your time in learning all there is to know about Adobe Experience Platform. If you have questions, want to share general feedback of have suggestions on future content, please contact Wouter Van Geluwe directly, by sending an email to **vangeluw@adobe.com**.

[Go Back to All Modules](../../overview.md)
