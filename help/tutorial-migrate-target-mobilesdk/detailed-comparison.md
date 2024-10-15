---
title: Comparison of the Target extension to the Optimize extension
description: Learn about the differences between at.js 2.x and Platform Web SDK including features, functions, settings, and data flow.
---
# Comparison of the Target extension to the Optimize extension

The standalone Adobe Target at.js library differs significantly from Platform Web SDK. The following tables are a reference to help you evaluate areas of your implementation you may need to focus on during the migration process. 

After reviewing the information below and assessing your current technical at.js implementation, you should be able to understand the following:

- Which Target features are supported by Platform Web SDK
- Which at.js functions have Platform Web SDK equivalents
- How Target settings are applied with Platform Web SDK
- How the data flow of at.js and Platform Web SDK differ 

If you are new to Platform Web SDK, don't worry - the items below are covered in more detail throughout this tutorial.

## Feature comparison

| | Target extension | Optimize extension (Target via Edge) | AJO Code-based Experiences (Messaging SDK) |
|---|---|---|---|
| Prefetch mode | Supported | Supported | Supported |
| Execute mode | Supported | Not supported | Not supported | 
| Custom parameters | Supported | Per mbox parameters are not supported | Not Supported | 
| Entry audiences | Supported | Supported | Supported via Campaign audience and experiment holdout setting | 
| Audience segmentation using mobile Lifecycle metrics | Supported | Supported via Data Collection rules | Experience targeting is not supported currently |
| thirdPartyId (mbox3rdPartyId) | Supported via Identity Map and namespace configuration in the datastream | Not supported | 
| Notifications (display, click) | Supported | Supported | Supported | 
| Response tokens | Supported | Supported |  No equivalent for returning Campaign specific metadata outside of content | 
| Dynamic offers | Supported | Supported | Profile and decision item related token rendering in content is supported |
| Analytics for Target (A4T) | Client-side only | Client-side and server-side |  Not Supported |
| Mobile previews (QA mode) | Supported | Limited Support | In Progress | 



## Noteworthy callouts

>[!NOTE]
>
>Migrating Target to Platform Web SDK while retaining an existing AppMeasurement Adobe Analytics implementation for a given page is not supported.
>
> It is possible to migrate your at.js (and AppMeasurement.js) implementation to Platform Web SDK one page at a time. If you take this approach, it is best to set the [`idMigrationEnabled`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#id-migration-enabled) and [`targetMigrationEnabled`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#targetMigrationEnabled) options to `true` with the `configure` command.

## Target extension functions and Optimize extension equivalents

Many Target extension functions have an equivalent approach using the Optimize extension outlined in the table below. For more details about the [functions](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/atjs-functions/), refer to the Adobe Target Developer Guide.

| Target extension | Optimize extension | 
| --- | --- | 
| |  | 

## Target extension settings and Optimize extension equivalents

The Target extension can be configured and downloaded with various settings in the ...

| Target extension | Optimize extension | 
| --- | --- | 
| |  | 


## System diagram comparison

The following diagrams should help you understand the data flow differences between a Target implementation using at.js and an implementation using the Platform Web SDK.

### Target extension system diagram



### Optimize extensionsystem diagram




>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Optimize extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
