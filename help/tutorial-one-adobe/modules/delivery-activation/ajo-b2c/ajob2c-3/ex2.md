---
title: Configure a journey with push messages
description: Configure a journey with push messages
kt: 5342
doc-type: tutorial
exl-id: 63d7ee24-b6b5-4503-b104-a345c2b26960
---
# 3.3.2 Configure a journey with push messages


## 3.4.4.6 Create a new event

Go to **Journey Optimizer**. In the left menu, go to **Configurations** and click **Manage** under **Events**.

![ACOP](./images/acopmenu.png)

On the **Events** screen, you'll see a view similar to this. Click **Create Event**.

![ACOP](./images/add.png)

You'll then see an empty event configuration.
First of all, give your Event a Name like this: `--aepUserLdap--StoreEntryEvent` and set description to `Store Entry Event`.
Next is the **Event Type** selection. Select **Unitary**.
Next is the **Event ID Type** selection. Select **System Generated**.

![ACOP](./images/eventname.png)

Next is the Schema selection. A schema was prepared for this exercise. Please use the schema `Demo System - Event Schema for Mobile App (Global v1.1) v.1`.

After selecting the Schema, you'll see a number of fields being selected in the **Payload** section. Your event is now fully configured.

Click **Save**.

![ACOP](./images/eventschema.png)

Your Event is now configured and saved. Click on your event again to open up the **Edit Event** screen again.

![ACOP](./images/eventdone.png)

Hover over the **Payload** field and click on the **View Payload** icon.

![ACOP](./images/hover.png)

You'll now see an example of the expected payload.

Your Event has a unique orchestration eventID, which you can find by scrolling down in that payload until you see `_experience.campaign.orchestration.eventID`.

![ACOP](./images/payloadeventID.png)

The event ID is what needs to be sent to Adobe Experience Platform in order to trigger the Journey that you'll build in the next step. Write down this eventID, as you'll need it in the next step.
`"eventID": "89acd341ec2b7d1130c9a73535029debf2ac35f486bc99236b1a5091d6f4bc68"`

Click **Ok**, followed by **Cancel**.

## 3.4.4.7 Create a journey

In the menu, go to **Journeys** and click **Create Journey**.

![DSN](./images/sjourney1.png)

You'll then see this. Give your journey a name. Use `--aepUserLdap-- - Store Entry journey`. Click **Save**.

![DSN](./images/sjourney3.png)

First, you need to add your event as the starting point of your journey. Search for your event `--aepUserLdap--StoreEntryEvent` and drag and drop it onto the canvas. Click **Save**.

![DSN](./images/sjourney4.png)

Next, under **Actions**, search for the **Push** action. Drag and drop the **Push** action onto the canvas.

Set the **Category** to **Marketing** and select a push surface that enables you to send push notifications. In this case, the email surface to select is **Push-iOS-Android**.

>[!NOTE]
>
>A Channel in Journey Optimizer needs to exist that is using the **App Surface** as reviewed before.

![ACOP](./images/journeyactions1push.png)

The next step is to create your message. To do that, click **Edit content**.

![ACOP](./images/journeyactions2push.png)

You'll then see this. Click the **personalization** icon for the **Title** field.

![Push](./images/bp5.png)

You'll then see this. You can now select any Profile attribute from the Real-time Customer Profile directly.

Search for the field **First Name**, then click the **+** icon next to the field **First Name**. You'll then see the personalization token for First Name being added: **{{profile.person.name.firstName}}**.

![Push](./images/bp9.png)

Next, add the text **, welcome to our store!** behind **{{profile.person.name.firstName}}**.

Click **Save**.

![Push](./images/bp10.png)

You now have this. Click the **personalization** icon for the **Body** field.

![Push](./images/bp11.png)

Enter this text **Click here to get a 10% discount when you buy today!** and click **Save**.

![Push](./images/bp12.png)

You'll then have this. Click the arrow in the top left corner to go back to your journey.

![Journey Optimizer](./images/bp12a.png)

Click **Save** to close your push action.

![DSN](./images/sjourney8.png)

Click **Publish**.

![DSN](./images/sjourney10.png)

Click **Publish** again.

![DSN](./images/sjourney10a.png)

Your journey is now published.

![DSN](./images/sjourney11.png)

## 3.4.4.8 Test your journey and push message

In your DX Demo 2.0 mobile application, go to the **Settings** screen. Click the **Store Entry** button.

>[!NOTE]
>
>The **Store Entry** button is currently being implemented. You won't yet find it in the app.

![DSN](./images/demo1b.png)

Make sure to close the app immediately after clicking the **Store Entry** icon, otherwise the push message won't be shown.

After a couple of seconds, you'll see the message appear.

![DSN](./images/demo2.png)

You have finished this exercise.

## Next Steps

Go to [3.3.3 Configure a campaign with in-app messages](./ex3.md){target="_blank"}

Go back to [Adobe Journey Optimizer: Push and In-app Messages](ajopushinapp.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
