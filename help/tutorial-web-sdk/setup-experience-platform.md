---
title: Stream data to Adobe Experience Platform with Web SDK
description: Learn how to stream web data to Adobe Experience Platform with Web SDK. This lesson is part of the Implement Adobe Experience Cloud with Web SDK tutorial.
exl-id: 4d749ffa-e1c0-4498-9b12-12949807b369
---
# Stream data to Experience Platform with Web SDK
 

>[!CAUTION]
>
>We expect to publish major changes to this tutorial on Friday March 15, 2024. After that point many exercises will change and you may need to restart the tutorial from the beginning in order to complete all of the lessons.

Learn how to stream web data to Adobe Experience Platform with Platform Web SDK. 

Experience Platform is the backbone of all new Experience Cloud applications, such as Adobe Real-Time Customer Data Platform, Adobe Customer Journey Analytics, and Adobe Journey Optimizer. These applications are designed to use Platform Web SDK as their optimal method of web data collection.

Experience Platform uses the same XDM schema you created earlier to capture event data from the Luma website. When that data is sent to Platform Edge Network, the datastream configuration can forward it to Experience Platform.

## Learning objectives

At the end of this lesson, you will be able to:

* Create a dataset within Adobe Experience Platform
* Configure the datastream to send Web SDK data to Adobe Experience Platform
* Enable streaming web data for Real-Time Customer Profile
* Validate the data has landed both in the Platform dataset and in Real-Time Customer Profile

## Prerequisites

You should have already completed the following lessons:

* The **Initial Configuration** lessons:
  * [Configure permissions](configure-permissions.md)
  * [Configure an XDM schema](configure-schemas.md)
  * [Configure a datastream](configure-datastream.md)
  * [Configure an identity namespace](configure-identities.md)

* The **Tags Configuration** lessons:
  * [Install Web SDK extension](install-web-sdk.md)
  * [Create data elements](create-data-elements.md)
  * [Create tag rules](create-tag-rule.md)


## Create a dataset

All data that is successfully ingested into Adobe Experience Platform is persisted within the data lake as datasets. A [dataset](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html?lang=en) is a storage and management construct for a collection of data, typically a table, that contains a schema (columns) and fields (rows). Datasets also contain metadata that describes various aspects of the data they store. 

In this exercise, you create a dataset to track content and e-commerce details for the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html).

>[!WARNING]
>
>You must have already created the `Luma Web Event Data` schema, as instructed in the previous lesson, [Configure an XDM schema](configure-schemas.md).


