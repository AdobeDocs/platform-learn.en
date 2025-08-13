---
title: Data Warehouse connection
seo-title: Configure a Data Warehouse connection | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Data Warehouse connection
description: In this visual exercise, we configure a connection between Adobe Experience Platform and your enterprise Data Warehouse to enable Federated Audience Composition.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-configure-a-data-warehouse-connection.jpg
hide: true
---

# Data Warehouse connection

We start by configuring a connection between Adobe Experience Platform and your enterprise Data Warehouse to enable Federated Audience Composition. This allows you to query data directly from supported warehouses without replication. Additionally, we create Schemas and Data Models based on the Data Warehouse tables. 

To demonstrate, we connect to a Snowflake account. Federated Audience Composition supports a growing list of cloud warehouse connections. See the [updated list of integrations](https://experienceleague.adobe.com/en/docs/federated-audience-composition/using/start/access-prerequisites){target="_blank"}.

## Steps

1. Browse to the **FEDERATED DATA** section on the left rail.
2. In the **Federated Databases** link, click on the **Add federated database** button.
3. Add a name and select **Snowflake**.
4. Fill in the details, click on the **Test connection** button, and then on the **Deploy functions** button.

   ![snowflake-connection-setup](assets/snowflake-connection-setup.png)

   ![snowflake-connection-setup-step2](assets/snowflake-connection-setup-step2.png)

   ![snowflake-connection-setup-step3](assets/snowflake-connection-setup-step3.png)

## Create a Schema

To create schemas in Federated Audience Composition, follow these steps:

### Steps

1. In the **FEDERATED DATA** section, click **Models**.
2. Browse the **Schema** tab and click on the **Create Schema** button.
3. Select your source database in the list, and click on the **Add tables** tab.
4. Choose the tables from the federated source. In our example:
   - FSI_CRM
   - FSI_CRM_CONSENT_PREFERENCE

   ![create-schema](assets/create-schema.png)

   ![select-table](assets/select-table.png)

After selecting the tables, review the columns in each table and select the primary key. To support the business case, **EMAIL** is selected as the primary key in both tables.

   ![create-schema](assets/create-schema.png)

   ![create-schema-step2](assets/create-schema-step2.png)

## Create a Data Model

Data models allow you to create a link between tables. The link can be created between tables in the same database, such as tables in Snowflake, or between tables in different databases, such as a link between a table in Snowflake and a table in Amazon Redshift.

### Steps

1. In the **FEDERATED DATA** section, click **Models** then click **Data Model**.
2. Click the **Create data model** button.
3. Provide a name for your data model.
4. Click on **Add schemas** and select the new federated data schemas. In this example, we seect the **FSI_CRM** and **FSI_CRM_CONSENT_PREFERENCE** schemas.
5. Create a link between these tables by clicking on **Create links**.

When creating a link, choose the applicable cardinality:

- **1-N**: One occurrence of the source table can have several corresponding occurrences of the target table, but one occurrence of the target table can have at most one corresponding occurrence of the source table.
- **N-1**: One occurrence of the target table can have several corresponding occurrences of the source table, but one occurrence of the source table can have at most one corresponding occurrence of the target table.
- **1-1**: One occurrence of the source table can have at most one corresponding occurrence of the target table.

Below is a preview of the link created given the above steps. The link enables a join between the CRM and consent tables, using the primary key of **EMAIL** to perform a join.

   ![preview-data-model](assets/preview-data-model.png)

Now, we're ready to [create and audience](audience-creation-exercise.md).
