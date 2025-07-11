---
title: Set up Adobe Analytics using Experience Platform Web SDK
description: Learn how to set up Adobe Analytics using Experience Platform Web SDK. This lesson is part of the Implement Adobe Experience Cloud with Web SDK tutorial.
solution: Data Collection, Analytics
jira: KT-15408
exl-id: de86b936-0a47-4ade-8ca7-834c6ed0f041
---
# Set up Adobe Analytics with Adobe Experience Platform Web SDK

Learn how to set up Adobe Analytics using [Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/en/docs/platform-learn/data-collection/web-sdk/overview), create tag rules to send data to Adobe Analytics, and validate that Analytics is capturing data as expected.

[Adobe Analytics](https://experienceleague.adobe.com/en/docs/analytics) is an industry-leading application that empowers you to understand your customers as people and steer your business with customer intelligence.

![Web SDK to Adobe Analytics diagram](assets/dc-websdk-aa.png)  

## Learning objectives

At the end of this lesson, you will be able to:

* Configure a datastream to enable Adobe Analytics
* Know which standard XDM fields auto-map to Analytics variables
* Set Analytics variables in the data object
* Send data to another report suite by overriding the datastream
* Validate Adobe Analytics variables using Debugger and Assurance

## Prerequisites

To complete this lesson, you must first:

* Be familiar with and have access to Adobe Analytics.

* Have at least one test/dev report suite ID. If you don't have a test/dev report suite that you can use for this tutorial, [please create one](https://experienceleague.adobe.com/en/docs/analytics/admin/admin-tools/manage-report-suites/c-new-report-suite/t-create-a-report-suite).

* Complete the earlier lessons in the Initial Configuration and Tags Configuration sections of this tutorial.

## Configure the datastream

Platform Web SDK sends data from your website to Platform Edge Network. Your datastream then tells Platform Edge Network to which Adobe Analytics report suites your data should be sent.

1. Go to [Data Collection](https://experience.adobe.com/#/data-collection){target="blank"} interface
1. On the left navigation, select **[!UICONTROL Datastreams]** 
1. Select the previously created `Luma Web SDK: Development Environment` datastream

    ![Select the Luma Web SDK datastream](assets/datastream-luma-web-sdk-development.png)

1. Select **[!UICONTROL Add Service]**
     ![Add a service to the datastream](assets/datastream-analytics-addService.png)
1. Select **[!UICONTROL Adobe Analytics]** as the **[!UICONTROL Service]**
1. Enter the **[!UICONTROL Report Suite ID]** of your development report suite
1. Select **[!UICONTROL Save]**

    ![Datastream save analytics](assets/datastream-add-analytics.png)

    >[!TIP]
    >
    >Adding more report suites by selecting **[!UICONTROL Add Report Suite]** is equivalent to multi-suite tagging.

>[!WARNING]
>
>In this tutorial, you only configure the Adobe Analytics report suite for your development environment. When you create datastreams for your own website, you should create additional datastreams and report suites for your staging and production environments.

## Set Analytics variables

There are several ways to set Analytics variables in a Web SDK implementation:

1. Automatic mapping of XDM fields to Analytics variables (automatic).
1. Set fields in the `data` object (recommended).
1. Map XDM fields to Analytics variables in Analytics processing rules (no longer recommended).
1. Map to Analytics variables directly in the XDM schema (no longer recommended).

As of May 2024, you no longer need to create an XDM schema to implement Adobe Analytics with Platform Web SDK. The `data` object (and the `data.variable` data element you created in the [Create data elements](create-data-elements.md) lesson) can be used to set all custom Analytics variables. Setting these variables in the data object will be familiar to existing Analytics customers, is more efficient than using processing rules interface, and prevents unnecessary data taking up space in Real-Time Customer Profiles (important if you have Real-Time Customer Data Platform or Journey Optimizer).

### Automatically mapped fields

Many XDM fields are automatically mapped to Analytics variables. For the most up-to-date list of mappings, please see [Analytics variable mapping in Adobe Experience Edge](https://experienceleague.adobe.com/en/docs/experience-platform/edge/data-collection/adobe-analytics/automatically-mapped-vars).

This occurs if _even if you have not defined a custom schema_. Experience Platform Web SDK automatically collects some data and sends it to Platform Edge Network as XDM fields. For example, Web SDK reads the current page URL and sends it as the XDM field `web.webPageDetails.URL`. This field is forwarded to Adobe Analytics and it automatically populates the Page URL reports in Adobe Analytics.

If you implement Web SDK for Adobe Analytics with an XDM schema, as you have in this tutorial, some of the XDM fields you have custom-implemented auto-map to Analytics variables, as outlined in this table:

|XDM to Analytics auto-mapped variables|Adobe Analytics variable|
|-------|---------|
|`identitymap.ecid.[0].id`| mid|
|`web.webPageDetails.name`|s.pageName|
|`web.webPageDetails.server`|s.server|
|`web.webPageDetails.siteSection`|s.channel|
|`commerce.productViews.value`|prodView|
|`commerce.productListViews.value`|scView|
|`commerce.checkouts.value`|scCheckout|
|`commerce.purchases.value`|purchase|
|`commerce.order.currencyCode`|s.currencyCode|
|`commerce.order.purchaseID`|s.purchaseID|
|`productListItems[].SKU`|s.products=;product name;;;; (primary - see Note below)|
|`productListItems[].name`|s.products=;product name;;;; (fallback - see Note below)|
|`productListItems[].quantity`|s.products=;;product quantity;;;|
|`productListItems[].priceTotal`|s.product=;;;product price;;|

The individual sections of the Analytics product string are set through different XDM variables under the `productListItems` object.

>[!NOTE]
>
>As of August 18, 2022, `productListItems[].SKU` takes priority for mapping to the product name in the s.products variable. 
>The value set to `productListItems[].name` is mapped to the product name only if `productListItems[].SKU` does not exist. Otherwise, it is unmapped and available in context data. 
>Do not set an empty string or null to `productListItems[].SKU`. This has the undesired effect of mapping to the product name in the s.products variable.


### Set variables in the data object

But what about evars, props, and events? Setting variables in the `data` object is the recommended way to set these Analytics variables with Web SDK. Setting variables in the data object can also overwrite any of the automatically-mapped variables.

First of all, what is the `data` object? In any Web SDK event you can send two objects with custom data, the `xdm` object and the `data` object. Both are sent to Platform Edge Network, but only the `xdm` object is sent to the Experience Platform dataset. Properties in the `data` object can be mapped on the Edge to `xdm` fields using the Data Prep for Data Collection feature, but otherwise are not sent to Experience Platform. This makes it an ideal way to send data to applications like Analytics, which aren't natively built on Experience Platform.

Here are the two objects in a generic Web SDK call:

![data and xdm objects](assets/analytics-data-object-intro.png)

Adobe Analytics is configured to look for any properties in the `data.__adobe.analytics` object and use them for Analytics variables.

Now let's see how this works. Let's set `eVar1` and `prop1` with our page name and see how XDM-mapped value can be overwritten

1. Open the tag rule `all pages - library loaded - set global variables - 1`
1. Add a new **[!UICONTROL Action]**
1. Select **[!UICONTROL Adobe Experience Platform Web SDK]** extension
1. Select **[!UICONTROL Action Type]** as **[!UICONTROL Update variable]**
1. Select `data.variable` as the **[!UICONTROL Data element]**
1. Select the **[!UICONTROL analytics]** object
1. Set `eVar1` as the `page.pageInfo.pageName` data element
1. Set `prop1` to copy the value of `eVar1`
1. To test the overwriting of XDM-mapped values, in the **[!UICONTROL Additional property]** section set the Page name as a static value `test`
1. Save the rule


Now, we need to include the data object in our send event rule.

1. Open the tag rule `all pages - library loaded - send event - 50`
1. Open the **[!UICONTROL Send Event]** action
1. Select `data.variable` as the **[!UICONTROL Data]**
1. Select **[!UICONTROL Keep Changes]**
1. Select **[!UICONTROL Save]**



 <!--


### Map to Analytics variables with processing rules

All fields in the XDM schema become available to Adobe Analytics as Context Data Variables with the following prefix `a.x.`. For example, `a.x.web.webinteraction.region`

In this exercise, you map one XDM variable to a prop. Follow these same steps for any custom mapping that you must do for any `eVar`, `prop`, `event`, or variable accessible via Processing Rules.

1. Go to the Analytics interface
1. Go to [!UICONTROL Admin] > [!UICONTROL Admin Tools] > [!UICONTROL Report Suites ]
1. Select the dev/test report suite that you are using for the tutorial > [!UICONTROL Edit Settings] > [!UICONTROL General] > [!UICONTROL Processing Rules]

    ![Analytics Purchase](assets/analytics-process-rules.png)   

1. Create a rule to **[!UICONTROL Overwrite value of]** `[!UICONTROL Product SKU (prop1)]` to `a.x.productlistitems.0.sku`. Remember to add a note about why you are creating the rule and name your rule title. Select **[!UICONTROL Save]**

    ![Analytics Purchase](assets/analytics-set-processing-rule.png)   

    >[!IMPORTANT]
    >
    >The first time you map to a processing rule, the UI does not show you the context data variables from the XDM object. To fix that select any value, Save, and come back to edit. All XDM variables should now appear.

### Map to Analytics variables using the Adobe Analytics field group

An alternative to processing rules is to map to Analytics variables in the XDM schema using the `Adobe Analytics ExperienceEvent Template` field group. This approach has gained popularity because many users find it simpler than configuring processing rules, however, by increasing the size of the XDM payload it could in turn increase the profile size in other applications like Real-Time CDP.

To add the `Adobe Analytics ExperienceEvent Template` field group to your schema:

1. Open the [Data Collection](https://experience.adobe.com/#/data-collection){target="blank"} interface
1. Select **[!UICONTROL Schemas]** from the left navigation
1. Make sure you are in the sandbox you are using from the tutorial
1. Open your `Luma Web Event Data` schema
1. In the **[!UICONTROL Field Groups]** section, select **[!UICONTROL Add]**
1. Find the `Adobe Analytics ExperienceEvent Template` field group and add it to your schema


Now, set a merchandising eVar in the product string. With the `Adobe Analytics ExperienceEvent Template` field group, you are able to map variables to merchandising eVars or events within the product string. This is also known as setting **Product Syntax Merchandising**. 

1. Go back to your tag property

1. Open the rule `ecommerce - library loaded - set product details variables - 20`

1. Open the **[!UICONTROL Set Variable]** action

1. Select to open `_experience > analytics > customDimensions > eVars > eVar1`

1. Set the **[!UICONTROL Value]** to `%product.productInfo.title%`

1. Select **[!UICONTROL Keep Changes]**

    ![Product SKU XDM object Variable](assets/set-up-analytics-product-merchandising.png)

1. Select **[!UICONTROL Save]** to save the rule

As you just saw, basically all of the Analytics variables can be set in the `Adobe Analytics ExperienceEvent Template` field group.

>[!NOTE]
>
> Notice the `_experience` object under `productListItems` > `Item 1`. Setting any variable under this [!UICONTROL object] sets Product Syntax eVars or Events.

-->

## Send data to a different report suite

You might want to change which Adobe Analytics report suite data is sent to when visitors are on certain pages. This requires a configuration in both the datastream and a rule.

### Configure the datastream for a report suite override

To configure the Adobe Analytics report suite override setting in the datastream:

1. Open your datastream
1. Edit the **[!UICONTROL Adobe Analytics]** configuration by opening the ![more](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) menu and then selecting **[!UICONTROL Edit]** 

   ![Overwrite the datastream](assets/datastream-edit-analytics.png)

1. Select **[!UICONTROL Advanced Options]** to open **[!UICONTROL Report Suite Overrides]**

1. Select the report suites that you would like to override. In this case, `Web SDK Course Dev` and `Web SDK Course Stg`

1. Select **[!UICONTROL Save]**

   ![Overwrite the datastream](assets/analytics-datastreams-edit-adobe-analytics-configurations-report-suites.png)


### Configure a rule for a report suite override

Let's create a rule to send an additional page view call to a different report suite. Use the datastream override feature to change the report suite for a page using the **[!UICONTROL Send Event]** Action.

1. Create a new rule, name it `homepage - library loaded - AA report suite override - 51`

1. Select the plus sign under **[!UICONTROL Event]** to add a new trigger

1. Under **[!UICONTROL Extension]**, select **[!UICONTROL Core]**

1. Under **[!UICONTROL Event Type]**, select **[!UICONTROL Library Loaded (Page Top)]**

1. Select to open **[!UICONTROL Advanced Options]**, type in `51`. This ensures the rule runs after the `all pages - library loaded - send event - 50` that sets the baseline XDM with the **[!UICONTROL Update variable]** action type.
1. Select **[!UICONTROL Keep Changes]**

    ![Analytics Report Suite Override](assets/set-up-analytics-rs-override.png)

1. Under **[!UICONTROL Conditions]**, select to **[!UICONTROL Add]**

1. Leave **[!UICONTROL Logic Type]** as **[!UICONTROL Regular]**

1. Leave **[!UICONTROL Extensions]** as **[!UICONTROL Core]**

1. Select **[!UICONTROL Condition Type]** as **[!UICONTROL Path Without Query String]**

1. On the right, leave the **[!UICONTROL Regex]** toggle disabled

1. Under **[!UICONTROL path equals]** set `/content/luma/us/en.html`. For the Luma demo site, it ensures the rule only triggers on the home page

1. Select **[!UICONTROL Keep Changes]**

    ![Analytics report suite override condition](assets/set-up-analytics-override-condition.png)

1. Under **[!UICONTROL Actions]** select **[!UICONTROL Add]**

1. As the **[!UICONTROL Extension]**, select **[!UICONTROL Adobe Experience Platform Web SDK]** 

1. As the **[!UICONTROL Action Type]**, select **[!UICONTROL Send Event]** 

1. As the **[!UICONTROL XDM data]**, select the `xdm.variable.content` data element you created in the [Create data elements](create-data-elements.md) lesson

1. As the **[!UICONTROL Data]**, select the `data.variable` data element you created in the [Create data elements](create-data-elements.md) lesson

    ![Analytics datastream override](assets/set-up-analytics-datastream-override-1.png)

1. Scroll down to the **[!UICONTROL Datastream Configurations Overrides]** section

1. Leave the **[!UICONTROL Development]** tab selected. 

    >[!TIP]
    >
    >    This tab determines in which tags environment the override occurs. For this excerise, you only specify the Development environment but when you deploy this to production remember to also do it in the **[!UICONTROL Production]** environment.

1. Select the **[!UICONTROL Sandbox]** you are using for the tutorial
1. Select the **[!UICONTROL Datastream]**, in this case `Luma Web SDK: Development Environment`

1. Under **[!UICONTROL Report suites]**, select the report site you would like to use to override for. In this case, `tmd-websdk-course-stg`. 

1. Select **[!UICONTROL Keep Changes]** 

1. And **[!UICONTROL Save]** your rule 

    ![Analytics datastream override](assets/analytics-tags-report-suite-override.png)


## Build your Development environment

Add your updated rules to your `Luma Web SDK Tutorial` tag library and rebuild your development environment. 

Congratulations! The next step is to validate your Adobe Analytics Implementation via Experience Platform Web SDK.

## Validate Adobe Analytics with Debugger

Learn how to validate that Adobe Analytics is capturing the ECID, page views, the product string, and e-commerce events with the Edge Trace feature of the Experience Platform Debugger.

In the [Debugger](validate-with-debugger.md) lesson, you learned how to inspect the client-side XDM request with the Platform Debugger and browser developer console, which is similar to how you debug an `AppMeasurement.js` Analytics implementation. You also learned about validating Platform Edge Network server-side requests sent to Adobe applications, and how to view a fully processed payload using Assurance. 

To validate Analytics is capturing data properly through Experience Platform Web SDK, you must go two steps further to:

1. Validate how data is processed by the XDM object on the Platform Edge Network, using Experience Platform Debugger's Edge Trace feature
1. Validate how data is fully processed by Analytics using Adobe Experience Platform Assurance

### Experience Cloud ID validation

1. Go to the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"}
1. Select the login button on the top right, and use credentials u: test@test.com p: test to authenticate 
1. Open the Experience Platform Debugger and [switch the tag property on the site to your own development property](validate-with-debugger.md#use-the-experience-platform-debugger-to-map-to-your-tags-property)


1. To enable the Edge Trace, go to Experience Platform Debugger, in the left navigation select **[!UICONTROL Logs]**, then select the **[!UICONTROL Edge]** tab, and select **[!UICONTROL Connect]**

    ![Connect Edge Trace](assets/analytics-debugger-edgeTrace.png)

1. It will be empty for now

    ![Connected Edge Trace](assets/analytics-debugger-edge-connected.png)    

1. Refresh the Luma page and check Experience Platform Debugger again, you should see data come through. The row starting with **[!UICONTROL Analytics Automatic Mapping]** is the Adobe Analytics beacon
1. Select to open both the `[!UICONTROL mappedQueryParams]` dropdown and the second dropdown to view Analytics variables

    ![Analytics beacon Edge Trace](assets/analytics-debugger-edge-analytics.png)    

    >[!TIP]
    >
    >The second dropdown corresponds to the Analytics report suite ID you are sending data to. It should match your own report suite, not the one in the screenshot.

1. Scroll down to find `[!UICONTROL c.a.x.identitymap.ecid.[0].id]`. It is a Context Data Variable that captures ECID
1. Keep scrolling down until you see the Analytics `[!UICONTROL mid]` variable. Both IDs match with your device's Experience Cloud ID.
1. On the Luma site:

    ![Analytics ECID](assets/analytics-debugger-ecid.png)    

    >[!NOTE]
    >
    >Since you are logged in, take a moment to validate the authenticated ID `b642b4217b34b1e8d3bd915fc65c4452` for the user **`test@test.com`** is captured as well in the `[!UICONTROL c.a.x.identitymap.lumacrmid.[0].id]`

### Report suite override validation

Above you configured a datastream override for the [Luma homepage](https://luma.enablementadobe.com/content/luma/us/en.html).  To validate this configuration  

1. Look for a row with **[!UICONTROL Datastream config after override was applied]**. Here you find the primary report suite and the additional report suite(s) that were configured for the report suite overrides.

    ![Analytics Report Suite Override List Validation](assets/aep-debugger-datastream-override.png)  
     
1. Scroll down to the row starting with **[!UICONTROL Analytics Automatic Mapping]**  and verify that the `[!UICONTROL reportSuiteIds]` shows the report suite you specified in your override configurations 

    ![Analytics Report Suite Override Call Validation](assets/aep-debugger-analytics-report-suite-override.png)

### Content page views validation

Go to a product page like the [Didi Sport Watch product page](https://luma.enablementadobe.com/content/luma/us/en/products/gear/watches/didi-sport-watch.html#24-WG02).  Validate that content page views are captured by Analytics. 

1. Look for `[!UICONTROL c.a.x.web.webpagedetails.pageviews.value]=1`. 
1. Scroll down to see the `[!UICONTROL gn]` variable. It is the Analytics dynamic syntax for the `[!UICONTROL s.pageName]` variable. It captures the page name from the data layer.

    >[!NOTE]
    >
    > The `gn` value might be `test` if you overwrote the `xdm` object with the `data` object in the earlier exercise.

    ![Analytics product string](assets/analytics-debugger-edge-page-view.png)  

### Product string and e-commerce events validation

Since you are already on a product page, this exercise continues to use the same Edge Trace to validate product data is captured by Analytics. Both the product string and e-commerce events are automatically mapped XDM variables to Analytics. As long as you have mapped to the proper `productListItem` XDM variable while [configuring an XDM schema for Adobe Analytics](setup-analytics.md#configure-an-xdm-schema-for-adobe-analytics), the Platform Edge Network takes care of mapping the data to the proper analytics variables. 

**First validate that the `Product String` is set**

1. Look for `[!UICONTROL c.a.x.productlistitems.][0].[!UICONTROL sku]`. The variable captures the data element value you mapped to the `productListItems.item1.sku` earlier in this lesson
1. Also look for `[!UICONTROL c.a.x.productlistitems.][0].[!UICONTROL _experience.analytics.customdimensions.evars.evar1]`. The variable captures the data element value you mapped to `productListItems.item1._experience.analytics.customdimensions.evars.evar1` 
1. Scroll down to see the `[!UICONTROL pl]` variable. It is the dynamic syntax of the Analytics product string variable
1. Note that product name from the data layer is mapped both to the `[!UICONTROL c.a.x.productlistitems.][0].[!UICONTROL sku]` and the `[!UICONTROL product]` parameter of the products string.  In addition, the product title from the data layer is mapped to merchandising evar1 in the products string. 

    ![Analytics product string](assets/analytics-debugger-prodstring.png)    

    The Edge Trace treats `commerce` events slightly differently than `productList` dimensions. You do not see a Context Data Variable mapped the same way you see the product name mapped to `[!UICONTROL c.a.x.productlistitem.[0].name]` above. Instead, the Edge Trace shows  the final event auto-mapping in the Analytics `event` variable. Platform Edge Network maps it accordingly as long as you map to the proper XDM `commerce` variable while [configuring the schema for Adobe Analytics](setup-analytics.md#configure-an-xdm-schema-for-adobe-analytics); in this case the `commerce.productViews.value=1`. 

1. Back on the Experience Platform Debugger window, scroll down to the `[!UICONTROL events]` variable, it is set to `[!UICONTROL prodView]`

1. Also note `[!UICONTROL c.a.x.eventType]` is set to `commerce.productViews` since you are on a product page.

    >[!TIP]
    >
    > The `ecommerce - library loaded - set product details variables - 20` rule is overwriting the value of `eventType` set by the `all pages - library loaded - set global variables - 1` rule as it is set to trigger later in the sequence


    ![Analytics Product View](assets/analytics-debugger-prodView.png) 

**Validate the rest of e-commerce events and product strings are set for Analytics**

1. Add [Didi Sport Watch](https://luma.enablementadobe.com/content/luma/us/en/products/gear/watches/didi-sport-watch.html#24-WG02) to cart
1. Go to the [Cart Page](https://luma.enablementadobe.com/content/luma/us/en/user/cart.html), check Edge Trace for 

    * `eventType` set to `commerce.productListViews`
    * `[!UICONTROL events: "scView"]`, and
    * the product string is set

    ![Analytics Cart View](assets/analytics-debugger-cartView.png) 

1. Proceed to checkout, check Edge Trace for

    * `eventType` set to `commerce.checkouts`
    * `[!UICONTROL events: "scCheckout"]`, and
    * the product string is set    

    ![Analytics Checkout](assets/analytics-debugger-checkout.png) 

1. Fill out just the **First Name** and **Last Name** fields on the shipping form and select **Continue**. On the next page, select **Place Order**
1. On confirmation page, check Edge Trace for

    * `eventType` set to `commerce.purchases`
    * Purchase event being set `[!UICONTROL events: "purchase"]`
    * Currency Code variable being set `[!UICONTROL cc: "USD"]`
    * Purchase ID being set in `[!UICONTROL pi]`
    * Product string `[!UICONTROL pl]` setting the product name, quantity, and price

    ![Analytics Purchase](assets/analytics-debugger-purchase.png)   



## Validate Adobe Analytics using Assurance

Adobe Experience Platform Assurance helps you inspect, proof, simulate, and validate how you collect data or serve experiences with your website and mobile application.  

In the previous exercise you validated that Adobe Analytics is capturing the ECID, page views, the product string, and e-commerce events with the Edge Trace feature of the Experience Platform Debugger.  Next you validate those same events using Adobe Experience Platform Assurance, an alternative interface to access the same data in Edge Trace.

As you learned in the [Assurance](validate-with-assurance.md) lesson, there are several ways to initiate an Assurance session. Since you already have Adobe Experience Platform Debugger open with an Edge Trace session initiated from the last exercise, we recommend accessing Assurance through the Debugger:
    ![Assurance through Adobe Experience Platform Data Collection](assets/assurance-open-aep-debugger.png)

Within the **[!UICONTROL "Web SDK Tutorial 3"]** Assurance Session enter **[!UICONTROL "hitdebugger"]** into the Events Search Bar to filter the results to the Adobe Analytics Post Processed data. 
    ![Assurance Adobe Analyitcs Post Processed Data](assets/assurance-hitdebugger.png)

### Experience Cloud ID validation

To validate Adobe Analytics is capturing the ECID, select a beacon and open the Payload.  The Vendor for this beacon should be **[!UICONTROL com.adobe.analytics.hitdebugger]**
    ![Adobe Analytics validation with Assurance](assets/assurance-hitdebugger-payload.png)

Then scroll down to **[!UICONTROL mcvisId]** to validate that the ECID is correctly captured
    ![Experience Cloud ID validation with Assurance](assets/assurance-hitdebugger-mcvisId.png)

### Content page views validation

Using the same beacon, validate that content page views are mapped to the correct Adobe Analytics variable.
Scroll down to **[!UICONTROL pageName]** to validate that the `Page Name` is correctly captured:


    >[!NOTE]
    >
    > The `pageName` value might be `test` if you overwrote the `xdm` object with the `data` object in the earlier exercise.

    ![Page name validation with Assurance](assets/assurance-hitdebugger-content-pagename.png)

### Product string and e-commerce events validation

Following the same validation use cases used when validating with the Experience Platform Debugger above, continue using the same beacon to validate the `Ecommerce Events` and the `Product String`. 

1. Look for payload where the **[!UICONTROL events]** contain `prodView`
    ![Product String validation with Assurance](assets/assurance-hitdebugger-prodView-event.png)
1. Scroll down to **[!UICONTROL product-string]** to validate the `Product String`.  
    * Note the `Product SKU` and `Merchandizing eVar1`.
1. Scroll down further and validate that `prop1`, which you configured using processing rules in the previous section, contains the `Product SKU`   
    ![Product String with Merchandizing Variables validation with Assurance](assets/assurance-hitdebugger-prodView-productString-merchVar.png)

Continue to validate your implementation by reviewing the cart, checkout, and purchase events.

1. Look for payload where the **[!UICONTROL events]** contain `scView` and validate the product string.
    ![Product String validation with Assurance](assets/assurance-hitdebugger-scView-event.png)
1. Look for payload where the **[!UICONTROL events]** contain `scCheckout` and validate the product string.
    ![Product String validation with Assurance](assets/assurance-hitdebugger-scView-event.png)
1. Look for payload where the **[!UICONTROL events]** contain `purchase` 
    ![Product String validation with Assurance](assets/assurance-hitdebugger-purchase-event.png)
1. When validating the `purchase` event, note that the `Product String` should contain the `Product SKU`, `Product Quantity` , and `Product Total Price`.  
1. In addition, for the `purchase` validate that the `purchase-id` and/or `purchaseId` are set       
 

Congratulations! You did it! This is the end of the lesson and now you are ready to implement Adobe Analytics with Platform Web SDK for your own website.

[Next: **Add Adobe Audience Manager**](setup-audience-manager.md)

>[!NOTE]
>
>Thank you for investing your time in learning about Adobe Experience Platform Web SDK. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
