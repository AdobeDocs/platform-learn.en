---
title: Set up Developer Console and Postman
seo-title: Set up Developer Console and Postman | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Set up Developer Console and Postman
description: In this lesson, you will set up a project in the Adobe Developer Console and provide you with [!DNL Postman] Collections so you can start using Platform APIs.
role: Data Architect, Data Engineer
feature: API
kt: 4348
thumbnail: 4348-set-up-developer-console-and-postman.jpg
exl-id: 72b541fa-3ea1-4352-b82b-c5b79ff98491
---
# Set up Developer Console and [!DNL Postman]

<!--30min-->

In this lesson, you will set up a project in the Adobe Developer Console and download [!DNL Postman] collections so you can start using Platform APIs.

In order to complete the API exercises in this tutorial, [download the Postman app for your operating system.](https://www.postman.com/downloads/) While not required in order to use Experience Platform APIs, Postman makes API workflows easier, and Adobe Experience Platform provides dozens of Postman collections to help you execute API calls and learn how they operate. The rest of this tutorial assumes some working knowledge of Postman. For assistance, please reference the [Postman documentation](https://learning.postman.com/).

Platform is built API-first. While interface options also exist for all major tasks, you might want to use the Platform API at some point. For example to ingest data, move items around between sandboxes, automate routine tasks or to use new Platform features before the user interface has been built.

**Data Architects** and **Data Engineers** may need to use Platform API outside of this tutorial.

## Permissions required

In the [Configure Permissions](configure-permissions.md) lesson, you set up all the access controls required to complete this lesson.

<!--
* Permission item Sandboxes > `Luma Tutorial`
* Developer-role access to the `Luma Tutorial Platform` product profile
-->

## Set up Adobe Developer Console

Adobe Developer Console is the developer destination to access Adobe APIs & SDKs, listen to near real-time Events, run functions on Runtime, or build plugins or App Builder applications. You will use it to access the Experience Platform API. For more details, see the [Adobe Developer Console documentation](https://www.adobe.io/apis/experienceplatform/console/docs.html)
 
1. Create a folder on your local machine named `Luma Tutorial Assets` for files used in the tutorial.

1. Open the [Adobe Developer Console](https://console.adobe.io){target="_blank"}

1. Log in and confirm that you are in the correct Org

1. Select **[!UICONTROL Create New Project]** in [!UICONTROL Quick Start] menu. 
    
    ![Create New Project](assets/adobeio-createNewProject.png)


1. In the newly created project, select the **[!UICONTROL Edit Project]** button
1. Change the **[!UICONTROL Project Title]** to `Luma Tutorial API Project` (add your name to the end, if multiple people from your company are taking this tutorial)
1. Select **[!UICONTROL Save]**

    ![Adobe Developer Console Project API Config](assets/adobeio-renameProject.png)


1. Select **[!UICONTROL Add API]**
   
    ![Adobe Developer Console Project API Config](assets/adobeio-addAPI.png)

1. Filter the list by selecting **[!UICONTROL Adobe Experience Platform]**

1. In list of available APIs, select **[!UICONTROL Experience Platform API]** and select **[!UICONTROL Next]**.

    ![Adobe Developer Console Project API Config](assets/adobeio-AEPAPI.png)

1. Select **[!UICONTROL OAuth Server-to-Server]** as the credential and select **[!UICONTROL Next]**.
    ![Select OAuth Server-to-Server](assets/adobeio-choose-auth.png)

1. Select the `AEP-Default-All-Users` product profile and select **[!UICONTROL Save Configured API]**

    ![Select Product Profile](assets/adobeio-selectProductProfile.png)

1. Now your Developer Console project has been created!

1. In the **[!UICONTROL Try it out]** section of the page, select **[!UICONTROL Download for Postman]** and then select **[!UICONTROL OAuth Server-to-Server]** to download the [!DNL Postman] environment json file. Save the `oauth_server_to_server.postman_environment.json` in your `Luma Tutorial Assets` folder.


    ![Adobe Developer Console Project API Config](assets/adobeio-io-api.png)

## Have a System Admin add the API Credential to the role

In order to use the API Credential to interact with Experience Platform, you will need to have a System Admin assign the API Credentials to the role created in the previous lesson.  If you are not a System Admin, send them:

1. The [!UICONTROL Name] of your API Credential (`Credential in Luma Tutorial API Project`)
1. The [!UICONTROL Technical Account Email] of your credential (this will help the System Admin find the credential)

    ![[!UICONTROL Name] and [!UICONTROL Technical Account Email] of your credential](assets/postman-credentialDetails.png)

Here are the instructions for the System Admin:

1. Log into [Adobe Experience Platform](https://platform.adobe.com)
1. Select **[!UICONTROL Permissions]** in the left navigation which will take you to the [!UICONTROL Roles] screen
1. Open the `Luma Tutorial Platform` role 
    ![Open the role](assets/postman-openRole.png)
1. Select the **[!UICONTROL API Credentials]** tab
1. Select **[!UICONTROL Add API Credentials]**
    ![Add credential](assets/postman-addCredential.png)
1. Find the `Credential in Luma Tutorial API Project` credential, filtering with the [!UICONTROL Technical Account Email] provided by the tutorial participant, if the list is long
1. Select the credential
1. Select **[!UICONTROL Save]**


    ![Add credential](assets/postman-findCredential.png)

## Set up Postman

>[!CAUTION]
>
>The Postman interface is regularly updated. The screenshots in this tutorial were taken with Postman v10.15.1 for Mac, but interface options may have changed.


1. Download and install [[!DNL Postman]](https://www.postman.com/downloads/)
1. Open [!DNL Postman] and create a workspace
   ![Import environment](assets/postman-createWorkspace.png)

1. Import the downloaded json environment file, `oauth_server_to_server.postman_environment.json`
   ![Import environment](assets/postman-importEnvironment.png)
1. In [!DNL Postman], select your environment in the dropdown

1. Select the icon to view the environment variables:

   ![Change environment](assets/postman-changeEnvironment.png)


### Add the Sandbox Name and Tenant ID

The `SANDBOX_NAME` and `TENANT_ID` and `CONTAINER_ID` variables are not included in the Adobe Developer Console export, so we add them manually:

1. In [!DNL Postman], open the **Environment Variables**
1. Select the **Edit** link to the right of the environment name
1. In the **Add new variable field**, enter `SANDBOX_NAME` 
1. Into both value fields, enter `luma-tutorial`, the name we gave to our sandbox in the previous lesson. If you used a different name for your sandbox, for example, luma-tutorial-ignatiusjreilly, make sure to use that value.
1. In the **Add new variable field**, enter `TENANT_ID`
1. Switch to your web browser and look up your company's tenant id by going to Experience Platform's interface and extracting the portion of the URL *after the @ sign*. For example, my tenant id is `techmarketingdemos` but yours is different:

    ![Obtaining the tenant id from the Platform interface URL](assets/postman-getTenantId.png)

1. Copy this value and return to the [!DNL Postman] Manage Environments screen
1. Paste your tenant id into both value fields
1. In the **Add new variable field**, enter `CONTAINER_ID`
1. Enter `global` into both value fields

    >[!NOTE]
    >
    >`CONTAINER_ID` is a field whose value we change several times during the tutorial. When `global` is used, the API interacts with Adobe-provided elements in your Platform account. When `tenant` is used, the API interacts with your own custom elements.

1. Select **Save**

    ![SANDBOX_NAME, TENANT_ID, and CONTAINER_ID fields added as environment variables](assets/postman-addEnvFields.png)



## Make API Calls

### Retrieve an access token

Adobe provides a rich set of [!DNL Postman] collections to help you explore Experience Platform's API. These collections are in the [Adobe Experience Platform Postman Samples GitHub repo](https://github.com/adobe/experience-platform-postman-samples). You should bookmark this repo as you will use this numerous times throughout this tutorial and later as you implement Experience Platform for your own company.

The first collection works with the Adobe Identity Management Service (IMS) APIs. It is a convenient way to retrieve an acccess token from within Postman.

To generate the access token:

1. Download the [Identity Management Service APIs collection](https://github.com/adobe/experience-platform-postman-samples/blob/master/apis/ims/Identity%20Management%20Service.postman_collection.json) to your `Luma Tutorial Assets` folder
1. Import the collection into [!DNL Postman]
1. Select the request **oAuth: Request Access Token** request and select **Send**
1. You should get a `200 OK` response with an access token in the response

    ![Request the tokens](assets/postman-requestToken.png)

1. The access token should be automatically stored as the **ACCESS_TOKEN** environment variable of your [!DNL Postman] environment.

    ![Postman](assets/postman-config.png)


### Interact with a Platform API

Now let's make a Platform API call to confirm that we've configured everything correctly.

Open the [Experience Platform [!DNL Postman] collections in GitHub](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform). There are many collections on this page, for various Platform APIs. I strongly recommend bookmarking it.

Now, let's make our first API call:

1. Download the [Schema Registry API collection](https://raw.githubusercontent.com/adobe/experience-platform-postman-samples/master/apis/experience-platform/Schema%20Registry%20API.postman_collection.json) to your `Luma Tutorial Assets` folder
1. Import it into [!DNL Postman]
1. Open **Schema Registry API > Schemas > List schemas**
1. Look at the **Params** and **Headers** tabs and note how they include some of the environment variables we entered earlier.
1. Note that the **Headers > Accept value field** is set to `application/vnd.adobe.xed-id+json`. The Schema Registry APIs require one of these [specified Accept header values](https://experienceleague.adobe.com/docs/experience-platform/xdm/api/getting-started.html?lang=en#accept) which provide different formats in the response.
1. Select **Send** to make your first Platform API call!
   
Hopefully you got a successful `200 OK` response containing a list of the available Adobe-provided XDM schemas in your sandbox, as pictured below. 

![First API call in Postman](assets/postman-firstAPICall.png)

If your call was not successful, take a moment to debug using the error response details of the API call and review the steps above. If you get stuck, please request help in the [Community Forum](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform/ct-p/adobe-experience-platform-community) or use the link in the right side of this page to "Log an issue".

With your Platform permissions, sandbox, and [!DNL Postman] set up, you are ready to [model data in schemas](model-data-in-schemas.md)!
