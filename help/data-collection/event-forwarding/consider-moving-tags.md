---
title: Consider moving vendor tags to event forwarding
description: Learn how to evaluate a client-side vendor tag for server-side data distribution.
feature: Event Forwarding, Tags, Integrations
solution: Data Collection, Experience Platform
kt: 9921
level: Intermediate, Experienced
role: Admin, Developer, Architect
exl-id: f8fd351a-435c-4cc1-b987-ed2ead20d4d6
---
# Consider moving client-side vendor tags to event forwarding

There are several compelling reasons to consider moving client-side vendor tags out of browsers and devices, and onto a server. In this article, we discuss how to evaluate a client-side vendor tag for potentially moving it to an event forwarding property.

This evaluation is only necessary if you are considering removing a client-side vendor tag and replacing it with server-side data distribution in an event forwarding property. This article assumes you are familiar with the basics of [data collection](https://experienceleague.adobe.com/docs/data-collection.html), and [event forwarding](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html).

>[!NOTE]
>
>Adobe Experience Platform Launch has been rebranded as a suite of data collection technologies in Adobe Experience Platform. Several terminology changes have rolled out across the product documentation as a result. Please refer to the following [document](https://experienceleague.adobe.com/docs/experience-platform/tags/term-updates.html) for a consolidated reference of the terminology changes.

Browser vendors are changing how they treat third party cookies. Advertising and marketing vendors and technologies often require the use of many client-side tags. These challenges are just two compelling reasons that our customers are adding server-side data distribution.

>[!NOTE]
>
>`Tag` in this article means client-side code, typically JavaScript from a vendor that's used for data collection in the browser or device while a visitor interacts with the site or app. `Website` or `site` here refers to a website, a web application, or an application for a mobile device. A "tag" for these purposes is also often called a pixel.

## Use cases and data {#use-cases-data}

The first step is to define the use cases implemented with the client-side vendor tag. For example, consider the Facebook (Meta) pixel. Moving it from our site to the [Facebook Conversions API](https://exchange.adobe.com/apps/ec/105509/facebook-conversions-api-extension) with the event forwarding extension means documenting the specific use cases first.

For the current client-side vendor code:

- Which specific event and other data points are exposed and passed to the client-side tag?
- When and where does that data transfer happen?

It's helpful to make a list, spreadsheet, diagram, or other record of the data and sequence of events to document this evaluation - even if it's only for your own use. Be sure to include labels for data sources&mdash;where does it come from? Destinations&mdash;where does it go? And transformations&mdash;what happens to it between source and destination?

In our example, we're tracking conversions with the Facebook pixel when visitors interact with our site after viewing a Facebook ad. They could also interact with our site after viewing related ads on another social platform. To see these conversions in the Facebook advertising tools and reports, the required data must get to Facebook. This data might include conversion events like downloads, registrations, likes, or purchases.

### Data {#data}

With the existing client-side tag, when it runs or executes on our site, what happens with the data for our use case? Can we capture the data we need in the client, without the vendor tag, so we can send it to event forwarding? When using [tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html) or other tag management systems, most visitor interaction data is available for collection and distribution. But is the data that we need for our use case available when we need it, where we need it, and in the format we need it&mdash;without the client-side vendor tag? Here are some further data questions to consider:

- Is there a vendor user ID required with every event?
- If so, how can it be collected or generated without the client-side tag?
- Does the vendor specifically require their client-side code at runtime?
- What other data is required? Where will that data come from?

Most client-side vendor tags don't require many data points for any particular use case, but it's helpful to note the use cases and required data during these evaluations.

## Vendor APIs {#vendor-apis}

Now we know the specific use cases to implement, the data required, and the sequence of events from source to destination. To determine if the use case is a good fit for event forwarding, we can now investigate the vendor API details.

>[!IMPORTANT]
>
>While many vendors are enabling APIs for server-to-server transfer, there are also many that do not currently have APIs fit for these purposes.

### Investigating APIs {#investigate-apis}

Here are some steps that we can take to investigate vendor API endpoints.

Does the vendor have APIs designed for server-to-server transfer of event data? First, find the requirements for those specific API endpoints:

- Do the API endpoints exist to send the required data? To find the endpoints that support your use cases, look at the vendor's developer or API documentation.
- Do they allow streaming event data, or only batch data?
- Which authentication methods do they support? Token, HTTP, OAuth client credentials version, or other? See [here](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/secrets.html) for methods supported by event forwarding.
- What is the refresh offset of their API? Is that limitation compatible with the event forwarding minimums? Details [here](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/secrets.html#:~:text=you%20can%20configure%20the%20Refresh%20Offset%20value%20for%20the%20secret).
- What data do they require for the relevant endpoints?
- Do they require a vendor-specific user identifier with every call to the endpoint?
- If they require that identifier, where and how can it be generated or captured, without client-side code?

In other words:

- Does the vendor provide the API endpoints required for our use cases?
- Do they have a compatible authentication method for event forwarding?
- Can we access all the data required for an event forwarding implementation (either from the client-side, or from other API calls)?

The tag is likely a good candidate to move from the client to our servers in an event forwarding property if we can answer yes to those questions.

If the vendor doesn't have the API endpoints to support our use cases, then obviously that vendor tag is not a good candidate for using event forwarding in place of the client-side vendor tag.

What if they have APIs, but also require some unique visitor or user ID with every API call? How can we access that ID if we don't have the vendor client-side code (tag) running on the site?

Some vendors are changing their systems for the new world without third party cookies. These changes include the use of alternative unique identifiers, like a [UUID](https://developer.mozilla.org/en-US/docs/Glossary/UUID) or other [customer-generated ID](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/first-party-device-ids.html). If the vendor allows a customer-generated ID, we can either send it from the client to Platform Edge Network with Web or Mobile SDK, or possibly get it from an API call in event forwarding. When we send data to that vendor in an event forwarding rule, we simply include that identifier as-needed.

If the vendor requires data (like a vendor-specific unique ID, for example) that can only be generated or accessed by their own client-side tag, then that vendor tag is likely not a good candidate to move. _Attempting to reverse-engineer a client-side tag with the idea of moving that data collection to event forwarding without the appropriate APIs is discouraged._

The [Adobe Experience Platform Cloud Connector](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/cloud-connector/overview.html) extension can make HTTP requests as-needed with vendors who have the appropriate APIs for server-to-server event data transfer. While vendor-specific extensions are nice to have, and more extensions are under active development right now, we can implement event forwarding rules today using the Cloud Connector extension, without waiting for additional vendor extensions.

## Tools {#tools}

Investigating and testing vendor API endpoints is easier with tools like [Postman](https://www.postman.com/), or text editor extensions like Visual Studio Code [Thunder Client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client), or [HTTP Client](https://marketplace.visualstudio.com/items?itemName=mkloubert.vscode-http-client).

## Next steps {#next-steps}

This article provided a sequence of steps to evaluate a vendor client-side tag and potentially move it server-side in an event forwarding property. For more information on related topics, see these links:

- [Tag management](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html) in Adobe Experience Platform
- [Event forwarding](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html) for server-side processing
- [Terminology updates](https://experienceleague.adobe.com/docs/experience-platform/tags/term-updates.html) in data collection
