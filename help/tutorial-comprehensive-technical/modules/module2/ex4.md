---
title: Foundation - Data Ingestion - Data Ingestion from Offline Sources
description: Foundation - Data Ingestion - Data Ingestion from Offline Sources
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: a5bd1edc-ec0f-4b6f-8c4a-86df6ec0ae66
---
# 2.4 Data Ingestion from Offline Sources

In this exercise, the goal is to onboard external data like CRM Data in Platform.

## Learning Objectives

- Learn how to generate test data
- Learn how to ingest CSV
- Learn how to use the web UI for data ingestion through Workflows
- Understand the data governance features of Experience Platform

## Resources

- Mockaroo UI: [https://www.mockaroo.com/](https://www.mockaroo.com/)
- Experience Platform UI: [https://experience.adobe.com/platform/](https://experience.adobe.com/platform/)

## Tasks

- Create a CSV file with demo date. Ingest the CSV file in Adobe Experience Platform by making use of the available workflows.
- Understand data governance options in Adobe Experience Platform

## 2.4.1 Create your CRM Dataset through a data generator tool

For this you need 1000 sample lines of CRM Data.

Open the Mockaroo Template by going to [https://www.mockaroo.com/12674210](https://www.mockaroo.com/12674210).

![Data Ingestion](./images/mockaroo.png)

On the template, you'll notice the following fields:

- id
- first_name
- last_name
- email
- gender
- birthDate
- home_latitude
- home_longitude
- country_code
- city
- country

All these fields have been defined to produce data that is compatible with Platform. 

![Data Ingestion](./images/dd.png)

To generate your CSV-file, click the **[!UICONTROL Download Data]** button which will give you a CSV-file with 1000 lines of demo-data. 

Open your CSV-file in Microsoft Excel to visualize its contents.

![Data Ingestion](./images/excel.png)

With your CSV-file ready, you can proceed with mapping it against XDM.

### 2.4.2 Verify the CRM Onboarding Dataset in Adobe Experience Platform

Open [Adobe Experience Platform](https://experience.adobe.com/platform) and go to **[!UICONTROL Datasets]**. 

Before you continue, you need to select a **[!UICONTROL sandbox]**. The sandbox to select is named ``--module2sandbox--``. You can do this by clicking the text **[!UICONTROL Production Prod]** in the blue line on top of your screen.

![Data Ingestion](./images/sb1.png)

From the list of available [!UICONTROL sandboxes], select the [!UICONTROL sandbox] that matches the number you've been assigned.

After selecting the appropriate [!UICONTROL sandbox], you'll see the screen change and now you're in your dedicated [!UICONTROL sandbox].

![Data Ingestion](./images/sb2.png)

In Adobe Experience Platform, click on **[!UICONTROL Datasets]** in the menu on the left side of your screen.

![Data Ingestion](./images/menudatasetssb.png)

You're going to use a shared dataset based in this enablement. The shared dataset has been created already and is called **[!UICONTROL Demo System - Profile Dataset for CRM]**. 

>[!NOTE]
>
> Depending on the Adobe Experience Platform template that was installed in your environment, the dataset may also be named **[!UICONTROL AEP Demo - CRM Onboarding]**. If that is the case, please proceed by using the dataset **[!UICONTROL AEP Demo - CRM Onboarding]**.

![Data Ingestion](./images/emeacrm.png)

Open the dataset **[!UICONTROL Demo System - Profile Dataset for CRM]**.

![Data Ingestion](./images/emeacrmoverview.png)

On the overview screen, you can see 3 main pieces of information.

![Data Ingestion](./images/dashboard.png)

First of all, the [!UICONTROL Dataset Activity] dashboard shows the total number of CRM records in the dataset and the ingested batches and their status

![Data Ingestion](./images/batchids.png)

Second, by scrolling down on the page you can check when batches of data were ingested, how many records were onboarded and also, whether or not the batch was successfully onboarded. The **[!UICONTROL Batch ID]** is the identifier for a specific batch job, and the **[!UICONTROL Batch ID]** is important as it can be used for troubleshooting why a specific batch was not successfully onboarded. More on that in Enablement Module 2.

![Data Ingestion](./images/datasetsettings.png)

Lastly, the [!UICONTROL Dataset Info] tab shows important information like the [!UICONTROL Dataset ID] (again, important from a troubleshooting perspective), the Dataset's Name and whether the dataset was enabled for Profile. 

![Data Ingestion](./images/ds_ups_link.png)

The most important setting here is the link between the dataset and the Schema. The Schema defines what data can be ingested and how that data should look like. 

In this case, we're using the **[!UICONTROL Demo System - Profile Schema for CRM]**, which is mapped against the class of **[!UICONTROL Profile]** and has implemented extensions, also called mixins. 

>[!NOTE]
>
> Depending on the Adobe Experience Platform template that was installed in your environment, the dataset may also be named **[!UICONTROL AEP Demo - CRM Onboarding Schema]**. If that is the case, please proceed by using the dataset **[!UICONTROL AEP Demo - CRM Onboarding Schema]**.

![Data Ingestion](./images/ds_schemalink.png)

By clicking on the name of the schema, you're taken to the [!UICONTROL Schema] overview were you can see all the fields that have been activated for this schema.

![Data Ingestion](./images/schemads.png)

Every schema needs to have a custom, primary descriptor defined. In the case of our CRM dataset, the schema has defined that the field **[!UICONTROL email]** should be the primary identifier. If you want to create a schema and link it to the [!UICONTROL Real-time Customer Profile], you need to define a custom [!UICONTROL Mixin] that refers to your primary descriptor.

![Data Ingestion](./images/schema_descriptor.png)

In the above screenshot, you can see that our descriptor is located in `--aepTenantId--.identification.emailId`, which is set as the [!UICONTROL Primary Identifier], linked to the [!UICONTROL namespace] of **[!UICONTROL email]**.

Every schema and as such, every dataset that should be used in the [!UICONTROL Real-time Customer Profile] should have one [!UICONTROL Primary identifier]. This [!UICONTROL Primary Identifier] is the identifier user by the brand for a customer in that dataset. In the case of a CRM dataset it might be the email-address or the CRM ID, in the case of a Call Center dataset it might be the mobile number of a customer.

It is best practice to create a separate, specific schema for every dataset and to set the descriptor for every dataset specifically to match how the current solutions used by the brand operate.

### 2.4.3 Using a workflow to map a CSV file to an XDM Schema

The goal of this is to onboard CRM data in Platform. All the data that is ingested in Platform should be mapped against the specific XDM Schema. What you currently have is a CSV dataset with 1000 lines on the one side, and a dataset that is linked to a schema on the other side. To load that CSV file in that dataset, a mapping needs to take place. To facilitate this mapping exercise, we have **[!UICONTROL Workflows]** available in Adobe Experience Platform.

![Data Ingestion](./images/workflows.png)

The [!UICONTROL workflow] that we'll use here, is the [!UICONTROL workflow] named **[!UICONTROL Map CSV to XDM Schema]** in the [!UICONTROL Data Ingestion] menu.

Click the **[!UICONTROL Map CSV to XDM Schema]** button.

![Data Ingestion](./images/mapcsvxdm.png)

Click **[!UICONTROL Launch]** to start the process.

![Data Ingestion](./images/launchprocess.png)

On the next screen, you need to select a dataset to ingest your file in. You have the choice between selecting an already existing dataset or creating a new one. For this exercise, we'll reuse an existing one: please select **[!UICONTROL Demo System - Profile Dataset for CRM]** as indicated below.

>[!NOTE]
>
> Depending on the Adobe Experience Platform template that was installed in your environment, the dataset may also be named **[!UICONTROL AEP Demo - CRM Onboarding]**. If that is the case, please proceed by using the dataset **[!UICONTROL AEP Demo - CRM Onboarding]**.

![Data Ingestion](./images/datasetselection.png)

Click **[!UICONTROL Next]** to go to the next step.

![Data Ingestion](./images/next.png)

Drag & Drop your CSV-file or click **[!UICONTROL Browse]** and navigate on your computer to your desktop and select your CSV-file.

![Data Ingestion](./images/dragdrop.png)

After selecting your CSV-file it will upload immediately and you will see a preview of your file within seconds.

![Data Ingestion](./images/previewcsv.png)

Click **[!UICONTROL Next]** to go to the next step. It can take a few seconds while the file is processed completely.

![Data Ingestion](./images/next.png)

It's now time to map your CSV Column Headers with an XDM-property in your **[!UICONTROL Demo System - Profile Dataset for CRM]**.

Adobe Experience Platform has already done some guessing for us, by trying to link the [!UICONTROL Source Attributes] with the [!UICONTROL Target Schema Fields].

![Data Ingestion](./images/mapschema.png)

First of all, we need to add the required mapping for the primary identifier field. The primary identifier field is a required field in this workflow and expects you to indicate what the primary identifier is of the file you're uploading, as defined in the schema that is linked to this dataset. 

Selecting the primary identifier is actually the most important thing: you'll be defining the custom, brand-specific, primary identifier. The primary identifier is a requirement for this data to be onboarded. Without the presence of the primary identifier, the ingestion of this CSV-file will fail.

The primary identifier for the **[!UICONTROL Demo System - Profile Dataset for CRM]**-dataset is the **[!UICONTROL email]** as it's the unique identifier for this dataset.
In this case, based on the selection of the dataset and the schema that is linked to the dataset, the required [!UICONTROL Target Schema Field] in XDM is `--aepTenantId--.identification.emailId`. You need to map the **[!UICONTROL email]**-field from your CSV file as the source attribute for this required [!UICONTROL Target Schema Field].

To do this, click the **[!UICONTROL Add new mapping]** button.

![Data Ingestion](./images/reqmapping.png)

In the [!UICONTROL Source Field], click the **[!UICONTROL arrow]** icon.

![Data Ingestion](./images/emptysource.png)

In the popup, select the field **[!UICONTROL email]**.

![Data Ingestion](./images/emptysourcepopup.png)

You'll then see this. Click the **[!UICONTROL schema]** icon.

![Data Ingestion](./images/emptytarget.png)

In the popup, select the field `--aepTenantId--.identification.emailId`.

![Data Ingestion](./images/emptytargetpopup.png)

The result should look like this:

![Data Ingestion](./images/filledsource.png)

For the [!UICONTROL Schema Mappings], Adobe Experience Platform has tried to link fields together already. However, not all proposals of mapping are correct.

![Data Ingestion](./images/schemamap.png)

For the [!UICONTROL Source Attribute] **[!UICONTROL email]**, the Target Schema Field should be **[!UICONTROL personalEmail.address]**. You can either enter **[!UICONTROL personalEmail.address]** in the field, or you can click the icon to visually locate the correct property in the **[!UICONTROL Demo System - Profile Dataset for CRM Schema]**.

![Data Ingestion](./images/schema_icon.png)

![Data Ingestion](./images/schema_viz.png)

You also need to update 2 fields: **[!UICONTROL home_latitude]** and **[!UICONTROL home_longitude]** haven't been filled out by the mapper tool.

Locate the **[!UICONTROL home_latitude]**-line.

![Data Ingestion](./images/newmapfield.png)

Click the **[!UICONTROL schema]** icon:
 
![Data Ingestion](./images/schema_icon.png)

Locate the property **[!UICONTROL homeAddress._schema.latitude]** by making use of the visual mapping tool.

![Data Ingestion](./images/schema_lat.png)

Click **[!UICONTROL Select]** to confirm your choice. You should then see this:

![Data Ingestion](./images/schema_lat_result.png)

Repeat the process for the Source Field **[!UICONTROL home_longitude]**, linking it to the [!UICONTROL Target Field] of **[!UICONTROL homeAddress._schema.longitude]** so that you have this as a result:
 
![Data Ingestion](./images/schema_long_result.png)

This should be the overall result of the mapping exercise. If you have additional lines, feel free to delete them as they aren't needed for this exercise.

![Data Ingestion](./images/overall.png)

Click the **[!UICONTROL Finish]** button to finish the workflow.

![Data Ingestion](./images/finish.png)

After clicking **[!UICONTROL Finish]**, you're taken to your dataset where your ingestion is being processed.

![Data Ingestion](./images/ingestdataset.png)

On the dataset, you'll see a [!UICONTROL Batch ID] that is being ingested just now, with 1000 records ingested and a status of **[!UICONTROL Processing]**.

![Data Ingestion](./images/batchsuccess.png)

Wait until the status changes into **[!UICONTROL Success]**.

![Data Ingestion](./images/batchsuccess1.png)

Click on the **[!UICONTROL Preview Dataset]**- button to get a quick view of a small sample of the dataset to ensure that the loaded data is correct.

![Data Ingestion](./images/preview.png)

![Data Ingestion](./images/previewdata.png)

Once data is loaded, you can define the correct data governance approach for our dataset.
   
### 2.5.4 Adding data governance to your dataset 

>[!NOTE]
>
> Depending on the Adobe Experience Platform template that was installed in your environment, the dataset to use may also be named **[!UICONTROL AEP Demo - CRM Onboarding]**. If that is the case, please proceed by using the dataset **[!UICONTROL AEP Demo - CRM Onboarding]**.

Now that your customer data is ingested, you need to make sure that this dataset is properly governed for usage and export control. Click on the **[!UICONTROL Data Governance]** tab and observe that you can set three types of restrictions: Contractual, Identity, and Sensitive Data.

You can find more info on the different labels and how they will be enforced in the future through the policy framework on this link: [https://experienceleague.adobe.com/docs/experience-platform/data-governance/home.html](https://experienceleague.adobe.com/docs/experience-platform/data-governance/home.html) 
 
![Data Ingestion](./images/dsgovernance.png)

Let's restrict identity data for the entire dataset. Hover over your dataset name, and click the Pencil icon to edit the settings. 

![Data Ingestion](./images/pencil.png)

Go to **[!UICONTROL Identity Data]** and you'll see that the **[!UICONTROL I2]** option is checked - this will assume that all pieces of information in this dataset are at least indirectly identifiable to the person.

![Data Ingestion](./images/identity.png)

Click **[!UICONTROL Save Changes]** and observe that **[!UICONTROL I2]** is now set for all data fields in the dataset. 

You can also set these flags for individual data fields - for example, the **[!UICONTROL firstName]** field is likely to be classified as an **[!UICONTROL I1]** level for directly identifiable information.

Select the field **[!UICONTROL firstName]** by checking the checkbox and click on **[!UICONTROL Edit Governance Labels]** in the upper right corner of your screen.

![Data Ingestion](./images/editfirstname.png)

Go to **[!UICONTROL Identity Data]** and you'll see that the **[!UICONTROL I2]** option is already checked (inherited from the dataset). The field firstName also has a field-specific configuration and is set as **[!UICONTROL I1 - Directly Identifiable Data]**.

![Data Ingestion](./images/fndii.png)

With this, you've now successfully ingested and classified CRM Data in Adobe Experience Platform.

Next Step: [Summary and benefits](./summary.md)

[Go Back to Module 2](./data-ingestion.md)

[Go Back to All Modules](../../overview.md)
