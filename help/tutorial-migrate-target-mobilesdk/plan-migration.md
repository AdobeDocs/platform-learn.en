---
title: Plan the migration - Migrate the Adobe Target implementation in your mobile app to the Adobe Journey Optimizer - Decisioning extension
description: Learn about the key differences between at.js and Platform Web SDK and how to plan your migration effort.
exl-id: 86849319-d2ad-4338-aa1a-d307d8807d4a
---
# Plan the migration

The level of effort to migrate from the Target extension to the Decisioning extension depends on the complexity of your current implementation and Target features used.

No matter how simple or complex your implementation is, it's important to fully understand your current  state before migrating. This guide helps you to break down the components of your current implementation and develop a manageable plan to migrate each piece. 

The migration process involves the following key steps:

1. Assess your current implementation and determine a migration approach
1. Set up the initial components to connect to the Adobe Experience Platform Edge Network
1. Update the foundational implementation to replace the Target extension with the Decisioning extension
1. Enhance the Optimize SDK implementation for your specific use cases. This may involve passing additional parameters, using response tokens, and more.
1. Update objects in the Target interface, such as profile scripts, activities, and audience definitions
1. Validate the final implementation before making the switch in your production app

>[!INFO]
>
>Within the Adobe Experience Platform Mobile SDK ecosystem, extensions are implemented by SDKs imported into your applications which may have different names:
>
> * **Target SDK** implements the **Adobe Target extension**
> * **Optimize SDK** implements the **Adobe Journey Optimizer - Decisioning extension**


Next, review the detailed [comparison of the Target extension and the Decisioning extension](detailed-comparison.md) to gain a better understanding of the technical differences and identify areas requiring additional focus. 

>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Decisioning extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-adobe-target-to-mobile-sdk-on-edge/m-p/747484#M625).
