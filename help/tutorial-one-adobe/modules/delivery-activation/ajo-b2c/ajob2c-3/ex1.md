---
title: Getting Started with push notifications
description: Getting Started with push notifications
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
---
# 3.3.1 Getting Started with push notifications

In order to use push notifications with Adobe Journey Optimizer, there are a number of settings to check and know about.

Here are all the settings to verify:

- Datasets and schemas in Adobe Experience Platform
- Datastream for mobile
- Data collection property for mobile
- App surface for push certificates
- Test your push setup using AEP Assurance

Let's review these one by one.

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxName--`. You'll then be in the **Home** view of your sandbox `--aepSandboxName--`.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

## 3.3.1.1 Push dataset

Adobe Journey Optimizer uses datasets to store things like the push tokens from mobile devices or interactions with push messages (such as: message sent, message opened, etc) in a dataset in Adobe Journey Optimizer.

You can find these datasets by going to **Datasets** in the menu on the left side of your screen. To show system datasets, click the **Enable filters** icon.

Enable the option for **System** and search for **AJO**. You'll then see the datasets used for push notifications.

![Data Ingestion](./images/menudsjo1.png)

## 3.3.1.2 Datastream for Mobile

Go to [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). 

In the left menu, go to **Datastreams** and search for your datastream that you created in [Getting Started](./../../../../modules/getting-started/gettingstarted/ex2.md), which is named `--aepUserLdap-- - One Adobe Datastream (Mobile)`. Click to open it.

![Datastreams](./images/edgeconfig1a.png)

Click **Edit** on the **Adobe Experience Platform** service.

![Datastreams](./images/edgeconfig1.png)

You'll then see the datastream settings that were defined, and into which datasets events and profile attributes will be stored.

You should also enable the following options if they aren't enabled yet:

- **Offer Decisioning**
- **Personalization Destinations**
- **Adobe Journey Optimizer**

Click **Save**.

![Name the Datastream and save](./images/edgeconfig2.png)

## 3.3.1.3 Review your Data Collection property for Mobile

Go to [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/), to **Tags**. As part of the [Getting Started](./../../../../modules/getting-started/gettingstarted/ex1.md) module, Data Collection Tags properties were created. 

You've been using these Data Collection Tags properties already as part of previous modules. 

Click to open the Data Collection property for mobile.

![DSN](./images/launchprop.png)

In your Data Collection property, go to **Extensions**. You'll then see the various extensions that are needed for the mobile app. Click to select the extension **Adobe Experience Platform Edge Network** and then select **Configure**.

![Adobe Experience Platform Data Collection](./images/launchprop1.png)

You'll then see that your datastream for mobile is linked here. Next, click **Cancel** to go back to the extensions overview.

![Adobe Experience Platform Data Collection](./images/launchprop2.png)

You'll then be back back here. You'll see the extension for **AEP Assurance**. AEP Assurance helps you inspect, proof, simulate, and validate how you collect data or serve experiences in your mobile app. You can read more about AEP Assurance here: [https://experienceleague.adobe.com/en/docs/experience-platform/assurance/home](https://experienceleague.adobe.com/en/docs/experience-platform/assurance/home).

![Adobe Experience Platform Data Collection](./images/launchprop8.png)

Next, click **Configure** to open the extension **Adobe Journey Optimizer**. This extension enables push notifications and measurement for Adobe Journey Optimizer.

![Adobe Experience Platform Data Collection](./images/launchprop9.png)

You'll then see that this is where the dataset for tracking push events is linked. There's no need to make any changes to your Data Collection property. Click **Cancel** to go back to the previous screen.

![Adobe Experience Platform Data Collection](./images/launchprop10.png)

## 3.3.1.4 Review your App Surface setup

Go to [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). In the left menu, go to **App Surfaces** and open the App Surface for **DX Demo App APNS**.

![Adobe Experience Platform Data Collection](./images/appsf.png)

You'll then see the configured App Surface for iOS and Android.

![Adobe Experience Platform Data Collection](./images/appsf1.png)

## 3.3.1.5 Test push notification setup using AEP Assurance.

You already installed the **DX Demo** mobile application as part of the **Getting Started** module. Once the app is installed, you'll find it on your device's home screen. Click the icon to open the app.

![DSN](./../../../../modules/getting-started/gettingstarted/images/mobileappn1.png)

When you're using the app the first time, you'll be requested to log in using your Adobe ID. Complete the login process.

![DSN](./../../../modules/../getting-started/gettingstarted/images/mobileappn2.png)

After logging in, you'll see a notification requesting your permission to send notifications. We'll send notifications as part of the tutorial, so click **Allow**.

![DSN](./../../../modules/../getting-started/gettingstarted/images/mobileappn3.png)

You'll then see the app's homepage. Go to **Settings**.

![DSN](./../../../modules/../getting-started/gettingstarted/images/mobileappn4.png)

In settings, you'll see that currently a **Public Project** is loaded in the app. Click **Custom Project**.

![DSN](./../../../modules/../getting-started/gettingstarted/images/mobileappn5.png)

You can now load a custom project. Click the QR code to easily load your project.

![DSN](./../../../modules/../getting-started/gettingstarted/images/mobileappn6.png)

After going through the **Getting Started** section, you had this result. Click to open the **Mobile Retail project** that was created for you.

![DSN](./../../../modules/../getting-started/gettingstarted/images/dsn5b.png)

In case you had accidentally closed your browser window, or for future demo or enablement sessions, you can also access your website project by going to [https://dsn.adobe.com/projects](https://dsn.adobe.com/projects). After logging in with your Adobe ID, you'll see this. Click your mobile app project to open it.

![DSN](./../../../modules/../getting-started/gettingstarted/images/web8a.png)

Next, click **Run**.

![DSN](./images/web8b.png)

You'll then see this popup, which contains a QR code. Scan this QR-code from within the mobile app.

![DSN](./../../../modules/../getting-started/gettingstarted/images/web8c.png)

You'll then see your project ID show in the app, after which you can click **Save**.

![DSN](./../../../modules/../getting-started/gettingstarted/images/mobileappn7.png)

Now, go back to **Home** in the app. Your app is now ready to be used.

![DSN](./../../../modules/../getting-started/gettingstarted/images/mobileappn8.png)

You now need to scan a QR code to connect your mobile device to your AEP Assurance session. 

To start an AEP Assurance session, Go to [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). Click **Assurance** in the left menu. Then, click **Create Session**.

![Adobe Experience Platform Data Collection](./images/griffon3.png)

Select **Deep link connect** and then click **Start**.

![Adobe Experience Platform Data Collection](./images/griffon5.png)

Fill out the values:

- Session Name: `--aepUserLdap-- - Push Debugging`
- Base URL: `dxdemo://default`

