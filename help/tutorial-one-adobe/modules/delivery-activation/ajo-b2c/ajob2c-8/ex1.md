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

Download the file [citisignal_ddl_tables_only.sql](./assets/citisignal_ddl_tables_only.sql) to your desktop. 

![AJO OC](./images/ajoocdata4.png)

Select the file **`citisignal_ddl_tables_only.sql`** and click **open**.

![AJO OC](./images/ajoocdata5.png)

You should then see this. Click **Next**.

![AJO OC](./images/ajoocdata6.png)

### Identity

Some of your schemas contain personal identifiers and those fields shuold be marked as **Identity**, and you need to select the **Namespace** that is applicable to that specific type of identity.

**`citisignal_accounts`**

For this schema, go to the field **account_id** and set the **Identity** type to **Demo System - CRMID**.

![AJO OC](./images/ajoocdata7.png)

**`citisignal_recipients`**

For this schema, go to the field **account_id** and set the **Identity** type to **Demo System - CRMID** and go to the field **email** and set the **Identity** type to **Email**.

![AJO OC](./images/ajoocdata8.png)

### Versioning

In order to keep track of updates to the data that will be ingested against these schemas, it is required to set a field that will be used to keep track of the version of the uploaded data. The field that is used for this in all these schemas is the field **lastmodified**, which contains a timestamp of the uploaded data.

You now need to check the checkbox for **Versioning** for the field **lastmodified** in each of these schemas.

**`citisignal_products`**

Check the checkbox for **Versioning** for the field **lastmodified**.

![AJO OC](./images/ajoocdata9.png)

**`citisignal_product_bundles`**

Check the checkbox for **Versioning** for the field **lastmodified**.

![AJO OC](./images/ajoocdata10.png)

**`citisignal_product_relationships`**

Check the checkbox for **Versioning** for the field **lastmodified**.

![AJO OC](./images/ajoocdata11.png)

**`citisignal_accounts`**

Check the checkbox for **Versioning** for the field **lastmodified**.

![AJO OC](./images/ajoocdata12.png)

**`citisignal_recipients`**

Check the checkbox for **Versioning** for the field **lastmodified**.

![AJO OC](./images/ajoocdata13.png)

**`citisignal_mobile_subscriptions`**

Check the checkbox for **Versioning** for the field **lastmodified**.

![AJO OC](./images/ajoocdata14.png)

**`citisignal_internet_subscriptions`**

Check the checkbox for **Versioning** for the field **lastmodified**.

![AJO OC](./images/ajoocdata15.png)

**`citisignal_tv_subscriptions`**

Check the checkbox for **Versioning** for the field **lastmodified**.

![AJO OC](./images/ajoocdata16.png)

**`citisignal_equipment_subscriptions`**

Check the checkbox for **Versioning** for the field **lastmodified**.

![AJO OC](./images/ajoocdata17.png)

**`citisignal_mobile_usage_summary`**

Check the checkbox for **Versioning** for the field **lastmodified**.

![AJO OC](./images/ajoocdata18.png)

**`citisignal_internet_usage_summary`**

Check the checkbox for **Versioning** for the field **lastmodified**.

![AJO OC](./images/ajoocdata19.png)

**`citisignal_offers`**

Check the checkbox for **Versioning** for the field **lastmodified**.

![AJO OC](./images/ajoocdata20.png)

**`citisignal_offer_eligibility`**

Check the checkbox for **Versioning** for the field **lastmodified**.

![AJO OC](./images/ajoocdata21.png)

### Schema name

WHen ingesting these schemas for enablement purposes in a shared sandbox, it is required to change the name of each schema so that it's unique in that specific sandbox. The reason for making this change is to avoid schema naming conflicts.

For this lab, you should add your LDAP in front of each schema name, which means that every schema name should have this prefix: `--aepUserLdap--_`

**`citisignal_products`**

Change the name of your schema to`--aepUserLdap--_ citisignal_products`.

![AJO OC](./images/ajoocdatan9.png)

**`citisignal_product_bundles`**

Change the name of your schema to`--aepUserLdap--_ citisignal_product_bundles`.

![AJO OC](./images/ajoocdatan10.png)

**`citisignal_product_relationships`**

Change the name of your schema to`--aepUserLdap--_ citisignal_product_relationships`.

![AJO OC](./images/ajoocdatan11.png)

