---
title: Track conversion events - Migrate the Adobe Target implementation in your mobile app to the Adobe Journey Optimizer - Decisioning extension
description: Learn how to track Adobe Target conversion events using the Adobe Journey Optimizer - Decisioning Mobile extension
exl-id: 7b53aab1-0922-4d9f-8bf0-f5cf98ac04c4
---
# Track Target conversion events using the Decisioning mobile extension

The goal of most Target activities is to drive valuable user actions in your application, such as purchases, registration, clicks and mroe. Target implementations commonly use custom conversion events to track these actions, often containing additional details about the conversion. Conversion events for Target can be tracked with Optimize SDK similar to Target SDK. Specific APIs need to be called to track conversion events as shown in the table below:

| Activity Goal | Target Extension | Decisioning Extension |
|---|---|---|

| Track a view conversion event for an mbox location (scope) | Call the [displayedLocations](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank} API when mbox location is viewed | Call the [displayed](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank} API when the Offer for the mbox location is viewed. This sends an event with event type decisioning.propositionDisplay to the Experience Edge network. |

| Track a click conversion event for an mbox location (scope) | Call the [clickedLocations](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank}  API in when mbox location is clicked | Call the [tapped](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank} API when the Offer for the mbox location is clicked. This sends an event with event type decisioning.propositionInteract to the Experience Edge network. |

| Track a custom conversion event that may also include additional data, such Target profile parameters and order details |Pass the additional data in the TargetParameters field provided by the [displayedLocations](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank} and [clickedLocations](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank} APIs | Use the public methods [generateDisplayInteractionXdm](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-edge-extension-api){target=_blank} and [generateTapInteractionXdm](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-edge-extension-api){target=_blank} APIs available in the Offer for the mbox location to generate the XDM formatted data for view and click respectively. Then call the Edge SDK [sendEvent](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#sendevent){target=_blank} API to send this tracking XDM data along with any additional XDM and freeform data to the Experience Edge network. |


Next, learn how to [update audiences and profile scripts](webview.md) to ensure compatibility with the Decisioning extension.

>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Decisioning extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
