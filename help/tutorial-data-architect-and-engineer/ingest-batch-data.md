---
title: Ingest Batch Data | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
description: 
feature: data ingestion
topics: 
kt: 4348
audience: data architect,data engineer
doc-type: tutorial
activity: implement
---

# Ingest Batch Data

Batch data ingestion allows you to ingest a large amount of data into Adobe Experience Platform at once. You can ingest batch data in a one time upload within Platform's interface or using the API. You can also configure regularly scheduled batch uploads from third-party services such as cloud storage services using Source connectors.

First, watch this short video to learn more about data ingestion:
>[!VIDEO](https://video.tv.adobe.com/v/27106?quality=12&learn=on)

**Data Engineers** will need to ingest batch data outside of this tutorial.

## Permissions required

In the [Configure Permissions](configure-permissions.md) lesson, you setup all the access controls you need to complete this lesson, specifically:

* Permission item **[!UICONTROL Datasets]** > **[!UICONTROL View Datasets]**, **[!UICONTROL Manage Datasets]** and **[!UICONTROL Data Monitoring]**
* Permission item **[!UICONTROL Data Ingestoin]** > **[!UICONTROL View Sources]** and **[!UICONTROL Manage Sources]**
* Permission item **[!UICONTROL Profile Management]** > **[!UICONTROL View Profiles]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
* Developer-role access to the `Luma Tutorial Platform` product profile (for API)

## Ingest data in batches by using Platform UI

1. Download [luma-loyalty.json](assets/luma-loyalty.json) file to your **Luma Tutorial Assets** folder.
1. In the Platform UI, click **[!UICONTROL Datasets]** in the left navigation
1. Click on your `Luma Loyalty Dataset`
1. Scroll down until you see the **[!UICONTROL Add Data]** section in the right column
1. Upload the `luma-loyalty.json` file.
1. Once the file uploads a row for the batch will appear
1. If you reload the page after a few minutes, you should see that the batch has successfully uploaded with 1000 records and 1000 profile fragments.

    ![Ingestion](assets/ingestion-loyalty-uploadJson.png)
<!--do i need to explain error diagnostics and partial ingestion-->

### Validate the data

There are a few places to confirm the data landed. In the dataset and in Real-time Customer Profile.

To confirm the data landed in the dataset:

1. On the same page where you have uploaded the data, click the **[!UICONTROL Preview dataset]** button on top-right
1. Click **Preview** button and you should be able to see all the uploaded data in dataset.

    ![Preview the successful dataset](assets/ingestion-loyalty-preview.png)


To confirm the data landed in Profile:

1. Click **[!UICONTROL Profiles]** in the left navigation
1. Click the icon next to the **[!UICONTROL Select identity namespace]** field to open the modal
1. Select your `Luma Loyalty Id` namespace
1. The enter one of the `loyaltyId` values from your dataset, e.g. `5625458`
1. Click the `Show profile` button
    ![Confirm a profile from the dataset](assets/ingestion-loyalty-profile.png)

## Ingest data in batches by using API

Now we will upload data using the API.  

Download [luma-crm.json](assets/luma-crm.json) into your `Luma Tutorial Assets` folder.

### Get the dataset id

First we need to get the id of the dataset id of the dataset into which we want to ingest data:

1. Open [!DNL Postman]
1. If you haven't made a call in the last 24 hours, your authorization tokens have probably expired. Open the call **[!DNL Adobe I/O Access Token Generation > Local Signing (Non-production use-only) > IMS: JWT Generate + Auth via User Token]** and click **Send** to request new JWT and Access Tokens, just like you did in the [!DNL Postman] lesson.
1. Open your environment variables and make sure the value of **CONTAINER_ID** is still `tenant`
1. Open the call **[!DNL Catalog Service API > Datasets > Retrieve a list of datasets.]** and click **Send**
1. You should get a `200 OK` response
1. Copy the id of the `Luma CRM Dataset` from the Response body
  ![Get the dataset id](assets/ingestion-crm-getDatasetId.png) 

### Create the batch

Now we can create a batch in the dataset:

1. Download [Data Ingestion API.postman_collection.json](https://raw.githubusercontent.com/adobe/experience-platform-postman-samples/master/apis/experience-platform/Data%20Ingestion%20API.postman_collection.json) to your `Luma Tutorial Assets` folder
1. Import the collection into [!DNL Postman]
1. Select the request **[!DNL Data Ingestion API > Batch Ingestion > Create a new batch in Catalog Service.]**
1. Paste the following as the **Body** of the request, ***replacing the datasetId value with your own***:

    ```json
    {
        "datasetId":"5f2db919136181194bcd821d"
    }
    ```

1. Click the **Send** button
1. You should get a 201 Created response containing the id of your new batch!
1. Copy the `id` of the new batch
    ![Batch Created](assets/ingestion-crm-createBatch.png)
   
### Ingest the data

Finally we upload the data into the batch
    
1. Select the request **[!DNL Data Ingestion API > Batch Ingestion > Upload a file to a dataset in a batch.]**
1. In the **Params** tab, enter your dataset id and batch id into their respective fields
1. In the **Body** tab, select the **binary** option
1. Select the downloaded `luma-crm.json` from your local `Luma Tutorial Assets` folder
1. Click Send and if everything goes well , you should get '1' as response.

    ![Data uploaded](assets/ingestion-crm-uploadFile.png)

### Validate the data

Validate the data has landed in the Platform UI just like you did for the Loyalty dataset.

First, confirm the batch using Preview dataset

Second, confirm one of your profiles has been created by looking up one of the profiles by the `Luma CRM Id` namespace, e.g. `112ca06ed53d3db37e4cea49cc45b71e`

![Profile ingested](assets/ingestion-crm-profile.png)

There is one interesting thing that just happened that I want to point out. Open that `Danny Wright` profile. Note that the profile has both a `Lumacrmid` and a `Lumaloyalty` id. Remember the `Luma Loyalty Schema` contained two identity fields, Luma Loyalty Id was the primary identity and CRM Id was a secondary identity. Now that we've uploaded both datasets, they've merged into profile. The Loyalty data had `Daniel` as the first name and "New York City" as the home address, while the CRM data had `Danny` as the first name and `Portland` as the home address for this customer. (We will come back to why the first name displays `Danny` in the lesson on merge policies).

Congratulations, you've just merged profiles!

![Profile merged ](assets/ingestion-crm-profileLinkedIdentities.png)

## Ingest data with Workflows

Let's look at another way of uploading data. 

Download [luma-products.csv](assets/luma-products.csv) into your `Luma Tutorial Assets` folder.

Now let's use a workflow:

1. Click **[!UICONTROL Workflows]** in the left navigation
1. Select **[!UICONTROL Map CSV to XDM schema]** and click the **[!UICONTROL Launch]** button
    ![Launch the workflow](assets/ingestion-products-launchWorkflow.png)
1. Select your `Luma Product Catalog Dataset` and click the **[!UICONTROL Next]** button
    ![Select your dataset](assets/ingestion-products-selectDataset.png)
1. Add the `luma-products.csv` file  you just downloaded and click the **[!UICONTROL Next]** button 
    ![Select your dataset](assets/ingestion-products-selectData.png)
1. Now you are in our mapper interface, in which you can map a field from the source data (one of the column names in our `luma-products.csv` file) to XDM fields in the target schema. In our example, the column names are close enough to the schema field names that the mapper is able to auto-detect the right mapping! If the mapper was unable to auto-detect the right field, you would click the icon to the right of the target field to select the correct XDM field. Also, if you didn't want to ingest one of the columns from the CSV, you could delete the row from the mapper. Feel free to play around and change column headings in the `luma-products.csv` to get familiar with how the mapper works.
1. Click the **[!UICONTROL Finish]** button
    ![Select your dataset](assets/ingestion-products-mapper.png)

### Verify the data

When the batch has uploaded, verify the upload by previewing the dataset.

Since the `Luma Product SKU` is a non-people namespace, we won't see any profiles for our product skus.

## Ingest data with Sources

Now let's move into the promised land of _automated_ batch ingestion! 

Click on **[!UICONTROL Sources]** in the left navigation to open the Sources catalog. Here you will see a variety of out-of-the-box integrations with industry-leading data and storage providers. 

![Source catalog](assets/ingestion-offline-sourceCatalog.png)

Okay, let's ingest data using a source connector.

This exercise will be choose-your-own-adventure style. I am going to show the workflow  using the FTP source connector. You can either use a different Cloud Storage source connector that you use at your company, or just upload the json file in the dataset like we did with the loyalty data.

Many of the Sources have a similar configuration workflow, in which you:

1. Enter your authentication details
1. Select the data you want to ingest
1. Select the Platform dataset into which you want to ingest it
1. Map the fields to your XDM schema
1. Choose the frequency with which you want to re-ingest data from that location

So let's get started:

1. Download the [luma-offline-purchases.json](assets/luma-offline-purchases.json) file to your local `Luma Tutorial Assets` folder.
1. Upload it to one of the [!UICONTROL Sources] in the catalog for which you have an account
1. Filter the [!UICONTROL Sources] catalog to **[!UICONTROL Cloud storage]**
1. In the box of your preferred Cloud storage vendor, click the **[!UICONTROL Configure]** button (note there are documentation links if you click the  `...`)
    ![Click configure](assets/ingestion-offline-selectFTP.png)

![Authenticate to the source](assets/ingestion-offline-authentication.png)




## Additional Resources

* [Batch Ingestion documentation](https://docs.adobe.com/content/help/en/experience-platform/ingestion/batch/overview.html)
* [Data Ingestion API reference](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/ingest-api.yaml)

Now let's [stream data using the Web SDK](ingest-streaming-data.md)