Click **Next**.

![Adobe Experience Platform Data Collection](./images/griffon4.png)

You'll then see a QR code on your screen, which you should scan with your iOS device.

![Adobe Experience Platform Data Collection](./images/griffon6.png)

On your mobile device, open the camera app and scan the QR code that is displayed by Assurance.

![Adobe Experience Platform Data Collection](./images/ipadPushTest8a.png)

You'll then see a popup screen, asking you to enter the PIN-code. Copy the PIN-code from your AEP Assurance screen and click **Connect**.

![Adobe Experience Platform Data Collection](./images/ipadPushTest9.png)

You'll then see this.

![Adobe Experience Platform Data Collection](./images/ipadPushTest11.png)

In Assurance, you'll now see that a client device is  connected to the Assurance session. Next, click **Configure**.

![Adobe Experience Platform Data Collection](./images/griffon7.png)

Scroll down to **Push Debug**. Click the **+** icon and then click **Save**. 

![Adobe Experience Platform Data Collection](./images/griffon7a.png)

Go to **Push Debug**. You should see this.

![Adobe Experience Platform Data Collection](./images/griffon10.png)

Some explanation:

- The first column, **Client**, shows the available identifiers on your iOS device. You'll see an ECID and a Push Token.
- The 2nd column shows the **App Store Credentials & Configuration**
- The second column shows **Profile** information, with additional info on what platform the Push Token lives in (APNS or APNSSandbox). If you click the **Inspect Profile** button, you'll be taken to Adobe Experience Platform and you'll see the full Real-time Customer Profile.

To test your Push configuration setup, go to **Send Test Push Setup** button. Click **Send Test Push Notification**

![Adobe Experience Platform Data Collection](./images/griffon11.png)

You need to make sure that the **DX Demo** app isn't open at the time of clicking the **Send Push Notification** button. If the app is open, the push notification might be received in the background and wouldn't be visible.

You'll then see a push notification like this one appear on your mobile device.

![Adobe Experience Platform Data Collection](./images/ipadPush2.png)

If you've received the push notification, that means that your setup is correct and working fine and you can now create a real journey that will result in sending a push message from Journey Optimizer. 

## Next Steps

Go to [3.3.2 Configure a journey with push messages](./ex2.md){target="_blank"}

Go back to [Adobe Journey Optimizer: Push and In-app Messages](ajopushinapp.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