**`citisignal_accounts`**

Change the name of your schema to`--aepUserLdap--_ citisignal_accounts`.

![AJO OC](./images/ajoocdatan12.png)

**`citisignal_recipients`**

Change the name of your schema to`--aepUserLdap--_ citisignal_recipients`.

![AJO OC](./images/ajoocdatan13.png)

**`citisignal_mobile_subscriptions`**

Change the name of your schema to`--aepUserLdap--_ citisignal_mobile_subscriptions`.

![AJO OC](./images/ajoocdatan14.png)

**`citisignal_internet_subscriptions`**

Change the name of your schema to`--aepUserLdap--_ citisignal_internet_subscriptions`.

![AJO OC](./images/ajoocdatan15.png)

**`citisignal_tv_subscriptions`**

Change the name of your schema to`--aepUserLdap--_ citisignal_internet_subscriptions`.

![AJO OC](./images/ajoocdatan16.png)

**`citisignal_equipment_subscriptions`**

Change the name of your schema to`--aepUserLdap--_ citisignal_equipment_subscriptions`.

![AJO OC](./images/ajoocdatan17.png)

**`citisignal_mobile_usage_summary`**

Change the name of your schema to`--aepUserLdap--_ citisignal_mobile_usage_summary`.

![AJO OC](./images/ajoocdatan18.png)

**`citisignal_internet_usage_summary`**

Change the name of your schema to`--aepUserLdap--_ citisignal_internet_usage_summary`.

![AJO OC](./images/ajoocdatan19.png)

**`citisignal_offers`**

Change the name of your schema to`--aepUserLdap--_ citisignal_offers`.

![AJO OC](./images/ajoocdatan20.png)

**`citisignal_offer_eligibility`**

Change the name of your schema to`--aepUserLdap--_ citisignal_offer_eligibility`.

![AJO OC](./images/ajoocdatan21.png)

Your schemas are now ready to be saved. Click **Done**.

![AJO OC](./images/ajoocdata22.png)

You should then see this. Click **Save**.

![AJO OC](./images/ajoocdata23.png)

Click **Open jobs**.

![AJO OC](./images/ajoocdata24.png)

You should then see this. You should wait until the job completes successfully before continuing to the next step.

![AJO OC](./images/ajoocdata25.png)

Once the job completes successfully, you can continue with the next step. This may take 5-10 minutes.

![AJO OC](./images/ajoocdata26.png)

Now that your relational XDM schemas are configured and with data being ingested, you can start to use that data to create your orchestrated campaign in the next exercise.

## 3.8.1.2 Data ingestion

Go to **Datasets**. You should then see a dataset that was created for each schema that you created.

![AJO OC](./images/ajoocdata27.png)

Download the file [data.zip](./assets/data.zip) to your desktop and unzip it.

![AJO OC](./images/ajoocdata28.png)

Open the folder **data**. You should see a CSV file for each of the schemas that were created. You now need to upload that data into each corresponding dataset. For this lab, you will be doing that by doing a loal file upload into each dataset.

![AJO OC](./images/ajoocdata29.png)

**`vangeluw_citisignal_products`**

Go to **Sources**, search for `local` and then click **Add data** under **Local File Upload**.

![AJO OC](./images/ajoocdatas10.png)

Enable the toggle for **Enable change data capture**.

Select the dataset `vangeluw_citisignal_products`.

Click **Next**.

![AJO OC](./images/ajoocdatas9a.png)

Click **Choose files**. Select the file **`citisignal_products.csv`** and click **open**.

![AJO OC](./images/ajoocdatas9b.png)

Click **Next**

![AJO OC](./images/ajoocdatas9c.png)

Click **Finish**.

![AJO OC](./images/ajoocdatas9d.png)

After a couple of minutes, you can see the data being ingested in your dataset.

![AJO OC](./images/ajoocdatas9e.png)

**`vangeluw_citisignal_product_bundles`**

Go to **Sources**, search for `local` and then click **Add data** under **Local File Upload**.

![AJO OC](./images/ajoocdatas10.png)

Enable the toggle for **Enable change data capture**.

Select the dataset `vangeluw_citisignal_product_bundles`.

Click **Next**.

![AJO OC](./images/ajoocdatas10a.png)

Click **Choose files**. Select the file **`citisignal_product_bundles.csv`** and click **open**.

