---
title: Create data elements
description: Learn how to create an XDM object and map data elements to it in tags. This lesson is part of the Implement Adobe Experience Cloud with Web SDK tutorial.
feature: Tags
exl-id: 4d351aed-482e-43ed-9266-52c6667db6fe
---
# Create data elements

Learn how to create data elements in tags for content, commerce, and identity data on the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html). Then populate fields in your XDM schema with the Platform Web SDK extension Variable data element type. 

## Learning objectives

At the end of this lesson, you are able to:

* Understand different approaches to mapping a data layer to XDM
* Create data elements to capture data
* Map data elements to an XDM object


## Prerequisites 

You have an understanding of what a data layer is and have completed the previous lessons in the tutorial:

* [Configure an XDM schema](configure-schemas.md)
* [Configure an identity namespace](configure-identities.md)
* [Configure a datastream](configure-datastream.md)
* [Web SDK extension installed in the tag property](install-web-sdk.md)


>[!IMPORTANT]
>
>The data for this lesson comes from the `[!UICONTROL digitalData]` data layer on the Luma site. To view the data layer, open your developer console and type in `[!UICONTROL digitalData]` to see the full data layer available.![digitalData data layer](assets/data-element-data-layer.png)


## Data layer approaches

There are multiple ways to map data from your data layer to XDM using the tags functionality of Adobe Experience Platform. Below are a few pros and cons of three different approaches. It is possible to combine approaches, if desired:

1. Implement XDM in the data layer
1. Map to XDM in tags
1. Map to XDM in the datastream

>[!NOTE]
>
>The examples in this tutorial follow the Map to XDM in tags approach.


### Implement XDM in the data layer

