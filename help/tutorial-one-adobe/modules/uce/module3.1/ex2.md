---
title: Data Collection - FAC - Create schemas, data model and links
description: Foundation - FAC - Create schemas, data model and links
kt: 5342
doc-type: tutorial
exl-id: 42004cb9-60b3-4ca8-97d9-3d169735c98f
---
# 3.1.2 Create schemas, data model and links

You can now configure your federated database in Adobe Experience Platform.

Log in to Adobe Experience Platform by going to this URL: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxName--``. After selecting the appropriate sandbox, you'll see the screen change and now you're in your dedicated sandbox.

![Data Ingestion](./images/sb1.png)

## 3.1.2.1 Set up a Federated database in AEP

Click **Federated databases** in the left menu. Then, click **Add federated database**.

![FAC](./images/fdb1.png)

As a **Label**, use `--aepUserLdap-- - CitiSignal Snowflake` and for the type, choose **Snowflake**.

Under details, you need to fill out your credentials, which will look like this:

![FAC](./images/fdb2.png)

**Server**: 

In Snowflake, go to **Admin > Accounts**. Click the 3 **...** next to your account and click **Manage URLs**.

![FAC](./images/fdburl1.png)

You'll then see this. Copy the **Current URL** and paste it in the **Server** field in AEP.

![FAC](./images/fdburl2.png)

**User**: the user name you created earlier, in exercise 1.3.1.1
**Password**: the password you created earlier, in exercise 1.3.1.1
**Database**: use **CITISIGNAL**

So finally, you should have this. Click **Test Connection**. If the test is successful, click **Deploy Functions**, which will create functions on the Snowflake side which are necessary for the workflow engine.
 
Once the connection was successfully tested and functions are deployed, your configuration will be stored.

![FAC](./images/fdb3.png)

When you then go back to the **Federated databases** menu, you'll see your connection there.

![FAC](./images/fdb4.png)

## 3.1.2.2 Create schemas in AEP

In the left menu, click **Models** and then go to **Schemas**. Click **Create schema**.

![FAC](./images/fdb5.png)

Select your federated database and click **+ Add tables**.

![FAC](./images/fdb6.png)

You'll then see this. Select the 5 tables you created in Snowflake before:

- `--aepUserLdap--_HOUSEHOLDS`
- `--aepUserLdap--_MOBILE_DATA_USAGE`
- `--aepUserLdap--_MONTHLY_DATA_USAGE`
- `--aepUserLdap--_PERSONS`
- `--aepUserLdap--_USERS`

Click **Add**.

![FAC](./images/fdb7.png)

AEP will then load the information of each table and show it in the UI. 

For each table, you can:

- change the label of the schema
- add a description
- rename all the fields, and set their visibility
- select the primary key for the schema

For this exercise, no changes are needed.

Click **Create**.

![FAC](./images/fdb8.png)

You'll then see this. You can click any schema and review the information. As an example, click **--aepUserLdap--_PERSONS**.

![FAC](./images/fdb9.png)

You'll then see this, with the ability to edit the configuration. Click **Data** to see a sample of the data that is in the Snowflake database.

![FAC](./images/fdb10.png)

You'll then see a sample of the data.

![FAC](./images/fdb11.png)

## 3.1.2.3 Create a model in AEP

In the left menu, go to **Models** and then go to **Data model**. Click **Create data model**.

![FAC](./images/fdb12.png)

For the label, use `--aepUserLdap-- - CitiSignal Snowflake Data Model`. Click **Create**.

![FAC](./images/fdb13.png)

Click **Add schemas**.

![FAC](./images/fdb14.png)

Select your schemas and click **Add**.

![FAC](./images/fdb15.png)

You'll then see this. Click **Save**.

### USERS - PERSONS

You can now start defining links between schemas. To start defining a link, you need to click **Create links**. 

![FAC](./images/fdb16.png)

First, let's define the link between the tabel `--aepUserLdap--_USERS` and `--aepUserLdap--_PERSONS`.

Click **Add**.

![FAC](./images/fdb18.png)


### HOUSEHOLDS - PERSONS

You'll then be back here. Click **Create links** to create another link.

![FAC](./images/fdb17.png)

Next, let's define the link between the tabel `--aepUserLdap--_HOUSEHOLDS` and `--aepUserLdap--_PERSONS`.

![FAC](./images/fdb19.png)

### USERS - MONTHLY_DATA_USAGE

You'll then be back here. Click **Create links** to create another link.

![FAC](./images/fdb20.png)

Next, let's define the link between the tabel `--aepUserLdap--_USERS` and `--aepUserLdap--_MONTHLY_DATA_USAGE`.

![FAC](./images/fdb21.png)


### USERS - HOUSEHOLDS

You'll then be back here. Click **Create links** to create another link.

![FAC](./images/fdb22.png)

Next, let's define the link between the tabel `--aepUserLdap--_USERS` and `--aepUserLdap--_HOUSEHOLDS`.

![FAC](./images/fdb23.png)

### USERS - MOBILE_DATA_USAGE

You'll then be back here. Click **Create links** to create another link.

![FAC](./images/fdb24.png)

Next, let's define the link between the tabel `--aepUserLdap--_USERS` and `--aepUserLdap--_MOBILE_DATA_USAGE`.

![FAC](./images/fdb25.png)

You should then see this. Click **Save**.

![FAC](./images/fdb26.png)

Your setup in AEP is now done. You can now start using your federated data in a federated audience composition.

Next Step: [3.1.3 Create a federated composition](./ex3.md)

[Go Back to Module 3.1](./fac.md)

[Go Back to All Modules](../../../overview.md)
