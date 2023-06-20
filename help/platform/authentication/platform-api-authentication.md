---
title: Authenticate and access Experience Platform APIs
description: Learn how to access to Adobe Experience Platform APIs. 
role: Developer
feature: API
kt: 3688
thumbnail: 28832.jpeg
last-substantial-update: 2023-06-21
exl-id: c1774670-436e-46dd-9c9b-177bfee5f749
---
# Authenticate and access [!DNL Experience Platform] APIs

To make requests to Adobe Experience Platform APIs, you must have an Experience Platform developer account.

## Create a project in Adobe Developer Console and export a Postman environment

[[!DNL Postman]](https://www.postman.com/) is a tool allowing developers to quickly and easily interact with Adobe Experience Platform APIs.

Adobe Developer Console's **Export Details for Postman** capability provides an easy way to export all the account details required to access and interact with an Experience Platform API in a single Postman Environment file, removing the need to copy and paste values from Adobe Developer Console into Postman.

>[!VIDEO](https://video.tv.adobe.com/v/28832/?quality=12&learn=on)

>[!IMPORTANT]
>
>After creating your API credential, a System Administrator at your company must associate the credential with an Experience Platform role.


## Generate an Access Token with Postman

Use the [Adobe Identity Management Service APIs](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims) to obtain an Access Token to access the Adobe Experience Platform APIs.

>[!VIDEO](https://video.tv.adobe.com/v/29698/?quality=12&learn=on)


## Interact with Experience Platform APIs using Postman

Explore interacting with Adobe Experience Platform APIs using the [Adobe-provided Experience Platform API Postman collections](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform), building upon the [Adobe Developer Console Environment Variables](#export-adobe-io-integration-details-to-postman) and [generated access token](#generate-an-access-token-with-postman).

>[!VIDEO](https://video.tv.adobe.com/v/29704/?quality=12&learn=on)


## Additional Resources

* [Adobe Developer Console](https://developer.adobe.com/console/home)
* [Adobe Experience Platform Postman Samples](https://github.com/adobe/experience-platform-postman-samples)
  * [Identity Management System Postman Collection for generating access tokens](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims)
  * [Adobe Experience Platform API Postman Collections](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform)
* [Download Postman](https://www.postman.com/)
