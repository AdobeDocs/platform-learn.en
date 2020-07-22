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
1. Click **Create Dataset** button in top-left
1. Click **Create Dataset from Schema** 
1. Select **Luma Loyalty Members** Schema  and  Press Next
1. Provide Name **Luma Loyalty Members Dataset**
1. Click Finish.


Follow same steps and create Dataset **Luma Offline Purchase Dataset** for **Luma Offline Purchase Event** Schema.

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

## DULE

In this video we will apply DULE labels on Schema e.g. Luma Loyalty Schema


### Apply Data Governance Labels

1. Go to Data Management and select Datasets option
1. Select **Luma Offline Purchase Dataset**
1. Select **Data Governance** tab for the dataset
1. Find and select **email_id** field in the list
1. Click **Edit Governance labels** pencil icon in right 
1. Select I1 as address field contains email address and it is directly identifiable data that can identify or contact a specific person, rather than a device.

![Dule Label](assets/datasets-dule.png)

1. Click Save changes


Repeat similar steps for other Schemas as well and identify appropriate fields and appropriate labels.

```
Note For SME : In this video you will be also explain what other labels are and when to use which label. You may ask learners to add more DULE label as they think would be right for the Schema. 

```