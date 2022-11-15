---
title: How to use the Adobe Client Data Layer
description: How to use the Adobe Client Data Layer
exl-id: b5af9e72-aa6c-4cd7-80dd-b2de762a7523
---
# How to use the Adobe Client Data Layer

In [What's a data layer?](whats-a-data-layer.md), you learned there are two parts to consider when discussing data layers: the container and the content. The [Adobe Client Data Layer](https://github.com/adobe/adobe-client-data-layer) is the container. It doesn't care how you [structure your data](../structuring-your-data.md) or what pieces of information you choose to put in your data. The data can be structured as [XDM](../structuring-your-data.md#xdm), as the examples below show, or you can build your own structure entirely.

Ideally, your company's engineering team is responsible for pushing any necessary data into the data layer through on-page code. The marketing team then retrieves data from the data layer, preferably using the Tags feature of Adobe Experience Platform, formerly named Launch.

## Pushing data to the data layer

The Adobe Client Data Layer is a JavaScript array. When you create the Adobe Client Data Layer, it starts out empty:

```js
window.adobeDataLayer = window.adobeDataLayer || [];
```

To place data into the data layer, call the `push` method on the data layer array:

```js
window.adobeDataLayer.push({
  "claims": {
    "ID": "CL10991306",
    "policyID": "IXP28113",
    "type": "automobile"
  }
});
```

You can push additional data into the data layer at any time by calling `push` again.

```js
window.adobeDataLayer.push({
  "claims": {
    "status": "approved",
    "benefitAmount": {
      "amount": 1827.90,
      "currencyCode": "USD"
    }
  }
});
```

## Making sense of pushed data

If you implemented the two previous `push` calls, you would end up with two entries in the data layer array. The data layer isn't useful in this state. Typically, you want to access the merged state of the data layer or, in other words, a single object that is the combined result of all the data you've pushed into the data layer. You learn how to access this merged state later in the tutorial. For now, it's sufficient to understand that the computed state of the data layer after our two `push` calls would be as follows:

```json
{
  "claims": {
    "ID": "CL10991306",
    "policyID": "IXP28113",
    "type": "automobile",
    "status": "approved",
    "benefitAmount": {
      "amount": 1827.90,
      "currencyCode": "USD"
    }
  }
}
```

## Removing data

Sometimes, you must remove pieces of data from the data layer. This is common in single-page applications when the user navigates from one view to the next. For example, if the user navigates from a product view to a contact view, it may make sense to clear out any product data on the data layer since it is no longer pertinent to the active view.

You can remove a piece of data by pushing a value of `undefined` for the key you would like removed. Building on our previous examples, if you want to remove `status` from the data layer, your code would look as follows:

```js
window.adobeDataLayer.push({
  "claims": {
    "status": undefined
  }
});
```

The computed state of the data layer would no longer include `status`:

```json
{
  "claims": {
    "ID": "CL10991306",
    "policyID": "IXP28113",
    "type": "automobile",
    "benefitAmount": {
      "amount": 1827.90,
      "currencyCode": "USD"
    }
  }
}
```

## Pushing events to the data layer

The Adobe Client Data Layer is not only used for storing data, but also for communicating which events are occurring on the page. In fact, you typically push data into the data layer _as a result_ of an event occurring on the page. These events include (1) interaction events, like opening a chat bot or typing a search term into a search bar or (2) non-interaction events, like impression of an ad or the completion of web page performance calculations.

To communicate that an event has occurred on the page, include an `event` key in the object you push to the data layer. For example, you may want to communicate that a user has entered a search query into a search field.

```js
window.adobeDataLayer.push({
  "event": "searchQueryEntered"
});
```

<!--Later, you'll learn how to trigger rules within Adobe Experience Platform Tags when a particular event is pushed to the data layer.--> Also note that the `event` key is not included in the computed state. It receives special treatment by the data layer.


## Pushing events and data to the data layer

Notifying listeners that the user has entered a search query is helpful, but what if you would like to provide additional information about the event? For example, maybe you would like to include the user's search query. You can provide this data in one of two ways:

1. Provide data so that it **is retained** in the data layer as part of the data layer's computed state.
1. Provide data so that it **is not retained** in the data layer as part of the data layer's computed state.

Whether you want to retain the data in the data layer usually depends on if you plan to reference that data throughout the duration of the user being on the page. If not, then retaining the data inside the data layer results in a cluttered data layer.

Here is an example of pushing an event with additional data that **is retained** in the data layer:

```js
window.adobeDataLayer.push({
  "event": "searchQueryEntered",
  "siteKnowledge": {
    "supportSiteSearch": {
      "term": "roller",
      "locationInPage": "topSearchBar"
    }
  }
});
```

After this `push` takes place, `siteKnowledge` will always show up in the data layer's computed state until the page is unloaded (unless you purposely remove or override `siteKnowledge`).

In contrast, here is an example of pushing an event with additional data that **is not retained** in the data layer:

```js
window.adobeDataLayer.push({
  "event": "searchQueryEntered",
  "eventInfo": {
    "siteKnowledge": {
      "supportSiteSearch": {
        "term": "roller",
        "locationInPage": "topSearchBar"
      }
    }
  }
});
```

Notice in this example that `siteKnowledge` is wrapped inside `eventInfo`. The `eventInfo` key receives special treatment by the data layer. It tells the data layer that this data _should_ be included with the event that gets sent to listeners, but it _should not_ be retained inside the data layer. After listeners (like a tag manager) are notified of the event, this data is forgotten. The `siteKnowledge` key never shows up inside the data layer's computed state.

Each time you call `push`, the Adobe Client Data Layer notifies any listeners. Later, you learn how to listen to these notifications <!--from Adobe Experience Platform Tags--> and trigger rules accordingly.

[Next: **Implement a data layer on a product page**](implement-product-page-data-layer.md)

>[!NOTE]
>
>Thank you for investing your time in learning about Data Collection. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)
