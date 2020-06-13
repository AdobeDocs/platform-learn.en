---
title: Offer Decisioning
description: Offer Decisioning
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: 
---

# 14. Offer Decisioning

In this module, you will get a hands-on preview of the Adobe Experience Platform Decisioning Service.

The Adobe Experience Platform Offer Decisioning Application Service provides the capability to create personalized, optimized, and orchestrated experiences in applications running on top of Adobe Experience Platform.

Using Decisioning Service, you can determine the best option from a set of available choices. These options, also called alternatives, could be offers, product recommendations, content components for a web experience, conversation scripts, and actions to take. **Currently** the use case and domain of **offer decisioning** is supported and is referred to as the **Offers Decisioning Engine** (**ODE**), where decision options are modeled specifically as offers (with support for more use cases to come).

In this module we will refer to the **Offers Decisioning Engine** (or simply **Offers**) as the first implementation of the **Decisioning Service** within Adobe Experience Platform.

## Learning Objectives

- Understand basic terminology used as part of Offer Decisioning,

- Get a feeling what is currently available with respect to next best offer functionality in Platform.

## Prerequisites

- Access to Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform) 
- Access to Offer Decisioning
- This documentation has been created to facilitate hands-on, technical enablement around Adobe Experience Platform. In order to complete some of the modules, you'll need to change some variables and replace them by your specific **Environment Variables**. Please contact your Adobe contact who will provide you with the required **Environment Variables** of your specific Adobe Experience Platform instance.

>[!IMPORTANT] 
>
>This tutorial was created to facilitate a particular workshop format. It uses specific systems and accounts to which you might not have access. Even without access, we think you can still learn a lot by reading through this very detailed content. If you're a participant in one of the workshops and need your access credentials, please contact your Adobe representative who will provide you with the required information.

## Architecture Overview

Have a look at the below architecture, which highlights the components that will be discussed and used in this module.

![Architecture Overview](../../assets/images/architecturem14.png)

## Terminology

To get a better understanding and before you start doing the exercises, we highly recommend you to read the [overview](https://docs.adobe.com/content/help/en/experience-platform/decisioning/home.html) on how the Offer Decisioning Application Service works in Adobe Experience Platform.

Working with Offers, you have to understand the following concepts:

 Term | Explanation
---------|----------
**Offer** | An offer is a marketing message that may have rules associated with it that specify who is eligible to see the offer. An offer has a status: draft, approved or archived.
**Container** | Everything in the Offers Decisioning Engine happens in the context of a container. In our module, we will work in the **Decisioning** container.
**Placement** | The combination of location (or channel) and context (or component type) in which an offer appears for an end-user. Effectively it is the combination of Text, HTML, Image Link for Email, Mobile, Web, Social, Instant Messaging, and non-Digital.
**Decision Rule** | The logic that defines and controls the eligibility of end-users for an offer.
**Personalized Offer** | A customizable marketing message based on eligibility rules and constraints.
**Fallback Offer** | The default offer displayed when an end-user is not eligible for any of the offers in the collection used.
**Capping** | Used in an offer definition to define how many times an offer can be presented in total and to a specific user.
**Priority** | Level to determine the priority rank from a result set of offers.
**Offer Filter** | Used to filter out a sub-set of offers from the personalized offer list to speed up the offer decisioning process.
**Activity** | A combination of a set of offers, placement and profile the marketer wants the decision engine to provide the best offer for.
**Experience Cloud Library** | A universal and centralized experience for storing, finding, and selecting assets across Adobe Experience Cloud Solutions and Adobe Experience Platform. It is indeed, arguably, the (first visible) incarnation of the content part of Adobe Experience Platform. **Note**: this is a different repository than what is (was previously) known as the Assets Core Service.

## Exercises

_**Exercises for this module are currently being developed**_

[Summary and benefits](./summary.md)

Summary of this module and overview of the benefits.

>[!NOTE]
>
>Thank you for investing your time in learning all there is to know about Adobe Experience Platform. If you have questions, want to share general feedback of have suggestions on future content, please contact Wouter Van Geluwe directly, by sending an email to **vangeluw@adobe.com**.

[Go Back to All Modules](../../overview.md)
