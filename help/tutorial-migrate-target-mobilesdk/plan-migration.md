---
title: Planning - Migrate from the Adobe Target to the Adobe Journey Optimizer - Decisioning Mobile extension
description: Learn how to plan for your Adobe Target implementation from at.js 2.x to Adobe Experience Platform Web SDK.
exl-id: 50eefe2d-ba20-45d5-8674-c4f5d035a9eb
---
# Plan the Target migration to the Decisioning extension

Before upgrading Target from the Target extension to the Decisioning extension in your mobile app, you should assess your current implementation.

## Assess current Target extension implementation

The first step to a successful migration is to have a firm understanding of your current Target extension implementation. There are features, functions, and custom code you may use that require updates. Consider the following as you assess:

### What features are supported?

<!--Platform Web SDK is under continuous active development and features and enhancements are added regularly. As you evaluate your current at.js implementation, refer to the [supported use cases](https://github.com/orgs/adobe/projects/18/views/1) page for the latest information.-->

### What functions do you use today?

<!--Platform Web SDK is a new library that consolidates all Adobe solutions for the websites into a single SDK. This enables tighter integration and enables new capabilities unique to Adobe Experience Platform. However, this also means at.js functions are not backwards compatible with Platform Web SDK. As you evaluate your current implementation, make note of the following:

- at.js functions such as `getOffer()` and `applyOffer()`
- Modifications to Target's global settings
- Integration with Adobe Analytics
- Use of a flicker mitigation script
- Use of response tokens
- Use of mbox, profile, and entity parameters
- Custom code unique to your implementation-->

### Which migration approach will you take?

<!--Once you have revisited your at.js implementation, you need to determine a migration approach. There are two options:

- Migrate all Adobe applications at once across the entire site
- Migrate on a page-by-page basis

Because Platform Web SDK combines and enables multiple Adobe applications, you must coordinate the Target migration of other Adobe applications like Analytics and Audience Manager. All Adobe libraries on a given page should be migrated at the same time. A mixed implementation of Platform Web SDK for Target and AppMeasurement for Analytics on a particular page is not supported. However, a mixed implementation across different pages is supported, for example Platform Web SDK on page A, and at.js with AppMeasurement on page B.

As you migrate, you should plan on following your company's process for testing and releasing new code and use things like development, qa, and staging environments before you release to production.-->

<!--
>[!CAUTION]
>
>Redirect offers are not supported in page-by-page migrations if redirecting from a page with one library to a page with a different library
-->


Next, review the detailed [comparison of the Target extension and the Decisioning extension](detailed-comparison.md) to gain a better understanding of the technical differences and identify areas requiring additional focus. 

>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Decisioning extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
