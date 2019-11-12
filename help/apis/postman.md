---
title: Use Postman with Experience Platform APIs
description: Postman is a tool allowing developers to quickly and easily interact with Experience Platform APIs.
seo-title: Use Postman with Adobe Experience Platform APIs
seo-description:  Postman is a tool allowing developers to quickly and easily interact with Adobe Experience Platform APIs.
feature: data-catalog, data-governance, data-ingestion, data-science, experience-data-model, gdpr, identity, observability, opt-in, query-service, real-time-customer-profile, segmentation
topics: 
doc-type: technical-video
activity: develop
audience: developer, implementer
team: tm
kt: 3688
---
 
# Use Postman with Experience Platform APIs

[Postman](https://www.getpostman.com/) is a tool allowing developers to quickly and easily interact with Adobe Experience Platform APIs.

## Export Adobe I/O Integration Details to Postman

Adobe I/O Console's **Export Details for Postman** capability provides an easy way to export all the account details required to access and interact with an Experience Platform API in a single Postman Environment file, removing the need to copy and paste values from the Adobe I/O Console into Postman.

>[!VIDEO](https://video.tv.adobe.com/v/28832/?quality=12)

## Generate an Access Token with Postman

Use the [Adobe I/O Access Token Generation Postman collection](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims) in conjunction with Adobe I/O's Postman Environment to quickly and easily generate an Adobe I/O Access Token that can be used to authenticate to Adobe Experience Platform, and any other Adobe I/O API.

>[!VIDEO](https://video.tv.adobe.com/v/29698/?quality=12)

>[!WARNING]
> As noted in the Adobe I/O Access Token Generation Postman collection, the denoted generation methods are suitable for non-production use. Local Signing loads a JavaScript library from a 3rd-party host, and Remote signing sends the private key to an Adobe owned and operated web service. While Adobe does not store this private key, production keys should never be shared with anyone.

## Interacting with Adobe I/O APIs using Postman

Explore interacting with Adobe I/O APIs using the [Adobe-provided Experience Platform API Postman collections](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform), building upon the [Adobe I/O Environment Variables](#export-adobe-io-integration-details-to-postman) and [generated access token].(#generate-an-access-token-with-postman).

>[!VIDEO](https://video.tv.adobe.com/v/29704/?quality=12)

Note that Adobe-provided Postman collections may not exist for every Adobe I/O API, however the provided [Experience Platform API Postman collections](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform) can be used as a guide on how to define your own Postman collections for these use-cases.

## Additional Resources

* [Adobe I/O Console](https://console.adobe.io)
* [Adobe Experience Platform Postman Samples](https://github.com/adobe/experience-platform-postman-samples)
  * [Adobe I/O Access Token Generation Postman Collection](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims)
  * [Adobe Experience Platform APIs Postman Collections](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform)
* [Download Postman](https://www.getpostman.com/)
