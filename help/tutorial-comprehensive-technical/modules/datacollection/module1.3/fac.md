---
title: Data Collection - Federated Audience Composition
description: Data Collection - Federated Audience Composition
kt: 5342
doc-type: tutorial
exl-id: 44660f3e-0594-4578-9531-1c918992aa9d
---
# 1.3 Federated Audience Composition

**Author: [Ludovic Latapie](https://www.linkedin.com/in/ludoviclatapie/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In this module, the goal is to learn all about creating audiences using Federated Audience Composition.

Federated Audience Composition (FAC) in Experience Platform enables you to access and create audiences with corresponding high-value attributes from enterprise data warehouses, which enrich and supplement the real-time customer profile and audiences in Experience Platform for improved segmentation, targeting, activation, and delivery of impactful customer experiences. Using Federated Audience Composition, a virtual database is created by linking remote databases through metadata. This approach simplifies access, reduces duplication, and enhances end-user experience. Teams are granted the flexibility to ingest datasets directly into Experience Platform or access datasets residing in data warehouses when assembling audiences for engagement workflows. This approach takes advantage of data warehouse investments and assets to complement Real-Time CDP and Journey Optimizer. Federated Audience Composition enables customers to utilize and combine batch and real-time functionality across critical new use-case patterns:

- Federated audience segmentation: A team can author an audience using the marketer-friendly drag-and-drop audience composition UI in Real-Time CDP and Journey Optimizer, but with a query pushed to the data warehouse, leaving sensitive underlying data in the warehouse without duplication and providing flexible access to essential datasets.
- Audience enrichment: Audiences built in Real-Time CDP and Journey Optimizer can be enriched with additional enterprise data to improve targeting and personalization with additional profile-based and non-profile-based datasets that will not persist in Adobe Experience Platform. For example, a retail brand may supplement an audience of recent online purchasers with a list of top brick-and-mortar locations to build an audience for a cross-channel online and in-store promotion.
- Profile enrichment: Teams can select profile attributes from the data warehouse that are critical for in-the-moment experiences to be retained within actionable customer profiles residing in Real-Time CDP and accessed via Journey Optimizer. These additional data points are then available for downstream segmentation and personalization triggered by event behaviors depending on the user action and customer use case. This will allow attributes brought along with federated audiences to be available for in-the-moment segmentation and personalization, alongside other attributes and behavioral signals retained in a customer profile.

Federated Audience Composition provides Real-Time CDP and Journey Optimizer customers with the flexibility to decide what data they want to use when and helps avoid unnecessarily duplicated datasets or integration patterns. This represents a unique combination of a federated approach to using enterprise data to curate audiences and high-value attributes, combined with a system optimized for in-the-moment cross-channel engagement. This results in less data movement, but also new opportunities to utilize high value audiences and attributes for consistent low-latency activation across channels.

## Learning Objectives

- Learn how to connect Snowflake with Adobe Experience Platform
- Learn how to create a data model for your federated data in Adobe Experience Platform
- Learn how to create federated audience compositions in Adobe Experience Platform

## Prerequisites

- Access to Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Access to a Snowflake data warehouse

## Exercises

[1.3.1 Setup your Snowflake account](./ex1.md)

In this exercise, you'll setup your Snowflake trial account and you'll connect it to Adobe Experience Platform

[1.3.2 Create schemas, data model and links](./ex2.md)

In this exercise, you'll configure your data model in AEP for the federated data.

[1.3.3 Create a federated composition](./ex3.md)

In this exercise, you'll configure your data model in AEP for the federated data.

[Summary and benefits](./summary.md)

Summary of this module and overview of the benefits.

>[!NOTE]
>
>Thank you for investing your time in learning all there is to know about Adobe Experience Platform and its applications. If you have questions, want to share general feedback of have suggestions on future content, please contact Tech Insiders directly, by sending an email to **techinsiders@adobe.com**.

[Go Back to All Modules](../../../overview.md)
