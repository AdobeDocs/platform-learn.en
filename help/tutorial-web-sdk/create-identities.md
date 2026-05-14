---
title: Capture identities for Platform Web SDK
description: Learn how to capture identities in XDM and use the Identity Map data element to capture user IDs. This lesson is part of the Implement Adobe Experience Cloud with Web SDK tutorial.
feature: Web SDK, Tags, Identities
jira: KT-15402
exl-id: 7ca32dc8-dd86-48e0-8931-692bcbb2f446
TQID: https://experienceleague.adobe.com/XfcK4y-Jz52jRfD1n2xTbcQjb9Z-3qZ1PQw9X7zdjFY
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
    internal-label: Acrobat Sign
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
    internal-label: Target
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: adee20bd-51f4-461d-b9db-d215f8756eeb
    internal-label: Audiences
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
    internal-label: Implementation
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: acc16deb-1d7f-4ec9-9ce3-6cdf355afde6
    internal-label: XDM
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: d9830f6f-ceb6-4faa-9744-f281fe4439f9
    internal-label: Tags
  - id: de9975b2-c43a-4287-9698-4f4cad92b83f
    internal-label: Schemas
  - id: f6ff4d13-7b5c-4533-8556-95e76673d4cb
    internal-label: Properties
  - id: f9a2105e-7a47-4e85-9193-31a519a2cb83
    internal-label: Data elements
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# Capture identities

