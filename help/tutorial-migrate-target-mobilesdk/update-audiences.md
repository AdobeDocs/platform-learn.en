---
title: Update Target audiences and profile scripts - Migrate the Adobe Target implementation in your mobile app to the Offer Decisioning and Target extension
description: Learn how to update Adobe Target audiences and profile scripts for compatibility with the Offer Decisioning and Target extension.
exl-id: de3ce2c7-0066-496a-a8a7-994d7ce3d92c
TQID: https://experienceleague.adobe.com/-JtifHi6P3KTQS9gnWiS1o0IxOYHTada4m-gzJtVGiQ
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
  - id: d051910f-2bda-47ea-a969-6ade9fcd71f1
    internal-label: Implement mobile
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
# Update Target audiences and profile scripts for Decisioning mobile extension compatibility


After you complete the technical updates to migrate Target to the Offer Decisioning and Target extension, you may need to update some of your audiences, profile scripts, and activities to ensure a smooth transition. 

>[!INFO]
>
>If you migrate all of your mbox parameters to the `data.__adobe.target` object, you will not need to update your audiences, profile scripts, and activities as shown below.


If you migrate mbox paramters to the `xdm` object, before publishing your changes to production, you should:

* Update audiences that use mbox parameters
* Update profile scripts that use mbox parameters
* Update any offers and activities use mbox parameter token replacement (for example, `${mbox.parameter_name}`)

## Adjust audiences

If you migrate mbox paramters to the `xdm` object, audiences that use custom mbox parameters should be updated to use the new XDM parameter names. For example, a custom parameter for `page_name` would likely be mapped to `web.webpagedetails.pageName`.

One approach to ensure compatibility with both the Target extension and the Offer Decisioning and Target extension is to update any relevant audiences so that `OR` conditions are used, as shown below:

![How to view update a Target audience for Offer Decisioning and Target extension compatibility](assets/target-audience-update.png){zoomable="yes"}

## Edit profile scripts
 
If you migrate mbox paramters to the `xdm` object, profile scripts should be updated to reference the new XDM parameter names, similar to audiences. Aside from the change of mbox parameter names, there is no difference in the way profile scripts work between a Target and Decisioning implementation.

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

For more information and best practices, refer to the dedicated documentation about [profile scripts](https://experienceleague.adobe.com/en/docs/target/using/audiences/visitor-profiles/profile-parameters). 

## Update parameter tokens for dynamic content

If you migrate mbox paramters to the `xdm` object, and if you have any offers, recommendations designs, or activities that use [dynamic content replacement](https://experienceleague.adobe.com/en/docs/target/using/experiences/offers/passing-profile-attributes-to-the-html-offer), they may need to be updated accordingly to account for the new XDM parameter names.

Depending on how you are using token replacement for mbox parameters, you may be able to enhance your existing setup to account for both old and new parameter names. However, in situations where custom JavaScript code is not possible, such as in JSON offers, you should create copies and make updates after the migration is complete and live on your production site.

Example JSON offer:

```JSON
{
  "pageName" : "${mbox.page_name}",
  "layoutVariation" : "grid"
}
```

Example JSON offer using XDM object parameter names:

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
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Offer Decisioning and Target extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
