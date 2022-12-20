---
title: Implement Adobe Experience Cloud with Web SDK tutorial
description: Learn how to implement Experience Cloud applications using Adobe Experience Platform Web SDK.
recommendations: catalog, noDisplay
exl-id: cf0ff74b-e81e-4f6d-ab7d-6c70e9b52d78
---
# Implement Adobe Experience Cloud with Web SDK tutorial

Learn how to implement Experience Cloud applications using Adobe Experience Platform Web SDK.

Experience Platform Web SDK is a client-side JavaScript library that allows customers of Adobe Experience Cloud to interact with both Adobe applications and third-party services through the Adobe Experience Platform Edge Network. See [Adobe Experience Platform Web SDK Overview](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) for more detailed information.

This tutorial guides you through the implementation of the Platform Web SDK on a sample retail website called Luma. The [Luma site](https://luma.enablementadobe.com/content/luma/us/en.html) has a rich data layer and functionality that lets you build a realistic implementation. After completing this tutorial, you should be ready to start implementing all of your marketing solutions through Platform Web SDK on your own website.

[![Luma website](assets/old-overview-luma.png)](https://luma.enablementadobe.com/content/luma/us/en.html)


## Learning objectives

After completing the tutorial, you will be able to:

* Configure datastreams

* Create XDM schemas

* Add the following Adobe Experience Cloud applications:
  * **[Adobe Experience Platform](setup-experience-platform.md)** (and applications built on Platform such as Adobe Real-Time Customer Data Platform, Adobe Journey Optimizer, and Adobe Customer Journey Analytics)
  * **[Adobe Analytics](setup-analytics.md)**
  * **[Adobe Audience Manager](setup-audience-manager.md)**
  * **[Adobe Target](setup-target.md)**

* Create tag rules and XDM object data elements to send data to Adobe applications 

* Validate the implementation using the Adobe Experience Platform Debugger

* Capture user consent

* Forward data to third-parties with event forwarding

>[!NOTE]
>
>A similar multi-solution tutorial is available for [Mobile SDK](../tutorial-mobile-sdk/overview.md).

## Prerequisites

All Experience Cloud customers can use Platform Web SDK. It is not a requirement to license a Platform-based application like Real-Time Customer Data Platform or Journey Optimizer to use Web SDK.

In these lessons, it is assumed that you have an Adobe account and the [required permissions](configure-permissions.md) to complete the lessons. If not, you must reach out to your Experience Cloud Administrator to request access.

Also, it is assumed that you are familiar with front-end development languages like HTML and JavaScript. You do not need to be an expert in these languages, but you get more out of this tutorial if you can read and understand code.

Let's get started!

[Next: **Configure permissions**](configure-permissions.md)

>[!NOTE]
>
>Thank you for investing your time in learning about Adobe Experience Platform Web SDK. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
