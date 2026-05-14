---
title: Create data elements for Platform Web SDK
description: Learn how to create an XDM object and map data elements to it in tags. This lesson is part of the Implement Adobe Experience Cloud with Web SDK tutorial.
feature: Tags
jira: KT-15401
exl-id: d662ec46-de9b-44ba-974a-f81dfc842e68
TQID: https://experienceleague.adobe.com/orD6U4iDTSG8w9zSnQNOBisvG-nRZd6cYPZygX4Y9KE
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: df80eeb1-8d72-467e-b0df-9d51c7d3a0a1
    internal-label: Audience Manager
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
    internal-label: Target
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
  - id: f002a92a-b99f-47a4-90c8-65e0e415bc7a
    internal-label: Pass
feature_v2:
  - id: a8b0238e-1d43-4679-a3b4-5ba1bad83baa
    internal-label: Implementation
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
    internal-label: Implementation
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: acc16deb-1d7f-4ec9-9ce3-6cdf355afde6
    internal-label: XDM
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: aff8c1fa-1be7-48bd-92b8-4b12a668ca13
    internal-label: Data prep
  - id: ca3d6bf4-a4af-4944-936b-8de1eb09f149
    internal-label: Datastreams
  - id: d9830f6f-ceb6-4faa-9744-f281fe4439f9
    internal-label: Tags
  - id: dc6ebdf7-9a94-43eb-9184-759cfdd0cf1c
    internal-label: Event forwarding
  - id: de9975b2-c43a-4287-9698-4f4cad92b83f
    internal-label: Schemas
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
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# Create data elements

