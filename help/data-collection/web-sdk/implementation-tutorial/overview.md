---
title: 
description: 
role: Developer
level: Intermediate
recommendations: noDisplay,noCatalog
kt: 10447
hide: yes
hidefromtoc: yes
---
# Overview

Collecting data about events occurring in a user's browser is a fundamental tenet of a marketing strategy. Adobe has provided several tools to help you manage this data. While you could familiarize yourself with each of these tools individually, this tutorial attempts to provide a broader view of what each of these tools do and how they work together to achieve a common goal.

In this tutorial, we'll discuss a strategy for (1) structuring and persisting your data within Adobe Experience Platform, (2) managing your data in the browser and communicating that certain events have occurred, and (3) reacting to such events by sending relevant data to Adobe Experience Platform.

While this tutorial uses the Adobe Client Data Layer, Adobe Experience Platform Web SDK, and Adobe Experience Platform Tags for a more prescriptive, seamless implementation, you can also mix and match these tools with third-party or in-house tools for ultimate flexibility.

## Example Scenario

For this tutorial, we'll assume you're implementing data collection for a simple product page on an ecommerce site. The product page will be loaded in the browser. Here, you'll track that the user has viewed the product. The user decides to purchase the product, so they click a button to add the product to their cart. Here, you'll track that the user has opened a new cart and added the product to the cart by sending experience events to Adobe Experience Platform. Finally, the user will click a _Download the app_ link because they are interested in your mobile app. You'll track that the user has clicked the link. 
