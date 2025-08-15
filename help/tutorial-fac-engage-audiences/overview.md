---
title: Engage with audiences directly from your data warehouse using Federated Audience Composition overview
description: Federated Audience Composition is a powerful feature that enables data architects and data engineers to curate and activate high-value audiences directly from supported data warehouses.
breadcrumb-title: Overview
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-overview.jpg
recommendations: catalog, noDisplay
last-substantial-update: 2025-08-11
exl-id: 9d5a2e40-6cda-4164-87db-1bfffe3438e3
---
# Engage with audiences directly from your data warehouse using Federated Audience Composition overview

Federated Audience Composition (FAC) is a module for Adobe Real-Time Customer Data Platform (Real-Time CDP) and Adobe Journey Optimizer. It is also, available with Adobe Real-Time CDP Composable Audiences ( a tailored solution for customers as a Composable CDP). It empowers data architects and data engineers to curate and activate high-value audiences directly from [supported enterprise data warehouses](https://experienceleague.adobe.com/en/docs/federated-audience-composition/using/start/access-prerequisites){target="_blank"}, without copying or moving customer data into Adobe Experience Platform (AEP). This composable CDP approach (a tailored solution for customers) aligns with industry trends, enabling businesses to leverage their data infrastructure for personalized digital experiences while maintaining data governance.

## Business context

SecurFinancial is a leading financial services firm. It leverages its wealth of customer data across disparate sources to personalize offers and campaigns for a large number of segments. They plan to use Adobe Real-Time CDP Federated Audience Composition module which allows businesses to use their data warehouse for data management while using Adobe Experience Platform for delivering personalized customer experiences. Key benefits include:

- **Access to warehouse data**: Create high-value audiences from datasets in supported data warehouses without data replication.
- **Minimized data movement**: Query data directly in the warehouse, without duplication and maintaining data governance.
- **Unified Experience Workflows**: Curate and activate audiences within Adobe Experience Platform for cross-channel use cases.
- **Enhanced personalization**: Enrich profiles and audiences with warehouse attributes to power real-time, triggered experiences.

## Business scenario

SecurFinancial would like to launch an email campaign to retarget its customers who are prequalified for a loan based on good credit and do not have an active loan in their SecurFinancial portfolio. While they are ingesting online behavioral data in real time, they face challenges in identifying customer pre-qualification, as they are restricted from ingesting credit information into AEP. To qualify pre-qualified customers without moving restricted data, they will use Federated Audience Composition to enrich their AEP behavioral audience.

## Guide

This guide demonstrates how we support the SecureFinancial Business scneario. Specfically, it covers how we expose audiences to systems that need these audiences, including an S3 storage account, a journey in Journey Optimizer to drive an email campaign, and onsite retargeting to customers who were pre-approved for a loan.

The steps, include:

1. Connect Adobe Experience Platform to an enterprise data warehouse.
2. Create an audience using Federated Audience Composition.
3. Map a federated audience to external Amazon S3 destination.
4. Build a customer journey using federated audience data.
5. Enrich an audience with federated data.
6. Drive "in-the-moment" personalization on the Edge.

## Prerequisites

To perform similar activities in your envrionment, ensure you have:

- Access to an Adobe Experience Platform account provisioned with Real-Time CDP or Journey Optimizer.
- System Administrator permissions or the ability to have permissions configured.
- Familiarity with Adobe Experience Platform concepts, such as schemas, datasets, and audiences (recommended: complete the [Introduction to Adobe Experience Platform playlist](https://experienceleague.adobe.com/en/playlists/experience-platform-introduction?lang=en){target="_blank"} on Experience League).
- Access to a supported [enterprise data warehouse](https://experienceleague.adobe.com/en/docs/federated-audience-composition/using/start/access-prerequisites){target="_blank"}. 
- Basic knowledge of SQL for querying data warehouses.
- **Sandbox Environments**: Create a sandbox in your organization's instance to safely experiment without affecting production data.
- **Data Warehouse Connection**: This tutorial uses a Snowflake connection, but you can use any [supported data warehouse](https://experienceleague.adobe.com/en/docs/federated-audience-composition/using/start/access-prerequisites).

First, let's review the [High-level Architecture & Flow for Federated Audience Composition](fac-architecture-and-flow.md).
