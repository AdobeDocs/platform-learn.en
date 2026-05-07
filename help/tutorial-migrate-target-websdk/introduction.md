---
title: Migrate Target from at.js 2.x to Web SDK
description: Learn how to migrate an Adobe Target implementation from at.js 2.x to Adobe Experience Platform Web SDK. Topics include loading the JavaScript library, sending parameters, rendering activities, and other noteworthy callouts.
last-substantial-update: 2023-02-23
exl-id: c8920fde-ad6b-4f2d-a35f-ce865b35bba0
---
# Migrate Target from at.js 2.x to Platform Web SDK

This guide is for experienced Adobe Target implementers to learn how to migrate an at.js implementation to Adobe Experience Platform Web SDK. 

Adobe Experience Platform Web SDK is a client-side JavaScript library that allows Adobe Experience Cloud customers to interact with Experience Cloud services through the Adobe Experience Platform Edge Network. This new library combines the capabilities of the separate Adobe application libraries into a single lightweight package that can take full advantage of new Adobe Experience Platform features.


>[!NOTE]
>
>Similar migration tutorials are available for:
>
> * [Adobe Analytics](../tutorial-migrate-analytics-websdk/migration-to-websdk-overview.md)
> * [Adobe Audience Manager](https://experienceleague.adobe.com/en/docs/audience-manager/user-guide/migrate-to-web-sdk/appmeasurement-to-web-sdk)

>[!CAUTION]
>
> Because Platform Web SDK supports multiple Adobe applications, all Adobe libraries on a given page should be migrated at the same time. For example, a mixed implementation of Web SDK for Target and AppMeasurement for Analytics on a single page _is not supported_. However, a mixed implementation across different pages is supported, for example Web SDK on page A, and at.js with AppMeasurement on page B.



## Key benefits

Some of the benefits of the Platform Web SDK compared to the standalone at.js library include:

* Faster sharing of audiences from [Real-Time Customer Data Platform](https://experienceleague.adobe.com/en/docs/platform-learn/tutorials/destinations/target/next-hit-personalization)
* Integrating Target with Journey Optimizer to support [Offer Decisioning delivery](https://experienceleague.adobe.com/en/docs/target/using/integrate/ajo/offer-decision)
* Ability to use [first-party ids](https://experienceleague.adobe.com/en/docs/platform-learn/data-collection/edge-network/generate-first-party-device-ids) to generate the ECID for longer duration visitor identification
* A smaller footprint for improved page speed metrics
* Additional implementation flexibility for developers

Arguably, the largest benefit to Target customers of migrating is for integration with Real-Time Customer Data Platform. Real-Time CDP offers tremendous audience-building capabilities based on the full range of data ingested into Experience Platform and its Real-time Customer Profile capability. A built-in data governance framework, automates responsible use of that data. Customer AI allows you to easily use machine learning models to construct propensity and churn models whose output can be shared back to Adobe Target. And finally, customers of the optional Healthcare and Privacy & Security Shield addons can use the consent enforcement feature to easily enforce individual customers' consent preferences. Platform Web SDK is a requirement to use these Real-Time CDP features in your web channel.

## Learning objectives

At the end of this tutorial, you will be able to:

* Understand the Target implementation differences between at.js and Platform Web SDK
* Set up the initial configuration for Target functionality
* Upgrade the at.js library to Platform Web SDK
* Render form-based and visual experience composer activities
* Pass parameters to Target
* Track conversion events
* Enable cross-domain support
* Update audiences and profile scripts
* Validate the implementation
* Debug Target experience delivery 


## Prerequisites

To complete this tutorial, you should first:

* Have a technical understanding of your current Target at.js implementation
* Ensure you have an [Editor or Publisher role](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/properties-overview.html#section_8C425E43E5DD4111BBFC734A2B7ABC80) for your Target instance so you can attempt examples on your own
* Know how to set up activities in Adobe Target. If you need a refresher, the following tutorials and guides are helpful for this lesson:
    * [Use the Visual Experience Composer](https://experienceleague.adobe.com/docs/target-learn/tutorials/experiences/use-the-visual-experience-composer.html)
    * [Use the Form-Based Experience Composer](https://experienceleague.adobe.com/docs/target-learn/tutorials/experiences/use-the-form-based-experience-composer.html)
    * [Create Experience Targeting Activities](https://experienceleague.adobe.com/docs/target-learn/tutorials/activities/create-experience-targeting-activities.html)

Once you are ready, the first step to a successful migration is to [learn about the migration process](migration-overview.md) and how at.js and Platform Web SDK differ.

>[!NOTE]
>
>We are committed to helping you be successful with your Target migration from at.js to Web SDK. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
