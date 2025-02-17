---
title: Adobe Journey Optimizer - External Weather API, SMS Action & more - Define an Event
description: Adobe Journey Optimizer - External Weather API, SMS Action & more
kt: 5342
doc-type: tutorial
---
# 3.2.1 Define an event

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxName--`. You'll then be in the **Home** view of your sandbox `--aepSandboxName--`.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

In the left menu, scroll down and click **Configurations**. Next, click the **Manage** button under **Events**.

![ACOP](./images/acopmenu.png)

You'll then see an overview of all available events. Click **Create Event** to start creating your own event.

![ACOP](./images/emptyevent.png)

A new, empty event window will then pop up.
As a name for the Event, use `--aepUserLdap--GeofenceEntry`.

Set Description to: `Geofence Entry Event`.

Make sure the **Type** is set to **Unitary**, and for the **Event ID Type** selection, select **System Generated**

![Demo](./images/evname.png)

Next, you need to select a schema. All schemas that are shown here, are Adobe Experience Platform Schemas.

![Demo](./images/evschema.png)

You'll notice that not all schemas are shown. There are many more schemas available in Adobe Experience Platform.
To show up in this list, a schema needs to have a very specific field group linked to it. The field group that is needed to show up here is called `Orchestration eventID`.

Let's have a quick look how these schemas are defined in Adobe Experience Platform.

In the left menu, go to **Schemas** and open this in a new browser tab. In **Schemas**, go to **Browse** to see the list of available Schemas.
Open the Schema `Demo System - Event Schema for Website (Global v1.1)`.

![Data Ingestion](./images/schemas.png)

After opening the Schema, you'll see that the field group `Orchestration eventID` is part of the schema.
This field group only has two fields, `_experience.campaign.orchestration.eventID` and `originJourneyID`.

![Data Ingestion](./images/schemageo.png)

Once this field group and this specific eventID field are part of a schema, that schema will be available for usage by Adobe Journey Optimizer.

Go back to your event configuration in Adobe Journey Optimizer.

![Demo](./images/evschema.png)

In this use case, you want to listen to a Geofence Event to understand if a customer is in a specific location, so now, select the Schema `Demo System - Event Schema for Website (Global v1.1)` as the Schema for your Event.

![Demo](./images/evschema1.png)

Adobe Journey Optimizer will then automatically select some required fields, but you can edit the fields that are made available to Adobe Journey Optimizer.

Click the **pencil** icon to edit the fields.

![Demo](./images/editfields.png)

You'll then see a popup-window with a schema hierarchy that allows you to select fields.

![Demo](./images/popup.png)

Fields like the ECID and the Orchestration eventID are required and as such preselected.

However, a marketeer needs to have flexible access to all data points that provide context to a journey. So let's make sure to select the following fields as a minimum as well (found within the Place context node):

- City

Once that's done, click **OK**.

![Demo](./images/popupok.png)

Adobe Journey Optimizer also needs an Identifier to identify the customer. Since Adobe Journey Optimizer is linked to Adobe Experience Platform, the Primary Identifier of a Schema is automatically taken as the Identifier for the Journey.
The Primary Identifier will also automatically take into account the full Identity Graph of Adobe Experience Platform and will link all behavior across all available identities, devices and channels to the same profile, so that Adobe Journey Optimizer is contextual, relevant and consistent. Click **Save**.

![Demo](./images/eventidentifier.png)

Your event will then be part of the list of available events.

![Demo](./images/eventlist.png)

Finally, you need to recover the `Orchestration eventID` for your custom event.

Open your event again by clicking it in the list of events.
On your Event, click on the **View Payload** icon next to **Fields**.

![Demo](./images/fieldseyepayload.png)

Clicking the **View Payload** icon opens up a sample XDM payload for this event. Scroll down in the **Payload** until you see the line `eventID`.

![Demo](./images/fieldseyepayloadev.png)

Write down the `eventID` as you'll need it in the last to test your configuration.

In this example, the `eventID` is `4df8dc10731eba7b0c37af83a9db38d4de7aa6aebcce38196d9d47929b9c598e`.

You've now defined the event that will trigger the journey we're building. Once the journey is triggered, the geofence-fields like City, and any others you may have chosen (like Country, Latitude and Longitude) will be made available to the journey.

As discussed in the use-case description, we then need to provide contextual promotions that depend on the weather. In order to get weather information, we'll need to define an external data sources that will provide us with the weather information for that location. You'll use the **OpenWeather API** service to provide us with that information.

## Next Steps

Go to [3.2.2 Define an external data source](./ex2.md){target="_blank"}

Go back to [Adobe Journey Optimizer: External data sources and custom actions](journey-orchestration-external-weather-api-sms.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}