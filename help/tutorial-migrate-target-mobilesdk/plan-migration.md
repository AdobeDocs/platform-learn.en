---
title: Plan the migration - Migrate from the Adobe Target to the Adobe Journey Optimizer - Decisioning Mobile extension
description: Learn about the key differences between at.js and Platform Web SDK and how to plan your migration effort.
exl-id: 86849319-d2ad-4338-aa1a-d307d8807d4a
---
# Plan the migration

The level of effort to migrate from the Target extension to the Decisioning extension depends on the complexity of your current implementation and product features used.

No matter how simple or complex your implementation is, it's important to fully understand your current  state before migrating. This guide helps you to break down the components of your current implementation and develop a manageable plan to migrate each piece. 

The migration process involves the following key steps:

1. Assess your current implementation and determine a migration approach
1. Set up the initial components to connect to the Adobe Experience Platform Edge Network
1. Update the foundational implementation to replace the Target extension and the Decisioning extension
1. Enhance the Optimize SDK implementation for your specific use cases. This may involve passing additional parameters, using response tokens, and more.
1. Update objects in the Target interface, such as profile scripts, activities, and audience definitions
1. Validate the final implementation before making the switch in your production environment

## Key differences between the Target extension and the Decisioning extension

Before starting the migration process, it is important to understand the differences between the Target extension and the Decisioning extension.

### Operational differences

| | Target at.js 2.x | Platform Web SDK |
|---|---|---|
| Process | Changes to a Target implementation may follow a process that has a different cadence or QA requirements compared to other applications like Analytics. | Changes to a Decisioning extension implementation should consider all downstream applications, and the QA and publish process should be adjusted accordingly. |
| Collaboration | Data specific to Target can be passed directly in the Target calls. If Target reporting source is Adobe Analytics, data specific to Target can also be passed to Adobe Analytics when appropriate tracking methods in the Target extension are called for Target content display and interaction. | Data passed in Decisioning extension calls can be forwarded to both Target and Analytics if Target reporting source is Adobe Analytics, Adobe Analytics is enabled in the data stream, and appropriate tracking methods in Decisioning extension are called when Target content is displayed and interacted with. |

### Technical differences

| | Target extension | Decisioning extension |
|---|---|---|
| Dependencies | Depends only on Mobile Core SDK | Depends on Mobile Core and Edge Network SDK |
| Library Functionality | Supports fetching content from Adobe Target only | Support fetching content from Adobe Target  and Offer decisioning |
| Requests | Target calls are largely independent from other network calls | Target network calls are queued along with network calls for other Edge-based solutions like Messaging in the Edge SDK and executed serially. |
| Edge Network | Uses the Target server value or the the Adobe Experience Cloud Edge Network with the client code (clientcode.tt.omtrdc.net), both specified in the [Target configuration](https://developer.adobe.com/client-sdks/solution/adobe-target/#configure-the-target-extension-in-the-data-collection-ui) in the Data Collection UI | Uses the Edge network domain specified in Adobe Experience Platform [Edge Network configuration](https://developer.adobe.com/client-sdks/edge/edge-network/#configure-the-edge-network-extension-in-data-collection-ui) in Data collection UI. |
| Basic Terminology | mbox, TargetParameters | DecisionScope, Map (Android)/dictionary (iOS) for target parameters |
| Default content | Allows passing client-side default content in TargetRequest which is returned if the network call fails or results in error. | Does not allow passing client-side default content. Does not return any content if network call fails or results in error. |
| Target parameters | Allows passing global TargetParameters per request and different TargetParameters per mbox | Allows passing global TargetParameters per request only |

Next, review the detailed [comparison of the Target extension and the Decisioning extension](detailed-comparison.md) to gain a better understanding of the technical differences and identify areas requiring additional focus. 

>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Decisioning extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