Learn how to capture identities with Adobe Experience Platform Web SDK. Capture both unauthenticated and authenticated identity data on the [Luma demo website](https://luma.enablementadobe.com). Learn how to use the data elements you created earlier for collecting authenticated data with a Platform Web SDK data element type called Identity map. 

This lesson focuses on the Identity map data element available with the Adobe Experience Platform Web SDK tags extension. You map data elements containing an authenticated user ID and authentication status to XDM. 



## Learning objectives

At the end of this lesson, you are able to:

* Understand the relationship between Experience Cloud ID (ECID) and First Party Device ID (FPID)
* Understand the difference between unauthenticated vs authenticated IDs
* Create an identity map data element

## Prerequisites 

You have an understanding of what a data layer is, gotten familiar with the [Luma demo website](https://luma.enablementadobe.com){target="_blank"} data layer, and know how to reference data elements in tags. You must have completed the previous lessons in the tutorial:

* [Configure an XDM schema](configure-schemas.md)
* [Configure an identity namespace](configure-identities.md)
* [Configure a datastream](configure-datastream.md)
* [Web SDK extension installed in the tag property](install-web-sdk.md)
* [Create data elements](create-data-elements.md)


## Experience Cloud ID

The [Experience Cloud ID (ECID)](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/ecid) is a shared identity namespace used across Adobe Experience Platform and Adobe Experience Cloud applications. ECID provides the foundation for customer identity and is the default identity for digital properties. ECID is the ideal identifier for tracking unauthenticated user behavior because it is always present.

<!-- 
FYI I commented this out because it was breaking the build - Jack
>[!TIP]
>
> When you use the Experience Platform Web SDK to set up Adobe applications on your digital properties, the ECID is generated at the Adobe Edge server level. As such, ECID is not viewable on the client-side network request payload. You can view the ECID by seeing the Preview tab of the network request, or by using the [Adobe Experience Platform Debugger Edge Trace](set-up-analytics.md#experience-cloud-id-validation).
>![View ECID](assets/validate-dev-console-ecid.png)
-->

Read more about how [ECIDs are tracked using Platform Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge/identity/overview).

ECIDs are set using a combination of first-party cookies and Platform Edge Network. By default, the first-party identity cookies are set client-side by the Web SDK. To account for browser restrictions on cookie lifespans, you can opt to set your own first-party identity cookies server-side instead. These identity cookies are referred to as first-party device IDs (FPIDs).

>[!IMPORTANT]
>
>The [Experience Cloud ID Service extension](https://exchange.adobe.com/apps/ec/100160/adobe-experience-cloud-id-launch-extension) is not needed when implementing Adobe Experience Platform Web SDK, as the ID Service functionality is built into Platform Web SDK.

## First Party Device ID (FPID)

FPIDs are first-party cookies _you set using your own web servers_ which Adobe then uses to create the ECID, instead of using the first-party cookie set by the Web SDK. While browser support may vary, first-party cookies tend to be more durable when set by a server that leverages a DNS A record (for IPv4) or AAAA record (for IPv6), as opposed to when set by a DNS CNAME or JavaScript code.

Once an FPID cookie is set, its value can be fetched and sent to Adobe as event data is collected. Collected FPIDs are used as seeds to generate ECIDs on Platform Edge Network, which continue to be the default identifiers in Adobe Experience Cloud applications. 

While FPIDs are not used in this tutorial, you are encouraged to use FPIDs in your own Web SDK implementation. Read more about [First-party device IDs in the Platform Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge/identity/first-party-device-ids)

>[!CAUTION]
>
> FPID is an alternative way of generating the ECID by using a cookie set by your web servers. It is not used for identifying authenticated users.

## Authenticated Id

As noted above, all visitors to your digital properties are assigned an ECID by Adobe when using Platform Web SDK. ECID is the default identity for tracking unauthenticated digital behavior. 

You can also send an authenticated user ID so that Platform can create [Identity Graphs](https://experienceleague.adobe.com/en/docs/platform-learn/tutorials/identities/understanding-identity-and-identity-graphs) and Target can set its [Third Party Id](https://experienceleague.adobe.com/en/docs/target/using/audiences/visitor-profiles/3rd-party-id). Setting the authenticated id is done by using the [!UICONTROL Identity Map] data element type.

To create the [!UICONTROL Identity Map] data element:

1. Go to **[!UICONTROL Data Elements]** and select **[!UICONTROL Add Data Element]**

1. **[!UICONTROL Name]** the data element `Identity Map`

1. As the **[!UICONTROL Extension]**, select `Adobe Experience Platform Web SDK`

1. As the **[!UICONTROL Data Element Type]**, select `Identity map`

1. As the  **[!UICONTROL Namespace]**, select the `lumaCrmId` namespace created in the [Configure Identities](configure-identities.md) lesson. If it does not appear in the dropdown, type it in.

1. As the **[!UICONTROL ID]**, select the `User Id` data element created in the [Create data elements](create-data-elements.md#create-data-elements-to-capture-the-data-layer) lesson. 

1. As the **[!UICONTROL Authenticated state]**, select **[!UICONTROL Authenticated]**
1. Select **[!UICONTROL Primary]**

1. Select **[!UICONTROL Save]**
   
    ![Data Collection interface](assets/identity-id-namespace.png)

>[!IMPORTANT]
>
> Adobe recommends sending identities that represent a person, such as `Luma CRM Id`, as the [!UICONTROL primary] identity.
>
> If the identity map contains the person identifier (for example, `Luma CRM Id`), then the person identifier becomes the [!UICONTROL primary] identity. Otherwise, `ECID` becomes the [!UICONTROL primary] identity.
>
> Additionally, for customers of Platform applications, Adobe recommends implementing [identity graph linking rules](https://experienceleague.adobe.com/en/docs/platform-learn/tutorials/identities/graph-linking-rules/overview) to prevent graph collapse.

>[!NOTE]
>
> You do not need to take any action to capture the ECID in a Web SDK implementation. It is captured automatically.


At the end of these steps, you should have the following data elements created:

|Core Extension Data Elements | Platform Web SDK Extension Data Elements|
|-----------------------------|-------------------------------|
| `Ecommerce Cart Products` | `Data Variable` |
| `Ecommerce Product Category` | `Identity Map` |
| `Ecommerce Product Id` | `XDM Variable` |
| `Ecommerce Product Name` | |
| `Ecommerce Purchase Id`| |
| `Ecommerce Purchase Products` |  |
| `Page Name`| |
| `User Id`| |
| `User Logged In` | |

With these data elements in place, you are ready to start sending data to Platform Edge Network by creating a rule in tags.

>[!NOTE]
>
>Thank you for investing your time in learning about Adobe Experience Platform Web SDK. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/adobe-experience-platform-18/tutorial-discussion-implement-adobe-experience-cloud-with-web-sdk-tutorial-248848)
