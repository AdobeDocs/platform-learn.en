---
title: Authenticate and access Experience Platform APIs
description: This document provides a link to the step-by-step tutorial for gaining access to Adobe Experience Platform APIs. 
role: Developer
feature: API
kt: 3688
thumbnail: 32977.jpg
exl-id: c1774670-436e-46dd-9c9b-177bfee5f749
---
# Authenticate and access [!DNL Experience Platform] APIs

In order to make calls to Adobe Experience Platform APIs, you must first gain access to an Experience Platform developer account.

For step-by-step instructions outlining how to gain access to a developer account, please visit the [Experience Platform API authentication tutorial](https://www.adobe.com/go/platform-api-authentication-en). 

## Create and export Experience Platform API to Postman

[Postman](https://www.getpostman.com/) is a tool allowing developers to quickly and easily interact with Adobe Experience Platform APIs.

Adobe Developer Console's **Export Details for Postman** capability provides an easy way to export all the account details required to access and interact with an Experience Platform API in a single Postman Environment file, removing the need to copy and paste values from Adobe Developer Console into Postman.

>[!VIDEO](https://video.tv.adobe.com/v/28832/?quality=12&learn=on)

## Generate an Access Token with Postman

Use the [Adobe Identity Management Service APIs](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims) to obtain an Access Token to access the Adobe Experience Platform APIs for Non-production Use

>[!VIDEO](https://video.tv.adobe.com/v/29698/?quality=12&learn=on)

>[!WARNING]
>
> As noted in the Adobe I/O Access Token Generation Postman collection, the denoted generation methods are suitable for non-production use. Local Signing loads a JavaScript library from a 3rd-party host, and Remote signing sends the private key to an Adobe owned and operated web service. While Adobe does not store this private key, production keys should never be shared with anyone.

## Interacting with Adobe I/O APIs using Postman

Explore interacting with Adobe I/O APIs using the [Adobe-provided Experience Platform API Postman collections](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform), building upon the [Adobe I/O Environment Variables](#export-adobe-io-integration-details-to-postman) and [generated access token](#generate-an-access-token-with-postman).

>[!VIDEO](https://video.tv.adobe.com/v/29704/?quality=12&learn=on)

Note that Adobe-provided Postman collections may not exist for every Adobe I/O API, however the provided [Experience Platform API Postman collections](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform) can be used as a guide on how to define your own Postman collections for these use-cases.

## Additional Resources

* [Adobe I/O Console](https://console.adobe.io)
* [Adobe Experience Platform Postman Samples](https://github.com/adobe/experience-platform-postman-samples)
  * [Adobe I/O Access Token Generation Postman Collection](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims)
  * [Adobe Experience Platform APIs Postman Collections](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform)
* [Download Postman](https://www.getpostman.com/)
