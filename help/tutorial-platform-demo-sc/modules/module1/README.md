# Module 1: Data Ingestion

#### Author: [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)

---

In this foundational exercise, the goal is to learn all about data ingestion. You'll learn about data ingestion in Streaming and Batch. You'll implement Streaming Data Ingestion by using Launch, so that the customer behaviour on the Hands-On Lab website is streamed to Adobe Experience Platform in real-time. You'll learn about Batch Data Ingestion by using an Adobe Experience Platform Workflow to take a CSV-file, map it against an XDM-schema and then ingest it into Adobe Experience Platform. 

## Learning Objectives

- Learn how to create an XDM Schema in Adobe Experience Platform
- Learn how to create Datasets in Adobe Experience Platform
- Learn how to create a streaming endpoint and configure the Adobe Experience Platform extension in Launch
- Learn how to create Rules in Launch to stream data to Adobe Experience Platform
- Learn how to integrate Adobe Experience Platform Launch onto a webpage
- Learn how to use an Adobe Experience Platform Workflow to ingest a CSV-file into Adobe Experience Platform

## Your Environment Variables

This documentation has been created to be reused across multiple Adobe Experience Platform instances for enablement purposes.
In order to complete some of the modules, you'll need to change some variables and replace them by your specific ``Environment Variables``.

You can view these variables [here](../../environment.md).

## Content

### [Exercise 1 - Explore the website](./ex1.md)
In this exercise, you'll explore the website that we'll use as part of this enablement.

### [Exercise 2 - Configure Schema's and Set Identifiers](./ex2.md)
In this exercise, you'll configure the required XDM schema's to capture profile information and customer behavior. In every XDM schema, you'll also have to configure a primary identifier to link all the information to.

### [Exercise 3 - Configure Datasets](./ex3.md)
In this exercise, you'll retrieve the required datasets to capture and store profile information and customer behavior.

### [Exercise 4 - Use Launch and the Adobe Experience Platform Extension](./ex4.md)
In this exercise, you'll learn how to use the Adobe Experience Platform extension in Launch to stream data to Adobe Experience Platform.

### [Exercise 5 - Data Ingestion from Offline Sources](./ex5.md)
In this exercise, you'll go on the website and mobile app and behave like a customer, streaming data to Platform.

---

[Go Back to All Modules](../../README.md)