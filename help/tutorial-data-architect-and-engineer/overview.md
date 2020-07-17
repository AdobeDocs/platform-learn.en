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

The roles of the Data Architect and Data Engineer are intertwined in a Platform deployment. The Data Architect designs a schema which the Data Engineer uses to map the data they ingest. Because of this co-dependent relationship, this tutorial takes you through the key tasks executed by both roles to provide a comprehensive overview of a Platform deployment. Along the way we will point out which role needs to accomplish which task, so you will know when to pay attention and take notes.

## What you will do

In this tutorial you will complete many tasks in Adobe Experience Platform, including:

* Create a Sandbox
* Configure the Platform API in Adobe IO
* Set up Postman Environment
* Create Schemas
* Create Datasets (one streaming, one batch)
* ETL
* Identity labels
* Merge Policies
* DULE Labels
* Data Usage Policies
* Ingest Batch data (csv in UI, mention sources)
* Ingest Streaming data (experience edge with Launch)
* Queries to Validate data
* Queries to extract data
* Build segments

## Business Scenario

Adobe Experience Platform is a technical platform designed to help you achieve marketing objectives. The business use cases should always be driving how you design and implement the technology. This tutorial focuses on a fictional retail brand called Luma. Luma operates brick-and-mortar stores in multiple countries and also has an online presence with a website and mobile apps. They are investing in Adobe Experience Platform to take their marketing to the next level by combining their various data sources into real-time customer profiles and activating these profiles to accomplish business objectives. The business objectives of Luma may or may not align with those of your own company, but we encourage you to take note of any ideas that may be sparked as you implement for Luma's objectives.

## Pre-requisites

* You have completed the Introduction to Adobe Experience Platform course on Experience League and are familiar with the basic capabilities of Platform
* You have access to a Platform instance and have the ability to do the following (more details on each of these will be provided in the relevant lesson)
* You have Postman and are familiar with how to use it

## Technical notes

You will use multiple technologies in this tutorial, although it is worth noting that we will stick mostly in the Adobe ecosystem. In a real Platform implementation you will be integrating Platform with specific third-party technologies. In order to keep this tutorial relevant for all customers, we will stick to a more generic implementation which does not require access to any specific third-party technologies which might be difficult to obtain. There are however, other enablement materials which may address the details of specific third-party tools and we will link to those where relevant.

### Sandboxes

This tutorial assumes you are already have a Platform account provisioned. Within your account, you will create a sandbox environment which you will use to complete this tutorial. The sandbox environment makes it safe for you to complete the exercises and experiment with Platform without being concerned about compromising your Production environment.

### API

Platform is built API-first. While interface methods exist for all major Platform tasks and will be used in the majority of the exercises, this tutorial contains some exercises that use the API. We will guide you through the basic project setup in the Adobe IO console and provide you with a Postman Collection to make the necessary API calls. After completing the tutorial, you will find it valuable to be familiar with the Platform API and use it in your own deployment to take advantage of brand new features for the UI has not been released and to copy assets from one sandbox environment to another,


