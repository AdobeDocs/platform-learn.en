---
title: Update audiences and profile scripts - Migrate Target from at.js 2.x to Web SDK
description: Learn how to update Adobe Target audiences and profile scripts for compatibility with Experience Platform Web SDK.
exl-id: 2c0f85f7-6e8c-4d0b-8ed5-53897d06e563
TQID: https://experienceleague.adobe.com/sta3FtxkTh-z0BvrRuJOc2JztEBVh8l4y2kwNF-aNG8
product_v2:
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
    internal-label: Target
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: adee20bd-51f4-461d-b9db-d215f8756eeb
    internal-label: Audiences
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
    internal-label: Implementation
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: b572b7ff-a413-4173-b2b4-d7d3874f1b9b
    internal-label: Best practices
  - id: fd0ff162-b6d3-4a11-8aeb-e165a01c0f0a
    internal-label: at.js
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# Update Target audiences and profile scripts for Platform Web SDK compatibility

After you complete the technical updates to migrate Target to the Platform Web SDK, you may need to update some of your audiences, profile scripts, and activities to ensure a smooth transition. 

All Target mbox parameters must be passed in XDM format with a Platform Web SDK implementation. Before publishing your changes to production, you should:

* Update audiences that use mbox parameters
* Update profile scripts that use mbox parameters
* Update any offers and activities use mbox parameter token replacement (for example, `${mbox.parameter_name}`)

## Adjust audiences

Any audiences that use custom mbox parameters should be updated to use the new XDM parameter names. For example, a custom parameter for `page_name` would likely be mapped to `web.webpagedetails.pageName`.

One approach to ensure compatibility with both at.js and Platform Web SDK is to update any relevant audiences so that `OR` conditions are used, as shown below:

![How to view update a Target audience for Platform Web SDK compatibility](assets/target-audience-update.png){zoomable="yes"}

## Edit profile scripts
 
Profile scripts should be updated to reference new XDM parameter names, similar to audiences. Aside from the change of mbox parameter names, there is no difference in the way profile scripts work between an at.js and a Platform Web SDK implementation.

One approach to ensure that compatibility is to use `OR` conditions in your profile script code.

Example profile script: 

```Javascript
if(mbox.param('pageName') == 'Product Details'){
  return true
}
```

Updated profile script for Platform Web SDK compatibility:

```Javascript
if((mbox.param('pageName') == 'Product Details') || (mbox.param('web.webPageDetails.pageName') =='Product Details')){
  return true
}
```

For more information and best practices, refer to the dedicated documentation about [profile scripts](https://experienceleague.adobe.com/docs/target/using/audiences/visitor-profiles/profile-parameters.html). 

## Update parameter tokens for dynamic content

If you have any offers, recommendations designs, or activities that use [dynamic content replacement](https://experienceleague.adobe.com/docs/target/using/experiences/offers/passing-profile-attributes-to-the-html-offer.html), they may need to be updated accordingly to account for the new XDM parameter names.

Depending on how you are using token replacement for mbox parameters, you may be able to enhance your existing setup to account for both old and new parameter names. However, in situations where custom JavaScript code is not possible, such as in JSON offers, you should create copies and make updates after the migration is complete and live on your production site.

Example JSON offer:

```JSON
{
  "pageName" : "${mbox.page_name}",
  "layoutVariation" : "grid"
}
```

Example JSON offer using Platform Web SDK parameter names:

```JSON
{
  "pageName" : "${mbox.web.webPagedDetails.pageName}",
  "layoutVariation" : "grid"
}
```

If you choose to make adjustments after the migration to account for the new XDM mbox parameter names, be sure to pause any impacted activities during the migration event to prevent activity display errors to visitors.

Next, learn how to [validate the Target implementation](validate.md).

>[!NOTE]
>
>We are committed to helping you be successful with your Target migration from at.js to Web SDK. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
