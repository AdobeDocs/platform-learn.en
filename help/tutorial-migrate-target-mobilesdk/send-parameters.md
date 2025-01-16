---
title: Send parameters - Migrate from the Adobe Target to the Adobe Journey Optimizer - Decisioning Mobile extension
description: Learn how to send mbox, profile, and entity parameters to Adobe Target using Experience Platform Web SDK.
exl-id: 927d83f9-c019-4a6b-abef-21054ce0991b
---
# Send parameters to Target using the Adobe Journey Optimizer - Decisioning Mobile extension

Target implementations differ across websites due to site architecture, business requirements, and features used. Most Target implementations include passing various parameters for contextual information, audiences, and content recommendations.  

Let's use a simple product details page and an order confirmation page to demonstrate the differences between the extensions when passing parameters to Target.


| Example at.js parameter | Platform Web SDK option | Notes |
| --- | --- | --- |
| `at_property` | N/A | Property tokens are configured in the [datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#target) and cannot be set in the `sendEvent` call. |
| `pageName` | `xdm.web.webPageDetails.name` | All Target mbox parameters must be passed as part of the `xdm` object and conform to a schema using the XDM ExperienceEvent class. Mbox parameters cannot be passed as part of the `data` object.|
| `profile.gender` | `data.__adobe.target.profile.gender` | All Target profile parameters must be passed as part of the `data` object and prefixed with `profile.` to be mapped appropriately. |
| `user.categoryId` | `data.__adobe.target.user.categoryId` | Reserved parameter used for Target's Category Affinity feature which must be passed as part of the `data` object. |
| `entity.id` | `data.__adobe.target.entity.id` <br>OR<br> `xdm.productListItems[0].SKU` | Entity IDs are used for Target Recommendations behavioral counters. These entity IDs can either be passed as part of the `data` object or automatically mapped from the first item in the `xdm.productListItems` array if your implementation uses that field group.|
| `entity.categoryId` | `data.__adobe.target.entity.categoryId` | Entity category IDs can be passed as part of the `data` object. | 
| `entity.customEntity` | `data.__adobe.target.entity.customEntity` | Custom entity parameters are used for updating the Recommendations product catalog. These custom parameters must be passed as part of the `data` object. | 
| `cartIds` | `data.__adobe.target.cartIds` | Used for Target's cart-based recommendations algorithms. | 
| `excludedIds` | `data.__adobe.target.excludedIds` | Used to prevent specific entity IDs from returning in a recommendations design. | 
| `mbox3rdPartyId` | Set in the `xdm.identityMap` object | Used for synching Target profiles across devices and Customer Attributes. The namespace to use for the customer ID must be specified in the [Target configuration of the datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/using-mbox-3rdpartyid.html). | 
| `orderId` | `xdm.commerce.order.purchaseID` | Used for identifying a unique order for Target conversion tracking. | 
| `orderTotal` | `xdm.commerce.order.priceTotal` | Used for tracking order totals for Target conversion and optimization goals. | 
| `productPurchasedId` | `data.__adobe.target.productPurchasedId` <br>OR<br> `xdm.productListItems[0-n].SKU` | Used for Target conversion tracking and recommendations algorithms. Refer to the [entity parameters](#entity-parameters) section below for details. | 
| `mboxPageValue` | `data.__adobe.target.mboxPageValue` | Used for the [custom scoring](https://experienceleague.adobe.com/docs/target/using/activities/success-metrics/capture-score.html) activity goal. | 

{style="table-layout:auto"}

## Custom parameters

Custom mbox parameters must be passed as XDM or using the data object with the `sendEvent` command. It is important to ensure that the XDM schema includes all fields required for your Target implementation. 


## Profile parameters

Target profile parameters must be passed...

## Entity parameters

Entity parameters are used to pass behavioral data and supplemental catalog information for Target Recommendations. All [entity parameters](https://experienceleague.adobe.com/docs/target/using/recommendations/entities/entity-attributes.html) supported by at.js are also supported by the Platform Web SDK. Similar to profile parameters, all entity parameters should be passed under the `data.__adobe.target` object in the Platform Web SDK `sendEvent` command payload.

Entity parameters for a specific item must be prefixed with `entity.` for proper data capture. The reserved `cartIds` and `excludedIds` parameters for recommendations algorithms should not be prefixed and the value for each must contain a comma-separated list of entity IDs.



## Purchase parameters

Purchase parameters are passed on an order confirmation page after a successful order and are used for Target conversion and optimization goals. With a Platform Mobile SDK implementation using the Decisioning extension, these parameters and are automatically mapped from XDM data passed as part of the `commerce` field group.


Purchase information is passed to Target when the `commerce` field group has `purchases.value` set to `1`. The order ID and order total are automatically mapped from the `order` object. If the `productListItems` array is present, then the `SKU` values are use for `productPurchasedId`.


## Customer Id (mbox3rdPartyId)

Target allows profile synching across devices and systems using a single customer Id.



Next, learn how to [track Target conversion events](track-events.md) with the Platform Web SDK.

>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Decisioning extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
