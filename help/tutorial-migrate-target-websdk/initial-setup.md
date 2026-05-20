---
title: Initial setup - Migrate Target from at.js 2.x to Web SDK
description: Learn about and set up the important foundational elements required for your Platform Web SDK implementation
exl-id: dbf9683b-1cfc-474a-9c38-432cad4d1533
TQID: https://experienceleague.adobe.com/6G49P15e6dfftWGERgtLZJEm9T19ZzYkoP0G858U1ro
product_v2:
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
    internal-label: Target
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
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
  - id: de9975b2-c43a-4287-9698-4f4cad92b83f
    internal-label: Schemas
  - id: fd0ff162-b6d3-4a11-8aeb-e165a01c0f0a
    internal-label: at.js
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
---
# Perform the initial Data Collection setup

Migrating from at.js to Platform Web SDK requires an initial setup to enable proper data capture, features, and functions of Platform Web SDK. The following steps from the [Platform Web SDK implementation tutorial](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/overview.html) must be completed before any website implementation changes take place: 

- [Configure the appropriate permissions](https://experienceleague.adobe.com/en/docs/platform-learn/implement-web-sdk/overview#prerequisites){target="_blank"} in the Adobe Admin Console for Data Collection
- [Configure an XDM schema](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-schemas.html){target="_blank"} for passing structured data to the Edge Network  
- [Configure an identity namespace](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-identities.html){target="_blank"} for cross-device personalization and mbox3rdPartyId functionality 
- [Create a datastream](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-datastream.html){target="_blank"} to enable forwarding of data from Edge Network
- [Configure the datastream](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/applications-setup/setup-target.html#configure-the-datastream){target="_blank"} to enable forwarding of data to Adobe Target

>[!CAUTION]
>
>Remember that these design aspects should be coordinated across Target, Analytics, and Audience Manager migrations.

Once the initial configuration is complete, Target functionality should be enabled using the Adobe Experience Platform Edge Network.

Next, learn how to [replace the at.js library and set up a basic Platform Web SDK implementation](replace-library.md).

>[!NOTE]
>
>We are committed to helping you be successful with your Target migration from at.js to Web SDK. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
