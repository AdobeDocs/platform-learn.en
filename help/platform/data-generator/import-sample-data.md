---
title: Import sample data to Adobe Experience Platform
description: Learn how to set up an Experience Platform sandbox environment with some sample data.
role: Developer
feature: API
kt: 7349
thumbnail: 7349.jpg
exl-id: da94f4bd-0686-4d6a-a158-506f2e401b4e
---
# Import sample data to Adobe Experience Platform

Learn how to set up an Experience Platform sandbox environment with sample data. Using a Postman collection, you can create field groups, schemas, datasets and then import sample data into Experience Platform.

## Sample data use case 

Experience Platform business users often have to go through a series of steps that include identifying field groups, creating schemas, preparing data, creating datasets, and then ingesting data before they can explore the marketing capabilities offered by Experience Platform. This tutorial automates some of the steps so you can get data into a Platform sandbox as quickly as possible. 

This tutorial focuses on a fictional, retail brand called Luma. Luma operates brick-and-mortar stores in multiple countries and has an online presence with a website and mobile apps. They invest in Adobe Experience Platform to combine loyalty, CRM, web, and offline purchase data into real-time customer profiles and activate these profiles to take their marketing to the next level. We have sample data generated for Luma, and in the next section, you can explore how to import data to Experience Platform.

