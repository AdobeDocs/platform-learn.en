---
title: Setting up your relational data foundation
description: Setting up your relational data foundation
kt: 5342
doc-type: tutorial
exl-id: 532e5f2c-971f-488f-bef4-3a8141408cc8
---
# 3.8.1 Setting up your relational data foundation

Login to Adobe Journey Optimizer by going to [https://experience.adobe.com](https://experience.adobe.com). Click **Journey Optimizer**.

![AJO OC](./images/aechome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxName--`.

![AJO OC](./images/ajohome.png)

## 3.8.1.1 Relational-based schema setup

A relational-based schema is the formal definition of the model-based data model.

It specifies:

- The set of tables
- The columns in each table
- The constraints
- The relationships across tables

Organizing schemas or tables in a model-based data model is about structuring your data into multiple tables. Ensure each table stores one type of entity/schemas.

When ingesting data into for usage with Adobe Journey Optimizer Orchestrated Campaigns, the following sources are available:

- Amazon S3
- Google Cloud Storage
- SFTP
- Snowflake
- Google BigQuery
- Data Landing Zone
- Azure Databricks
- Local File Upload

The first step in this exercise is the configuration of your relational-based XDM schemas. In the left menu, scroll down to **Data Management** and select **Schemas**. Click **+ Create schema**.

![AJO OC](./images/ajoocdata1.png)

Select **Relational**.

![AJO OC](./images/ajoocdata2.png)

Select **Upload DDL file** and then click **Choose files**.

![AJO OC](./images/ajoocdata3.png)

Now that your relational XDM schemas are configured and with data being ingested, you can start to use that data to create your orchestrated campaign in the next exercise. 

## 3.8.1.2 Data ingestion


## Next Steps

Go to [Create your orchestrated campaign](./ex2.md){target="_blank"}

Go back to [Adobe Journey Optimizer: Campaigns](./ajocampaigns.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
