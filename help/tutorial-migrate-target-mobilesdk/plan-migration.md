---
title: Plan the migration - Migrate the Adobe Target implementation in your mobile app to the Offer Decisioning and Target extension
description: Learn about the key differences between at.js and Platform Web SDK and how to plan your migration effort.
exl-id: 86849319-d2ad-4338-aa1a-d307d8807d4a
TQID: https://experienceleague.adobe.com/ZkLIbybuiFNOF5thbxadzuag2nuV-jbjpBHJWGRPU-w
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
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: d051910f-2bda-47ea-a969-6ade9fcd71f1
    internal-label: Implement mobile
  - id: ee602049-8a18-43df-9299-a689a025a371
    internal-label: Use cases
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
---
# Plan the migration

The level of effort to migrate from the Target extension to the Offer Decisioning and Target extension depends on the complexity of your current implementation and Target features used.

No matter how simple or complex your implementation is, it's important to fully understand your current  state before migrating. This guide helps you to break down the components of your current implementation and develop a manageable plan to migrate each piece. 

The migration process involves the following key steps:

1. Assess your current implementation and determine a migration approach
1. Set up the initial components to connect to the Adobe Experience Platform Edge Network
1. Update the foundational implementation to replace the Target extension with the Offer Decisioning and Target extension
1. Enhance the Optimize SDK implementation for your specific use cases. This may involve passing additional parameters, using response tokens, and more.
1. Update objects in the Target interface, such as profile scripts, activities, and audience definitions
1. Validate the final implementation before making the switch in your production app

>[!INFO]
>
>Within the Adobe Experience Platform Mobile SDK ecosystem, extensions are implemented by SDKs imported into your applications which may have different names:
>
> * **Target SDK** implements the **Adobe Target extension**
> * **Optimize SDK** implements the **Offer Decisioning and Target extension**


Next, review the detailed <!--[comparison of the Target extension and the Offer Decisioning and Target extension](detailed-comparison.md)--> to gain a better understanding of the technical differences and identify areas requiring additional focus. 

>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Offer Decisioning and Target extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-adobe-target-to-mobile-sdk-on-edge/m-p/747484#M625).