1. Go to the [Experience Platform interface](https://experience.adobe.com/platform/)
1. Confirm you are in the development sandbox you are using for this tutorial
1. Open **[!UICONTROL Datasets]** from the left navigation
1. Select **[!UICONTROL Create dataset]**

    ![Create schema](assets/experience-platform-create-dataset.png)

1. Select the **[!UICONTROL Create dataset from schema]** option

    ![Create dataset from schema](assets/experience-platform-create-dataset-schema.png)

1. Select the `Luma Web Event Data` schema created in the [earlier lesson](configure-schemas.md) and then select **[!UICONTROL Next]**

    ![Dataset, select schema](assets/experience-platform-create-dataset-schema-selection.png)

1. Provide a **[!UICONTROL Name]** and optional **[!UICONTROL Description]** for the dataset. For this exercise, use `Luma Web Event Data`, then select **[!UICONTROL Finish]**

    ![Dataset Name ](assets/experience-platform-create-dataset-schema-name.png)

A dataset is now configured to start collecting data from your Platform Web SDK implementation.

## Configure the datastream

Now you can configure your [!UICONTROL datastream] to send data to [!UICONTROL Adobe Experience Platform]. The datastream is the link between your tag property, the Platform Edge Network, and the Experience Platform dataset.

1. Open the [Data Collection](https://experience.adobe.com/#/data-collection){target="blank"} interface
1. Select **[!UICONTROL Datastreams]** from the left navigation
1. Open the datastream you created in the [Configure a datastream](configure-datastream.md) lesson, `Luma Web SDK`

    ![Select the Luma Web SDK datastream](assets/datastream-luma-web-sdk.png)

1. Select **[!UICONTROL Add Service]**
     ![Add a service to the datastream](assets/experience-platform-addService.png)
1. Select **[!UICONTROL Adobe Experience Platform]** as the **[!UICONTROL Service]**
1. Select `Luma Web Event Data` as the **[!UICONTROL Event Dataset]**

1. Select **[!UICONTROL Save]**. 

     ![Datastream Config](assets/experience-platform-datastream-config.png)

As you generate traffic in on the [Luma Demo Site](https://luma.enablementadobe.com/content/luma/us/en.html) mapped to your tag property, the data will populate the dataset in Experience Platform!

## Validate the dataset

This step is critical to make sure that the data has landed in the dataset. There are two aspects of validating data sent to the dataset. 

* Validate using [!UICONTROL Experience Platform Debugger]
* Validate using [!UICONTROL Preview Dataset]
* Validate using [!UICONTROL Query Service]

### Experience Platform Debugger

These steps are more or less the same as what you did in the [Debugger lesson](validate-with-debugger.md). However, since data will only be sent to Platform after you have enabled it in the datastream, you must generate some more sample data:

1. Open the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html) and select the [!UICONTROL Experience Platform Debugger] extension icon

1. Configure the Debugger to map the tag property to *your* Development environment, as described in the [Validate with Debugger](validate-with-debugger.md) lesson

   ![Your Launch development environment shown in Debugger](assets/experience-platform-debugger-dev.png)

1. Log into the Luma site using the credentials `test@adobe.com`/`test`

1. Return to the [Luma homepage](https://luma.enablementadobe.com/content/luma/us/en.html)

1. Within the Platform Web SDK network beacons shown by the debugger, select the "events" row to expand details in a pop-up

   ![Web SDK in Debugger](assets/experience-platform-debugger-dev-eventType.png)

1. Search for the "identityMap" within the pop-up. Here you should see lumaCrmId with three keys of authenticatedState, id, and primary
   ![Web SDK in Debugger](assets/experience-platform-debugger-dev-idMap.png)

Now data should be populated in the `Luma Web Event Data` dataset and ready for 'Preview Dataset' validation.

### Preview the dataset

To confirm that the data has landed in Platform's data lake, a quick option is to use the **[!UICONTROL Preview dataset]** feature. Web SDK data is micro-batched to the data lake and refreshed in the Platform interface on a periodic basis. It might take 10-15 minutes to see the data that you generated.

1. In the [Experience Platform](https://experience.adobe.com/platform/) interface, select **[!UICONTROL Datasets]** in the left-navigation to open the **[!UICONTROL Datasets]** dashboard. 

    The dashboard lists all available datasets for your organization. Details are displayed for each listed dataset, including its name, the schema the dataset adheres to, and status of the most recent ingestion run.

1. Select your `Luma Web Event Data` dataset to open its **[!UICONTROL Dataset activity]** screen. 

    ![Dataset Luma Web Event](assets/experience-platform-dataset-validation-lumaSDK.png)

    The activity screen includes a graph visualizing the rate of messages being consumed as well as a list of successful and failed batches.

1. From the **[!UICONTROL Dataset activity]** screen, select **[!UICONTROL Preview dataset]** near the top-right corner of your screen to preview up to 100 rows of data. If the dataset is empty, the preview link is deactivated.

    ![Dataset Preview](assets/experience-platform-dataset-preview.png)

    In the preview window, the hierarchical view of the schema for the dataset is shown on the right.

    ![Dataset Preview 1](assets/experience-platform-dataset-preview-1.png)

>[!INFO]
>
>Adobe Experience Platform's query service is a more robust method to validate data in the lake, but is beyond the scope of this tutorial. For more details, see [Explore data](https://experienceleague.adobe.com/docs/platform-learn/tutorials/queries/explore-data.html) in the Platform tutorials section.


## Enable the dataset and schema for Real-Time Customer Profile

The next step is to enable the dataset and schema for Real-Time Customer Profile. Data streaming from Web SDK will be one of many data sources flowing into Platform and you want to join your web data with other data sources to build 360-degree customer profiles. To learn more about Real-Time Customer Profile, watch this short video:

>[!VIDEO](https://video.tv.adobe.com/v/27251?learn=on&captions=eng)

>[!CAUTION]
>
>When working with your own website and data, we recommend more robust validation of data before enabling it for Real-Time Customer Profile.


**To enable the dataset:**

1. Open the dataset you created, `Luma Web Event Data`

1. Select the **[!UICONTROL Profile Toggle]** to turn it on
    
    ![Profile Toggle](assets/setup-experience-platform-profile.png)

1. Confirm you want to **[!UICONTROL Enable]** the dataset

   ![Profile Enable Toggle](assets/setup-experience-platform-profile-enable.png)

**To enable the schema:**

1. Open the schema you created, `Luma Web Event Data`

1. Select the **[!UICONTROL Profile Toggle]** to turn it on
    
    ![Profile Toggle](assets/setup-experience-platform-profile-schema.png)

1. Select **[!UICONTROL Data for this schema will contain a primary identity in the identityMap field.]**

    >[!IMPORTANT]
    >
    >    Primary identities are required in every record sent to Real-Time Customer Profile. Typically, identity fields are labeled within the schema. When using identity maps, however, the identity fields are not visible within the schema. This dialog is to confirm that you have a primary identity in mind and that you will specify it in an identity map when sending your data. As you know, Web SDK uses an identity map, and the Experience Cloud Id (ECID) is the default primary identity.


1. Select **[!UICONTROL Enable]**

   ![Profile Enable Toggle](assets/setup-experience-platform-profile-schema-enable.png)

1. Select **[!UICONTROL Save]** to save the updated schema

Now the schema is also enabled for profile.

>[!IMPORTANT]
>
>    Once a schema is enabled for Profile, it cannot be disabled or deleted. Also, fields cannot be removed from the schema after this point. These implications are important to keep in mind later on when you are working with your own data in your Production environment. You should be using a development sandbox in this tutorial, which can be deleted at any time. 
>
>   
> When working with your own data, we recommend you do things in the following order:
> 
> * First, ingest some data into your datasets.
> * Address any issues that arise during the data ingestion process (for example, data validation or mapping issues).
> * Enable your datasets and schemas for Profile
> * Re-ingest the data


### Validate a profile

You can look up a customer profile in the Platform interface (or Journey Optimizer interface) to confirm that the data has landed in Real-Time Customer Profile. As the name suggests, profiles populate in real-time, so there is no delay like there was with validating data in the dataset.

First you must generate more sample data. Repeat the steps from earlier in this lesson to log into the Luma website when it is mapped to your tag property. Inspect the Platform Web SDK request to make sure it sends data with the `lumaCRMId`.

1. In the [Experience Platform](https://experience.adobe.com/platform/) interface, select **[!UICONTROL Profiles]** in the left-navigation

1. As the **[!UICONTROL Identity namespace]** use `lumaCRMId`
1. Copy & paste the value of the `lumaCRMId` passed in the call you inspected in the Experience Platform Debugger (probably `112ca06ed53d3db37e4cea49cc45b71e`).

    ![Profile](assets/experience-platform-validate-dataset-profile.png)

1. If there is a valid value in the Profile for `lumaCRMId`, a Profile ID populates in the console:

    ![Profile](assets/experience-platform-validate-dataset-profile-set.png)

1. Click into the [!UICONTROL Profile ID] and a [!UICONTROL Customer profile] console populates. Here you can see all the identities linked to the `lumaCRMId`, such as the `ECID`:

    ![Customer profile](assets/experience-platform-validate-dataset-custProfile.png)

You have now enabled Platform Web SDK for Experience Platform (And Real-Time CDP! And Customer Journey Analytics! And Journey Optimizer!)!


[Next: **Set up Adobe Analytics**](setup-analytics.md)

>[!NOTE]
>
>Thank you for investing your time in learning about Adobe Experience Platform Web SDK. If you have questions, want to share general feedback, or have suggestions on future content, share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)