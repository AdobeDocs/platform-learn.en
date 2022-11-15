---
title: Create rules for tracking page view and commerce events
description: Create rules for tracking page view and commerce events
exl-id: 00bf3374-9319-47ce-a75a-2b94f793c938
---
# Create rules for tracking page view and commerce events

To track that the user has viewed the product page, create a rule within Adobe Experience Platform [!DNL Tags]. 

1. Click on **[!UICONTROL Rules]** in the left side navigation, then click **[!UICONTROL Create New Rule]**.

1. For the rule name, enter **_Page Viewed_**.

## Add an event

1. Click the **[!UICONTROL Add]** button under [!UICONTROL Events]. You show now be on the event view. For the [!UICONTROL Extension] field, select **[!UICONTROL Adobe Client Data Layer]**. For the [!UICONTROL Event Type] field, select **[!UICONTROL Data Pushed]**.
1. Because you only want this rule to be triggered when the `pageViewed` event is pushed to the data layer, select **[!UICONTROL Specific Event]** under [!UICONTROL Listen to] and type **_pageViewed_** into the [!UICONTROL Event / Key to register for] text field.
1. Click **[!UICONTROL Keep Changes]**.
    ![Page viewed event](../assets/page-viewed-event.png)

## Add an action

Now that you're back at the rule view:

1. Click the **[!UICONTROL Add]** button under [!UICONTROL Actions]. You should now be on the action view. For the [!UICONTROL Extension] field, select **[!UICONTROL Adobe Experience Platform Web SDK]**. For the [!UICONTROL Action Type] field, select **[!UICONTROL Send event]**. This action allows you to send an experience event to Adobe Experience Platform Edge Network.
1. In the middle of the screen, find the [!UICONTROL Type] field and select **`web.webpagedetails.pageViews`**. This is one of the canonical Experience Event types that Adobe Experience Platform provides out of the box. It represents a page view.
1. For the [!UICONTROL XDM data] field, enter **`%event.fullState%`**. This indicates that the computed state (also known as full state) of the data layer, which is captured at the time the rule was triggered. This should be sent as part of the experience event.
1. Click the **[!UICONTROL Keep Changes]** button.
    ![Page viewed action](../assets/page-viewed-action.png)

If the data you pushed into the data layer from your website did not conform to your XDM schema, or if you only want to send a portion of the data layer's computed state, use the [!UICONTROL XDM Object] data element type (provided by the Adobe Experience Platform Web SDK extension) to build an appropriate object that matches your schema.

## Save the rule

1. Save the rule by clicking **[!UICONTROL Save]**.
![Page viewed rule](../assets/page-viewed-rule.png)

## Repeat the process

Repeat the process outlined above to create rules for when a product is viewed, a shopping cart is opened, and a product is added to the cart. The only differences among the rules are the rule name, the value entered into the [!UICONTROL Event / Key to register for] field in the [!UICONTROL Data Pushed] event, and the [!UICONTROL Type] field in the [!UICONTROL Send event] action. Here are the values for each rule:

Product-viewed rule:

* **Rule name**: _Product Viewed_
* **Event / Key to register for** within [!UICONTROL Data Pushed] event: `productViewed`
* **Type** within [!UICONTROL Send event] action: `commerce.productViews`

Cart opened rule:

* **Rule name**: _Cart Opened_
* **Event / Key to register for** within [!UICONTROL Data Pushed] event: `cartOpened`
* **Type** within [!UICONTROL Send event] action: `commerce.productListOpens`

Product added to cart rule:

* **Rule name**: _Product Added To Cart_
* **Event / Key to register for** within [!UICONTROL Data Pushed] event: `productAddedToCart`
* **Type** within [!UICONTROL Send event] action: `commerce.productListAdds` 

Next, we handle tracking clicks on the [!UICONTROL Download the app] link.

[Next: **Create a data element and rule for tracking app downloads**](create-a-data-element-and-rule-for-tracking-app-downloads.md)

>[!NOTE]
>
>Thank you for investing your time in learning about Data Collection. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)