Learn how to create data elements in tags for content, commerce, and identity data on the [Luma demo website](https://luma.enablementadobe.com). Then populate fields in your XDM schema. 



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
>The data for this lesson comes from the `[!UICONTROL adobeDataLayer]` data layer on the [Luma site](https://luma.enablementadobe.com). To view the data layer, open your developer console and type in `[!UICONTROL adobeDataLayer]` to see the full data layer available.![adobeDataLayer data layer](assets/data-element-data-layer-new.png)


## Data layer approaches

There are multiple ways to map data from your data layer to XDM using the tags functionality of Adobe Experience Platform. Below are a few pros and cons of three different approaches. It is possible to combine approaches, if desired:

1. Implement XDM in the data layer
1. Map to XDM in tags
1. Map to XDM in the datastream

>[!NOTE]
>
>The examples in this tutorial follow the Map to XDM in tags approach.


### Implement XDM in the data layer

In this approach, web developers implement a fully-defined XDM object as the structure for the data layer. Then you simply map the entire data layer to an XDM object in tags. If your implementation does not use a tag manager, this approach may be ideal because you can send data to XDM directly from your application using the [XDM sendEvent command](https://experienceleague.adobe.com/en/docs/experience-platform/edge/fundamentals/tracking-events#sending-xdm-data). If you do use tags, you can create a custom code data element capturing the entire data layer as a pass-through JSON object to the XDM. Then, you map the pass-through JSON to the XDM object field in the Send Event Action. 

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
* It may be quicker to deploy if your web development team also owns the tagging of digital behavior

Cons

* Complete reliance on development team and dev cycle for updating what data goes to XDM
* Limited flexibility as XDM receives the exact payload from the data layer 
* Cannot use built-in tags features, such as scraping, persistence, features for quick deployments
* Harder to use the data layer for third-party pixels (but you might want to move these pixels to [event forwarding](setup-event-forwarding.md)!)
* No ability to transform the data between the data layer and XDM

### Map to XDM in tags 

This approach involves mapping individual data layer variables to data elements in tags and eventually to XDM. This is the traditional approach to implementation using a tag management system. 

#### Pros

* The most flexible approach as you can control individual variables and transform data before it gets to XDM
* Can use Adobe tags triggers and scraping functionality to pass data to XDM
* Can map data elements to third-party pixels client-side

#### Cons

* Takes time to reconstruct the data layer as tags data elements


>[!IMPORTANT]
>
>As noted earlier, the examples in this tutorial follow the Map to XDM in tags approach.

### Map to XDM in the datastream

This approach uses functionality built-into the datastream configuration called [Data Prep for Data Collection](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/data-prep) and skips mapping data layer variables to XDM in tags. 

#### Pros

* Flexible mapping of individual variables to XDM in a point-and-click UI
* Ability to [compute new values](https://experienceleague.adobe.com/en/docs/experience-platform/data-prep/functions) or [transform data types](https://experienceleague.adobe.com/en/docs/experience-platform/data-prep/data-handling) from a data layer before it goes to XDM 

#### Cons

* Cannot use data layer variables as data elements for client-side third-party pixels, but can use them with event forwarding
* Cannot use the scraping functionality in tags
* Maintenance complexity increases if mapping the data layer both in tags and in datastream 


>[!TIP] 
>
> Google Data Layer
> 
> If your organization already uses Google Analytics and has the traditional Google dataLayer object on your website, you can use the [Google Data Layer extension](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/client/google-data-layer/overview) in tags. This allows you to deploy Adobe technology quicker without having to request support from your IT team. Mapping the Google data layer to XDM would follow the same steps as above.


## Create data elements to capture the data layer

Before you populate XDM fields, first capture the data points you need as tags data elements:

1. Go to **[!UICONTROL Data Elements]** and select **[!UICONTROL Add Data Element]** (or **[!UICONTROL Create New Data Element]** if there are no existing data elements in the tag property)

    ![Create Data Element](assets/data-element-create.png)

1. Name the data element `Page Name`
1. Use the **[!UICONTROL JavaScript Variable]** **[!UICONTROL Data Element type]** to point to the value in Luma's data layer: `adobeDataLayer.0.page.name`

1. Check the boxes for **[!UICONTROL Force lowercase value]** and **[!UICONTROL Clean text]** to standardize the case and remove extraneous spaces

1. Leave `None` as the **[!UICONTROL Storage Duration]** setting since this value is different on every page

1. Select **[!UICONTROL Save]**

    ![Page Name Data Element](assets/data-element-pageName.png)

Create these additional data elements by following the same steps:

* **`User Id`**  mapped to 
`adobeDataLayer.0.user.id`

* **`User Logged In`** mapped to
`adobeDataLayer.0.user.loggedIn`

* **`Ecommerce Product Id`** mapped to `adobeDataLayer.0.ecommerce.detail.products.0.id`
* **`Ecommerce Product Name`** mapped to `adobeDataLayer.0.ecommerce.detail.products.0.name`
* **`Ecommerce Purchase Id`** mapped to `adobeDataLayer.0.ecommerce.purchase.actionField.id` 
* **`Ecommerce Product Category`** using the **[!UICONTROL Custom Code]** **[!UICONTROL Data Element type]** and the following custom code:

   ```javascript
   return adobeDataLayer[0].ecommerce.detail.products[0].category+":"+adobeDataLayer[0].ecommerce.detail.products[0].subcategory;
   ```

* **`Ecommerce Cart Products`** using the following custom code:

   ```javascript
   const cartProducts = adobeDataLayer
   .flatMap(evt => Array.isArray(evt?.ecommerce?.cart?.items) ? evt.ecommerce.cart.items : [])
   .filter(item => item && item.id && item.name && item.brand)
   .map(({ id, name, brand }) => ({ id, name, brand }));

   return cartProducts;
   ```

* **`Ecommerce Purchase Products`** using the following custom code:

   ```javascript
   const purchaseEvent = adobeDataLayer.find(e => e.event === "purchase");

   const currencyCode = purchaseEvent?.ecommerce?.currencyCode ?? "USD";

   const purchasedProducts = (purchaseEvent?.ecommerce?.purchase?.products || []).map(p => {
      const unitPrice = parseFloat(String(p.price).replace(/[^0-9.-]/g, "")) || 0;
      const qty = Number(p.quantity) || 0;

      return {
      SKU: p.id,                       // id -> SKU
      name: p.name,                    // name -> name
      quantity: qty,                   // quantity -> quantity
      priceTotal: unitPrice * qty,     // price -> priceTotal (unit price × quantity)
      currencyCode                     // "USD" -> currencyCode (from ecommerce.currencyCode)
      };
   });

   return(purchasedProducts);
   ```


>[!CAUTION]
>
>The [!UICONTROL JavaScript variable] data element type treats array references as dots instead of brackets, so referencing the username data element as `adobeDataLayer[0].page.name` **will not work**.

## Create Variable data elements for XDM and data objects

The data elements you just created will be used to build an XDM object (for Platform applications) and a data object (for Analytics, Target, and Audience Manager). These objects have their own special data elements called **[!UICONTROL Variable]** data elements which are very easy to create. 

To create the Variable data element for XDM, you tie it to the schema you created in the [Configure a schema](configure-schemas.md) lesson:

1. Select **[!UICONTROL Add Data element]**
1. Name your Data Element `XDM Variable`. It is recommended you prefix with "XDM" the Data Elements specific to XDM to better organize your tag property
1. Select the **[!UICONTROL Adobe Experience Platform Web SDK]** as the **[!UICONTROL Extension]**
1. Select the **[!UICONTROL Variable]** as the **[!UICONTROL Data Element Type]**
1. Select **[!UICONTROL XDM]** as the **[!UICONTROL property]**
1. Select the **[!UICONTROL Sandbox]** in which you created the schema
1. Select the appropriate **[!UICONTROL Schema]**, in this case `Luma Web Event Data`
1. Select **[!UICONTROL Save]**

    ![Variable data element for XDM](assets/analytics-tags-data-element-xdm-variable.png)

Next, create the Variable data element for your data object:

1. Select **[!UICONTROL Add Data element]**
1. Name your Data Element `Data Variable`. 
1. Select the **[!UICONTROL Adobe Experience Platform Web SDK]** as the **[!UICONTROL Extension]**
1. Select the **[!UICONTROL Variable]** as the **[!UICONTROL Data Element Type]**
1. Select **[!UICONTROL data]** as the **[!UICONTROL property]**
1. Select the Experience Cloud solutions you wish to implement as part of this tutorial
1. Select **[!UICONTROL Save]**

    ![Variable data element for data object](assets/data-element-data-variable.png)


At the end of these steps, you should have the following data elements created:

|Core Extension Data Elements | Platform Web SDK Extension Data Elements|
| ----------------------------- | ------------------------------- |
| `Ecommerce Cart Products` | `Data Variable` |
| `Ecommerce Product Category` | `XDM Variable` |
| `Ecommerce Product Id` | |
| `Ecommerce Product Name` | |
| `Ecommerce Purchase Id` | |
| `Ecommerce Purchase Products` | |
| `Page Name` | |
| `User Id` | |
| `User Logged In` | |

With these data elements in place, you are ready to start sending data to Platform Edge Network with a tags rule. But first, learn about collecting identities with Web SDK. 

>[!NOTE]
>
>Thank you for investing your time in learning about Adobe Experience Platform Web SDK. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/adobe-experience-platform-18/tutorial-discussion-implement-adobe-experience-cloud-with-web-sdk-tutorial-248848)
