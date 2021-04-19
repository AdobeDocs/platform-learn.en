---
title: Module 6, Exercise
description: Module 6.2 Journey Orchestration - Setup Journey
kt: 5342
audience: 
doc-type: tutorial
activity: develop
exl-id: b8052c08-4215-49c5-9fa0-6fa6687a9877
---
# 6.2 Journey Orchestration: Setup Journey

In this exercise, you'll configure the journey that needs to be triggered when someone creates an account on the Platform Demo website.

Login to Journey Orchestration by going to [Adobe Experience Cloud](https://experience.adobe.com).

![ACOP](./images/acophome.png)

Click on **Journey Orchestration**.

![ACOP](./images/acoptrig.png)

You'll be redirected to the **Home** view in Journey Orchestration.

![ACOP](./images/acoptriglp.png)

First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxId--`. To change from one sandbox to another, click on **PRODUCTION Prod (VA7)** and select the sandbox from the list. In this example, the sandbox is named **AEP Enablement**.

![ACOP](./images/sb.png)

You'll then be in the **Home** view of your sandbox --aepSandboxId--.

![ACOP](./images/home.png)

Let's create a new journey by clicking the **Create** button.

![ACOP](./images/create.png)

You'll then see an empty Journey screen.

![ACOP](./images/journeyempty.png)

In the previous exercise, you created a new **Event**. You named it like this `ldapAccountCreationEvent` and replaced `ldap` with your ldap. This was the result of the Event creation:

![ACOP](./images/eventdone.png)

You now need to take this event as the start of this Journey. You can do this by going to the left side of your screen and searching for your event in the list of events.

![ACOP](./images/eventlist.png)

Select your event, drag and drop it on the Journey  canvas. Your Journey now looks like this:

![ACOP](./images/journeyevent.png)

As the second step in the journey, you need to add an **Email** action. Go to the left side of your screen to **Actions**, select the **Email** action, then drag and drop it on the second node in your journey.

![ACOP](./images/journeyactions.png)

Your journey now looks like this:

![ACOP](./images/journeyemailaction.png)

On the right side of your screen, you now need to configure the email.

![ACOP](./images/emptymsg.png)

Go to **Message** and open the dropdown list. In that list, you need to select the template with the name **Thanks for Signing Up**.

![ACOP](./images/emailmsglist.png)

Selecting this message automatically opens up a number of additional fields. These are the fields that. have been configured to be dynamic field in the email template. You now need to link each of the expected dynamic fields to a field coming from the Payload that is sent to Platform.

![ACOP](./images/emailpersdata.png)

Let's start with the **Email** field.

Click on the **Edit** icon.

![ACOP](./images/msgemail.png)

You'll then see a window to select a source field to use as Email Source.

![ACOP](./images/emptylink.png)

Click on the name of the event you created to open it.

![ACOP](./images/eventnode.png)

Navigate to `--aepTenantId--.accountcreation.email` and click it.

![ACOP](./images/srcemail.png)

Click **OK** to save your configuration.

Next, let's configure the Brand Logo field. This field has to be configured as you'll be doing many personalized demo's in the future and you probably want those emails to also reference the same brand logo as what is used on the website, mobile app and Alexa. This is where you can make that happen.

Click on the **Edit** icon.

![ACOP](./images/msgbrandlogo.png)

Navigate to `--aepTenantId--.brand.brandLogo` and click it.

![ACOP](./images/srclogo.png)

Click **OK** to save your configuration.

Next, let's configure the Brand Name field. This field has to be configured as you'll be doing many personalized demos in the future and you probably want those emails to also reference the same Brand Name as what is used on the website, mobile app and Alexa. This is where you can make that happen.

Click on the **Edit** icon.

![ACOP](./images/msgbrandname.png)

Navigate to `--aepTenantId--.brand.brandName` and click it.

![ACOP](./images/srcbrandname.png)

Click **OK** to save your configuration.

Next, let's configure the First Name field. Personalization requires the usage of First Name.

Click on the **Edit** icon.

![ACOP](./images/msgfn.png)

Navigate to `--aepTenantId--.accountcreation.firstName` and click it.

![ACOP](./images/srcfn.png)

Click **OK** to save your configuration.

Next, let's configure the Last Name field. Personalization may also require the usage of Last Name.

Click on the **Edit** icon.

![ACOP](./images/msgln.png)

Navigate to `--aepTenantId--.accountcreation.lastName` and click it.

![ACOP](./images/srcln.png)

Click **OK** to save your configuration.

Your configuration now looks like this.

![ACOP](./images/srcoverview.png)

Click **OK** again to save your configuration.

![ACOP](./images/ok.png)

For this exercise, our Journey is fine like it is now.

Let's add an Orchestration Event to **End** the Journey. In the left side of the screen, go to **Orchestration** and select **End**. Drag and Drop this onto the 3rd step of the Journey.

![ACOP](./images/orch.png)

Your Journey now looks like this.

![ACOP](./images/journeyfinal.png)

You still need to give your Journey a Name. You can do that by clicking the **Edit** icon in the top right side of your screen.

![ACOP](./images/journeyname.png)

You can then enter the Journey's name here. Please use `ldap - Account Creation Journey` as a naming convention and replace `ldap` with your LDAP.
  
![ACOP](./images/journeyname1.png)

Click **OK** to save your changes.

![ACOP](./images/ok.png)

You now see this in the top of your screen.

![ACOP](./images/journeyname2.png)

You can now publish your journey by clicking **Publish**.

![ACOP](./images/publish.png)

Click **Publish** again.

![ACOP](./images/publish1.png)

You'll then see a green confirmation bar saying that your Journey is now Publish.

![ACOP](./images/published.png)

You've now finished this exercise.

Next Step: [6.3 Update your Configuration ID and Test your Journey](./ex3.md)

[Go Back to Module 6](./journey-orchestration-create-account.md)

[Go Back to All Modules](../../overview.md)
