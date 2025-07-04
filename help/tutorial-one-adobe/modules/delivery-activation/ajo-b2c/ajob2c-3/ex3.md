---
title: Offer Decisioning - Test your Decision
description: Offer Decisioning - Test your Decision
kt: 5342
doc-type: tutorial
---
# 3.3.3 Configure a campaign with in-app messages

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxName--`. You'll then be in the **Home** view of your sandbox `--aepSandboxName--`.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

## 3.3.3.1 In-app Messages Channel configuration

In the left menu, go to **Channels** and then select **Channel configurations**. Click **Create channel configuration**.

![InApp](./images/inapp1.png)

Enter the name: `--aepUserLdap--_In-app_Messages`, select the channel **In-app messaging** and then enable the platforms **Web**, **iOS** and **Android**.

![InApp](./images/inapp2.png)

Scroll down, you should then see this.

![InApp](./images/inapp3.png)

Ensure that **Single page** is enabled.

For **Web**, enter the URL of the website that was created earlier as part of the **Getting Started** module, which looks like this: `https://dsn.adobe.com/web/--aepUserLdap---XXXX`. Don't forget to change the **XXXX** to the unique code of your website.

For **iOS** and **Android**, enter `com.adobe.dsn.dxdemo`.

![InApp](./images/inapp4.png)

Scroll up and click **Submit**.

![InApp](./images/inapp5.png)

Your channel configuration is now ready to be used.

![InApp](./images/inapp6.png)

## 3.3.3.2 Configure a scheduled campaign for In-app Messages

In the left menu, go to **Campaigns** and then click **Create campaign**.

![InApp](./images/inapp7.png)

Select **Scheduled - Marketing** and then click **Create**.

![InApp](./images/inapp8.png)

Enter the name `--aepUserLdap-- - CitiSignal Fiber Max` and then click **Actions**.

![InApp](./images/inapp9.png)

Click **+ Add action** and then select **In-app message**.

![InApp](./images/inapp10.png)

Select the in-app message channel configuration that you created in the previous step, which is named: `--aepUserLdap--_In-app_Messages`. Click **Edit content**.

![InApp](./images/inapp11.png)

You should then see this. Click **Modal**.

![InApp](./images/inapp12.png)

Click **Change layout**.

![InApp](./images/inapp13.png)

Click the **Media URL** icon to pick an assets from AEM Assets.

![InApp](./images/inapp14.png)

Go to the folder **citisignal-images** and select the image file **neon-rabbit.jpg**. Click **Select**.

![InApp](./images/inapp15.png)

For the **Header** text, use: `CitiSignal Fiber Max`.
For the **Body** text, use: `Conquer lag with Fiber Max`.

![InApp](./images/inapp16.png)

Set the **Button #1 text** to: `Go to Plans`. 
Set the **target** to `com.adobe.dsn.dxdemo://plans`.

Click **Review to activate**.

![InApp](./images/inapp17.png)

Click **Activate**.

![InApp](./images/inapp18.png)

The status of your campaign is now set to **Activating**. It may take a couple of minutes before the campaign is live.

![InApp](./images/inapp19.png)

Once the status has changed to **Live**, you can test your campaign.

![InApp](./images/inapp20.png)

## 3.3.3.3 Test your In-app Messaging campaign on mobile

On your mobile device, open the app. You should then see the new in-app message appear after launching the app. Click the button **Go to Plans**.

![InApp](./images/inapp21.png)

You'll then be taken to the **Plans** page.

![InApp](./images/inapp22.png)

## Next Steps

Go to [Summary and benefits](./summary.md){target="_blank"}

Go back to [Adobe Journey Optimizer: Push and In-app Messages](ajopushinapp.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