![AJO OC](./images/ajoocdatas10b.png)

Click **Next**

![AJO OC](./images/ajoocdatas10c.png)

Click **Finish**.

![AJO OC](./images/ajoocdatas10d.png)

After a couple of minutes, you can see the data being ingested in your dataset.

![AJO OC](./images/ajoocdatas10e.png)

**`vangeluw_citisignal_product_relationships`**

Go to **Sources**, search for `local` and then click **Add data** under **Local File Upload**.

![AJO OC](./images/ajoocdatas10.png)

Enable the toggle for **Enable change data capture**.

Select the dataset `vangeluw_citisignal_product_relationships`.

Click **Next**.

![AJO OC](./images/ajoocdatas11a.png)

Click **Choose files**. Select the file **`citisignal_product_relationships.csv`** and click **open**.

![AJO OC](./images/ajoocdatas11b.png)

Click **Next**

![AJO OC](./images/ajoocdatas11c.png)

Click **Finish**.

![AJO OC](./images/ajoocdatas11d.png)

After a couple of minutes, you can see the data being ingested in your dataset.

![AJO OC](./images/ajoocdatas11e.png)

**`vangeluw_citisignal_accounts`**

Go to **Sources**, search for `local` and then click **Add data** under **Local File Upload**.

![AJO OC](./images/ajoocdatas10.png)

Enable the toggle for **Enable change data capture**.

Select the dataset `vangeluw_citisignal_accounts`.

Click **Next**.

![AJO OC](./images/ajoocdatas12a.png)

Click **Choose files**. Select the file **`citisignal_accounts.csv`** and click **open**.

![AJO OC](./images/ajoocdatas12b.png)

Click **Next**

![AJO OC](./images/ajoocdatas12c.png)

Click **Finish**.

![AJO OC](./images/ajoocdatas12d.png)

After a couple of minutes, you can see the data being ingested in your dataset.

![AJO OC](./images/ajoocdatas12e.png)

**`vangeluw_citisignal_recipients`**

Go to **Sources**, search for `local` and then click **Add data** under **Local File Upload**.

![AJO OC](./images/ajoocdatas10.png)

Enable the toggle for **Enable change data capture**.

Select the dataset `vangeluw_citisignal_recipients`.

Click **Next**.

![AJO OC](./images/ajoocdatas13a.png)

Click **Choose files**. Select the file **`citisignal_recipients.csv`** and click **open**.

![AJO OC](./images/ajoocdatas13b.png)

Click **Next**

![AJO OC](./images/ajoocdatas13c.png)

Click **Finish**.

![AJO OC](./images/ajoocdatas13d.png)

After a couple of minutes, you can see the data being ingested in your dataset.

![AJO OC](./images/ajoocdatas13e.png)

**`vangeluw_citisignal_mobile_subscriptions`**

Go to **Sources**, search for `local` and then click **Add data** under **Local File Upload**.

![AJO OC](./images/ajoocdatas10.png)

Enable the toggle for **Enable change data capture**.

Select the dataset `vangeluw_citisignal_mobile_subscriptions`.

Click **Next**.

![AJO OC](./images/ajoocdatas14a.png)

Click **Choose files**. Select the file **`citisignal_mobile_subscriptions.csv`** and click **open**.

![AJO OC](./images/ajoocdatas14b.png)

Click **Next**

![AJO OC](./images/ajoocdatas14c.png)

Click **Finish**.

![AJO OC](./images/ajoocdatas14d.png)

After a couple of minutes, you can see the data being ingested in your dataset.

![AJO OC](./images/ajoocdatas14e.png)

**`vangeluw_citisignal_internet_subscriptions`**

Go to **Sources**, search for `local` and then click **Add data** under **Local File Upload**.

![AJO OC](./images/ajoocdatas10.png)

Enable the toggle for **Enable change data capture**.

Select the dataset `vangeluw_citisignal_internet_subscriptions`.

Click **Next**.

![AJO OC](./images/ajoocdatas15a.png)

Click **Choose files**. Select the file **`citisignal_internet_subscriptions.csv`** and click **open**.

![AJO OC](./images/ajoocdatas15b.png)

Click **Next**

![AJO OC](./images/ajoocdatas15c.png)

Click **Finish**.

![AJO OC](./images/ajoocdatas15d.png)

After a couple of minutes, you can see the data being ingested in your dataset.

