---
title: Federated Audience Composition High-level Architecture & Flow
seo-title: Federated Audience Composition high-level architecture & flow | Engage with audiences directly from your data warehouse using Federated Audience Composition
breadcrumb-title: Federated Audience Composition high-level architecture & flow
description: Overview of the high-level architecture and flow of Federated Audience Composition.
role: Developer
jira: KT-18743
thumbnail: 18743-high-level-architecture.jpg
exl-id: 4cb0b730-4206-476b-93d9-776dfbd464ff
TQID: https://experienceleague.adobe.com/jlOxj1Ec0X3yRb7tzmUlRO9xbP8K665nQ8b1xYwrGvw
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: b5520579-b31f-4df7-9281-f0d9f91e2edc
    internal-label: Customer engagement
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
    internal-label: Customer experience
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
    internal-label: Data management
---
# Federated Audience Composition high-level architecture & flow

Before we dive into the steps for supporting the business scenario for SecurFinancial, we'll review the high-level architecture and flow for this composable CDP approach.

Federated Audience Composition module in Adobe Experience Platform expands access to data warehouse datasets without copying the underlying data thereby minimizing data movement and duplication. 

This also provides organizations the required Composable architecture, who have already completed the required data management work on their warehouse and wants to use a zero-copy pattern where Adobe Experience Platform becomes the engagement engine.

It allows businesses to quickly process information stored in one or more data warehouses. It removes the need to ingest data to Adobe Experience. Additionally, it provides access to new datasets that reside in enterprise data warehouses but have up until now been inaccessible for customer experience workflows. Examples may include historical transactions or personal data that will be useful at an aggregated audience level for customer engagement.

![fac-architecture](assets/fac-architecture.png)

Now we'll move on to creating a [Data Warehouse Connection](data-warehouse-connection.md).
