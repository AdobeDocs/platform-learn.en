---
title: Send parameters - Migrate from the Adobe Target to the Adobe Journey Optimizer - Decisioning Mobile extension
description: Learn how to send mbox, profile, and entity parameters to Adobe Target using Experience Platform Web SDK.
exl-id: 927d83f9-c019-4a6b-abef-21054ce0991b
---
# Send parameters to Target using the Adobe Journey Optimizer - Decisioning Mobile extension

Target implementations differ across websites due to site architecture, business requirements, and features used. Most Target implementations include passing various parameters for contextual information, audiences, and content recommendations.

With the Target extension, all Target paramters were passed using the `TargetParameters` function.

With the Decisioning extension:

* Parameters intended for multiple Adobe applications can be passed in the XDM object 
* Parameters intended only for Target can be passed in the `data.__adobe.target` object


>[!IMPORTANT]
>
> With the Decsioning extension, parameters sent in a request apply to all scopes in the request. If you need to set different parameters for different scopes you must make additional requests.

## Custom parameters

Custom mbox parameters are the most basic way to pass data to Target and can be be passed in the `xdm` or `data.__adobe.target` objects. 

## Profile parameters

Profile parameters store data for an extended period of time in the user's Target profile and must be passed in the `data.__adobe.target` object.

## Entity parameters

