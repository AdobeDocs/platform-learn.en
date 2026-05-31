---
title: Track conversion events - Migrate the Adobe Target implementation in your mobile app to the Offer Decisioning and Target extension
description: Learn how to track Adobe Target conversion events using the Offer Decisioning and Target Mobile extension
exl-id: 7b53aab1-0922-4d9f-8bf0-f5cf98ac04c4
TQID: https://experienceleague.adobe.com/teurSjzfmfxjnoMNh-XzsdcyzgNv2cWeN-s5vIQ4Tkg
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
# Track Target conversion events using the Decisioning mobile extension

The goal of most Target activities is to drive valuable user actions in your application, such as purchases, registration, clicks and mroe. Target implementations commonly use custom conversion events to track these actions, often containing additional details about the conversion. Conversion events for Target can be tracked with Optimize SDK similar to Target SDK. Specific APIs need to be called to track conversion events as shown in the table below:

| Activity Goal | Target Extension | Offer Decisioning and Target extension |
|---|---|---|
| Track a view conversion event for an mbox location (scope) | Call the [displayedLocations](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank} API when mbox location is viewed | Call the [displayed](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-direct-offer-class-methods){target=_blank} API when the Offer for the mbox location is viewed. This sends an event with event type decisioning.propositionDisplay to the Experience Edge network. **This is essential to increment visitors in your Target activities and must be done when delivering both regular and default Target offers.** |
| Track a click conversion event for an mbox location (scope) | Call the [clickedLocations](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank}  API in when mbox location is clicked | Call the [tapped](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-direct-offer-class-methods){target=_blank} API when the Offer for the mbox location is clicked. This sends an event with event type decisioning.propositionInteract to the Experience Edge network. |
| Track a custom conversion event that may also include additional data, such Target profile parameters and order details |Pass the additional data in the TargetParameters field provided by the [displayedLocations](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank} and [clickedLocations](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank} APIs | Use the public methods [generateDisplayInteractionXdm](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-edge-extension-api){target=_blank} and [generateTapInteractionXdm](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-edge-extension-api){target=_blank} APIs available in the Offer for the mbox location to generate the XDM formatted data for view and click respectively. Then call the Edge SDK [sendEvent](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#sendevent){target=_blank} API to send this tracking XDM data along with any additional XDM and freeform data to the Experience Edge network. |


Next, learn how to [update audiences and profile scripts](update-audiences.md) to ensure compatibility with the Offer Decisioning and Target extension.

>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Offer Decisioning and Target extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
