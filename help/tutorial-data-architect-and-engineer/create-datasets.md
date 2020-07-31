---
title: Create Datasets | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
description: 
feature: data ingestion
topics: 
kt: 4348
audience: data architect,data engineer
doc-type: tutorial
activity: implement
---

# Create Datasets

All data that is successfully ingested into Adobe Experience Platform is persisted within the Data Lake as datasets. A dataset is a storage and management construct for a collection of data, typically a table, that contains a schema (columns) and fields (rows). Datasets also contain metadata that describes various aspects of the data they store.

In this lesson, you will create datasets so that you can ingest data into them later on.

First, watch this short video to learn more about datasets:
>[!VIDEO](https://video.tv.adobe.com/v/27269?quality=12&learn=on)

## Permissions required

In the [Configure Permissions](configure-permissions.md) lesson, you setup all the access controls you need to complete this lesson, specifically:

* Permission Item Data Management > View Datasets
* Permission Item Data Management > Manage Datasets
* Permission item Sandboxes > `Luma Tutorial`
* User-role access to the `Luma Tutorial` product profile
* Developer-role access to the `Luma Tutorial` product profile (for API)

## Create a dataset in the UI

In this chapter we will create dataset for following Schema using UI.

  1. Luma Loyalty Members
  1. Luma Offline Purchase Event

```
Note to SME : If you want to create dataset using CSV file , you can create one of the dataset later in the chapter or as a different exercise.
```



### Exercise : Create Dataset

1. Go to **Data Management**
1. Select **Datasets** 
1. Click **Create Dataset** button
1. Click **Create Dataset from Schema** 
1. Select **Luma Loyalty Members** Schema  and  Press Next
1. Provide Name **Luma Loyalty Members Dataset**
1. Click Finish.


Follow same steps and create datasets:

1. `Luma Offline Purchase Dataset` for `Luma Offline Purchase Event** schema
1. `Luma Web Events` for `Luma Web Events` schema

```
Note to SME : Learners not taking API based excersise have to create dataset for LUMA CRM Schema as well. Roles like EA or TC needs to create all datasets using UI . 

In the video you can announce it.

```


## Dataset Using API

In this chapter we will create Dataset for Luma CRM Schama using API


1. Open Postman and authenticate if you have not done so already.

### Get Id of Schema whose dataset needs to created.

1. In Platform collection, Go to folder **3-XDM**
1. Select **Get XDM Status** and press Send button. Request URL should look like as following:

    ```
    GET : https://platform.adobe.io/data/foundation/schemaregistry/stats
    ```

1. In response, you should get details of all schemas. Find **LUMA CRM Schema**

1. Find and Copy **$id** property of **LUMA CRM Schema**


#### Create Dataset

1. In Platform Collection, Go to  folder **4-Datasets** and select **Create Dataset** request.
   
1. Verify Request URL should be as following

    ```
    https://platform.adobe.io/data/foundation/catalog/dataSets?requestDataSource=true

    ```

1. Go to body of Request  and verify body should have similar structure as following, 


    ```

    {
        "name": "Luma CRM Dataset",

        "schemaRef": {
            "id": "https://ns.adobe.com/wwfovlab011/schemas/82c25e828b29cd1a1b092c641ee4cfeb0202ee1a06ee1e10",
            "contentType": "application/vnd.adobe.xed-full+json;version=1"
        },
        "fileDescription": {
            "persisted": true,
            "containerFormat": "parquet",
            "format": "parquet"
        }
    
    }
    ```

1. Replace value of id in **schemaRef** with the id you have copied in exercise 1 step 
1. Press Save & Send 
1. As response you should get Id of dataset as following

    ```
    [
        "@/dataSets/5ef324e3656c671915b229f5"
    ]
    ```

1. You can go to AEP User Interface, Go to **Datasets** under **Data Management** and verify availability of new dataset.

## Additional Resources

* [Datasets documentation](https://docs.adobe.com/content/help/en/experience-platform/catalog/datasets/overview.html)
* [Datasets API (part of Catalog Service) reference](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#/Datasets)