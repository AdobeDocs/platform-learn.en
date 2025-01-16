---
title: Query Service - Prerequisites
description: Query Service - Prerequisites
kt: 5342
doc-type: tutorial
exl-id: b8a404d1-7796-46e3-b245-553acdc753ae
---
# 5.1.1 Prerequisites

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

Next Step: [5.1.2 Getting Started](./ex2.md)

[Go Back to Module 5.1](./query-service.md)

[Go Back to All Modules](../../../overview.md)
