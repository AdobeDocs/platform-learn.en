---
title: Create tag rules for Platform Web SDK
description: Learn how to send an event to the Platform Edge Network using tag rules. This lesson is part of the Implement Adobe Experience Cloud with Web SDK tutorial.
feature: Tags
jira: KT-15403
exl-id: e06bad06-3ee3-475f-9b10-f0825a48a312
TQID: https://experienceleague.adobe.com/1sNvHTtlS1CzmxfOjC68tHDaAbBR7xlcCmGAFZpaixI
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: abc02dd6-664f-446a-9aaa-675bc0f2fe4a
    internal-label: Sources
  - id: acc16deb-1d7f-4ec9-9ce3-6cdf355afde6
    internal-label: XDM
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: d9830f6f-ceb6-4faa-9744-f281fe4439f9
    internal-label: Tags
  - id: de9975b2-c43a-4287-9698-4f4cad92b83f
    internal-label: Schemas
  - id: f6ff4d13-7b5c-4533-8556-95e76673d4cb
    internal-label: Properties
  - id: f9a2105e-7a47-4e85-9193-31a519a2cb83
    internal-label: Data elements
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# Create tag rules

Learn how to send events to the Adobe Experience Platform Edge Network using tag rules. A tag rule is a combination of events, conditions, and actions that tells the tag property to do something. With Platform Web SDK, rules are used to send events to Platform Edge Network with the right data.
 


## Learning objectives

At the end of this lesson, you are able to:

* Use a naming convention for managing rules within tags
* Send an event with XDM fields using Update Variable and Send Event actions
* Stack multiple sets of XDM fields across multiple rules
* Map individual or entire array data elements to the XDM object
* Publish a tag rule to a development library


## Prerequisites

