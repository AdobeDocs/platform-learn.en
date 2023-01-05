---
title: Migration overview | Migrate Target from at.js 2.x to Web SDK
description: Learn about the key differences between at.js and Platform Web SDK and how to plan your migration effort.=
---
# Target at.js to Platform Web SDK migration overview

The level of effort to migrate from at.js to Platform Web SDK depends on the complexity of your current implementation and product features used.

No matter how simple or complex your implementation is, it's important to fully understand your current  state before migrating. This guide helps you to break down the components of your current implementation and develop a manageable plan to migrate each piece. 

The migration process involves the following key steps:

1. Assess your current implementation and determine a migration approach
1. Set up the initial components to connect to the Adobe Experience Platform Edge Network
1. Update the foundational implementation to replace at.js with the Platform Web SDK
1. Enhance the Platform Web SDK implementation for your specific use cases. This may involve passing additional parameters, accounting for single-page app (SPA) view changes, using response tokens, and more.
1. Update objects in the Target interface, such as profile scripts, activities, and audience definitions
1. Validate the final implementation before making the switch in your production environment

## Key differences between at.js and Platform Web SDK

Before starting the migration process, it is important to understand the differences between at.js and the Platform Web SDK.

### Operational differences

The Platform Web SDK combines the functionality of multiple Adobe applications into a single library. This unified approach means you should consider cross-team responsibilities and processes to ensure a healthy implementation.

| | Target at.js 2.x | Platform Web SDK |
|---|---|---|
| Ownership | The at.js library is independent from other application libraries. Customizations and ownership of these disparate libraries may align to different teams in the organization. | The Platform Web SDK library and the data passed is unified for all Adobe applications. Ownership of the Platform Web SDK implementation should represent stakeholders of all downstream applications. |
| Maintenance | Separate teams may work on implementation enhancements for each Adobe application, like Target and Analytics. | Ideally, a single team should be responsible for enhancements that impact the Platform Web SDK implementation. |
| Process | Changes to a Target implementation may follow a process that has a different cadence or QA requirements compared to other applications like Analytics. | Changes to a Platform Web SDK implementation should consider all downstream applications, and the QA and publish process should be adjusted accordingly. |
| Collaboration | Data specific to Target can be passed directly in the Target calls. Depending on the implementation, there may be additional Target calls. This has no direct impact on Adobe Analytics data and coordination with the analytics team is not as critical. | Data passed in Platform Web SDK calls can be forwarded to both Target and Analytics. Coordination between teams is required to ensure that changes do not adversely impact a specific application. |

### Technical differences

The Platform Web SDK is not an evolution of the Target at.js library. It is a new and unified approach for implementing all Adobe applications for the web channel. There are several technical differences to be aware of.

| | Target at.js 2.x | Platform Web SDK |
|---|---|---|
| Library Functionality | Target functionality provided by at.js. Integrations with other applications provided by Visitor.js and AppMeasurement.js | Functionality for all Adobe applications provided by a single Platform Web SDK library: alloy.js |
| Performance | at.js is one of multiple libraries that must be loaded for proper integration across applications. This results in less than optimal load time. | The Platform Web SDK is a single lightweight library that removes the need for multiple application-specific libraries resulting in better page load performance. |
| Requests | Separate calls for each Adobe application. Target calls are largely independent from other network calls. | A single call for all Adobe applications. Changes to the data passed in these calls could impact multiple downstream applications. |
| Load Order | Proper integration with other Adobe applications requires a specific load order of libraries and network calls. | Proper integration does not rely on stitching data from disparate application-specific network calls, thus load order is not a concern. |
| Edge Network | Uses the Adobe Experience Cloud Edge Network (tt.omtrdc.net), optionally with a CNAME specific to Target. | Uses the Adobe Experience Platform Edge Network (edge.adobedc.net), optionally with a single CNAME. |
| Basic Terminology | at.js naming: <br> - `mbox` <br> - `pageLoad` event (global mbox) <br> - `offer` | Platform Web SDK equivalent: <br> - `decisionScope` <br> - `__view__` decisionScope <br> - `proposition`|

### Video overview

The following video gives an overview of the Adobe Experience Platform Web SDK and Adobe Experience Platform Edge Network.

>[!VIDEO](https://video.tv.adobe.com/v/34141/?quality=12&learn=on)

Now that you understand the high-level differences between at.js and the Platform Web SDK, you can [plan the migration](plan-migration.md).

>[!NOTE]
>
>We are committed to helping you be successful with your Target migration from at.js to Web SDK. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).