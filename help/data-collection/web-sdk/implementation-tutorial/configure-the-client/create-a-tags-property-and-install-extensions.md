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
# Create an Adobe Experience Platform tag property and install extensions

Now that on-page code is pushing data and events into the data layer, it's time for the marketer to read the data from the data layer and send this data to Adobe Experience Platform. This would typically require two JavaScript libraries:

* Adobe Client Data Layer: In previous steps, you created a data layer array and pushed objects into it. In order to access data, you must load the Adobe Client Data Layer JavaScript library, which provides ways to be notified of data layer changes and events and also provides simple ways to access the data.
* Adobe Experience Platform Web SDK: This JavaScript library communicates with Adobe Experience Platform Edge Network. The SDK handles identity, consent, data collection, personalization, audiences, and more.

While you could load these individual libraries onto your website and use them directly, we recommend you use [Adobe Experience Platform Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html). With Tags, you can embed a single script into your HTML and use the Tags user interface to deploy both the Adobe Client Data Layer and Adobe Experience Platform Web SDK. Tags also allows you to create rules for sending data, among other things. This tutorial uses Tags for this purpose and assumes you have a basic understand of how Tags operates.

## Create a property within Tags

If you haven't already, [create a property within Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/companies-and-properties.html#create-or-configure-a-property).

## Install the Adobe Client Data Layer extension

Install the Adobe Client Data Layer extension by navigating to the extension catalog, finding the extension, and clicking the respective [!UICONTROL Install] button. You should see a configuration screen.

![Adobe Client Data Layer extension installation](../../../assets/implementation-strategy/acdl-extension-installation.png)

For this tutorial, there's no need to change the default values. Click [!UICONTROL Save].

## Install the Adobe Experience Platform Web SDK extension

Next, install the Adobe Experience Platform Web SDK extension by finding the extension in the extension catalog and clicking the respective [!UICONTROL Install] button. You should see a configuration screen.

![Adobe Experience Platform Web SDK extension installation](../../../assets/implementation-strategy/web-sdk-extension-installation.png)

In [Create a datastream](../configure-the-server/create-a-datastream.md), you created a datastream that Adobe Experience Platform Edge Network references to determine where to send your inbound data. When making requests from Adobe Experience Platform Web SDK to Edge Network, you must indicate which datastream Edge Network should reference.

To do so, find the [!UICONTROL Datastream] field and select the datastream you previously created. You're presented with the same datastream environments you saw in [Create a datastream](../configure-the-server/create-a-datastream.md).

![Datastream selection](../../../assets/implementation-strategy/web-sdk-datastream-selection.png)

As discussed in [Create a datastream](../configure-the-server/create-a-dataset.md), these dataset environments have a relationship to Tags environments. Assume for a moment that you complete installation of the Adobe Experience Platform Web SDK extension, create a tag library that includes the extension, then publish the library to a Tags development environment. When the tag library is loaded onto your web page and the Adobe Experience Platform Web SDK extension makes a request to Edge Network, the extension includes the [!UICONTROL Development Environment] datastream environment ID. Edge Network, in turn, uses that ID to read the configuration of the [!UICONTROL Development Environment] datastream environment and forward data to the appropriate Adobe products.

At the moment, you only have one development datastream environment, one staging datastream environment, and one production datastream environment. This is why the extension configuration user interface shows them all pre-selected and unchangeable. It is possible, however, to create multiple datastream development environments (one for you and one for your co-worker, perhaps) using the datastream user interface. If you had multiple development datastream environments, you would be able to select which one you want to use for this tag property.

Finally, scroll down and uncheck [!UICONTROL Enable click data collection]. By default, the SDK automatically tracks links for you. In this tutorial, however, we'll demonstrate how you can track your own link clicks using custom link information. 

Click on the [!UICONTROL Save] button to finish installing the Adobe Experience Platform Web SDK extension.

The appropriate extensions have been installed. It's time to create rules and data elements.
