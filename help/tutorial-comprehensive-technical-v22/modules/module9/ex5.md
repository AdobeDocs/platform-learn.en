---
title: Offer Decisioning - Use your decision in an email
description: Use your decision in an email
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 0fb8c244-1025-479f-b82e-374d1aa5e4dc
---
# 9.5 Use your decision in an email

In this exercise, you'll use your decision to personalize the delivery of an email and SMS.

Go to **Messages**. Find the message that you have created in a previous exercise; which is named `--demoProfileLdap-- - Registration Email`. Click your message to open it. 

![Journey Optimizer](./images/emailoffer1.png)

You'll then see the message dashboard. Click **Modify**. 

![Journey Optimizer](./images/emailoffer2.png)

Click **Confirm**.

![Journey Optimizer](./images/emailoffer3.png)

Click **Email Designer**.

![Journey Optimizer](./images/emailoffer4.png)

You'll then see this.

![Journey Optimizer](./images/emailoffer5.png)

You'll then see this.

![Journey Optimizer](./images/emailoffer6.png)

In the menu, go to **Content Components**. Select the **Offer decision** component and drag and drop this component in the email's content offer placeholder as indicated. Then, click **Add**.

![Journey Optimizer](./images/emailoffer7.png)

Select the type of placement that you want to include in the email. In the **Placements** dropdown menu select **Email - Image**, then select your decision `--demoProfileLdap-- - Luma Decision`. Click **Add**.

![Journey Optimizer](./images/emailoffer8.png)

You now see all personalized offers and the fallback offer being visualized inside the email designer. Click  **Preview** to preview the email message with a real customer profile.

![Journey Optimizer](./images/emailoffer9.png)

Start by identifying which profile you want to use for the preview. Select the **email** namespace and enter the email address of a customer profile you've created on the demo website. Next, click **Preview**.

![Journey Optimizer](./images/emailoffer10.png)

Once the email has been displayed and the offer is correctly displayed click on the **Close** button.

![Journey Optimizer](./images/emailoffer11.png)

Finally, click **Save**.

![Journey Optimizer](./images/emailoffer12.png)

Now, click the arrow to go back to the previous screen.

![Journey Optimizer](./images/emailoffer13.png)

Click **Publish** to publish your message again.

![Journey Optimizer](./images/emailoffer14.png)

Confirm by clicking **Publish** again.

![Journey Optimizer](./images/emailoffer15.png)

Your message is now published.

![Journey Optimizer](./images/emailoffer16.png)

When you create a new account on the demo website, you'll now get this email:

![Journey Optimizer](./images/emailoffer17.png)

You have finished this exercise. 

Next Step: [9.6 Test your Decision using the API](./ex6.md)

[Go Back to Module 9](./offer-decisioning.md)

[Go Back to All Modules](./../../overview.md)
