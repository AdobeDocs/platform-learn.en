---
title: Comparison of the Target extension to the Decisioning extension
description: Learn about the differences between Target extension to the Decisioning extension including features, functions, settings, and data flow.
exl-id: 6c854049-4126-45cf-8b2b-683cf29549f3
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
| Custom parameters | Supported | Supported* | 
| Profile parameters | Supported | Supported* | 
| Entity parameters | Supported | Supported* | 
| Target audiences | Supported | Supported | 
| Real-Time CDP audiences | ??? | Supported | 
| Real-Time CDP attributes | ??? | Supported | 
| Lifecycle metrics | Supported | Supported via Data Collection rules | 
| thirdPartyId (mbox3rdPartyId) | Supported | Supported via Identity Map and Target Third Party ID Namespace in the datastream | 
| Notifications (display, click) | Supported | Supported | 
| Response tokens | Supported | Supported |  
| Analytics for Target (A4T) | Client-side only | Client-side and server-side | 
| Mobile previews (QA mode) | Supported | Limited Support with Assurance | 

>[!IMPORTANT]
>
> \* Parameters sent in a request apply to all scopes in the request. If you need to set different parameters for different scopes you must make additional requests.



## Noteworthy callouts

>[!NOTE]
>
>Migrating Target to Platform Web SDK while retaining an existing AppMeasurement Adobe Analytics implementation for a given page is not supported.
>
> It is possible to migrate your at.js (and AppMeasurement.js) implementation to Platform Web SDK one page at a time. If you take this approach, it is best to set the [`idMigrationEnabled`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#id-migration-enabled) and [`targetMigrationEnabled`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#targetMigrationEnabled) options to `true` with the `configure` command.

## Target extension functions and Decisioning extension equivalents

Many Target extension functions have an equivalent approach using the Decisioning extension outlined in the table below. For more details about the [functions](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/atjs-functions/), refer to the Adobe Target Developer Guide.

| Target extension | Decisioning extension | Notes |
| --- | --- | --- | 
| `prefetchContent` | `updatePropositions` |  | 
| `retrieveLocationContent` | `getPropositions` | When using `getPropositions` API, no remote call is made to fetch non-cached scopes in the SDK.  | 
| `displayedLocations` | Offer -> `displayed()` |     In addition, `generateDisplayInteractionXdm` Offer method can be used to generate the XDM for item display. Subsequently, Edge network SDK's sendEvent API can be used to attach additional XDM, free-form data and send an Experience Event to the remote. | 
| `clickedLocation` | Offer -> `tapped()` | In addition, `generateTapInteractionXdm` Offer method can be used to generate the XDM for item tap. Subsequently, Edge network SDK's sendEvent API can be used to attach additional XDM, free-form data and send an Experience Event to the remote. | 
| `clearPrefetchCache` | `clearCachedPropositions` |  | 
| `resetExperience` | n/a | Use `removeIdentity` API from Identity for Edge Network extension for the SDK to stop sending the visitor identifier to the Edge network. For more details, see [the removeIdentity API documentation](https://developer.adobe.com/client-sdks/edge/identity-for-edge-network/api-reference/#removeidentity). <br><br>Note: Mobile Core's `resetIdentities` API clears all stored identities in the SDK, including the Experience Cloud ID (ECID) and it should be sparingly used! | 
| `getSessionId` | n/a | `state:store` response handle carries session-related information. Edge network extension helps manage it by attaching non-expired state store items to subsequent requests. | 
| `setSessionId` | n/a | `state:store` response handle carries session-related information. Edge network extension helps manage it by attaching non-expired state store items to subsequent requests. | 
| `getThirdPartyId`  |  n/a | Use updateIdentities API from Identity for Edge Network extension to supply the third party ID value. Then, configure the third party ID namespace in the datastream. For more details, see [the Target Third Party Id mobile documentation](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id).  |
| `setThirdPartyId` | n/a | Use updateIdentities API from Identity for Edge Network extension to supply the third party ID value. Then, configure the third party ID namespace in the datastream. For more details, see [the Target Third Party Id mobile documentation](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id). | 
| `getTntId` | n/a | `locationHint:result` response handle carries the Target location hint information. It is assumed Target edge will be co-located with Experience Edge. <br> <br>Edge network extension uses the EdgeNetwork location hint to determine the Edge network cluster to send requests to. To share Edge network location hint across SDKs (hybrid apps), use `getLocationHint` and `setLocationHint` APIs from Edge Network extension. For more details, see [the `getLocationHint` API documentation](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#getlocationhint). | 
| `setTntId` | n/a | `locationHint:result` response handle carries the Target location hint information. It is assumed Target edge will be co-located with Experience Edge. <br> <br>Edge network extension uses the EdgeNetwork location hint to determine the Edge network cluster to send requests to. To share Edge network location hint across SDKs (hybrid apps), use `getLocationHint` and `setLocationHint` APIs from Edge Network extension. For more details, see [the `getLocationHint` API documentation](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#getlocationhint).  | 

## Target extension settings and Decisioning extension equivalents

The Target extension can be configured with various settings.

| Target extension | Decisioning extension | Notes |
| --- | --- | --- | 
| Client Code | n/a | Set automatically by the edge using the IMS Org details |
| Environment ID | Target Environment ID | Set in the datastream |
| Target Workspace Property | Property Token | Set in the datastream |
| Timeout | not currently configurable |  |
| Server Domain | Edge Network domain | Set in the Adobe Experience Platform Edge Network extension |

## Decisioning extension system diagram

The following diagram should help you understand the data flow using the Adobe Journey Optimizer - Decisioning extension.

![Adobe Target Edge Decisioning with client-side Mobile SDK](assets/diagram.png)


>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Decisioning extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
