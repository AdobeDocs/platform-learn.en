---
title: Query Service - Prerequisites
description: Query Service - Prerequisites
kt: 5342
doc-type: tutorial
exl-id: e9e4d478-cb8d-42a9-87a3-319e5a8b8522
TQID: https://experienceleague.adobe.com/cn2R7T-R3JiFfrsEAbV8gu7z3UKkxJtQeZs1I7jAKrY
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: c20d46e7-1c7d-476c-a50e-3961d4dce35f
    internal-label: Reporting
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
    internal-label: Insights
---
# 2.1.1 Prerequisites

## Install PSQL Command Line Utility

Follow the instruction outlined in the Adobe Experience Platform documentation to install the psql client:
[PSQL Install Guide](https://experienceleague.adobe.com/docs/experience-platform/query/clients/psql.html)

Once you've installed PSQL, you may need to update your **PATH** by running the below command in a terminal window:

For macOS (replace XX in the below command by the version number of PSQL that you installed):

`export PATH=/Library/PostgreSQL/XX/bin:$PATH`

## Install Power BI

Only for Windows users

[Install Microsoft Power BI](https://experienceleague.adobe.com/docs/experience-platform/query/clients/power-bi.html)

Make sure that you install the exact version of **npgsql** as mentioned on the document, otherwise you will not be able to connect Power BI to Adobe Experience Platform Query Service.

## Install Tableau

For Windows or Mac users

[Install Tableau Desktop](https://experienceleague.adobe.com/docs/experience-platform/query/clients/tableau.html) as per the documentation.

Tableau gives you a 14-day trial period automatically.

If you want to use Tableau beyond those 14 days, you'll need a license key.

## Next Steps

Go to [2.1.2 Getting Started](./ex2.md){target="_blank"}

Go back to [Query Service](./query-service.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
