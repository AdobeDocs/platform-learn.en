---
title: Journey Optimizer Create your event
description: Journey Optimizer Create your event
kt: 5342
doc-type: tutorial
---
# 3.1.1 Create your event

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](./images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxName--`. 

![ACOP](./images/acoptriglp.png)

In the left menu, scroll down and click **Configurations**. Next, click the **Manage** button under **Events**.

![ACOP](./images/acopmenu.png)

You'll then see an overview of all available events. Click **Create Event** to start creating your own event.

![ACOP](./images/emptyevent.png)

A new, empty event window will then pop up.

![ACOP](./images/emptyevent1.png)

First of all, give your Event a Name like this: `--aepUserLdap--AccountCreationEvent`.
Set the description to `Account Creation Event`, make sure the **Type** is set to **Unitary** and for the **Event ID Type** selection, select **System Generated**.

![ACOP](./images/eventdescription.png)

Next is the Schema selection. Please use the schema `Demo System - Event Schema for Website (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

After selecting the Schema, you'll see a number of fields being selected in the **Payload** section. You should now hover over the **Payload** section and you'll see 3 icons popup. Click on the **Edit** icon.

![ACOP](./images/eventpayload.png)

You'll see a **Fields** window popup, in which you need to select some of the fields that we need to personalize the email.  We will choose other profile attributes later, using the data already in Adobe Experience Platform.

![ACOP](./images/eventfields.png)

In the object `--aepTenantId--.demoEnvironment`, please make sure to select the fields **brandLogo** and **brandName**.

![ACOP](./images/eventpayloadbr.png)

In the object `--aepTenantId--.identification.core`, please make sure to select the field **email**. Click **Ok** to save your changes.

![ACOP](./images/eventpayloadbrid.png)

You should then see this. Set the **Namespace** to **ECID (ECID)**. Click **Save**.

![ACOP](./images/eventsave.png)

Your event is now configured and saved.

![ACOP](./images/eventdone.png)

Click your event again to open up the **Edit Event** screen again. Hover over the **Payload** field again to see the 3 icons again. Click on the **View Payload** icon. 

![ACOP](./images/viewevent.png)

You'll now see an example of the expected payload.

![ACOP](./images/fullpayload.png)

Your Event has a unique orchestration eventID, which you can find by scrolling down in that payload until you see `_experience.campaign.orchestration.eventID`.

The event ID is what needs to be sent to Adobe Experience Platform in order to trigger the journey that you'll build next. Remember this eventID, as you'll need it in one of the next exercises.
`"eventID": "5ae9b8d3f68eb555502b0c07d03ef71780600c4bd0373a4065c692ae0bfbd34d"`

Click **Ok**.

![ACOP](./images/payloadeventID.png)

Click **Cancel**.

![ACOP](./images/payloadeventID1.png)

You've now finished this exercise.

Next Step: [3.1.2 Journey Optimizer: Create your journey and email message](./ex2.md)

[Go Back to Module 3.1](./journey-orchestration-create-account.md)

[Go Back to All Modules](../../../overview.md)
