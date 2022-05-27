---
title: Overview
description: Overview
exl-id: 527d8f73-33d0-45a6-b7a4-5e46cdb7c138
---
# Implement Web SDK with JavaScript

Collecting data about events occurring in a user's browser is a fundamental tenet of a marketing strategy. Adobe has provided several tools to help you manage this data. While you could familiarize yourself with each of these tools individually, this tutorial attempts to provide a broader view of what each of these tools do and how they work together to achieve a common goal.

In this tutorial, we discuss a strategy for:

1. Structuring and persisting your data within Adobe Experience Platform,
1. Managing your data in the browser and communicating that certain events have occurred, and 
1. Reacting to such events by sending relevant data to Adobe Experience Platform.

This tutorial uses a JavaScript-only Adobe Experience Platform Web SDK and Adobe Client Data Layer implementation. For a tutorial showcasing how to implement Web SDK with the tags feature, see the [Implement Adobe Experience Cloud with Web SDK tutorial](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/overview.html). You can also mix and match these tools with third-party or in-house tools for ultimate flexibility.

## Example Scenario

During this tutorial, you implement data collection for a simple product page on an e-commerce site:

1. The product page is loaded in the browser. Here you'll track that the user has viewed the product. 
1. The user decides to purchase the product, so they click a button to add the product to their cart. Here, you'll track that the user has opened a new cart and added the product to the cart by sending experience events to Adobe Experience Platform. 
1. Finally, the user clicks a _Download the app_ link because they are interested in your mobile app. You'll track that the user has clicked the link. 

Let's get started!

[Next: **Structuring your data**](structuring-your-data.md)

>[!NOTE]
>
>Thank you for investing your time in learning about Adobe Experience Platform Web SDK. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
