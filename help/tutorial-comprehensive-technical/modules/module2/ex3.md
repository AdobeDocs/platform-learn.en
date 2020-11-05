---
title: Foundation - Data Ingestion - Configure Datasets
description: Foundation - Data Ingestion - Configure Datasets
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
---

# 2.3 Configure Datasets

In this exercise, you'll configure the required datasets to capture and store profile information and customer behavior. Every dataset that you create in this will use one of the schemas that you built in the previous step.

The URL to login to Adobe Experience Platform is: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

## Story

After defining what the answer to the questions **Who is this customer?** and **What does this customer do?** should look like, you now need to create a bucket that uses that information, to receive and validate data that was sent to Adobe Experience Platform.

## 2.3.1 - Create Datasets

You now need to create 2 datasets:

* 1 dataset to capture the information that answers the **Who is this customer?** - question.
* 1 dataset to capture the information that answers the **What does this customer do?** - question.

Log in to Adobe Experience Platform by going to this URL: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named **Module 2 - Data Ingestion**. You can do this by clicking the text **Production Prod** in the blue line on top of your screen.

![Data Ingestion](./images/sb1.png)

From the list of available sandboxes, select the sandbox that matches the number you've been assigned.

After selecting the appropriate sandbox, you'll see the screen change and now you're in your dedicated sandbox.

![Data Ingestion](./images/sb2.png)

In Adobe Experience Platform, click on **Datasets** in the menu on the left side of your screen.

![Data Ingestion](./images/menudatasets.png)

In Datasets, you'll see something like this: 

![Data Ingestion](./images/datasets.png)

**Let's start by creating the dataset to capture the Website Registration Information.**

You should create a new dataset. To create a new dataset, click on the button **+ Create Dataset**.

![Data Ingestion](./images/createdataset.png)

After clicking the **+ Create Dataset** button, you'll see the following screen. 

![Data Ingestion](./images/datasetsetup.png)

You have to define a dataset from the schema that you defined in the previous step. Click the **Create Dataset from Schema** - option.

![Data Ingestion](./images/datasetfromschema.png)

In the next screen, you have to select the schema that you created in 1, **ldap - AEP Demo - Website Registrations Schema**.

![Data Ingestion](./images/schemaselection.png)

After selecting the schema, click **Next** to continue.

![Data Ingestion](./images/next.png)

Let's give a name to your dataset. 

As the name for our dataset, we'll use this:

**ldap - AEP Demo - Website Registrations**

Replace **ldap** by your specific ldap. As an example, for ldap **vangeluw**, this should be the name of the schema:

**vangeluw - AEP Demo - Website Registrations**
  
That should give you something like this:

![Data Ingestion](./images/datasetname.png)

Click **Finish** to finish your dataset configuration.

![Data Ingestion](./images/finish.png)

You'll now see this:

![Data Ingestion](./images/dsoverview1.png)

Go back to the Datasets overview. 

![Data Ingestion](./images/dsoverview2.png)

**Next, you'll have to configure a 2nd dataset to capture Website Interactions.**

You should create a new dataset. To create a new dataset, click on the button **+ Create Dataset**.

![Data Ingestion](./images/createdataset.png)

After clicking the **+ Create Dataset** button, you'll see the following screen. 

![Data Ingestion](./images/datasetsetup.png)

You have to define a dataset from the schema that you defined in the previous step. Click the **Create Dataset from Schema** - option.

![Data Ingestion](./images/datasetfromschema.png)

In the next screen, you have to select the schema that you created in 2.2, **ldap - AEP Demo - Website Interactions Schema**.

![Data Ingestion](./images/schemaselectionee.png)

After selecting the schema, click **Next** to continue.

![Data Ingestion](./images/next.png)

Let's give a name to your dataset. 

As the name for our dataset, we'll use this:

**AEP Demo - Website Interactions**

Replace **ldap** by your specific ldap. As an example, for ldap **vangeluw**, this should be the name of the schema:

**vangeluw - AEP Demo - Website Interactions**
  
That should give you something like this:

![Data Ingestion](./images/datasetnameee.png)

Click **Finish** to finish your dataset configuration.

![Data Ingestion](./images/finish.png)

You'll then see this:

![Data Ingestion](./images/finish1.png)

Go back to the Datasets overview screen.

![Data Ingestion](./images/datasetsoverview.png)

You now have to enable your datasets to be part of Adobe Experience Platform's Real-time Customer Profile.

Open you dataset **ldap - AEP Demo - Website Registrations** by clicking it.

Locate the Profile toggle icon on the right side of the screen.

![Data Ingestion](./images/ds1.png)

Click the Profile toggle to enable this dataset for Profile.

![Data Ingestion](./images/ds2.png)

Click the **Enable**.

![Data Ingestion](./images/ds3.png)

Your dataset is now enabled for Profile.

Open you dataset **ldap - AEP Demo - Website Interactions** by clicking it.

Locate the Profile toggle icon on the right side of the screen.

![Data Ingestion](./images/ds4.png)

Click the Profile toggle to enable Profile.

![Data Ingestion](./images/ds2.png)

Click Enable.

![Data Ingestion](./images/ds5.png)

Your dataset is now enabled for Profile.

Next Step: [2.4 Data Ingestion from Offline Sources](./ex4.md)

[Go Back to Module 2](./data-ingestion.md)

[Go Back to All Modules](../../overview.md)
