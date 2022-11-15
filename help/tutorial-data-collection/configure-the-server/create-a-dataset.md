---
title: Create a dataset
description: Create a dataset
exl-id: 19a60087-2f78-4510-b127-b1007a6b7a56
---
# Create a dataset

In addition to describing the data you send into Adobe Experience Platform, you need a place to persist the data. In Adobe Experience Platform, these buckets where you can put data are called datasets. 

>[!NOTE]
>
>Datasets are not required if you are only using Platform Web SDK to send data to Adobe Analytics, Adobe Target, and Adobe Audience Manager or using Event Forwarding. If you are only using Web SDK for those purposes, you can skip this page of the tutorial.

1. Select **[!UICONTROL Datasets]** under [!UICONTROL Data Management] from the left side menu in Adobe Experience Platform.
1. Next, select the **[!UICONTROL Create dataset]** command in the top-right corner.
    ![Datasets view](../assets/datasets-view.png)

## Create a dataset from schema

1. From the [!UICONTROL Workflow] interface, select the first tile, **[!UICONTROL Create dataset from schema]**.
1. Search for the [the schema you previously created](create-a-schema.md) and select it.
    ![Schema selection](../assets/schema-selection.png)
1. Select **[!UICONTROL Next]** and provide a name and a description.
    ![Dataset name and description](../assets/dataset-name-description.png)
1. Select **[!UICONTROL Finish]**. Your dataset has been created and is ready to receive data.

As you begin to send data into a dataset, Adobe Experience Platform validates that the data you're attempting to place into the dataset conforms to the applied schema. If the data does not conform to the schema, the data is rejected and is not placed into the dataset. As a result of this validation step, consumers of the dataset (Adobe products, third parties, or your own company) can have some level of certainty regarding the structure and cleanliness of the dataset's data.

For more information about creating datasets, see [Create datasets and ingest data](/help/platform/data-ingestion/create-datasets-and-ingest-data.md).

[Next: **Create a datastream**](create-a-datastream.md)

>[!NOTE]
>
>Thank you for investing your time in learning about Data Collection. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)