This approach involves using the fully defined XDM object as the structure for your data layer. Then you map the entire data layer to an XDM object data element in tags. If your implementation is not using a tag manager, this approach may be ideal because you can send data to XDM directly from your application using the [XDM sendEvent command](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/tracking-events.html?lang=en#sending-xdm-data). If you do you use tags, you can create a custom code data element capturing the entire data layer as a pass-through JSON object to the XDM. Then, you map the pass-through JSON to the XDM object field in the Send Event Action. 

Below is an example of how the data layer would look like using the Adobe Client Data Layer format:

+++XDM in Data Layer example

```JSON
window.adobeDataLayer.push({
"eventType": "web.webPageDetails.pageViews",
"web":{
         "webInteraction":{
            "linkClicks":{
               "id":"",
               "value":""
            },
            "URL":"",
            "name":"",
            "region":"",
            "type":""
         },
         "webPageDetails":{
            "pageViews":{
               "id":"",
               "value":"1"
            },
            "URL":"https://luma.enablementadobe.com/",
            "isErrorPage":"",
            "isHomePage":"",
            "name":"luma:home",
            "server":"enablementadobe.com",
            "siteSection":"home",
            "viewName":""
         },
         "webReferrer":{
            "URL":"",
            "type":""
         }
      }
});
```

+++

Pros

* Eliminates additional steps remap to data layer variables to XDM
* May be quicker to deploy if your development team owns tagging digital behavior

Cons

* Complete reliance on development team and dev cycle for updating what data goes to XDM
* Limited flexibility as XDM receives the exact payload from the data layer 
* Cannot use built-in tags features, such as scraping, persistence, features for quick deployments
* Cannot use the data layer for third-party pixels
* No ability to transform the data between the data layer and XDM

### Map data layer in tags 

This approach involves mapping individual data layer variables OR data layer objects to data elements in tags and eventually to XDM. This is the traditional approach to implementation using a tag management system. 

#### Pros

* The most flexible approach as you can control individual variables and transform data before it gets to XDM
* Can use Adobe tags triggers and scraping functionality to pass data to XDM
* Can map data elements to third-party pixels client-side

#### Cons

* Takes time to reconstruct the data layer as data elements


>[!TIP] 
>
> Google Data Layer
> 
> If your organization already uses Google Analytics and has the traditional Google dataLayer object on your website, you can use the [Google Data Layer extension](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/google-data-layer/overview.html?lang=en) in tags. This allows you to deploy Adobe technology quicker without having to request support from your IT team. Mapping the Google data layer to XDM would follow the same steps as above.

### Map to XDM in the datastream

This approach uses functionality built-into the datastream configuration called [Data Prep for Data Collection](https://experienceleague.adobe.com/docs/experience-platform/datastreams/data-prep.html) and skips mapping data layer variables to XDM in tags. 

#### Pros

* Flexible as you can map individual variables to XDM
* Ability to [compute new values](https://experienceleague.adobe.com/docs/experience-platform/data-prep/functions.html) or [transform data types](https://experienceleague.adobe.com/docs/experience-platform/data-prep/data-handling.html) from a data layer before it goes to XDM 
* Leverage a [Mapping UI](https://experienceleague.adobe.com/docs/experience-platform/datastreams/data-prep.html#create-mapping) to map fields in your source data to XDM with a point-and-click UI

#### Cons

* Cannot use data layer variables as data elements for client-side third-party pixels, but can use them with event forwarding
* Cannot use the scraping functionality of the tags feature of Adobe Experience Platform 
* Maintenance complexity increases if mapping the data layer both in tags and in datastream 



>[!IMPORTANT]
>
>As noted earlier, the examples in this tutorial follow the Map to XDM in tags approach.

## Create data elements to capture the data layer

Before you create the XDM object, create the following set of data elements for the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} data layer:

1. Go to **[!UICONTROL Data Elements]** and select **[!UICONTROL Add Data Element]** (or **[!UICONTROL Create New Data Element]** if there are no existing data elements in the tag property)

    ![Create Data Element](assets/data-element-create.png)

1. Name the data element `page.pageInfo.pageName`
1. Use the **[!UICONTROL JavaScript Variable]** **[!UICONTROL Data Element type]** to point to a value in Luma's data layer: `digitalData.page.pageInfo.pageName`

1. Check the boxes for **[!UICONTROL Force lowercase value]** and **[!UICONTROL Clean text]** to standardize the case and remove extraneous spaces

1. Leave `None` as the **[!UICONTROL Storage Duration]** setting since this value is different on every page

1. Select **[!UICONTROL Save]**

    ![Page Name Data Element](assets/data-element-pageName.png)

Create these additional data elements by following the same steps:

* **`page.pageInfo.server`**  mapped to 
`digitalData.page.pageInfo.server`

* **`page.pageInfo.hierarchie1`**  mapped to 
`digitalData.page.pageInfo.hierarchie1`

* **`user.profile.attributes.username`**  mapped to 
`digitalData.user.0.profile.0.attributes.username`

* **`user.profile.attributes.loggedIn`** mapped to
`digitalData.user.0.profile.0.attributes.loggedIn`

* **`product.productInfo.sku`** mapped to `digitalData.product.0.productInfo.sku`
<!--digitalData.product.0.productInfo.sku
    ```javascript
    var cart = digitalData.product;
    var cartItem;
    cart.forEach(function(item){
    cartItem = item.productInfo.sku;
    });
    return cartItem;
    ```
    -->
* **`product.productInfo.title`** mapped to `digitalData.product.0.productInfo.title`
* **`cart.orderId`** mapped to `digitalData.cart.orderId` 
<!--
    ```javascript
    var cart = digitalData.product;
    var cartItem;
    cart.forEach(function(item){
    cartItem = item.productInfo.title;
    });
    return cartItem;
    ```
    -->
* **`product.category`** using the **[!UICONTROL Custom Code]** **[!UICONTROL Data Element type]** and the following custom code to parse the site URL for the top-level category:

   ```javascript
   var cat = location.pathname.split(/[/.]+/);
   if (cat[5] == 'products') {
      return (cat[6]);
   } else if (cat[5] != 'html') { 
      return (cat[5]);
   }
   ```

* **`cart.productInfo`** using the following custom code:

    ```javascript
    var cart = digitalData.cart.cartEntries; 
    var cartItem = [];
    cart.forEach(function(item, index, array){
    cartItem.push({
    "SKU": item.sku
    });
    });
    return cartItem; 
    ```

* **`cart.productInfo.purchase`** using the following custom code:

    ```javascript
    var cart = digitalData.cart.cartEntries; 
    var cartItem = [];
    cart.forEach(function(item, index, array){
    var qty = parseInt(item.qty);
    var price = parseInt(item.price);
    cartItem.push({
    "SKU": item.sku,
    "quantity": qty,
    "priceTotal": price
    });
    });
    return cartItem; 
    ```



>[!CAUTION]
>
>The [!UICONTROL JavaScript variable] data element type treats array references as dots instead of brackets, so referencing the username data element as `digitalData.user[0].profile[0].attributes.username` **will not work**.

## Create Variable data element

After you create the data elements, map them to the XDM using the **[!UICONTROL Variable]** data element that defines the schema used for the XDM object. This object should conform to the XDM schema you created during the [Configure a schema](configure-schemas.md) lesson. 

To create the Variable data element:

1. Select **[!UICONTROL Add Data element]**
1. Name your Data Element `xdm.variable.content`. It is recommended you prefix with "xdm" the Data Elements specific to XDM to better organize your tag property
1. Select the **[!UICONTROL Adobe Experience Platform Web SDK]** as the **[!UICONTROL Extension]**
1. Select the **[!UICONTROL Variable]** as the **[!UICONTROL Data Element Type]**
1. Select the appropriate Experience Platform **[!UICONTROL Sandbox]**
1. Select the appropriate **[!UICONTROL Schema]**, in this case `Luma Web Event Data`
1. Select **[!UICONTROL Save]**

    ![Variable data element](assets/analytics-tags-data-element-xdm-variable.png)


At the end of these steps, you should have the following data elements created:

|Core Extension Data Elements | Platform Web SDK Extension Data Elements|
-----------------------------|-------------------------------
| `cart.orderId` | `xdm.variable.content` |
| `cart.productInfo`| |
| `cart.productInfo.purchase`| |
| `page.pageInfo.hierarchie1` | |
| `page.pageInfo.pageName` | |
| `page.pageInfo.server` | |
| `product.category`| | 
| `product.productInfo.sku`| | 
| `product.productInfo.title`| |
| `user.profile.attributes.loggedIn` | |
| `user.profile.attributes.username` | |

>[!TIP]
>
>In a future [Create tag rules](create-tag-rule.md) lesson, you learn how the **[!UICONTROL Variable]** data element allows you to stack multiple rules in tags using the **[!UICONTROL Update Variable Action type]**.

With these data elements in place, you are ready to start sending data to Platform Edge Network with a tags rule. But first, learn about collecting identities with Web SDK. 

[Next: **Create identities**](create-identities.md)

>[!NOTE]
>
>Thank you for investing your time in learning about Adobe Experience Platform Web SDK. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
