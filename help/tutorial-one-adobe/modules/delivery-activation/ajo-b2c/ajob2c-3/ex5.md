---
title: Offer Decisioning - Use your decision in an email
description: Use your decision in an email
kt: 5342
doc-type: tutorial
exl-id: c94b4ed4-0122-4cfd-a69f-40ae2063d449
---
# 3.3.5 Use your decision in an email

In this exercise, you'll use your decision to personalize the delivery of an email and SMS.

Go to **Journeys**. Find the journey you created in exercise 3.1.3, which is named `--aepUserLdap-- - Registration Journey`. Click your journey to open it. 

![Journey Optimizer](./images/emailoffer1.png)

You'll then see this. Click **... More** and then click **Create a new version**.

![Journey Optimizer](./images/journey1.png)

Click **Create a new version**.

![Journey Optimizer](./images/journey2.png)

Click the **Email** action and then click **Edit content**.

![Journey Optimizer](./images/journey3.png)

You'll then see the message dashboard. Click **Edit email body**.

![Journey Optimizer](./images/emailoffer2.png)

You'll then see this. Drag a new **1:1 column** structure component onto the canvas.

![Journey Optimizer](./images/emailoffer6.png)

In the menu, go to **Contents**. Select the **Offer decision** component and drag and drop this component in the email's content offer placeholder as indicated. Then, click **Add**.

![Journey Optimizer](./images/emailoffer7.png)

Select the type of placement that you want to include in the email. In the **Placements** dropdown menu select **Email - Image**, then select your decision `--aepUserLdap-- - CitiSignal Decision`. Click **Add**.

![Journey Optimizer](./images/emailoffer8.png)

You can now cycle through all personalized offers and the fallback offer, all of them being visualized inside the email designer. Click **Save**.

![Journey Optimizer](./images/emailoffer9.png)

Now, click the arrow to go back to the previous screen.

![Journey Optimizer](./images/emailoffer13.png)

Click the arrow in the top left corner to go back to your journey.

![Journey Optimizer](./images/emailoffer14.png)

Click **Save** to close your **Email** action.

![Journey Optimizer](./images/emailoffer14a.png)

Click **Publish** to publish your updated journey.

![Journey Optimizer](./images/emailoffer14b.png)

Confirm by clicking **Publish** again.

![Journey Optimizer](./images/emailoffer15.png)

Your message is now published.

![Journey Optimizer](./images/emailoffer16.png)

When you create a new account on the demo website, you'll now get this email:

![Journey Optimizer](./images/emailoffer17.png)

You have finished this exercise. 

## Next Steps

Go to [3.3.6 Test your Decision using the API](./ex6.md){target="_blank"}

Go back to [Offer Decisioning](offer-decisioning.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