[Entity parameters](https://experienceleague.adobe.com/docs/target/using/recommendations/entities/entity-attributes.html) are used to pass behavioral data and supplemental catalog information for Target Recommendations. Similar to profile parameters, most entity parameters should be passed under the `data.__adobe.target` object. The only exception is the `xdm.productListItems` array is present, then the first `SKU` value is used as the `entity.id`.

Entity parameters for a specific item must be prefixed with `entity.` for proper data capture. The reserved `cartIds` and `excludedIds` parameters for recommendations algorithms should not be prefixed and the value for each must contain a comma-separated list of entity IDs.

## Purchase parameters

Purchase parameters are passed on an order confirmation page after a successful order and are used for Target conversion and optimization goals. With a Platform Mobile SDK implementation using the Decisioning extension, these parameters and are automatically mapped from XDM data passed as part of the `commerce` field group.

Purchase information is passed to Target when the `commerce` field group has `purchases.value` set to `1`. The order ID and order total are automatically mapped from the `order` object. If the `productListItems` array is present, then the `SKU` values are use for `productPurchasedId`.

If you are not passing `commerce` fields in the `xdm` object, you can pass the order details to target using the `data.__adobe.target.orderId`, `data.__adobe.target.orderTotal`, and `data.__adobe.target.productPurchasedId` fields.

## Customer Id (mbox3rdPartyId)

Target allows profile synching across devices and systems using a single customer id. This customer id should be passed in the `identityMap` field of the XDM object and mapped to the Target Third Party Id field in the datastream.

## Table

| Example at.js parameter | Platform Web SDK option | Notes |
| --- | --- | --- |
| `at_property` | N/A | Property tokens are configured in the [datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#target) and cannot be set in the `sendEvent` call. |
| `pageName` | `xdm.web.webPageDetails.name` or <br> `data.__adobe.target.pageName`| Target mbox parameters can be passed as either part of the `xdm` object or part of the `data.__adobe.target` object.|
| `profile.gender` | `data.__adobe.target.profile.gender` | All Target profile parameters must be passed as part of the `data` object and prefixed with `profile.` to be mapped appropriately. |
| `user.categoryId` | `data.__adobe.target.user.categoryId` | Reserved parameter used for Target's Category Affinity feature which must be passed as part of the `data` object. |
| `entity.id` | `data.__adobe.target.entity.id` <br>OR<br> `xdm.productListItems[0].SKU` | Entity IDs are used for Target Recommendations behavioral counters. These entity IDs can either be passed as part of the `data` object or automatically mapped from the first item in the `xdm.productListItems` array if your implementation uses that field group.|
| `entity.categoryId` | `data.__adobe.target.entity.categoryId` | Entity category IDs can be passed as part of the `data` object. | 
| `entity.customEntity` | `data.__adobe.target.entity.customEntity` | Custom entity parameters are used for updating the Recommendations product catalog. These custom parameters must be passed as part of the `data` object. | 
| `cartIds` | `data.__adobe.target.cartIds` | Used for Target's cart-based recommendations algorithms. | 
| `excludedIds` | `data.__adobe.target.excludedIds` | Used to prevent specific entity IDs from returning in a recommendations design. | 
| `mbox3rdPartyId` | Set in the `xdm.identityMap` object | Used for synching Target profiles across devices and Customer Attributes. The namespace to use for the customer ID must be specified in the [Target configuration of the datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/using-mbox-3rdpartyid.html). | 
| `orderId` | `xdm.commerce.order.purchaseID`<br> (when `commerce.purchases.value` is set to `1`)<br> or<br> `data.__adobe.target.orderId`| Used for identifying a unique order for Target conversion tracking. | 
| `orderTotal` | `xdm.commerce.order.priceTotal`<br> (when `commerce.purchases.value` is set to `1`)<br> or<br> `data.__adobe.target.orderTotal` | Used for tracking order totals for Target conversion and optimization goals. | 
| `productPurchasedId` | `xdm.productListItems[0-n].SKU`<br> (when `commerce.purchases.value` is set to `1`) <br>OR<br> `data.__adobe.target.productPurchasedId` | Used for Target conversion tracking and recommendations algorithms. | 
| `mboxPageValue` | `data.__adobe.target.mboxPageValue` | Used for the [custom scoring](https://experienceleague.adobe.com/docs/target/using/activities/success-metrics/capture-score.html) activity goal. | 

{style="table-layout:auto"}


## Examples of passing parameters

Let's use a simple example to demonstrate the differences between the extensions when passing parameters to Target.

### Android

>[!BEGINTABS]

>[!TAB Optimize SDK] 

```Java

final Map<String, Object> data = new HashMap<>();
final Map<String, String> targetParameters = new HashMap<>();
 
// Mbox parameters
targetParameters.put("status", "platinum");
 
// Profile parameters - prefix with profile.
targetParameters.put("profile.gender", "male");
 
// Product parameters
targetParameters.put("productId", "pId1");
targetParameters.put("categoryId", "cId1");
 
// Order parameters
targetParameters.put("orderId", "id1");
targetParameters.put("orderTotal", "1.0");
targetParameters.put("purchasedProductIds", "ppId1");
 
data.put("__adobe", new HashMap<String, Object>() {
  {
    put("target", targetParameters);
  }
});
 
// Target location (or mbox)
final DecisionScope decisionScope = DecisionScope("myTargetLocation")
 
final List<DecisionScope> decisionScopes = new ArrayList<>();
decisionScopes.add(decisionScope);
 
Optimize.updatePropositions(decisionScopes, null, data);

```

>[!TAB Target SDK] 

```Java

Map<String, String> mboxParameters = new HashMap<String, String>();
mboxParameters1.put("status", "platinum");
 
Map<String, String> profileParameters = new HashMap<String, String>();
profileParameters1.put("gender", "male");
 
List<String> purchasedProductIds = new ArrayList<String>();
purchasedProductIds.add("ppId1");
TargetOrder targetOrder = new TargetOrder("id1", 1.0, purchasedProductIds);
 
TargetProduct targetProduct = new TargetProduct("pId1", "cId1");
 
TargetParameters targetParameters = new TargetParameters.Builder()
                                    .parameters(mboxParameters)
                                    .profileParameters(profileParameters)
                                    .product(targetProduct)
                                    .order(targetOrder)
                                    .build();
```

>[!ENDTABS]

### iOS

>[!BEGINTABS]

>[!TAB Optimize SDK] 

```Swift

var data: [String: Any] = [:]
var targetParameters: [String: String] = [:]
 
// Mbox parameters
targetParameters["status"] = "platinum"
 
// Profile parameters - prefix with profile.
targetParameters["profile.gender"] = "make"
 
// Product parameters
targetParameters["productId"] = "pId1"
targetParameters["categoryId"] = "cId1"
 
// Add order parameters
targetParameters["orderId"] = "id1"
targetParameters["orderTotal"] = "1.0"
targetParameters["purchasedProductIds"] = "ppId1"
 
data["__adobe"] = [
  "target": targetParameters
]
 
// Target location (or mbox)
let decisionScope = DecisionScope(name: "myTargetLocation")
Optimize.updatePropositions(for: [decisionScope] withXdm: nil andData: data)
```

>[!TAB Target SDK] 

```Swift

let mboxParameters = [
                        "status": "platinum"
                     ]
 
let profileParameters = [
                            "gender": "male"
                        ]
 
let order = TargetOrder(id: "id1", total: 1.0, purchasedProductIds: ["ppId1"])
 
let product = TargetProduct(productId: "pId1", categoryId: "cId1")
 
let targetParameters = TargetParameters(parameters: mboxParameters, profileParameters: profileParameters, order: order, product: product))

```


>[!ENDTABS]






Next, learn how to [track Target conversion events](track-events.md) with the Platform Web SDK.

>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Decisioning extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
