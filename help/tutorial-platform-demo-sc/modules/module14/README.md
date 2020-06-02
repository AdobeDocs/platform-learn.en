# Module 14: Offer Decisioning

**In Module 14**, you will get a hands-on preview of the Adobe Experience Platform -  Decisioning Service.

The Adobe Experience Platform - Offer Decisioning Application Service provides the capability to create personalized, optimized, and orchestrated experiences in applications running on top of Adobe Experience Platform.

Using Decisioning Service, you can determine the best option from a set of available choices. These options, also called alternatives, could be offers, product recommendations, content components for a web experience, conversation scripts, and actions to take. **Currently** the use case and domain of **offer decisioning** is supported and is referred to as the **Offers Decisioning Engine** (**ODE**), where decision options are modeled specifically as offers (with support for more use cases to come). 

In this module we will refer to the **Offers Decisioning Engine** (or simply **Offers**) as the first implementation of the **Decisioning Serice** within Adobe Experience Platform.

## Key Takeaways

- Understand basic terminology used as part of Offer Decisioning,

- Get a feeling what is currently available with respect to next best offer functionality in AEP.

## Terminology

To get a better understanding and before you start doing the exercises, we highly recommend you to read the [overview](https://www.adobe.io/apis/experienceplatform/home/services/decisioning-service.html#!api-specification/markdown/narrative/technical_overview/decisioning-overview/decisioning-service-overview.md) on how the Decisioning Service works in Adobe Experience Platform.

Working with Offers, you have to understand the following concepts:

 Term | Explanation
---------|----------
 **Offer** | An offer is a marketing message that may have rules associated with it that specify who is eligible to see the offer. An offer does have a status: draft, approved or archived.
 **Container** | Everything you work with in the Offers Decisioning Engine, happens in the context of a container. In our module, we will work in the **Decisioning** container.
 **Placement** | Is the combination of location (or channel) and context (or component type) in which an offer appears for an end-user. Effectively it is the combination of Text, HTML, Image Link for Email, Mobile, Web, Social, Instant Messaging, and Non Digital.
 **Decision Rule** | The logic that defines and controls the eligibility of end-users for an offer.
**Personalised Offer** | A customizable marketing message based on eligibility rules and constraints.
**Fallback Offer** | The default offer displayed when an end-user is not eligible for any of the offers in the collection used.
**Capping** | Used in an offer definition to define how many times an offer can be presented in total and to a specific user.
**Priority** | Level to determine the priority rank from a result set of offers.
**Offer Filter** | Used to filter out a sub-set of offers from the personalized offer list to speed up the offer decisioning process..
**Activity** | A combination of a set of offers, placement and profile the marketer wants the decision engine to provide the best offer for.
**Experience Cloud Library** | A universal and centralized experience for storing, finding, and selecting assets across Adobe Experience Cloud Solutions and Adobe Experience Platform. It is indeed, arguably, the (first visible) incarnation of the content part of Adobe Experience Platform. **Note**: this is a different repository than what is (was previously) known as the Assets Core Service.

## Your Environment Variables

This documentation has been created to be reused across multiple Adobe Experience Platform instances for enablement purposes.
In order to complete some of the modules, you'll need to change some variables and replace them by your specific ``Environment Variables``.

You can view these variables [here](../../environment.md).

## Content

### Content for this module is currently being developed.

---

[Go Back to All Modules](../../README.md)
