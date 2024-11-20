---
title: Foundation - Data Ingestion - Configure Datasets
description: Foundation - Data Ingestion - Configure Datasets
kt: 5342
doc-type: tutorial
---
# 1.2.3 Configure Datasets

In this exercise, you'll configure datasets to capture and store profile information and customer behavior. Every dataset that you create in this will use one of the schemas that you built in the previous step.

## Context

After defining what the answer to the questions **Who is this customer?** and **What does this customer do?** should look like, you now need to create a bucket that uses that information, to receive and validate data that was sent to Adobe Experience Platform.

## Create Datasets

You now need to create 2 datasets:

- 1 dataset to capture the information that answers the **Who is this customer?** - question.
- 1 dataset to capture the information that answers the **What does this customer do?** - question.

Log in to Adobe Experience Platform by going to this URL: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./images/home.png)

Before you continue, you need to select a **[!UICONTROL sandbox]**. The sandbox to select is named ``--aepSandboxName--``. After selecting the appropriate [!UICONTROL sandbox], you'll see the screen change and now you're in your dedicated [!UICONTROL sandbox].

![Data Ingestion](./images/sb1.png)

In Adobe Experience Platform, click on **[!UICONTROL Datasets]** in the menu on the left side of your screen.  You'll then see this:

![Data Ingestion](./images/menudatasets.png)

Let's start by creating the dataset to capture the website registration information.

You should create a new dataset. To create a new dataset, click on the button **[!UICONTROL + Create Dataset]**.

![Data Ingestion](./images/createdataset.png)

You have to define a dataset from the schema that you defined in the previous step. Click the **[!UICONTROL Create Dataset from Schema]** - option.

![Data Ingestion](./images/datasetfromschema.png)

In the next screen, you have to select the schema that you created in 1, `--aepUserLdap-- - Demo System - Profile Schema for Website`.

Click **Next**.

![Data Ingestion](./images/schemaselection.png)

Let's give a name to your dataset. 

As the name for your dataset, use this:

`--aepUserLdap-- - Demo System - Profile Dataset for Website`

Click **Finish**.

![Data Ingestion](./images/datasetname.png)

You'll now see this:

![Data Ingestion](./images/dsoverview1.png)

Go back to the [!UICONTROL Datasets] overview. You'll now see the dataset you created pop up in the overview.

![Data Ingestion](./images/dsoverview2.png)

Next, you'll configure a second dataset to capture website interactions.

Click **[!UICONTROL + Create Dataset]**.

![Data Ingestion](./images/createdataset.png)


You have to define a dataset from the schema that you defined in the previous step. Click the **[!UICONTROL Create Dataset from Schema]** - option.

![Data Ingestion](./images/datasetfromschema.png)

In the next screen, you have to select the schema that you created eralier, `--aepUserLdap-- - Demo System - Event Schema for Website`.

Click **Next**.

![Data Ingestion](./images/schemaselectionee.png)

Let's give a name to your dataset. 

As the name for our dataset, use this:

`--aepUserLdap-- - Demo System - Event Dataset for Website`

Click **Finish**.

![Data Ingestion](./images/datasetnameee.png)

You'll then see this:

![Data Ingestion](./images/finish1ee.png)

Go back to the [!UICONTROL Datasets] overview screen.

![Data Ingestion](./images/datasetsoverview.png)

You now have to enable your datasets to be part of Adobe Experience Platform's Real-time Customer Profile.

Open your dataset `--aepUserLdap-- - Demo System - Profile Dataset for Website` by clicking it.

Locate the [!UICONTROL Profile] toggle icon on the right side of the screen. 
Click the [!UICONTROL Profile] toggle to enable this dataset for [!UICONTROL Profile].

![Data Ingestion](./images/ds1.png)

Click **[!UICONTROL Enable]**.

![Data Ingestion](./images/ds3.png)

Your dataset is now enabled for [!UICONTROL Profile].

Go back to the datasets overview and open your dataset `--aepUserLdap-- - Demo System - Event Dataset` for Website by clicking it.

Locate the [!UICONTROL Profile] toggle icon on the right side of the screen. Click the [!UICONTROL Profile] toggle to enable [!UICONTROL Profile].

![Data Ingestion](./images/ds4.png)

Click **[!UICONTROL Enable]**.

![Data Ingestion](./images/ds5.png)

Your dataset is now enabled for [!UICONTROL Profile].

Next Step: [1.2.4 Data Ingestion from Offline Sources](./ex4.md)

[Go Back to Module 1.2](./data-ingestion.md)

[Go Back to All Modules](../../../overview.md)
