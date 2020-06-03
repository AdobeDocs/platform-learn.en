---
title: Module 15, Exercise
description: 
kt: 5342
audience: 
doc-type: tutorial
activity: 
---

# Module 15: Data Science Workspace - Car Insurance Sales Propensity

**In Module 15**, you'll learn basic Data Science concepts, and also, how to use Adobe Experience Platform Data Science Workspace to build a Car Insurance Sales Propensity Model, schedule the model to re-train, and prepare the model for Real-time Scoring.

Please watch this video to understand the value, demo storyline and process: [Luma Insurance](http://bit.ly/lumainsurance)

## Key Takeaways

In this module, you'll learn:

- Understand the ``Luma Insurance`` Real-Time Machine Learning use-case
- How to use Anaconda and a local JupyterLab instance to interact with data in Adobe Experience Platform for building an ML Model
- How to operationalize a ML Model by creating a Recipe to then train and score that Recipe.
- How to publish a Recipe as a Service for recurring, automated training.

## Business Context

Luma Insurance is a typical Insurance Company with a big offline dealer-network and a website with lots of traffic.
Luma Insurance has been trying to personalize their digital communication for years, but it’s very hard to personalize anything if you don’t know who you’re speaking to. As most of the traffic on the website is from unknown, anonymous users who only visit the website once or twice, it’s difficult for Luma Insurance to build out a deep customer profile.

Most of these unknown, anonymous visitors only come to the website with one goal: get a quick indication of the cost of an insurance, by filling out a form which then gives them an idea of the insurance cost.

Because of this limited amount of information, Luma Insurance has a hard time optimizing any kind of digital campaign which leads to prospects being bombarded with irrelevant and inconsistent messaging.

As a consequence, Luma Insurance can’t understand which customer are interesting targets and which customers aren’t, they’re unable to optimise their ad spend and they’re unable to understand which channels are best used to interact with any given customer.

## Your Environment Variables

This documentation has been created to be reused across multiple Adobe Experience Platform instances for enablement purposes.
In order to complete some of the modules, you'll need to change some variables and replace them by your specific ``Environment Variables``.

You can view these variables [here](../../environment.md).

## Content

### Exercise 15.1 - Introduction to Luma Insurance

[Exercise 15.1 - Introduction to Luma Insurance](./ex1.md)

In this exercise, you'll learn how to use the Luma Insurance Demo Brand and how to demo the Real-time ML Use-Case.

### Exercise 15.2 - Interact with data in Adobe Experience Platform from a local JupyterLab environment

[Exercise 15.2 - Interact with data in Adobe Experience Platform from a local JupyterLab environment](./ex2.md)

In this exercise, you'll install Anaconda on your local machine so you can run Jupyter Notebooks on your local machine, to then interact with the data in Adobe Experience Platform through the Query Service.

### Exercise 15.3 - Operationalize your model using a Recipe

[Exercise 15.3 - Operationalize your model using a Recipe](./ex3.md)

In this exercise, you'll take your model and operationalize it in Adobe Experience Platform by creating a Recipe.

### Exercise 15.4 - Train and Score your Recipe

[Exercise 15.4 - Train and Score your Recipe](./ex4.md)

After creating a Recipe, you can now Train and Score your Recipe without having to touch code again.

### Exercise 15.5 - Publish your Recipe as a Scheduled Service

[Exercise 15.5 - Publish your Recipe as a Scheduled Service](./ex5.md)

Finally, you can select your best experiment and Publish it as a Scheduled Service which will score customers and their propensity to buy on a recurring basis.

### [FAQ](./qa.md)

[Go Back to All Modules](../../README.md)
