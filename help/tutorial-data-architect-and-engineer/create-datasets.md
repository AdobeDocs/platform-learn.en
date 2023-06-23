---
title: Create datasets
seo-title: Create datasets | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Create datasets
description: In this lesson, you will create datasets to receive your data.
role: Data Architect, Data Engineer
feature: Data Management
jira: KT-4348
thumbnail: 4348-create-datasets.jpg
exl-id: 80227af7-4976-4fd2-b1d4-b26bc4626fa0
---
# Create datasets

<!--15min-->

In this lesson, you will create datasets to receive your data. You will be excited to know that this is the shortest lesson in the tutorial!

All data that is successfully ingested into Adobe Experience Platform is persisted in the data lake as datasets. A dataset is a storage and management construct for a collection of data, typically a table, that contains a schema (columns) and fields (rows). Datasets also contain metadata that describes various aspects of the data they store.

**Data Architects** will need to create datasets outside of this tutorial.

Before you begin the exercises, watch this short video to learn more about datasets:
>[!VIDEO](https://video.tv.adobe.com/v/27269?quality=12&learn=on)

## Permissions required

In the [Configure Permissions](configure-permissions.md) lesson, you set up all the access controls required to complete this lesson.

<!--
* Permission items **[!UICONTROL Data Management]** > **[!UICONTROL View Datasets]** and **[!UICONTROL Manage Datasets]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
* Developer-role access to the `Luma Tutorial Platform` product profile (for API)
-->

## Create datasets in the UI

In this exercise, we will create datasets in the UI. Let's start with the loyalty data:

1. Go to **[!UICONTROL Datasets]** in the Platform user interface's left navigation
1. Select the **[!UICONTROL Create dataset]** button
    ![Create a dataset](assets/datasets-createDataset.png)

1. On the next screen, select **Create dataset from schema** 
1. On the next screen, select your `Luma Loyalty Schema` and then select the **[!UICONTROL Next]** button
    ![Select the dataset](assets/datasets-selectSchema.png)

1. Name the dataset `Luma Loyalty Dataset` and select the **[!UICONTROL Finish]** button
    ![Name the dataset](assets/datasets-nameDataset.png)
1. When the dataset has saved, you will be taken to a screen like this:
    ![Dataset created](assets/datasets-created.png)

That's it! I told you this was going to be quick. Create these other datasets using the same steps:

1. `Luma Offline Purchase Events Dataset` for your `Luma Offline Purchase Events Schema`
1. `Luma Web Events Dataset` for your `Luma Web Events Schema`
1. `Luma Product Catalog Dataset` for your `Luma Product Catalog Schema`


## Create a dataset using API

Now create the `Luma CRM Dataset` using the API. 

>[!NOTE]
>
>If you want to skip the API exercise and create the `Luma CRM Dataset` in the user interface that's fine. Name it `Luma CRM Dataset` and use the `Luma CRM Schema`.

### Get the id of the schema to be used in the dataset

First we need to get the `$id` of the `Luma CRM Schema`:

1. Open [!DNL Postman]
1. If you don't have an access token, open the request **[!DNL OAuth: Request Access Token]** and select **Send** to request a new access token, just like you did in the [!DNL Postman] lesson.
1. Open the request **[!DNL Schema Registry API > Schemas > Retrieve a list of schemas within the specified container.]**
1. Select the **Send** button
1. You should get a 200 response
1. Look in the response for the `Luma CRM Schema` item and copy the `$id` value
 ![Copy the $id](assets/dataset-crm-getSchemaId.png) 

### Create the dataset

Now you can create the dataset:

1. Download [Catalog Service API.postman_collection.json](https://raw.githubusercontent.com/adobe/experience-platform-postman-samples/master/apis/experience-platform/Catalog%20Service%20API.postman_collection.json) to your `Luma Tutorial Assets` folder.
1. Import the collection into [!DNL Postman]
1. Select the request **[!DNL Catalog Service API > Datasets > Create a new dataset.]**
1. Paste the following as the **Body** of the request, ***replacing the id value with your own***:

    ```json
    {
        "name": "Luma CRM Dataset",

        "schemaRef": {
            "id": "REPLACE_WITH_YOUR_OWN_ID",
            "contentType": "application/vnd.adobe.xed-full+json;version=1"
        },
        "fileDescription": {
            "persisted": true,
            "containerFormat": "parquet",
            "format": "parquet"
        }
    }
    ```

1. Select the **Send** button
1. You should get a 201 Created response containing the id of your new dataset!
    ![Dataset created with API, your custom $id used in the body](assets/datasets-crm-created.png) 
   
>[!TIP]
>
> Common issues making this request and likely fixes:
>
> * `400: There was a problem retrieving xdm schema`. Make sure you have replaced the id in the sample above with the id of your own `Luma CRM Schema`
> * No auth token: Run the **OAuth: Request Access Token** request to generate a new token
> * `401: Not Authorized to PUT/POST/PATCH/DELETE for this path : /global/schemas/`: Update the **CONTAINER_ID** environment variable from `global` to `tenant`
> * `403: PALM Access Denied. POST access is denied for this resource from access control`: Verify your user permissions in the Admin Console


You can go back to the **[!UICONTROL Datasets]** screen in the Platform user interface, you can verify the successful creation of all five datasets!
![Five datasets complete](assets/datasets-allComplete.png) 


## Additional Resources

* [Datasets documentation](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html)
* [Datasets API (part of Catalog Service) reference](https://www.adobe.io/experience-platform-apis/references/catalog/#tag/Datasets)

Now that all of our schemas, identities, and datasets are in place, we can [enable them for Real-Time Customer Profile](enable-profiles.md).
