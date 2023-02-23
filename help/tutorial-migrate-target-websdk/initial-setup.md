---
title: Initial setup | Migrate Target from at.js 2.x to Web SDK
description: Learn about and set up the important foundational elements required for your Platform Web SDK implementation
---
# Perform the initial Data Collection setup

Migrating from at.js to Platform Web SDK requires an initial setup to enable proper data capture, features, and functions of Platform Web SDK. The following steps from the [Platform Web SDK implementation tutorial](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/overview.html) must be completed before any website implementation changes take place: 

- [Configure the appropriate permissions](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/initial-configuration/configure-permissions.html){target="_blank"} in the Adobe Admin Console for Data Collection
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
