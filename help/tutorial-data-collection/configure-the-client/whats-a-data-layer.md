---
title: What's a data layer?
description: What's a data layer?
exl-id: a53572c1-1295-4ed4-8a3d-aafff3235138
---
# What's a data layer?

When implementing marketing technologies on your site, it's likely you have important pieces of data scattered throughout your UI. For example, a product's name might be in a heading on the page and the price might be lower on the page below the product image. If you want to send that data to Adobe or another vendor, find the HTML elements that contain the data you need, pull the data from those elements, and send them off. But what happens when your engineering team decides to move the product name from the header to a sidebar? Your implementation breaks. Your implementation can no longer find the heading or, worse, it finds the heading and sends irrelevant data to the server.

One major goal of a data layer is to solve this problem. At its simplest, a data layer is a JavaScript object or, an array that contains data about the product on the page. It includes all relevant data your marketing technologies require to meet your goals. By not relying on the user interface elements to provide this data, our implementation becomes more robust. The data layer holds the data and should be considered a contract. This contract is typically between the engineering team, who is placing data into the data layer, and the marketing team, who is retrieving data from the data layer.

If an engineer is about to change the structure of the data layer, they're much more likely to consider working with the marketing team so that appropriate changes can be made to the marketing implementation. This communication and cooperation _must_ be established in your organization to ensure a robust implementation.

## Container vs. content

In the industry, the term "data layer" is thrown around a bit loosely and can often lead to confusion and miscommunication. Consider a box of marbles. There are two parts: the container (the box) and the content (the marbles). Similarly, a data layer is often considered to have two parts: the container (the JavaScript object or array) and the content (the pieces of data like `priceTotal`, `currencyCode`, and `purchaseOrderNumber` ).

As this tutorial refers to the Adobe Client Data Layer, it is referring to the container and not the content. When it refers to XDM, it is referring to the content and not the container. When using the Adobe Client Data Layer, it doesn't matter if the content is XDM or your own data model. The Adobe Client Data Layer doesn't care. It's just a box. But, it _is_ a box with special powers...

## Communicating changes

When using a data layer, you can change the content at any time. That's a nice feature, because data may become available at different times. For example, you may have some data about the user available immediately, but may need to make an asynchronous request to a third party for additional information. This requires special consideration. If you need to send this asynchronous data to Adobe Experience Platform at some point, how do your marketing technologies know when certain pieces of data have been added to the data layer and are ready to be sent? You need a smarter data layer -- an event-driven data layer.

An event-driven data layer is able to communicate that its content has changed so that marketing technologies can react to the change. Used properly, this can help avoid timing issues that often arise with data layers that have no means to communicate when changes occur.

The Adobe Client Data Layer is an event-driven data layer.

[Next: **How to use the Adobe Client Data Layer**](how-to-use-the-adobe-client-data-layer.md)

>[!NOTE]
>
>Thank you for investing your time in learning about Data Collection. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)
