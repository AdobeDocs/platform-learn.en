---
title: Track events | Migrate Target from at.js 2.x to Web SDK
description: Learn how to track Adobe Target conversion events using Experience Platform Web SDK.
---

# Track Target conversion events using Platform Web SDK

Conversion events for Target can be tracked with the Platform Web SDK similar to at.js. Conversion events typically fall into the following categories:

* Automatically tracked events that do not require any configuration
* Purchase conversion events that should be adjusted for a best practice Platform Web SDK implementation
* Non-purchase conversion events that require code updates

>[!WARNING]
>
> Platform Web SDK implementations begun after October 1, 2022 may need to use the [prefetch workaround](prefetch-workaround.md) in order to successfully track some of the events described on this page.

## Goal tracking comparison

The following table compares how at.js and Platform Web SDK track conversion events

| Activity Goal | Target at.js 2.x | Platform Web SDK |
|---|---|---|
| Conversion > Viewed a Page | Tracked automatically. Based on the value of `context.address.url` in the at.js request payload. | Tracked automatically. Based on the value of `xdm.web.webPageDetails.URL` in the `sendEvent` payload |
| Conversion > Viewed an mbox | Tracked with the request for a display mbox location or a notification using `trackEvent()` or `sendNotifications()` with a `type` value of `display`. | Tracked with a Platform Web SDK `sendEvent` call with the `eventType` of `decisioning.propositionDisplay`.  |
| Conversion > Clicked an element | Tracked automatically for VEC-based activities. Appears as an at.js network call with a `notifications` object in the in request payload and a `type` value of `click`. | Tracked automatically for VEC-based activities. Appears as a Platform Web SDK `sendEvent` call with the `eventType` of `decisioning.propositionInteract`. |
| Engagement > Page Views | Tracked automatically | Tracked automatically |
| Engagement > Time on Site | Tracked automatically | Tracked automatically |

<!--
| Revenue > RPV, AOV, or Total Sales | Tracked based on the `orderTotal` parameter values for the specified mbox(es) | Tracked based on the `xdm.commerce.order.priceTotal` values. Its best to use the "any mbox" option in the goal setup. |
| Revenue > Orders | Tracked based on the unique `orderId` parameter values for the specified mbox(es) | Tracked based on the unique values for `xdm.commerce.order.purchaseID`. Its best to use the "any mbox" option in the goal setup. |
| Engagement > Custom Scoring | Tracked with the `mboxPageValue` parameter. Refer to the [dedicated documentation](https://experienceleague.adobe.com/docs/target/using/activities/success-metrics/capture-score.html) for more details. | Tracked with `data.__adobe.target.mboxPageValue` in the `sendEvent` payload |
-->

## Automatically tracked events

The following conversion goals do not require any specific adjustments to your implementation:

* Conversion > Viewed a Page
* Conversion > Clicked an Element
* Engagement > Page Views
* Engagement > Time on Site

>[!NOTE]
>
>The Platform Web SDK allows greater control over the values passed in the request payload. To ensure Target features such as QA URLs and "Viewed a Page" conversion goals work properly, check that the `xdm.web.webPageDetails.URL` value contains the full page URL with the proper character case. 

<!--
## Purchase conversion events

The following conversion goals are based on the order details information passed in the Platform Web SDK `sendEvent` payload:

* Revenue > Revenue per Visit (RPV)
* Revenue > Average Order Value (AOV)
* Revenue > Total Sales
* Revenue > Orders

Target at.js implementations typically use an order confirmation mbox with the `trackEvent()` or `sendNotifications()` functions to pass the order ID, order total, and a list of product IDs purchased. These methods are specific to Target.

The Platform Web SDK is a shared library for all Adobe applications and you may have other applications such as Adobe Analytics to consider. Because of this shared nature, its best send a single order confirmation call using the appropriate commerce XDM field group.

For more information and an example, refer to the tutorial section about [sending purchase parameters to Target](send-parameters.md#purchase-parameters). 
-->

## Custom-tracked events

Target implementations commonly use custom conversion events to track clicks for form-based activities, to signify a conversion in a flow, or to pass parameters without requesting new content.

The table below outlines the at.js approach and the Platform Web SDK equivalent for a few common conversion-tracking use cases.

| Use case | Target at.js 2.x | Platform Web SDK |
|---|---|---|
| Track a click conversion event for an mbox location (scope) | Execute `trackEvent()` or `sendNotifications()` with a `type` value of `click` for a specific mbox location | Execute a `sendEvent` command with an event type of `decisioning.propositionInteract` |
| Track a custom conversion event that may also include additional data, such Target profile parameters | Execute `trackEvent()` or `sendNotifications()` with a `type` value of `display` for a specific mbox location | Execute a `sendEvent` command with an event type of `decisioning.propositionDisplay` |

>[!NOTE]
>
>Although `decisioning.propositionDisplay` is most commonly used for incrementing impressions for specific scopes, it should also be used as a direct replacement for at.js `trackEvent()` usually. The `trackEvent()` function  defaults to a type of `display` if not specified. Check your implementation to ensure you use the correct event type for any custom conversions you may have defined.

Refer to the dedicated at.js documentation for more information on how to use [`trackEvent()`](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/adobe-target-trackevent/) and [`sendNotifications()`](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/adobe-target-sendnotifications-atjs-21/) for tracking Target events.

at.js example using `trackEvent()` to track a click on an mbox location:

```JavaScript
adobe.target.trackEvent({
  "type": "click",
  "mbox": "homepage_hero"
});
```

With a Platform Web SDK implementation, you can track events and user actions by calling the `sendEvent` command, populating the `_experience.decisioning.propositions` XDM field group, and setting the `eventType` to one of two values:

* `decisioning.propositionDisplay`: Signals the rendering of the Target activity.
* `decisioning.propositionInteract`: Signals a user interaction with the activity, like a mouse click.

The `_experience.decisioning.propositions` XDM field group is an array of objects. The properties of each object are derived from the `result.propositions` that gets returned in the `sendEvent` command: `{ id, scope, scopeDetails }`

```JavaScript
alloy("sendEvent", {
  xdm: { ...},
  decisionScopes: ["hero-banner"]
}).then(function (result) {
  var propositions = result.propositions;

  if (propositions) {
    // Find the discount proposition, if it exists.
    for (var i = 0; i < propositions.length; i++) {
      var proposition = propositions[i];
      for (var j = 0; j < proposition.items; j++) {
        var item = proposition.items[j];

        if (item.schema === "https://ns.adobe.com/personalization/measurement") {
          // add metric to the DOM element
          const button = document.getElementById("form-based-click-metric");

          button.addEventListener("click", event => {
            const executedPropositions = [
              {
                id: proposition.id,
                scope: proposition.scope,
                scopeDetails: proposition.scopeDetails
              }
            ];
            // send the click track event
            alloy("sendEvent", {
              "xdm": {
                "eventType": "decisioning.propositionInteract",
                "_experience": {
                  "decisioning": {
                    "propositions": executedPropositions
                  }
                }
              }
            });
          });
        }
      }
    }
  }
});
```

Next, learn how to [enable cross-domain ID sharing](cross-domain.md) for consistent visitor profiles.

>[!NOTE]
>
>We are committed to helping you be successful with your Target migration from at.js to Web SDK. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).