---
title: Adobe Journey Optimizer - Configure a batch-based journey
description: In this section you will configure a batch email journey to send a newsletter
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 761da5b4-682f-430b-951c-278302fc4c54
---
# 10.2 Configure a batch-based newsletter journey 

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxId--`. To change from one sandbox to another, click on **PRODUCTION Prod (VA7)** and select the sandbox from the list. In this example, the sandbox is named **AEP Enablement FY22**. You'll then be in the **Home** view of your sandbox `--aepSandboxId--`.

![ACOP](../module7/images/acoptriglp.png)

## 10.2.1 Create Newsletter Email Message

You'll now create a new email message, to send a newsletter using a batch-based journey. The newsletter email message you'll create in this exercise will be very basic and won't include much personalization. In the next exercise, 10.2, you'll add personalization based on segment memberships and also using Offer Decisioning. For now, let's start with the basic email creation.

In the menu, click **Messages**. 

On the Messages screen, you’ll see a view similar to this. Click **Create Message**.

![Journey Optimizer](./images/batch1.png)

Name your message `--demoProfileLdap-- - Newsletter`, select the **Email Preset** and select the **Email** channel. Click **Create**.

![Journey Optimizer](./images/batch2.png)

First, make sure that the 2 checkboxes under **Optional features** are checked. If not, please **make sure they are both activated**. 

![Journey Optimizer](./images/batch3.png)

Click the **Subject line** text field.

![Journey Optimizer](./images/batch4.png)

Enter this text for the subject line: `Luma Newsletter - your monthly update has arrived.`. Click **Save**.

![Journey Optimizer](./images/batch5.png)

You'll then be back here. Click **Email Designer** to start creating the email content. 

![Journey Optimizer](./images/batch6.png)

You'll then see this. Click **Import HTML**.

![Journey Optimizer](./images/batch7.png)

In the pop-up screen, you'll need to drag and drop the HTML file of the email. You can find the HTML template [here](assets/html/ajo-newsletter.html.zip). Download the zip-file with the HTML template to your local machine and unzip in onto your desktop.

![Journey Optimizer](./images/html1.png)

Drag and drop the file **ajo-newsletter.html** to upload it in Journey Optimizer. Click **Import**.

![Journey Optimizer](./images/batch8.png)

This email content is ready to go since it has all the expected personalization, imagery and text. Only the offer placeholder is left empty. 

You might get an error message: **Error when trying to fetch assets**. This is linked to the image in the email.

![Journey Optimizer](./images/errorfetch.png)

If you get this error, select the image and click the **Edit image** button.

![Journey Optimizer](./images/errorfetch1.png)

Click **Assets Essentials** to go back to your AEM Assets Essentials library.

![Journey Optimizer](./images/errorfetch2.png)

You'll then see this popup. Navigate to the folder **enablement-assets** and select the image **luma-newsletterContent.png**. Click **Select**.

![Journey Optimizer](./images/errorfetch3.png)

Your basic newsletter email is now ready. Click **Save**.

![Journey Optimizer](./images/ready.png)

Go back to the message dashboard by clicking the **arrow** next to the subject line text in the top-left corner.

![Journey Optimizer](./images/batch9.png)

You've now completed the draft version of your registration email. Click **Publish** to publish your message so you can use it in a journey.

![Journey Optimizer](./images/batch10.png)

Click **Publish** again.

![Journey Optimizer](./images/batch11.png)

Wait until you see a green confirmation pop-up at the bottom of the screen indicating that the message is published. 

![Journey Optimizer](./images/batch12.png)

## 10.2.2 Create newsletter journey

Next, go to **Journeys**.

You'll now create a batch-based journey. Unlike the event-based journey of the previous exercise which relies on incoming experience events or segment entries or exits to trigger a journey for 1 specific customer, batch-based journeys target a whole segment once with unique content like newsletters, one-off promotions, or generic information or periodically with similar content sent on a regular basis like for instance birthday campaigns and reminders. 

Click **Create Journey**.

![Journey Optimizer](./images/batchj1.png)

On the right-hand side you will see a form where you need to specify the journey name and description. Enter the following values:

- **Name**: `--demoProfileLdap-- - Newsletter Journey`. For instance: **vangeluw - Newsletter Journey**.
- **Description**: Monthly Newsletter

Click **Ok**. 

![Journey Optimizer](./images/batchj2.png)

Under **Orchestration**, drag and drop **Read Segment** onto the canvas. This means that, once published, the journey will start by retrieving the whole segment audience, which then becomes the target audience of the journey and message. 

![Journey Optimizer](./images/batchj3.png)

Select **Read Segment**. Click **Select a segment**. 

![Journey Optimizer](./images/batchj4.png)

In the **Choose a segment** popup, search for your ldap and select the segment you created in [Module 6 - Real-time CDP - Build a segment and take action](../module6/real-time-cdp-build-a-segment-take-action.md) named `--demoProfileLdap-- - Interest in PROTEUS FITNESS JACKSHIRT`. for example: vangeluw - Interest in PROTEUS FITNESS JACKSHIRT. Click **Save**.

![Journey Optimizer](./images/batchj5.png)

Click **Ok**.

![Journey Optimizer](./images/batchj6.png)

In the left menu, find the **Actions** section and drag and drop a **Message** action onto the canvas.

![Journey Optimizer](./images/batchj7.png)

Click on the **Message** activity to display the menu on the right-hand side. Click on the **Select a message** drop-down menu.

![Journey Optimizer](./images/batchj8.png)

Select the message you created in the previous exercise, which is named `--demoProfileLdap - Newsletter`. Click **Select**.

![Journey Optimizer](./images/batchj9.png)

Click **OK**.

![Journey Optimizer](./images/batchj10.png)

In the menu, click **Orchestration** and drag and drop **End** onto the canvas. Click **Ok**.

![Journey Optimizer](./images/batchj11.png)

Your newsletter journey is now ready to be published. Before you do so, notice the **Schedule** section where you can switch this journey from being a one-off to a recurring campaign. Click the **Schedule** button.

![Journey Optimizer](./images/batchj12.png)

You'll then see this. Select **Once**.

![Journey Optimizer](./images/sch1.png)

Select a date and time within the next hour so you can test your journey. Click **Ok**.

>[!NOTE]
>
>Message send date and time must be within more than one hour.

![Journey Optimizer](./images/sch2.png)

Click **Publish**.

![Journey Optimizer](./images/batchj13.png)

Click **Publish** again.

![Journey Optimizer](./images/batchj14.png)

Your basic newsletter journey is now published. Your newsletter email message will be sent as you defined it in your schedule, and your journey will stop as soon as the last email has been sent.

You have finished this exercise.

Next Step: [10.3 Apply personalization in an email message](./ex3.md)

[Go Back to Module 10](./journeyoptimizer.md)

[Go Back to All Modules](../../overview.md)
