---
title: Data Collection - Federated Audience Composition
description: Data Collection - Federated Audience Composition
kt: 5342
doc-type: tutorial
exl-id: a2449e72-794a-4ff0-a208-28303fd574d1
TQID: https://experienceleague.adobe.com/tSBmHGoMUXZoTV-ceFX9G6NN4-dtq5E5zK5OSKN-sPo
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: a37e4ecd-c740-426a-addf-cb1b483c5c5a
    internal-label: Segmentation
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: b784da9a-7978-4766-bf1f-5ab2b23d894a
    internal-label: Federated Audience Composition
  - id: d1823595-9241-4128-8a33-e4ac3bf08773
    internal-label: Audiences
  - id: d3f95e25-a50e-4fd0-bc23-9a22409a183b
    internal-label: Profile enrichment
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
    internal-label: Customer experience
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
    internal-label: Customer profiles
  - id: ff2b9b37-92e0-45fc-b853-379d44c08c89
    internal-label: Audience segmentation
---
# 1.3 Federated Audience Composition

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

[1.3.1 Setup your Snowflake environment](./ex1.md)

In this exercise, you'll setup your Snowflake trial account and you'll connect it to Adobe Experience Platform

[1.3.2 Create schemas, data model and links](./ex2.md)

In this exercise, you'll configure your data model in AEP for the federated data.

[1.3.3 Create a federated composition](./ex3.md)

In this exercise, you'll configure your data model in AEP for the federated data.

![Tech Insiders](./../../../../assets/images/techinsiders.png){width="50px"}

>[!NOTE]
>
>Thank you for investing your time in learning all there is to know about Adobe Experience Platform and its applications. If you have questions, want to share general feedback of have suggestions on future content, please contact Tech Insiders directly, by sending an email to **techinsiders@adobe.com**.

[Go Back to All Modules](./../../../../overview.md)
