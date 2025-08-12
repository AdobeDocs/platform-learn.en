---
title: Unlock cross-channel insights with Federated Audience Composition
description: Federated Audience Composition is a powerful feature that enables data architects and data engineers to build and enrich audiences directly from third-party data warehouses.
breadcrumb-title: Overview
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-overview.jpg
recommendations: catalog, noDisplay
last-substantial-update: 2025-08-11
exl-id: 9d5a2e40-6cda-4164-87db-1bfffe3438e3
---
# Overview

Federated Audience Composition is a powerful feature available for Adobe Real-Time Customer Data Platform (Real-Time CDP) and Adobe Journey Optimizer environments. It enables data architects and data engineers to build and enrich audiences directly from [supported](https://experienceleague.adobe.com/en/docs/federated-audience-composition/using/start/access-prerequisites){target="_blank"} third-party data warehouses without replicating data into Adobe Experience Platform. This tutorial provides hands-on guidance for technical users to connect enterprise data warehouses, create and enrich audiences, and activate them for personalized marketing experiences.

## Learning Objectives

By completing this tutorial, you will:

- Understand how to connect Adobe Experience Platform to an enterprise data warehouse.
- Learn to create and manage audiences using Federated Audience Composition.
- Explore how to enrich existing audiences with warehouse data.
- Map federated audiences to external destinations like Amazon S3.
- Build customer journeys using federated audience data.
- Validate data and processes through hands-on exercises and demos.

This tutorial is designed for data architects and data engineers working with Real-Time CDP or Journey Optimizer. It assumes familiarity with Adobe Experience Platform and basic data warehouse concepts.

## Business Context

SecurFinancial is a leading financial services firm. It leverages its wealth of customer data across disparate sources to personalize offers and campaigns for a large number of segments. They plan to use Adobe's Real-Time CDP Federated Audience Composition feature which allows businesses to use their existing data warehouse while using Adobe Experience Platform's applications to deliver personalized customer experiences. Key benefits include:

- **Access to warehouse data**: Create high-value audiences from datasets in supported data warehouses without data replication.
- **Minimized data movement**: Query data directly in the warehouse, reducing duplication and maintaining data governance.
- **Unified experience workflows**: Curate and activate audiences within Adobe Experience Platform for cross-channel use cases.
- **Enhanced personalization**: Enrich profiles and audiences with warehouse attributes to power real-time, triggered experiences.

## Business Scenario

SecurFinancial would like to launch an email campaign to retarget its customers who are prequalified for a loan based on good credit and do not have an active loan in their SecurFinancial portfolio. While they are ingesting online behavioral data in real time, they face challenges in identifying customer prequalification, as they are restricted from ingesting credit information into AEP. To qualify prequalified customers without moving restricted data, they will use Federated Audience Composition to enrich their AEP behavioral audience.



## Prerequisites

To follow this tutorial, ensure you have:

- Access to an Adobe Experience Platform account provisioned with Real-Time CDP or Journey Optimizer.
- System Administrator permissions or the ability to have permissions configured.
- Familiarity with Adobe Experience Platform concepts, such as schemas, datasets, and audiences (recommended: complete the [Introduction to Adobe Experience Platform playlist](https://experienceleague.adobe.com/en/playlists/experience-platform-introduction?lang=en){target="_blank"} on Experience League).
- Access to a supported enterprise data warehouse (e.g., Amazon Redshift, Azure Synapse Analytics, Snowflake, or Google BigQuery).
- Basic knowledge of SQL for querying data warehouses.

## Using This Tutorial

This tutorial is structured for technical users. Lessons build on each other, so complete them in order unless otherwise noted. 

## Technical Notes

- **Sandbox Environments**: Create a sandbox in your organization's Real-Time CDP instance to safely experiment without affecting production data.
- **Data Warehouse Connection**: This tutorial uses a Snowflake connection, but you can use any [supported cloud warehouse](https://experienceleague.adobe.com/en/docs/federated-audience-composition/using/start/access-prerequisites).

Start with the [Data Warehouse Connection](data-warehouse-connection.md) lesson to begin configuring your environment.
