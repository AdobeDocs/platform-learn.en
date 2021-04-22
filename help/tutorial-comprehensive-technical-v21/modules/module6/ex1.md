---
title: Module 6 Journey Orchestration Setup Event
description: Journey Orchestration Setup Event
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
exl-id: 98e2ea4b-3c9a-445c-9474-8f3461d33cd2
---
# 6.1 Journey Orchestration: Setup Event

Login to Journey Orchestration by going to [Adobe Experience Cloud](https://experience.adobe.com).

![ACOP](./images/acophome.png)

Click on **Journey Orchestration**.

![ACOP](./images/acoptrig.png)

You'll be redirected to the **Journeys**  view in Journey Orchestration.

![ACOP](./images/acoptriglp.png)

First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxId--`. To change from one sandbox to another, click on **PRODUCTION Prod (VA7)** and select the sandbox from the list. In this example, the sandbox is named **AEP Enablement FY21**.

![ACOP](./images/sb.png)

You'll then be in the **Home** view of your sandbox `--aepSandboxId--`.

![ACOP](./images/home.png)

In the menu, click **Events**.

![ACOP](./images/acopmenu.png)

On the **Events** screen, you'll see a view similar to this. Click the **Add** button.

![ACOP](./images/add.png)

You'll then see an empty event configuration.

![ACOP](./images/emptyevent.png)

First of all, give your Event a Name like this: `ldapAccountCreationEvent` and replace `ldap` with your ldap.

![ACOP](./images/eventname.png)

Next, add a description like this `Account Creation Event`.

![ACOP](./images/eventdescription.png)

Next is the **Event ID Type** selection. Select **System Generated**

![ACOP](./images/eventidtype.png)

Next is the Schema selection. A schema was prepared for this exercise. Please use the schema `Demo System - Event Schema for Website (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

After selecting the Schema, you'll see a number of fields being selected in the **Payload** section. You should now hover over the **Payload** section and you'll see 3 icons popup. Click on the **Edit** icon.

![ACOP](./images/eventpayload.png)

You'll see a **Fields** window popup, in which you need to select some of the fields that we need to personalize the email.  We will choose other profile attributes later, using the data already in Adobe Experience Platform.

![ACOP](./images/eventfields.png)

In the object `--aepTenantId--.demoEnvironment`, please make sure to select the fields **brandLogo** and **brandName**.

![ACOP](./images/eventpayloadbr.png)

In the object `--aepTenantId--.identification.core`, please make sure to select the field **email**.

![ACOP](./images/eventpayloadbrid.png)

Click **Ok** to save your changes.

![ACOP](./images/saveok.png)

You should then see this:

![ACOP](./images/eventsave.png)

Click **Save** once more to save your changes.

![ACOP](./images/save1.png)

Your Event is now configured and saved.

![ACOP](./images/eventdone.png)

Click on your event again to open up the **Edit Event** screen again.

![ACOP](./images/viewevent.png)

Hover over the **Payload** field again to see the 3 icons again.

![ACOP](./images/hover.png)

Click on the **View Payload** icon. You'll now see an example of the expected payload.

![ACOP](./images/fullpayload.png)

Your Event has a unique orchestration eventID, which you can find by scrolling down in that payload until you see `_experience.campaign.orchestration.eventID`.

![ACOP](./images/payloadeventID.png)

The event ID is what needs to be sent to Adobe Experience Platform in order to trigger the Journey that you'll build in Exercise 6.2. Remember this eventID, as you'll need it in Exercise 6.3.
`"eventID": "801dccf3d3ce2afbed286b4fbd15ae8120758dcd7b0d487128342285b3732121"`

Click **Close**.

You've now finished this exercise.

Next Step: [6.2 Journey Orchestration: Setup Journey](./ex2.md)

[Go Back to Module 6](./journey-orchestration-create-account.md)

[Go Back to All Modules](../../overview.md)
