---
title: Configure a journey with push messages
description: Configure a journey with push messages
kt: 5342
doc-type: tutorial
---
# 3.3.2 Configure a journey with push messages

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxName--`. You'll then be in the **Home** view of your sandbox `--aepSandboxName--`.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

## 3.3.2.1 Create a new event

In the left menu, go to **Configurations** and click **Manage** under **Events**.

![ACOP](./images/acopmenu.png)

On the **Events** screen, you'll see a view similar to this. Click **Create Event**.

![ACOP](./images/add.png)

You'll then see an empty event configuration.
First of all, give your Event a Name like this: `--aepUserLdap--StoreEntryEvent` and set description to `Store Entry Event`.
Next is the **Event Type** selection. Select **Unitary**.
Next is the **Event ID Type** selection. Select **System Generated**.

![ACOP](./images/eventname.png)

Next is the Schema selection. A schema was prepared for this exercise. Please use the schema `Demo System - Event Schema for Mobile App (Global v1.1) v.1`.

After selecting the Schema, you'll see a number of fields being selected in the **Payload** section. Verify that the field **Namespace** is set to **ECID**. Your event is now fully configured.

Click **Save**.

![ACOP](./images/eventschema.png)

Your event is now configured and saved. Click on your event again to open up the **Edit Event** screen again.

![ACOP](./images/eventdone.png)

Hover over the **Payload** field and click on the **View Payload** icon.

![ACOP](./images/hover.png)

You'll now see an example of the expected payload.

Your Event has a unique orchestration eventID, which you can find by scrolling down in that payload until you see `_experience.campaign.orchestration.eventID`.

The event ID is what needs to be sent to Adobe Experience Platform in order to trigger the Journey that you'll build in the next step. Write down this eventID, as you'll need it in the next step.
`"eventID": "aa895251f76831e6440f169f1bb9d2a4388f0696d8e2782cfab192a275817dfa"`

Click **Ok**.

![ACOP](./images/payloadeventID.png)

Click **Cancel**.

![ACOP](./images/payloadeventIDa.png)

## 3.3.2.2 Create a journey

In the left menu, go to **Journeys** and click **Create Journey**.

![DSN](./images/sjourney1.png)

You'll then see this. Give your journey a name: `--aepUserLdap-- - Store Entry journey`. Click **Save**.

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

You'll then see this. You can now select any profile attribute from the Real-time Customer Profile directly.

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

## 3.3.2.3 Update your data collection property for mobile

In **Getting Started**, Demo System Next created Tags properties for you: one for the website and one for the mobile app. Find them by searching for `--aepUserLdap--` in the **Search** box. Click to open the **Mobile** property.

![DSN](./images/pushpoi1.png)

You should then see this.

![DSN](./images/pushpoi2.png)

In the left menu, go to **Rules** and click to open the rule **Location entry**.

![DSN](./images/pushpoi3.png)

You should then see this. Click the action **Mobile Core - Attach Data**.

![DSN](./images/pushpoi4.png)

You should then see this.

![DSN](./images/pushpoi5.png)

Paste the eventID of your event `--aepUserLdap--StoreEntryEvent` in the **JSON Payload** window. Click **Keep Changes**.

![DSN](./images/pushpoi6.png)

Click **Save** or **Save to Library**.

![DSN](./images/pushpoi7.png)

Go to **Publishing Flow** and click to open the library **Main**.

![DSN](./images/pushpoi8.png)

Click **Add All Changed Resources** and then click **Save & Build to Development**.

![DSN](./images/pushpoi9.png)

## 3.3.2.4 Test your journey and push message

Open the **DSN Mobile** application.

![DSN](./images/dxdemo1.png)

Go to the **Store Locator** page.

![DSN](./images/dxdemo2.png)

Click **Simulate POI Entry**.

![DSN](./images/dxdemo3.png)

After a couple of seconds, you'll see the push notification appear.

![DSN](./images/dxdemo4.png)

## Next Steps

Go to [3.3.3 Configure a campaign with in-app messages](./ex3.md){target="_blank"}

Go back to [Adobe Journey Optimizer: Push and In-app Messages](ajopushinapp.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}