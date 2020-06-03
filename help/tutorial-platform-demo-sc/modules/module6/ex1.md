# Exercise 6.1: Journey Orchestration: Setup Event

The end goal of this module is to receive an email after creating your account on the AEP Demo-website.

Login to Journey Orchestration by clicking this link: [https://experience.adobe.com/](https://experience.adobe.com).

![ACOP](./images/acophome.png)

Click on ``Journey Orchestration``.

![ACOP](./images/acoptrig.png)

You'll be redirected to the ``Journeys`` - view in Journey Orchestration.

![ACOP](./images/acoptriglp.png)

In the menu, click ``Events``.

![ACOP](./images/acopmenu.png)

In events, you'll see a similar view to this:

![ACOP](./images/acopeventview.png)

Click the ``Add`` - button.

![ACOP](./images/add.png)

You'll then see an empty Event configuration.

![ACOP](./images/emptyevent.png)

First of all, give your Event a Name like this: ``ldapAccountCreationEvent`` and replace **ldap** with your ldap.

![ACOP](./images/eventname.png)

Next, add a description like this ``Account Creation Event``.

![ACOP](./images/eventdescription.png)

Next is the Schema selection. A schema was prepared for this exercise. Please use the schema ``AEP Demo - Account Creation Schema v.1``.

![ACOP](./images/eventschema.png)

After selecting the Schema, you'll see a number of fields being selected in the ``Payload`` - section. You should now hover over the ``Payload`` - section and you'll see 3 icons popup. Click on the ``Edit`` - icon.

![ACOP](./images/eventpayload.png)

You'll see a ``Fields`` - window popup, in which you need to select the fields that we need to personalize the email.

![ACOP](./images/eventfields.png)

In the object ``<aepTenantId>.accountcreation``, please make sure to select the fields ``firstName`` and ``lastName``.

![ACOP](./images/eventpayloadac.png)

In the object ``<aepTenantId>.brand``, please make sure to select the fields ``brandLogo`` en ``brandName``.

![ACOP](./images/eventpayloadbr.png)

Click ``Save`` to save your changes.

![ACOP](./images/save.png)

Click ``Save`` once more to save your changes.

![ACOP](./images/save1.png)

Your Event is now configured and saved.

![ACOP](./images/eventdone.png)

Click on your event again to open up the ``Edit Event`` - screen again.

![ACOP](./images/viewevent.png)

Hover over the ``Payload`` - field again to see the 3 icons again.

![ACOP](./images/hover.png)

Click on the ``View`` - icon. You'll now see an example of the expected payload.

![ACOP](./images/fullpayload.png)

Your Event has a unique orchestration eventID, which you can find by scrolling down in that payload until you see ``_experience.campaign.orchestration.eventID``.

![ACOP](./images/payloadeventID.png)

The event ID is what needs to be sent to Adobe Experience Platform in order to trigger the Journey that you'll build in exercise 2. Remember this eventID, as you'll need it in exercise 3.
``"eventID": "71d98ef80980453e03a3bfc6aab57d15663784265a9363c097b6b9608f1a54bf"``

Click ``Close``.

You've now finished this exercise.

---

Next Step: [Exercise 6.2: Journey Orchestration: Setup Journey](./ex2.md)

[Go Back to Module 6](./README.md)

[Go Back to All Modules](../../README.md)