To complete this tutorial, you can either use the [Postman application's UI](#postman) or use the command line [Collection Runner for Postman (Newman)](#newman)

>[!NOTE]
>
>The end-result of this tutorial is a sandbox containing the same sample data as the [Getting Started with Adobe Experience Platform for Data Architects and Data Engineers tutorial](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html).


## Prerequisites

* You have access to Experience Platform APIs and know how to authenticate. If not, please review this [tutorial](https://experienceleague.adobe.com/docs/platform-learn/tutorials/platform-api-authentication.html).
* You have access to an Experience Platform development sandbox.
* You know your Experience Platform tenant id. Your tenant id should appear in the URL when you log into your Platform account. In the following URL, the tenant is "`techmarketingdemos`" `https://experience.adobe.com/#/@techmarketingdemos/sname:prod/platform/home`. You can also obtain it by making an authenticated [API request](https://experienceleague.adobe.com/docs/experience-platform/xdm/api/getting-started.html?lang=en#know-your-tenant_id).

## Using Postman {#postman}

### Set up environment variables

Before you follow the steps, please ensure that you have downloaded the [Postman](https://www.postman.com/downloads/) application.  Let's get started!

1. Download the [platform-utils-main.zip](../assets/data-generator/platform-utils-main.zip) file, which contains all files required for this tutorial. 

    >[!NOTE]
    >
    >User data contained in the [platform-utils-main.zip](../assets/data-generator/platform-utils-main.zip) file is fictitious and is to be used for demonstration purposes only.

1. From your downloads folder, move the `platform-utils-main.zip` file to the desired location on your computer, and unzip it.
1. In the `luma-data` folder, open all of the `json` files in a text editor and replace all instances of `_techmarketingdemos` with your own tenant id, preceded by an underscore.
1. Note the location of the unzipped folder, as you need it later when setting up the `FILE_PATH` Postman environment variable:

    >[!NOTE]
    > To obtain file path on your Mac, navigate to the `platform-utils-main` folder, right click on the folder and select **Get Info** option.
    >
    > ![MAC file path](../assets/data-generator/images/mac-file-path.png)

    >[!NOTE]
    > To obtain file path on your windows, click to open the location of the desired folder, and then right-click to the right of the path in the address bar. Copy address to obtain the file path.
    > 
    > ![Windows file path](../assets/data-generator/images/windows-file-path.png)

1. Open Postman and create a new workspace from the **Workspaces** dropdown menu:  
    ![Create workspace](../assets/data-generator/images/create-workspace.png)
1. Enter a **Name** and optional **Summary** for your workspace and click **Create Workspace**. Postman will switch to your new workspace when you create it.
   ![Save workspace](../assets/data-generator/images/save-workspace.png)
1. Now adjust some settings to run the Postman collections in this workspace. In the header of Postman, click the wrench icon and select **Settings** to open the settings modal. You can also use the keyboard shortcut (CMD/CTRL + ,) to open the modal.
1. Under the `General` tab, update the request time out in ms to `5000 ms` and enable `allow reading file outside this directory`
    ![Settings](../assets/data-generator/images/settings.png)

    >[!NOTE]
    > If files are loaded from within the working directory it will run smoothly across devices if the same files are stored on the other devices. However, if you wish to run files from outside the working directory, then a setting has to be turned on to state the same intent. If your `FILE_PATH` is not same as the Postman's working directory path, then this option should be enabled.

1. Close the **Settings** panel.
1. Select the **Environments** and then select **Import**: 
    ![Environment Import](../assets/data-generator/images/env-import.png)
1. Import the downloaded json environment file, `DataInExperiencePlatform.postman_environment`
1. In Postman, select your environment in the top-right dropdown and click the eye icon to view the environment variables:
    ![Environment Selection](../assets/data-generator/images/env-selection.png)

1. Make sure that the following environment variables are populated. To learn how to obtain the environment variables' value, check out the [Authenticate to Experience Platform APIs](/help/platform/authentication/platform-api-authentication.md) tutorial for step-by-step instructions. 

    * `CLIENT_SECRET` 
    * `API_KEY`
    * `TECHNICAL_ACCOUNT_ID`
    * `META_SCOPE`
    * `IMS`
    * `IMS_ORG`
    * `PRIVATE_KEY`
    * `SANDBOX_NAME`
    * `CONTAINER_ID`
    * `TENANT_ID`
    * `platform_end_point`
    * `FILE_PATH`&mdash;use the local folder path where you have unzipped the `platform-utils-main.zip` file. Be sure it includes the folder name, e.g. `/Users/dwright/Desktop/platform-utils-main`

1. **Save** the updated environment

### Import Postman collections

Next you need to import the collections into Postman.

1. Select **Collections** and then choose the import option:

    ![Collections](../assets/data-generator/images/collections.png)

1. Import the following collections:

    * `0-Authentication.postman_collection.json`
    * `1-Luma-Loyalty-Data.postman_collection.json`
    * `2-Luma-CRM-Data.postman_collection.json`
    * `3-Luma-Product-Catalog.postman_collection.json`
    * `4-Luma-Offline-Purchase-Events.postman_collection.json`

    ![Collections Import](../assets/data-generator/images/collection-files.png)

### Authenticate

1. Open the `Authentication` collection, Select the `IMS: JWT Generate + Auth via User Token` POST request, and click `SEND` to authenticate and obtain the access token.

    ![Collections Import](../assets/data-generator/images/authentication.png)

1. Review the environment variables, and notice that the `JWT_TOKEN` and `ACCESS_TOKEN` are now populated.

### Import data

Now you can prepare and import the data into your Platform sandbox. The Postman collections you imported will do all of the heavy lifting!

1. Open the `Luma-Loyalty-Data` collection and click **Run** on the overview tab to start a Collection Runner.

    ![Collections Import](../assets/data-generator/images/loyalty.png)

1. In the collection runner window, make sure to select the environment from the dropdown, update the **Delay** to `4000ms`, check the **Save responses** option, and make sure that the run order is correct. Click the **Run Luma Loyalty Data** button

    ![Collections Import](../assets/data-generator/images/loyalty-run.png)

    >[!NOTE]
    >
    >**Luma-Loyalty-Data** creates a schema for customer loyalty data. The schema is based on XDM Individual Profile class, standard field group, and a custom field group and dataype. The collection creates a dataset using the schema and uploads sample customer loyalty data to Adobe Experience Platform.

    >[!NOTE]
    >
    >If any collection requests fail during the Postman collection runner, stop the execution and run the collection requests one by one. 

1. If everything goes well, all requests in the `Luma-Loyalty-Data` collection should pass. 

    ![Loyalty Result](../assets/data-generator/images/loyalty-result.png)

1. Now let's login to [Adobe Experience Platform UI](https://platform.adobe.com/) and navigate to datasets. 
1. Open the `Luma Loyalty Dataset` dataset, and under the dataset activity window, you can view a successful batch run that ingested 1000 records. You can also click on the preview dataset option to verify the records ingested.
     ![Loyalty Dataset](../assets/data-generator/images/loyalty-dataset.png)
1. Repeat steps 1-4 to run the other collections:
    * `2-Luma-CRM-Data.postman_collection.json` creates a schema and populated dataset for CRM data of customers. The schema is based on XDM Individual Profile class that comprises Demographic Details, Personal Contact Details, Preference Details and custom identity field groups. 
    * `3-Luma-Product-Catalog.postman_collection.json` creates a schema and populated dataset for product catalog information. The schema is based on a custom, product catalog class and uses a custom, product catalog field group.
    * `4-Luma-Offline-Purchase-Events.postman_collection.json` creates a schema and populated dataset for offline purchase event data of customers. The schema is based on XDM ExperienceEvent class and comprises the custom identity and Commerce Details field groups.


## Using Newman {#newman}

Before you follow the steps, please make sure that you have access to Experience Platform APIs. For this tutorial, we will be using a sandbox environment as it provides an isolated environment where you can try out functionality without mixing resources and data with your Production environment.

### Install NodeJs and Newman

1. To run Newman, ensure that you have Node.js >= v10. [Install Node.js via package manager](https://nodejs.org/en/download/package-manager/).
1. Run the command `node -v` to make sure that node is installed. 
1. The easiest way to install Newman is using NPM. If you have Node.js installed, it is most likely that you have NPM installed as well.
1. Follow the steps [here](https://www.npmjs.com/package/newman#using-newman-cli) to install newman for your system
1. Run the command `newman -v` to make sure that newman is installed. 
1. Download the [platform-utils-main.zip](../assets/data-generator/platform-utils-main.zip) file, which contains all files required for this tutorial. 

    >[!NOTE]
    >
    >User data contained in the [platform-utils-main.zip](../assets/data-generator/platform-utils-main.zip) file is fictitious and is to be used for demonstration purposes only.

1. From your downloads folder, move the [`platform-utils-main.zip`](../assets/data-generator/platform-utils-main.zip) file to the desired location on your computer, and unzip it.
1. In the `luma-data` folder, open all of the `json` files in a text editor and replace all instances of `_techmarketingdemos` with your own tenant id, preceded by an underscore.
1. Please make a note of the location of the unzipped file, as we might need it later when setting up the `FILE_PATH` Postman environment variable
1. Open the `platform-utils-main` folder in a terminal window.
1. Run `1-Luma-Loyalty-Data.postman_collection.json` to build field groups, schema, dataset, and to ingest sample loyalty data to Adobe Experience Platform
    * `newman run 1-Luma-Loyalty-Data.postman_collection.json -e DataInExperiencePlatform.postman_environment.json --export-environment DataInExperiencePlatform.postman_environment.json —insecure --delay-request 4000`
1. If everything goes well, all requests in the `1-Luma-Loyalty-Data` collection should pass. 
1. Now let's login to [Adobe Experience Platform UI](https://platform.adobe.com/) and navigate to datasets. 
1. Open the `Luma Loyalty Dataset` dataset, and under the dataset activity window, you can view a successful batch run that ingested 1000 records. You can also click on the preview dataset option to verify the records ingested.

     ![Loyalty Dataset](../assets/data-generator/images/loyalty-dataset.png)

1. Repeat steps 10 - 13 to run below collections:
    * Run `2-Luma-CRM-Data.postman_collection.json` to build field groups, schema, dataset, and to ingest sample CRM data to Adobe Experience Platform
      * `newman run 2-Luma-CRM-Data.postman_collection.json -e DataInExperiencePlatform.postman_environment.json --export-environment DataInExperiencePlatform.postman_environment.json --insecure --delay-request 4000`
    * Run `3-Luma-Product-Catalog.postman_collection.json` to build field groups, schema, dataset, and to ingest sample product data to Adobe Experience Platform
      * `newman run 3-Luma-Product-Catalog.postman_collection.json -e DataInExperiencePlatform.postman_environment.json --export-environment DataInExperiencePlatform.postman_environment.json --insecure --delay-request 4000`
    * Run `4-Luma-Offline-Purchase-Events.postman_collection.json` to build field groups, schema, dataset, and to ingest sample product data to Adobe Experience Platform
      * `newman run 4-Luma-Offline-Purchase-Events.postman_collection.json -e DataInExperiencePlatform.postman_environment.json --export-environment DataInExperiencePlatform.postman_environment.json --insecure --delay-request 4000`

## Validation

The sample data have been designed so that when the collections have run, Real-time Customer Profiles are built that combine data from multiple systems. A good example of this is the first record of the loyalty, CRM, and offline purchase datasets. Look up that profile to confirm the data was ingested:

1. Go to **[!UICONTROL Profiles]** > **[!UICONTROL Browse]**
1. Select `Luma Loyalty Id` as the **[!UICONTROL Identity namespace]**
1. Search for `5625458` as the **[!UICONTROL Identity value]**
1. Open the `Danny Wright` profile

![Opening a profile](../assets/data-generator/images/validation-profile-open.png)

By browsing through the data in the **[!UICONTROL Attributes]** and **[!UICONTROL Events]** tabs, you should see that the profile contains data from the various data files:
![Event data from the Offline Purchase events file](../assets/data-generator/images/validation-profile-events.png)

## Next steps

If you would like to learn about merge policies, data governance, query service, and the segment builder, jump over to [lesson 11 in the Getting Started for Data Architects and Data Engineers tutorial](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/create-merge-policies.html?lang=en). The earlier lessons in this tutorial have you manually build everything that was just populated by these Postman collections--enjoy the head start! We hope to add more tutorials which build on this sample data in the future.

## Reset Sandbox environment {#reset-sandbox}

Resetting a non-production sandbox deletes all resources associated with that sandbox (schemas, datasets, and so on), while maintaining the sandbox’s name and associated permissions. This “clean” sandbox continues to be available under the same name for users that have access to it.

Follow the steps [here](https://experienceleague.adobe.com/docs/experience-platform/sandbox/ui/user-guide.html?lang=en#reset-a-sandbox) to reset a sandbox environment.