![AJO OC](./images/ajoocdatas15e.png)

**`vangeluw_citisignal_tv_subscriptions`**

Go to **Sources**, search for `local` and then click **Add data** under **Local File Upload**.

![AJO OC](./images/ajoocdatas10.png)

Enable the toggle for **Enable change data capture**.

Select the dataset `vangeluw_citisignal_tv_subscriptions`.

Click **Next**.

![AJO OC](./images/ajoocdatas16a.png)

Click **Choose files**. Select the file **`citisignal_tv_subscriptions.csv`** and click **open**.

![AJO OC](./images/ajoocdatas16b.png)

Click **Next**

![AJO OC](./images/ajoocdatas16c.png)

Click **Finish**.

![AJO OC](./images/ajoocdatas16d.png)

After a couple of minutes, you can see the data being ingested in your dataset.

![AJO OC](./images/ajoocdatas16e.png)

**`vangeluw_citisignal_equipment_subscriptions`**

Go to **Sources**, search for `local` and then click **Add data** under **Local File Upload**.

![AJO OC](./images/ajoocdatas10.png)

Enable the toggle for **Enable change data capture**.

Select the dataset `vangeluw_citisignal_equipment_subscriptions`.

Click **Next**.

![AJO OC](./images/ajoocdatas17a.png)

Click **Choose files**. Select the file **`citisignal_equipment_subscriptions.csv`** and click **open**.

![AJO OC](./images/ajoocdatas17b.png)

Click **Next**

![AJO OC](./images/ajoocdatas17c.png)

Click **Finish**.

![AJO OC](./images/ajoocdatas17d.png)

After a couple of minutes, you can see the data being ingested in your dataset.

![AJO OC](./images/ajoocdatas17e.png)

**`vangeluw_citisignal_mobile_usage_summary`**

Go to **Sources**, search for `local` and then click **Add data** under **Local File Upload**.

![AJO OC](./images/ajoocdatas10.png)

Enable the toggle for **Enable change data capture**.

Select the dataset `vangeluw_citisignal_mobile_usage_summary`.

Click **Next**.

![AJO OC](./images/ajoocdatas18a.png)

Click **Choose files**. Select the file **`citisignal_mobile_usage_summary.csv`** and click **open**.

![AJO OC](./images/ajoocdatas18b.png)

Click **Next**

![AJO OC](./images/ajoocdatas18c.png)

Click **Finish**.

![AJO OC](./images/ajoocdatas18d.png)

After a couple of minutes, you can see the data being ingested in your dataset.

![AJO OC](./images/ajoocdatas18e.png)

**`vangeluw_citisignal_internet_usage_summary`**

Go to **Sources**, search for `local` and then click **Add data** under **Local File Upload**.

![AJO OC](./images/ajoocdatas10.png)

Enable the toggle for **Enable change data capture**.

Select the dataset `vangeluw_citisignal_internet_usage_summary`.

Click **Next**.

![AJO OC](./images/ajoocdatas19a.png)

Click **Choose files**. Select the file **`citisignal_internet_usage_summary.csv`** and click **open**.

![AJO OC](./images/ajoocdatas19b.png)

Click **Next**

![AJO OC](./images/ajoocdatas19c.png)

Click **Finish**.

![AJO OC](./images/ajoocdatas19d.png)

After a couple of minutes, you can see the data being ingested in your dataset.

![AJO OC](./images/ajoocdatas19e.png)

**`vangeluw_citisignal_offers`**

Go to **Sources**, search for `local` and then click **Add data** under **Local File Upload**.

![AJO OC](./images/ajoocdatas10.png)

Enable the toggle for **Enable change data capture**.

Select the dataset `vangeluw_citisignal_offers`.

Click **Next**.

![AJO OC](./images/ajoocdatas20a.png)

Click **Choose files**. Select the file **`citisignal_offers.csv`** and click **open**.

![AJO OC](./images/ajoocdatas20b.png)

Click **Next**

![AJO OC](./images/ajoocdatas20c.png)

Click **Finish**.

![AJO OC](./images/ajoocdatas20d.png)

After a couple of minutes, you can see the data being ingested in your dataset.

![AJO OC](./images/ajoocdatas20e.png)

**`vangeluw_citisignal_offer_eligibility`**

Go to **Sources**, search for `local` and then click **Add data** under **Local File Upload**.

