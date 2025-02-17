---
title: Adobe Journey Optimizer - Apply personalization in an email message
description: This exercise explains how to use segment personalization within an email content
kt: 5342
doc-type: tutorial
---
# 3.4.3 Apply segment-based personalization in an email message

Login to Adobe Experience Cloud by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Adobe Journey Optimizer**.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

You'll be redirected to the **Home** view in Journey Optimizer. Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepTenantId--``. 

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

## 3.4.3.1 Segment-based personalization

In this exercise you'll improve the newsletter email message that you created in the previous exercise with a personalized text based on segment membership.

Go to **Campaigns**. Find the newsletter journey that you have created in the previous exercise. Search for `--aepUserLdap-- - CitiSignal Newsletter`. Right-click on the 3 dots **...** and click **Duplicate**.

![Journey Optimizer](./images/sbp1.png)

You'll then see this. Use this for the **Title**: `--aepUserLdap-- - CitiSignal Newsletter (SBP)`. Click **Duplicate**. 

![Journey Optimizer](./images/sbp2.png)

Click the duplicated campaign to open it.

![Journey Optimizer](./images/sbp3.png)

Click **Edit** to change the content.

![Journey Optimizer](./images/sbp3a.png)

Click **Edit email body**.

![Journey Optimizer](./images/sbp4.png)

You'll then see this.

![Journey Optimizer](./images/sbp5.png)

Open **Content Components** and drag a **1:1 column** above the AirPods offer. 

![Journey Optimizer](./images/sbp6.png)

Drag and drop a **Text** component into that 1:1 column.

![Journey Optimizer](./images/sbp6a.png)

Select the whole default text and delete it. Then click on the **Add personalization** button in the toolbar.

![Journey Optimizer](./images/sbp7.png)

You'll then see this. In the left menu, click **Audiences**.

![Journey Optimizer](./images/seg1.png)

Select the segment `--aepUserLdap-- - Interest in Plans` and click the **+** icon to add it to the canvas.

![Journey Optimizer](./images/seg3.png)

You should then leave the first line as it is, and replace line 2 and 3 by this code:

``
    PS: It may be a good idea to check if your plan still meets your needs! Click here to be contacted by one of our experts!
{%else%}
    PS: Thanks for taking the time to read our newsletter. Here is a 10% promo code to use on the website: NEWSLETTER10
{%/if%}
``

You'll then have this. Click **Save**.

![Journey Optimizer](./images/seg4.png)

Change the text alignment to **Center alignment**. 

![Journey Optimizer](./images/sbp9.png)

You can now save this message by clicking the **Save** button in the top-right corner. Then, click **arrow** next to the subject line text in the top-left corner.

![Journey Optimizer](./images/sbp9a.png)

Click **Review to activate**.

![Journey Optimizer](./images/oc79afff.png)

Click **Activate**.

![Journey Optimizer](./images/oc79bfff.png)

Your newsletter with segment-based personalization is now published. Your newsletter email message will be sent based on your schedule and your journey will stop as soon as the last email has been sent.

If you qualify for the segment that was used, you'll see this in the email that you'll receive:

![Journey Optimizer](./images/sbp20fff.png)

You have finished this exercise.

## Next Steps

Go to [3.4.4 Setup and use push notifications for iOS](./ex4.md){target="_blank"}

Go back to [Adobe Journey Optimizer](journeyoptimizer.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}