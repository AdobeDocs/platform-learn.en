---
title: Consider moving vendor tags to Event Forwarding
description: Learn how to evaluate a client-side vendor tag for server-side data distribution.
feature: Event Forwarding, Tags, Integrations
solution: Experience Platform, Data Collection
kt: 9921
level: Intermediate, Experienced
role: Admin, Developer, Architect
---
# Consider moving client-side vendor tags to Event Forwarding

There are several compelling reasons to consider moving client-side vendor tags out of browsers and devices, and onto a server. In this article we'll discuss how to evaluate a client-side vendor tag for potentially moving it to an Event Forwarding property.

This evaluation is really only necessary if you are considering removing a client-side vendor tag and replacing it with server-side data distribution in an Event Forwarding property. This article assumes you are familiar with the basics of [data collection](https://experienceleague.adobe.com/docs/data-collection.html), and [Event Forwarding](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html).

>[!NOTE]
>
>Adobe Experience Platform Launch has been rebranded as a suite of data collection technologies in Adobe Experience Platform. Several terminology changes have rolled out across the product documentation as a result. Please refer to the following [document](https://experienceleague.adobe.com/docs/experience-platform/tags/term-updates.html) for a consolidated reference of the terminology changes.

Browser vendors are changing how they treat 3rd party cookies. Advertising and marketing vendors and technologies often require the use of many client-side tags. These are just two compelling reasons currently motivating our customers to consider server-side data distribution.

>[!NOTE]
>
>`Tag` in this article means client-side code, typically JavaScript from a vendor that's used for data collection in the browser or device while a visitor interacts with the site or app. `Website` or `site` here refers to a website, a web application, or an application for a mobile device. A "tag" for these purposes is also often called a pixel.

## Use cases and data {#use-cases-data}

The first step is to define the use cases we implemented for the client-side vendor tag. For example, if we're considering eliminating the Facebook (Meta) pixel from our site client-side, and moving that data management to the [Facebook Conversions API](https://exchange.adobe.com/apps/ec/105509/facebook-conversions-api-extension) edge extension, we need to know the specific use cases to support.

For the current client-side vendor code:

- Which specific event and other data points are we exposing or passing to the client-side tag?
- When and where does that happen?

It's helpful to make a list, spreadsheet, diagram, or other record of the data and sequence of events to document this evaluation - even if it's only for your own use. Be sure to include labels for data sources - where does it come from? Destinations - where will it go? And transformations - what happens to it between source and destination?

In our example, we're tracking conversions with the Facebook pixel when visitors interact with our site after viewing a Facebook ad or interacting with one of our related ads on another social platform. We want to send data to Facebook so we can see these conversions in their advertising tools and reports. This might include data from conversion events like downloads, registrations, likes, purchases, etc.

### Data {#data}

With our existing client-side tag, when it runs or executes on our site, what happens with the data we need for our use case? Can we capture the data we need in the client, without the vendor tag, so we can send it to Event Forwarding? When using [tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html) or other tag management system, most visitor interaction data is available, but we need to make sure the data we need for our use case is available when we need it, where we need it, and in the format we need it, without the client-side vendor tag running. Some further data questions to consider:

- Is there a vendor user ID required with every event?
- If so, how can we obtain or generate it without the client-side tag?
- Does the vendor specifically require their client-side code at runtime?
- What other data is required? Where will we get it?

Most client-side vendor tags don't require a large number of data points for any particular use case, but it's helpful to note the use cases and required data during these evaluations.

## Vendor APIs {#vendor-apis}

Now that we know the specific use cases to implement, the specific data required for those cases, and the sequence of events from source to destination, we can investigate the vendor API details to determine if they're a good fit for Event Forwarding.

>[!IMPORTANT]
>
>While many vendors are enabling APIs for server-to-server transfer, there are also many that do not currently have APIs fit for these purposes.

### Investigating APIs {#investigate-apis}

Here are some steps we can take to investigate vendor API endpoints.

Does the vendor have APIs designed for server-to-server transfer of event data?

- Do the API endpoints exist to send the required data? Look at the vendor's developer or API documentation to find the endpoints that support your use cases.
- Find the requirements for those specific API endpoints:
  - Do they allow streaming event data, or only batch data?
  - Which authentication methods do they support? Token, HTTP, OAuth client credentials version, or other? See [here](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/secrets.html) for methods supported by Event Forwarding.
  - What is the refresh offset of their API? Is that compatible with the Event Forwarding minimums? Details [here](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/secrets.html#:~:text=you%20can%20configure%20the%20Refresh%20Offset%20value%20for%20the%20secret).
  - What data do they require for the relevant endpoints?
  - Do they require a vendor-specific user identifier with every call to the endpoint?
  - If so, how can that be generated or obtained?
  - Would that require client-side vendor tags?

If the vendor provides the API endpoints required for our use cases, and they have a compatible authentication method, and we have access to all the data required for the Event Forwarding implementation (either from the client-side, or from other API calls), then the tag is likely a good candidate to move from the client to our servers in an Event Forwarding property with the goal of removing the client-side tag.

If the vendor doesn't have the API endpoints to support our use cases, then obviously that vendor tag is not a good candidate for using Event Forwarding in place of any client-side vendor tag.

What if they have APIs, but also require some unique visitor or user ID with every API call? How can we access that ID if we don't have the vendor client-side code (tag) running on our site?

Some vendors are changing their systems for the new world without 3rd party cookies. This includes allowing alternative unique identifiers, like a [UUID](https://developer.mozilla.org/en-US/docs/Glossary/UUID) or other customer-generated ID (CRM ID, hashed email address, etc.). If the vendor we're investigating allows a customer-generated ID, and we can either send it to Experience Edge with a Send Event from our Web or Mobile SDKs, or we can obtain it from an API call, then we likely don't have any issues related to visitor/user IDs. When we send data to that vendor in an Event Forwarding Rule, we simply include that identifier as-needed.

If the vendor requires data (like a vendor-specific unique ID, for example) that can only be generated or accessed by their own client-side tag, then that vendor is likely not a good candidate to move into an Event Forwarding property. _Attempting to reverse-engineer a client-side tag with the idea of moving that data collection to Event Forwarding without the appropriate APIs is strongly discouraged._

The [Adobe Experience Platform Cloud Connector](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/cloud-connector/overview.html) extension can make HTTP requests as-needed with vendors who have the appropriate APIs for server-to-server event data transfer. While vendor-specific extensions are nice to have, and more extensions are under active development right now, we can implement Event Forwarding rules today using the Cloud Connector extension, without needing to wait for additional vendor extensions.

## Tools {#tools}

Investigating and testing vendor API endpoints can be done with [Postman](https://www.postman.com/), or for quick requests, several IDEs or text editors like Visual Studio Code offer helpful extensions like [Thunder Client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client), or [HTTP Client](https://marketplace.visualstudio.com/items?itemName=mkloubert.vscode-http-client).

## Next steps {#next-steps}

This article provided a sequence of steps we can take to evaluate a vendor client-side tag and potentially moving it server-side in an Event Forwarding property. For more information on related topic, see these links:

- [Tag management](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html) in Adobe Experience Platform
- [Event forwarding](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html) for server-side processing
- [Terminology updates](https://experienceleague.adobe.com/docs/experience-platform/tags/term-updates.html)