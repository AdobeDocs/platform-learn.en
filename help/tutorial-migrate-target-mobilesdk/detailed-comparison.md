---
title: Comparison of the Target extension to the Decisioning extension
description: Learn about the differences between Target extension to the Decisioning extension including features, functions, settings, and data flow.
---
# Comparison of the Target extension to the Decisioning extension

The Adobe Journey Optimizer - Decisioning extension differs from the Adobe Target extension for mobile apps. The following tables are a reference to help you evaluate areas of your implementation you may need to focus on during the migration process. 

After reviewing the information below and assessing your current technical Target extension implementation, you should be able to understand the following:

- Which Target features are supported by Adobe Journey Optimizer - Decisioning
- Which Adobe Target extension functions have Adobe Journey Optimizer - Decisioning equivalents
- How Target settings are applied with Adobe Journey Optimizer - Decisioning
- How the data flow of the Adobe Target extension and the Adobe Journey Optimizer - Decisioning extension differ 

If you are new to Platform Web SDK, don't worry - the items below are covered in more detail throughout this tutorial.

## Feature comparison

| Feature | Target extension | Decisioning extension (Target via Edge) | 
|---|---|---|
| Prefetch mode | Supported | Supported | 
| Execute mode | Supported | Not supported |  
| Custom parameters | Supported | Per mbox parameters are not supported | 
| Entry audiences | Supported | Supported | 
| Audience segmentation using mobile Lifecycle metrics | Supported | Supported via Data Collection rules | 
| thirdPartyId (mbox3rdPartyId) | Supported via Identity Map and namespace configuration in the datastream | 
| Notifications (display, click) | Supported | Supported | 
| Response tokens | Supported | Supported |  
| Dynamic offers | Supported | Supported | 
| Analytics for Target (A4T) | Client-side only | Client-side and server-side | 
| Mobile previews (QA mode) | Supported | Limited Support | 



## Noteworthy callouts

>[!NOTE]
>
>Migrating Target to Platform Web SDK while retaining an existing AppMeasurement Adobe Analytics implementation for a given page is not supported.
>
> It is possible to migrate your at.js (and AppMeasurement.js) implementation to Platform Web SDK one page at a time. If you take this approach, it is best to set the [`idMigrationEnabled`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#id-migration-enabled) and [`targetMigrationEnabled`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#targetMigrationEnabled) options to `true` with the `configure` command.

## Target extension functions and Decisioning extension equivalents

Many Target extension functions have an equivalent approach using the Decisioning extension outlined in the table below. For more details about the [functions](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/atjs-functions/), refer to the Adobe Target Developer Guide.

| Target extension | Decisioning extension | 
| --- | --- | 
| |  | 

## Target extension settings and Decisioning extension equivalents

The Target extension can be configured and downloaded with various settings in the ...

| Target extension | Decisioning extension | 
| --- | --- | 
| |  | 


## System diagram comparison

The following diagrams should help you understand the data flow differences between a Target implementation using the Adobe Journey Optimizer - Decisioning extension and an implementation using the Adobe Target extension.

### Target extension system diagram



### Decisioning extension system diagram




>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Decisioning extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
