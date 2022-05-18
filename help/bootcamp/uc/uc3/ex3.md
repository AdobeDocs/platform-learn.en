---
title: Bootcamp - Blending physical and digital - Journey Optimizer Create your push notification
description: Bootcamp - Blending physical and digital - Journey Optimizer Create your push notification
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
exl-id: 41d8b01b-f373-4f21-a55e-4a758d0165e0
---
# 3.3 Create your push notification

In this exercise, you'll configure the journey that needs to be triggered when someone creates an account on the demo website.

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](./images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `Bootcamp`. To change from one sandbox to another, click on **Prod** and select the sandbox from the list. In this example, the sandbox is named **Bootcamp**. You'll then be in the **Home** view of your sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

In the left menu, click **Messages**. 

On the Messages screen, you’ll see a view similar to this. Click **Create Message**.

![Journey Optimizer](./images/msg1.png)

Give your Message a title following this naming convention `yourLastName - Beacon Entry Push Notification`. Select the preset **mmeeewis-app-mobile-bootcamp** and enable the **Push Notification** channel. Click on the **Create** button to create your push notification.

![Journey Optimizer](./images/msg2.png)

The next screen is the message dashboard, from there you will be able to see the push notification preview when the content will be provided.

![Journey Optimizer](./images/msg3.png)

Let's define the content of the push notification.

Click the **Title** text field.

![Journey Optimizer](./images/msg5.png)

In the text area start writing **Hi**.

![Journey Optimizer](./images/msg6.png)

The title is not done yet. Next you need to bring in the personalization token for the field **First name** which is stored under `profile.person.name.firstName`. In the left menu, scroll down to find the **Person** element and click on the arrow to go a level deepern until you reach the field `profile.person.name.firstName`. Click **Save**.

![Journey Optimizer](./images/msg7.png)

You'll then be back here. Click the field **Body**. 

![Journey Optimizer](./images/msg11.png)

In the text area, write `Welcome at the `. Then, click **Save**. You'll come back to this message later to add more context.

![Journey Optimizer](./images/msg12.png)

You've now completed the draft version of your push notification. Don't publish your message yet, you'll do that at a later stage.

You have finished this exercise.

Next Step: [3.4 Create your journey](./ex4.md)

[Go Back to User Flow 3](./uc3.md)

[Go Back to All Modules](../../overview.md)