![AJO OC](./images/ajoocdatas10.png)

Enable the toggle for **Enable change data capture**.

Select the dataset `vangeluw_citisignal_offer_eligibility`.

Click **Next**.

![AJO OC](./images/ajoocdatas21a.png)

Click **Choose files**. Select the file **`citisignal_offer_eligibility.csv`** and click **open**.

![AJO OC](./images/ajoocdatas21b.png)

Click **Next**

![AJO OC](./images/ajoocdatas21c.png)

Click **Finish**.

![AJO OC](./images/ajoocdatas21d.png)

After a couple of minutes, you can see the data being ingested in your dataset.

![AJO OC](./images/ajoocdatas21e.png)

All data is now ingested. 

## 3.8.1.3 Profile Target Dimension

With Orchestrated Campaigns, you can design and deliver targeted communications at the entity level, leveraging Adobe Experience Platform’s relational schema capabilities. Experience Platform uses schemas to describe the structure of data in a consistent and reusable way. When data is ingested into Experience Platform, it is structured according to an XDM schema.

Although segmentation for Orchestrated Campaigns operates primarily on relational schemas, the actual message delivery always occurs at the Profile level.

When configuring targeting, you define two key aspects:

- Targetable Schemas: You specify which relational schemas are eligible for targeting. By default, the schema named Recipient is used, but you can configure alternatives such as Visitors, Customers, etc.

- Profile Linkage: The system must understand how the target schema maps to the Profile schema. This is achieved through a shared identity field — one that exists both in the target schema and the Profile schema and is configured as an identity namespace.

You now need to configure your Profile Target Dimensions. Go to **Administration** > **Configuration** and then click **Manage** under **Profile Target Dimension**.

![AJO OC](./images/ajoocptd1.png)

You should then see this. Click **Create**.

![AJO OC](./images/ajoocptd2.png)

For the **Schema**, select `--aepUserLdap--_citisignal_accounts`. For the **Identity value**, select **account_id**.

Click **Save**.

![AJO OC](./images/ajoocptd3.png)

Click **Create** again.

![AJO OC](./images/ajoocptd4.png)

For the **Schema**, select `--aepUserLdap--_citisignal_recipients`. For the **Identity value**, select **account_id**.

Click **Save**.

![AJO OC](./images/ajoocptd5.png)

Click **Create** again.

![AJO OC](./images/ajoocptd6.png)

For the **Schema**, select `--aepUserLdap--_citisignal_recipients`. For the **Identity value**, select **email**.

Click **Save**.

![AJO OC](./images/ajoocptd7.png)

You should then have this.

![AJO OC](./images/ajoocptd8.png)

## 3.8.1.4 Email channel

In the left menu, go to **Channels**. Click **Create channel configuration**.

![AJO OC](./images/ajoocchannel1.png)

Use the name: `--aepUserLdap---citisignal-email-oc`. Select the channel **Email**

![AJO OC](./images/ajoocchannel2.png)

Select an available **subdomain** and **IP pool**.

![AJO OC](./images/ajoocchannel3.png)

Scroll down and fill out the **Header parameters**.

- **From name**: `info@techinsiders.org`
- **From email prefix**: `info`
- **Reply to name**: `info@techinsiders.org`
- **Reply to email**: `info@techinsiders.org`
- **Error email prefix**: `error`

![AJO OC](./images/ajoocchannel4.png)

Scroll down. Go to **Orchestrated campaign**. Check the checkbox for **Enabled**. Select **Targetng dimension**.

![AJO OC](./images/ajoocchannel5.png)

For **Profile Target Dimension**, select `--aepUserLdap--_citisignal_recipients - email`.

Select **Target Dimension** and click the **open folder** icon.

![AJO OC](./images/ajoocchannel6.png)

Click `--aepUserLdap--_citisignal_recipients`.

![AJO OC](./images/ajoocchannel7.png)

Select the field **email** and click **Select**.

![AJO OC](./images/ajoocchannel8.png)

Scroll up and click **Submit**.

![AJO OC](./images/ajoocchannel9.png)

In the next exercise you'll start to use that data as part of an orchestrated campaign.

## Next Steps

Go to [Create your orchestrated campaign](./ex2.md){target="_blank"}

Go back to [Adobe Journey Optimizer: Orchestrated Campaigns](./ajocampaigns.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
