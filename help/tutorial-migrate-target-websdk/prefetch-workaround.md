---
title: Workaround for prefetch | Migrate Target from at.js 2.x to Web SDK
description: Learn how to implement a workaround for passing parameters with prefetch
---
# Workaround for prefetch

All Target customers who were not in production with Experience Platform Web SDK before October 1, 2022 make a request to Target from Experience Platform Edge Network using "prefetch" mode. Prefetch allows the browser to preload and cache Target offers so they are ready to be applied when the visitor reaches the correct state of the page. This is advantageous in Single Page Applications (SPAs) since the desired user experience can be rendered as quickly as possible, without additional network requests. There are important implications, though, for both SPA and non-SPA implementations.

Instead of counting a visitor in an activity when the offer content is delivered in the network request, visitors are now counted in activities when a `propositionDisplay` sendEvent request is made by Web SDK. These requests are made automatically by Visual Experience Composer (VEC) activities when renderDecisions is set to true and when the experience has been successfully rendered on the page. With custom scopes and when renderDecisions is set to false, the propositionDisplay requests need to be intentionally initiated by the implementer. Also, _all parameters used for purposes other than immediate activity qualification must be sent through a `propositionDisplay`  event_.

## Why is the workaround needed?

In many Target implementations, important network requests are sometimes made without an expectation of an activity being delivered. For example, requests may be made to:

* Record order conversions
* Set profile parameters
* Trigger profile scripts
* Send entity parameters to populate the Recommendations catalog

Unfortunately, in prefetch mode, these do not behave as expected. In prefetch mode, this data is not ingested unless it is part of a `propositionDisplay`.

## What is the workaround?

The workaround consists of three parts:

1. Define a custom scope as part of your `sendEvent`
1. Use the custom scope in a form-based activity (the activity can serve default content)
1. Use a response handler to make another `sendEvent` for the propositionDisplay and include the parameters you need to capture the order, set the profile parameters, trigger the profile script, send the entity parameters, etcetera.

For example, here is an example of how the workaround could be used to send a profile parameter:


```JavaScript
var data = {
    "__adobe": {
        "target": {
            "profile.gender": "male"
        }
    }
};
// Send the initial event with the data object and custom decision scope
alloy("sendEvent", {
    "renderDecisions": true,
    data,
    decisionScopes: ['profile-param-example']
}).then(function(result) {
    var propositions = result.propositions;
    var ctaProposition;
    if (propositions) {
        // Find the discount proposition, if it exists.
        for (var i = 0; i < propositions.length; i++) {
            var proposition = propositions[i];
            if (proposition.scope === "profile-param-example") {
                ctaProposition = proposition;
                break;
            }
        }
    }
    if (ctaProposition) {
        // Send a "decisioning.propositionDisplay" event signaling that the proposition has been rendered, and includes the data object again
        alloy("sendEvent", {
            xdm: {
                eventType: "decisioning.propositionDisplay",
                _experience: {
                    decisioning: {
                        propositions: [{
                            id: ctaProposition.id,
                            scope: ctaProposition.scope,
                            scopeDetails: ctaProposition.scopeDetails
                        }]
                    }
                }
            },
            data
        });
    }
});
```

When the profile is set as part of the propositionDisplay, it saves to the visitor's profile and be available in subsequent requests. The same approach can be used to report order conversion details and entity parameters.

In tags, use the Send Event Complete event type to trigger an event containing the additional sendEvent.

## How do I know if my implementation uses prefetch mode?

You must open a Customer Care ticket in order to find out if your account is using prefetch mode.


>[!NOTE]
>
>We are committed to helping you be successful with your Target migration from at.js to Web SDK. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).