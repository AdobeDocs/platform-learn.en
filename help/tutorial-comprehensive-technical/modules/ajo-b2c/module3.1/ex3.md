---
title: Journey Optimizer Create your journey and email message
description: Journey Optimizer Create your email message
kt: 5342
doc-type: tutorial
exl-id: 6807f93d-bd44-4f63-8005-6819c9f5f1ed
---
# 3.1.3 Create your Journey, Fragments and Message

In this exercise, you'll configure the journey and the message that needs to be triggered when someone creates an account on the demo website.

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](./images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxName--`.

![ACOP](./images/acoptriglp.png)

## 3.1.3.1 Create your Journey

In the left menu, click **Journeys**. Next, click **Create Journey** to create a new journey.

![ACOP](./images/createjourney.png) 

You'll then see an empty journey screen.

![ACOP](./images/journeyempty.png)

In the previous exercise, you created a new **Event**. You named it like this `--aepUserLdap--AccountCreationEvent` and replaced `ldap` with your ldap. This was the result of the Event creation:

![ACOP](./images/eventdone.png)

You now need to take this event as the start of this Journey. You can do this by going to the left side of your screen and searching for your event in the list of events.

![ACOP](./images/eventlist.png)

Select your event, drag and drop it on the Journey canvas. Your Journey now looks like this:

![ACOP](./images/journeyevent.png)

As the second step in the journey, you need to add a short **Wait** step. Go to the left side of your screen to the **Orchestration** section to find this. You'll be using profile attributes and need to make sure they are populated into the Real-time Customer Profile.

![ACOP](./images/journeywait.png)

Your journey now looks like this. On the right side of the screen you need to configure the wait time. Set it to 1 minute. This will give plenty of time for the profile attributes to be available after the event fires. Click **Save** to save your changes.

![ACOP](./images/journeywait1.png)

As the third step in the journey, you need to add an **Email** action. Go to the left side of your screen to **Actions**, select the **Email** action, then drag and drop it on the second node in your journey. You now see this.

![ACOP](./images/journeyactions.png)

Set the **Category** to **Marketing** and select an email configuration that enables you to send email. In this case, the email configuration to select is **Email**. Ensure that the checkboxes for **Clicks on email** and **email opens** are both enabled.

![ACOP](./images/journeyactions1.png)

## 3.1.3.2 Create your Message

To create your message, click **Edit content**.

![ACOP](./images/journeyactions2.png)

You now see this.

![ACOP](./images/journeyactions3.png)

Click the **Open personalization dialog** icon.

![Journey Optimizer](./images/msg5.png)

Write the text `Hi `. Next you need to bring in the personalization token for the field **First name** which is stored under `profile.person.name.firstName`. In the left menu, navigate to find the **Person > Full Name > First Name** field and click on the **+** icon. You'll then see the personalization token appear in the text field.

![Journey Optimizer](./images/msg9.png)

Next, add the text **, thank you for signing up!**. Click **Save**.

![Journey Optimizer](./images/msg10.png)

You can now start configuring the body of your email. Click **Edit email body**. 

![Journey Optimizer](./images/msg11.png)

Before starting to create the content of the actual message itself, it's a good idea to think about the content in the message. Some of the content in the message is unique to the message itself, but other parts are standard components that will likely be the same for every email you'll be sending to customers. 

In the previous exercise, you already created these standard components as Fragments in Journey Optimizer, which you can now reference in this message and all the other future messages you'll be creating.

In the next screen you will be prompted with 3 different methods to provide the email's content:

- **Design from scratch**: Start with a blank canvas and use the WYSIWYG-editor to drag and drop structure and content components to visually build up the email's content.
- **Code your own**: Create your own email template by coding it using HTML
- **Import HTML**: Import an existing HTML template, which you'll be able to edit.

Click **Design from scratch**.

![Journey Optimizer](./images/msg12.png)

In the left menu, you'll find the structure components that you can use to define the structure of the email (rows and columns).

![Journey Optimizer](./images/msg13.png)

You'll also find **Fragments** in the left menu, where you'll see the fragments you created earlier.

![Journey Optimizer](./images/msg14.png)

Before you can add the header and footer onto the canvas, you need to add 2 structures to the email. Click the **+** icon in the left menu, and drag 2 **1:1 column** components onto the canvas.

![Journey Optimizer](./images/msg14a.png)

In the left menu, go back to **Fragments**. Drag and drop the header fragment into the first component and the footer fragment into the second component. You'll then see this.

![Journey Optimizer](./images/msg15.png)

Click the **+** icon in the left menu and drag and drop 2 more **1:1 column** components onto the canvas, in between the header and the footer.

![Journey Optimizer](./images/msg16.png)

Drag and drop an **Image** component in the first **1:1 column** component. Click **Browse**.

![Journey Optimizer](./images/msg17.png)

In the **citi-signal-images** folder. Select the image **`welcome_email_image.png`** and click **Select**. 

![Journey Optimizer](./images/msg28.png)

You'll then have this:

![Journey Optimizer](./images/msg30.png)

Next, go to **Contents** and drag and drop a **Text** component in the structure component on the fourth row. 

![Journey Optimizer](./images/msg33.png)

Select the default text **Please type your text here.** as you would do with any text editor. Write **Welcome to the family,** instead. In the toolbar, click the **Add personalization** icon.

![Journey Optimizer](./images/msg34.png)

Next, you need to bring the **First name** personalization token which is stored under `profile.person.name.firstName`. In the menu, find the **Person** element, drill down to the **Full Name** element, and then click the **+** icon to add the First Name field onto to expression editor.

Click **Save**.

![Journey Optimizer](./images/msg36.png)

You'll now notice how the personalization field has been added to your text. 

![Journey Optimizer](./images/msg37.png)

In the same text field, hit **Enter** twice to add two lines and copy and paste the following text:

```
Welcome aboard! We're thrilled to have you join the CitiSignal family. 
As a valued member of our community, you're now poised to experience top-notch telecommunications services that cater to your every need.

At CitiSignal, we understand that staying connected is more than just a convenience - it's a necessity. Whether you're browsing the web, streaming your favourite content, or keeping in touch with loved ones, we're here to ensure you have the best tools and resources at your fingertips.
```

![Journey Optimizer](./images/msg38.png)

Set the **Text alignment** to be centered, and feel free to adjust the look and feel of the message to meet your own needs. When you're done, click **Save**.

![Journey Optimizer](./images/msg39.png)

The final check to perform to ensure your email is ready is to preview it, click on the **Simulate Content** button.

![Journey Optimizer](./images/msg50.png)

Before you can simulate the email message, you need to add a test profile. Click **Manage test profiles**.

![Journey Optimizer](./images/test1.png)

Select the **email** namespace by clicking on the icon next to **Enter identity namespace** field.

In the list of identity namespaces, select the **Email** namespace. In the **Identity value** field, enter the email address of a previous profile that you used in a previous exercise, and that is already stored in Adobe Experience Platform. Click **Add profile**. Go back to the previous screen.

![Journey Optimizer](./images/msg53.png)

You'll then see your email message, now simulated for this customer profile. You can now validate the personalization in the subject line and the body and send a proof email if desired.

Click **Close** to close the preview.

![Journey Optimizer](./images/msg54.png)

Click **Save** to save your message and go back to the message dashboard by clicking the **arrow** next to the subject line text in the top-left corner.

![Journey Optimizer](./images/msg55.png)

Click the **arrow** to go back to your journey.

![Journey Optimizer](./images/msg57a.png)

## 3.1.3.3 Publish your journey

Click **Save**.

![Journey Optimizer](./images/msg58.png)

You still need to give your journey a name. You can do that by clicking the **Properties** icon in the top right side of your screen.

![ACOP](./images/journeyname.png)

You can then enter the journey's name here. Please use `--aepUserLdap-- - Registration Journey`. Click **Save**.

![ACOP](./images/journeyname1.png)

You can now publish your journey by clicking **Publish**.

![ACOP](./images/publishjourney.png)

Click **Publish** again.

![ACOP](./images/publish1.png)

After a coupleof minutes, the status of your journey will change to **Live** and you'll see a real-time dashboad of your journey's performance.

![ACOP](./images/published.png)

You've now finished this exercise.

Next Step: [3.1.4 Update your Data Collection property and test your journey](./ex4.md)

[Go Back to Module 3.1](./journey-orchestration-create-account.md)

[Go Back to All Modules](../../../overview.md)
