---
title: Initial setup - Migrate the Adobe Target implementation in your mobile app to the Offer Decisioning and Target extension
description: Learn about and set up the important foundational elements required for your Platform Web SDK implementation
exl-id: dfc5abc8-0e79-454a-b1bb-6a42b1219771
TQID: https://experienceleague.adobe.com/Nrn5f5OpYbrPbEvR9U8XNbt1-ZOmkGqi-zc2MXvz3qA
product_v2:
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
    internal-label: Target
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: c20d46e7-1c7d-476c-a50e-3961d4dce35f
    internal-label: Reporting
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
  - id: c1f1ac67-ccab-4be9-a93a-b7faba1192c4
    internal-label: Assurance
  - id: d051910f-2bda-47ea-a969-6ade9fcd71f1
    internal-label: Implement mobile
  - id: d9830f6f-ceb6-4faa-9744-f281fe4439f9
    internal-label: Tags
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
---
# Perform the initial Data Collection setup

Migrating from Target SDK to Optimize SDK requires an initial setup to enable proper data capture, features, and functions of Optimize SDK. The following steps must be completed before any mobile app implementation changes take place:

- [Configure the appropriate permissions](https://experienceleague.adobe.com/en/docs/platform-learn/implement-web-sdk/overview#permissions){target="_blank"} in the Adobe Admin Console for Data Collection
- [Configure an XDM schema](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/initial-configuration/create-schema){target="_blank"} for passing structured data to the Edge Network  
- [Configure the schema](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/experience-cloud/target#update-your-schema){target="_blank"} to receive Adobe Target data
- [Configure an identity namespace](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/app-implementation/identity#set-up-a-custom-identity-namespace){target="_blank"} for cross-device personalization and mbox3rdPartyId functionality 
- [Create a datastream](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/initial-configuration/create-datastream){target="_blank"} to enable forwarding of data from Edge Network
- [Configure the datastream](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/experience-cloud/target#update-datastream-configuration){target="_blank"} to enable forwarding of data to Adobe Target
- [Configure the Tag property](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/experience-cloud/target#install-adobe-journey-optimizer---decisioning-tags-extension){target="_blank"} for Offer Decisioning and Target extension

## Extension configuration

>[!BEGINTABS]

>[!TAB Offer Decisioning and Target extension]

Tag extensions installed when using the Offer Decisioning and Target extension:

1. Offer Decisioning and Target
1. Adobe Experience Platform Edge Network
1. Mobile Core
1. Profile
1. Consent
1. Identity
1. AEP Assurance (Optional, needed for debugging)

![Tag extensions installed when using the Offer Decisioning and Target extension](assets/tag-extensions-decisioning.png)

>[!TAB Target extension] 

Tag extensions installed when using the Target extension:

1. Adobe Target
1. Mobile Core
1. Profile
1. Adobe Analytics (Optional, needed if using Adobe Analytics as reporting source for Adobe Target activities)

![Tag extensions installed when using the Target extension](assets/tag-extensions-target.png)

>[!ENDTABS]

## Datastream configuration

The Target extension has [configurable settings](https://developer.adobe.com/client-sdks/solution/adobe-target/#configure-the-target-extension-in-the-data-collection-ui) which with the Decision extension are [configured in the datastream](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#adobe-experience-platform-data-collection-setup).

| Target extension | Offer Decisioning and Target extension | Notes |
| --- | --- | --- |
| Client Code | n/a | Set automatically by the edge using the IMS Org details |
| Environment ID | Target Environment ID | Configured in the datastream |
| Target Workspace Property | Property Token | Configured in the datastream |
| Timeout | Timeout | Configurable in the Offer Decisioning and Target extension and in the Optimize SDK. The default timeout is 10 seconds. |
| Server Domain | Edge Network domain | Set in the Adobe Experience Platform Edge Network extension |

Next, learn how to [replace the Target SDK](replace-sdk.md).

>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Offer Decisioning and Target extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-adobe-target-to-mobile-sdk-on-edge/m-p/747484#M625).
