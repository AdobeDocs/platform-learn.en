---
title: Adobe Journey Optimizer - Configure and use the SMS channel within Adobe Journey Optimizer
description: Adobe Journey Optimizer - Configure and use the SMS channel within Adobe Journey Optimizer
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 1a08f666-4ea3-43bc-ace7-5dc9854b89ad
---
# 8.4 Create your SMS messages

In this exercise, you'll create SMS messages by making use of Adobe Journey Optimizer.

For this use case, the goal is to send different SMS messages based on the weather conditions of the location of your customer. 3 scenarios have been defined:

- Colder than 10° Celsius
- Between 10° and 25° Celsius
- Warmer than 25° Celsius

For these 3 conditions, you'll need to define 3 SMS messages in Adobe Journey Optimizer.

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxId--`. To change from one sandbox to another, click on **PRODUCTION Prod (VA7)** and select the sandbox from the list. In this example, the sandbox is named **AEP Enablement FY22**. You'll then be in the **Home** view of your sandbox `--aepSandboxId--`.

![ACOP](../module7/images/acoptriglp.png)

## 8.4.1 Message 1: Colder than 10° Celsius

In the left menu, go to **Messages** and click **Create Message**.

![AJO](./images/sms1.png)

Give your Message a title following this naming convention `--demoProfileLdap-- - Weather <10`, select the **SMS Preset** and enable the **SMS** channel. Click on the **Create** button to create your SMS message.

![Journey Optimizer](./images/sms2.png)

The next screen is the message dashboard, where you can configure the text of your SMS. Click the **Compose message** area to create your message.

![Journey Optimizer](./images/sms3.png)

Enter the following text: `Brrrr... {{profile.person.name.firstName}}, it's freezing. 20% discount on jackets today!`. Click **Save**.

![Journey Optimizer](./images/sms4.png)

This message is now ready. Click **Publish**.

![Journey Optimizer](./images/sms5.png)

Click **Publish** again.

![Journey Optimizer](./images/sms6.png)

Your message is now published and can be used in a journey.

![Journey Optimizer](./images/sms7.png)

## 8.4.2 Message 2: Between 10° and 25° Celsius

Go to **Messages** and click **Create Message** again.

![AJO](./images/sms1a.png)

Give your Message a title following this naming convention `--demoProfileLdap-- - Weather 10-25`, select the **SMS Preset** and enable the **SMS** channel. Click on the **Create** button to create your SMS message.

![Journey Optimizer](./images/sms2a.png)

The next screen is the message dashboard, where you can configure the text of your SMS. Click the **Compose message** area to create your message.

![Journey Optimizer](./images/sms3a.png)

Enter the following text: `What a nice weather for the time of year, {{profile.person.name.firstName}} - 20% discount on Sweaters today!`. Click **Save**.

![Journey Optimizer](./images/sms4a.png)

This message is now ready. Click **Publish**.

![Journey Optimizer](./images/sms5a.png)

Click **Publish** again.

![Journey Optimizer](./images/sms6a.png)

Your message is now published and can be used in a journey.

![Journey Optimizer](./images/sms7a.png)

## 8.4.3 Message 3: Warmer than 25° Celsius

Go to **Messages** and click **Create Message** again.

![AJO](./images/sms1ab.png)

Give your Message a title following this naming convention `--demoProfileLdap-- - Weather >25`, select the **SMS Preset** and enable the **SMS** channel. Click on the **Create** button to create your SMS message.

![Journey Optimizer](./images/sms2ab.png)

The next screen is the message dashboard, where you can configure the text of your SMS. Click the **Compose message** area to create your message.

![Journey Optimizer](./images/sms3ab.png)

Enter the following text: `So warm, {{profile.extendedWorkDetails.assistantDetails.name.firstName}}! 20% discount on swimwear today!`. Click **Save**.

![Journey Optimizer](./images/sms4ab.png)

This message is now ready. Click **Publish**.

![Journey Optimizer](./images/sms5ab.png)

Click **Publish** again.

![Journey Optimizer](./images/sms6ab.png)

Your message is now published and can be used in a journey.

![Journey Optimizer](./images/sms7ab.png)

You can now proceed by creating your journey.

Next Step: [8.5 Design a trigger-based journey](./ex5.md)

[Go Back to Module 8](journey-orchestration-external-weather-api-sms.md)

[Go Back to All Modules](../../overview.md)
