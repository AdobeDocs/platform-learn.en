---
title: Authenticate and access Experience Platform APIs
description: Learn how to access to Adobe Experience Platform APIs. 
feature: API
role: Developer
level: Beginner
jira: KT-3688
thumbnail: 28832.jpeg
last-substantial-update: 2023-06-21
exl-id: c1774670-436e-46dd-9c9b-177bfee5f749
---
# Authenticate and access [!DNL Experience Platform] APIs

Learn how to get started with Adobe Experience Platform APIs. This tutorial guides you through the process to create authentication credentials and start making Experience Platform API requests.

## Create a project in Adobe Developer Console and export a Postman environment{#export-integration-details-to-postman}

[[!DNL Postman]](https://www.postman.com/) is a third-party application which helps developers quickly and easily interact with Adobe Experience Platform APIs.

[Adobe Developer Console's](https://developer.adobe.com/console/home) **Export Details for Postman** capability provides an easy way to export the account details required to access and interact with an Experience Platform APIs in a single Postman Environment file, removing the need to copy-and-paste values from Adobe Developer Console into Postman.

>[!IMPORTANT]
>
>To access the [Adobe Developer Console](https://developer.adobe.com/console/home), you must be a either a [System Administrator](https://helpx.adobe.com/enterprise/using/admin-roles.html) or a [Developer](https://helpx.adobe.com/enterprise/using/manage-developers.html#:~:text=Add%20developers%20to%20a%20single%20product%20profile&text=In%20the%20Admin%20Console%2C%20navigate,in%20the%20upper%2Dright%20corner.) in the [Adobe Admin Console](https://adminconsole.adobe.com).
>
> After creating your API credential, a System Administrator must associate the credential with a role in the Experience Platform.

>[!VIDEO](https://video.tv.adobe.com/v/28832/?learn=on&enablevpops)

## Generate an Access Token with Postman{#generate-an-access-token-with-postman}

Use the [Adobe Identity Management Service APIs](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims) to obtain an Access Token to access the Adobe Experience Platform APIs.

>[!VIDEO](https://video.tv.adobe.com/v/29698/?learn=on&enablevpops)


## Interact with Experience Platform APIs using Postman

Explore interacting with Adobe Experience Platform APIs using the [Adobe-provided Experience Platform API Postman collections](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform), building upon the [Adobe Developer Console Environment Variables](#export-integration-details-to-postman) and [generated access token](#generate-an-access-token-with-postman).

>[!VIDEO](https://video.tv.adobe.com/v/29704/?learn=on&enablevpops)


## Resources referenced in these videos

* [Adobe Developer Console](https://developer.adobe.com/console/home)
* [Adobe Experience Platform Postman Samples](https://github.com/adobe/experience-platform-postman-samples)
  * [Identity Management System Postman Collection for generating access tokens](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims)
  * [Adobe Experience Platform API Postman Collections](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform)
* [Download Postman](https://www.postman.com/)