You are familiar with Data Collection tags and the [Luma demo website](https://luma.enablementadobe.com) and have completed the previous lessons in the tutorial:

* [Configure an XDM schema](configure-schemas.md)
* [Configure an identity namespace](configure-identities.md)
* [Configure a datastream](configure-datastream.md)
* [Install Web SDK extension](install-web-sdk.md)
* [Create data elements](create-data-elements.md)
* [Capture identities](create-identities.md)

## Naming Conventions

To manage rules in tags, it is recommended to follow a standard naming convention. This tutorial uses a four-part naming convention:

* [**location**] - [**event**] - [**purpose**] - [**order**]

where;

1. **location** is the page or pages on the site where the rule fires
1. **event** is the trigger for the rule
1. **purpose** is the main action performed by the rule
1. **order** is the order in which the rule should fire in relation to other rules sharing the same event
<!-- minor update --> 

## Add Adobe Client Data Layer extension

The Luma website uses an event-driven data layer called the Adobe Client Data Layer (ACDL). Whenever an data layer event occurs, it is pushed into the `adobeDataLayer` array. This tutorial uses a tags extension called Adobe Client Data Layer to conveniently tap into these events to construct our rules. 

To add the extension:

1. Go to **[!UICONTROL Extensions]**
1. Filter to **[!UICONTROL Adobe Client Data Layer]**
1. Select **[!UICONTROL Install]**

    ![Add Adobe Client Data Layer extension](assets/rules-acdl-extension.png)

1. Leave the default settings
1. Select **[!UICONTROL Save]**

>[!NOTE]
>
> It is not necessary to use the Adobe Client Data Layer to implement Experience Platform Web SDK. Many other types of events are commonly used in tags implementations (Library Loaded, DOM Ready, Window Loaded, and so on) to fire rules. 

## Create tag rules

In tags, rules are used to execute actions such as setting variables and firing network calls under various conditions. The Experience Platform Web SDK tags extension includes two actions that are used in rules:

* **[!UICONTROL Update variable]** maps data elements to your XDM or data variables
* **[!UICONTROL Send Event]** makes the network call to send data to Experience Platform Edge Network

In the rest of this lesson we:

1. Use the **[!UICONTROL Update variable]** action to define a "global configuration" of XDM fields.

1. Use the **[!UICONTROL Update variable]** action again to override our "global configuration" and contribute additional XDM fields under certain conditions (for example, adding product details on product pages).

1. Use the **[!UICONTROL Send Event]** action to send the data to Adobe Experience Platform Edge Network.

All of these rules will be sequenced properly using the "[!UICONTROL order]" option.

This video gives an overview of the process:

>[!VIDEO](https://video.tv.adobe.com/v/3427710/?learn=on&enablevpops)

### Global configuration fields

To create a tag rule for the global XDM fields:

1. Open the tag property that you are using for this tutorial

1. Go to **[!UICONTROL Rules]** in the left navigation

1. Select the **[!UICONTROL Create New Rule]** button

    ![Create a rule](assets/rules-create.png)
    
1. Name the rule `all pages - adobeDataLayer push - set global variables - 1`

1. In the **[!UICONTROL Events]** section, select **[!UICONTROL Add]**

    ![Name the rule and add an event](assets/rule-name-new.png)

1. Use the **[!UICONTROL Adobe Client Data Layer]** extension and select **[!UICONTROL Data Pushed]** as the **[!UICONTROL Event Type]** 

1. Select **[!UICONTROL Advanced]** dropdown and enter `1` as the **[!UICONTROL Order]**

    >[!NOTE]
    >
    > The lower the order number, the earlier it executes. Therefore, we give our "global configuration" a low order number.

1. Listen to **[!UICONTROL All Events]** 
1. Select **[!UICONTROL Keep Changes]** to return to the main rule screen
    ![Select Library Loaded Trigger](assets/create-tag-rule-trigger-loaded.png)

1. In the **[!UICONTROL Actions]** section, select **[!UICONTROL Add]**

1. As the **[!UICONTROL Extension]**, select **[!UICONTROL Adobe Experience Platform Web SDK]** 

1. As the **[!UICONTROL Action Type]**, select **[!UICONTROL Update variable]** 

1. As the **[!UICONTROL Data element]**, select the `XDM Variable` you created in the [Create data elements](create-data-elements.md) lesson

    ![Update Variable Schema](assets/create-rule-update-variable.png)

1. Now, specify the XDM fields by mapping them to appropriate values:

    | XDM Field | Map to |
    |---|---|
    | `eventType` | `Web Webpagedetails Page Views` (begin typing to see the suggested values)|
    | `identityMap` | `Identity Map` data element |
    | `web.webPageDetails.name` | `Page Name` data element |
    | `web.webPageDetails.pageViews.value` | `1` |


    >[!TIP]
    >
    > XDM fields will not be included in the network request if the data element is null. Therefore, when the user is not authenticated and the `Identity Map` data element is null, the `identityMap` object will not be sent. This is why we can safely define it in our "global configuration". 

    >[!TIP]
    >
    > Setting `web.webPageDetails.pageViews.value` provides a standard way to indicate a page view for other downstream applications. It is not required for Adobe Analytics to process a network call as a page view.

1. When you are done, your `XDM Variable` will look something like this. Note how the populated and partially populated fields are indicated with the blue circles:
     ![XDM Variable](assets/rule-xdm-variable.png)
1. Select **[!UICONTROL Keep Changes]** and then **[!UICONTROL Save]** the rule



### Product page fields

Now, start to use **[!UICONTROL Update variable]** in additional, sequenced rules to enrich the XDM object before sending it to [!UICONTROL Platform Edge Network]. 

>[!TIP]
>
>Rule order determines which rule runs first when an event is triggered. If two rules have the same event type, the rule with the lowest order number runs first.
> 

Start by tracking product views on the product detail page of Luma:

1. Select **[!UICONTROL Add Rule]**
1. Name it  [!UICONTROL `product detail pages - adobeDataLayer push - set product details variables - 20`]
1. Select the ![+ symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) under Event to add a new trigger
1. Under **[!UICONTROL Extension]**, select **[!UICONTROL Adobe Client Data Layer]**
1. Under **[!UICONTROL Event Type]**, select **[!UICONTROL Data Pushed]**
1. Select to open **[!UICONTROL Advanced Options]**, type in `20`. This order value ensures the rule runs _after_ the global variables rule.
1. Listen to a **[!UICONTROL Specific Event]**
1. Enter `productView` as the **[!UICONTROL Event / Key to register for]**
1. Select **[!UICONTROL Keep changes]**

    ![Analytics XDM rules](assets/rule-pdp-event.png)


1. Under **[!UICONTROL Actions]** select **[!UICONTROL Add]**
1. Select **[!UICONTROL Adobe Experience Platform Web SDK]** extension
1. Select **[!UICONTROL Action Type]** as **[!UICONTROL Update variable]**
1. Select `XDM Variable` as the **[!UICONTROL Data element]**  
1. Map these XDM fields to appropriate values:

    | XDM Field | Map to |
    |---|---|
    | `eventType` | `Commerce Product Views` (begin typing to see the suggested values)|
    | `commerce.productViews.value` | `1` |
    | `productListItems.name` | `Ecommerce Product Name` data element (Select **[!UICONTROL Provide individual items]** and **[!UICONTROL Add Item]** first ) |
    | `productListItems.sku` | `Ecommerce Product Id` data element |

1. Select **[!UICONTROL Keep Changes]**

1. Select **[!UICONTROL Save]** to save the rule

    >[!NOTE]
    >
    >Because this rule has a higher order, it will overwrite the `eventType` set in the "global configuration" rule. `eventType` can only contain one value and we recommend setting it with the most valuable event.

    >[!TIP]
    >
    >Setting commerce.productViews.value=1 in XDM automatically maps to the `prodView` event in Analytics


### Shopping cart fields

You can map entire array to an XDM object, provided the array matches the format of the XDM schema. The custom code data element `Ecommerce Cart Products` you created earlier loops through the `adobeDataLayer.ecommerce.cart.items` data layer object on the Luma website and translates it into the required format of the `productListItems` object of the XDM schema.

To illustrate, see the comparison below of the Luma site data layer (left) to the translated data element (right): 

![XDM object array format](assets/data-element-xdm-array.png)


Compare the data element to the `productListItems` structure (hint, it should match).

>[!NOTE]
>
> You will not be able to run `_satellite.getVar('Ecommerce Cart Products')` at this point in the tutorial.

>[!IMPORTANT]
>
>When mapping fields from your data layer to XDM, make sure the fields match the data type of the XDM field. In the example above `quantity` and `priceTotal` must be integers or the record will not ingest into Platform.
> ![XDM schema data type](assets/set-up-analytics-quantity-integer.png)

Now, let's map our array to the XDM object:


1. Create a new rule named `cart page - adobeDataLayer push - set cart variables - 20`
1. Select the ![+ symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) under Event to add a new trigger
1. Under **[!UICONTROL Extension]**, select **[!UICONTROL Adobe Client Data Layer]**
1. Under **[!UICONTROL Event Type]**, select **[!UICONTROL Data Pushed]**
1. Select to open **[!UICONTROL Advanced Options]**, type in `20`. This order value ensures the rule runs _after_ the global variables rule.
1. Listen to a **[!UICONTROL Specific Event]**
1. Enter `cartView` as the **[!UICONTROL Event / Key to register for]**
1. Select **[!UICONTROL Keep Changes]**


    ![Event for Cart rule](assets/rule-cart-event.png)

1. Under **[!UICONTROL Actions]** select **[!UICONTROL Add]**
1. Select **[!UICONTROL Adobe Experience Platform Web SDK]** extension
1. Select **[!UICONTROL Action Type]** as **[!UICONTROL Update variable]**
1. Select `XDM Variable` as the **[!UICONTROL Data element]**  
1. Map these XDM fields to appropriate values:

    | XDM Field | Map to |
    |---|---|
    | `eventType` | `Commerce Product List (Cart) Views` (begin typing to see the suggested values)|
    | `commerce.productListViews.value` | `1` |
    | `productListItems` | `Ecommerce Cart Products` data element (Select **[!UICONTROL Provide entire array]**  first ) |

    >[!TIP]
    >
    >Setting commerce.productListViews.value=1 in XDM automatically maps to the `scView` event in Analytics

1. Select **[!UICONTROL Keep Changes]**

1. Select **[!UICONTROL Save]** to save the rule


### Order confirmation fields

Create another rule for purchase events:

1. Create a new rule named `order confirmation - adobeDataLayer push - set purchase variables -  20`
1. Select the ![+ symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) under Event to add a new trigger
1. Under **[!UICONTROL Extension]**, select **[!UICONTROL Adobe Client Data Layer]**
1. Under **[!UICONTROL Event Type]**, select **[!UICONTROL Data Pushed]**
1. Select to open **[!UICONTROL Advanced Options]**, type in `20`. This order value ensures the rule runs _after_ the global variables rule.
1. Listen to a **[!UICONTROL Specific Event]**
1. Enter `purchase` as the **[!UICONTROL Event / Key to register for]**
1. Select **[!UICONTROL Keep Changes]**
1. Under **[!UICONTROL Actions]** select **[!UICONTROL Add]**
1. Select **[!UICONTROL Adobe Experience Platform Web SDK]** extension
1. Select **[!UICONTROL Action Type]** as **[!UICONTROL Update variable]**
1. Select `XDM Variable` as the **[!UICONTROL Data element]**  
1. Map these XDM fields to appropriate values:

    | XDM Field | Map to |
    |---|---|
    | `eventType` | `Commerce Purchases` (begin typing to see the suggested values)|
    | `commerce.productListViews.value` | `1` |
    |  `commerce.order.purchaseID` | `Ecommerce Purchase Id` data element |
    | `commerce.order.currencyCode` | `USD` |
    | `productListItems` | `Ecommerce Cart Products` data element(Select **[!UICONTROL Provide entire array]**  first ) |

    >[!TIP]
    >
    >Setting `commerce.productListViews.value` to `1`, `commerce.order.purchaseID`, and `commerce.order.currencyCode` in XDM automatically maps to the `purchase`,  `s.purchaseID`, and `s.currencyCode` variables in Analytics, respectively.


1. Select **[!UICONTROL Keep Changes]**
1. Select **[!UICONTROL Save]**


### Send event rule

Now that you have set the variables, you can create the rule to send the complete XDM object to Platform Edge Network with the **[!UICONTROL Send event]** action.


1. Create a new rule named `all pages - adobeDataLayer push - send event - 50`
1. Select the ![+ symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) under Event to add a new trigger
1. Under **[!UICONTROL Extension]**, select **[!UICONTROL Adobe Client Data Layer]**
1. Under **[!UICONTROL Event Type]**, select **[!UICONTROL Data Pushed]**
1. Select to open **[!UICONTROL Advanced Options]**, type in `50` (which is probably the default). This order value ensures the rule runs _after_ the variable-setting rules.
1. Listen to a **[!UICONTROL All Events]**
1. Select **[!UICONTROL Keep Changes]**
1. Under **[!UICONTROL Actions]** select **[!UICONTROL Add]**
1. Select **[!UICONTROL Adobe Experience Platform Web SDK]** extension
1. Select **[!UICONTROL Action Type]** as **[!UICONTROL Send Event variable]**



1. As the  **[!UICONTROL Action Type]**, select **[!UICONTROL Send event]** 

1. As the **[!UICONTROL XDM]**, select the `XDM Variable` data element created in the previous lesson

1. Select **[!UICONTROL Keep Changes]** to return to the main rule screen

    ![Add the Send Event action](assets/create-rule-send-event-action.png)
1. Select **[!UICONTROL Save]** to save the rule    

    ![Save the rule](assets/create-rule-save-rule.png)   

You should have the following rules in your property:

![Verify list of rules](assets/create-rule-list-of-rules.png)   

## Publish the rules in a library

Next, publish the rule to your development environment so you can verify it works.

To create a library:

1. Go to **[!UICONTROL Publishing Flow]** in the left navigation

1. Select **[!UICONTROL Add Library]**

    ![Select Add Library](assets/rule-publish-library.png)
1. For the **[!UICONTROL Name]**, enter `Luma Web SDK Tutorial`
1. For the **[!UICONTROL Environment]**, select `Development`
1. Select  **[!UICONTROL Add All Changed Resources]** 

    >[!NOTE]
    >
    >    You should see all the tag components created in previous lessons. The Core extension contains the base JavaScript required by all web tag properties.

1. Select **[!UICONTROL Save & Build for Development]**

    ![Create and build the library](assets/create-tag-rule-library-changes.png)

The library may take a few minutes to build and when it is complete it displays a green dot to the left of the library name:

![Build complete](assets/create-rule-development-success.png)   

As you can see on the [!UICONTROL Publishing Flow] screen, there is a lot more to the publishing process, which is beyond the scope of this tutorial. This tutorial just uses a single library in your Development environment.

Now, you are ready to validate the data in the request using the Adobe Experience Platform Debugger.

>[!NOTE]
>
>Thank you for investing your time in learning about Adobe Experience Platform Web SDK. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/adobe-experience-platform-18/tutorial-discussion-implement-adobe-experience-cloud-with-web-sdk-tutorial-248848)
