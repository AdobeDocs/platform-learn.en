---
title: GenStudio for Performance Marketing Campaign Activation to Meta
description: GenStudio for Performance Marketing Campaign Activation to Meta
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 9837c076-e6ca-47a0-96b9-5fa5fdba3fd2
---
# 1.3.4 Create Email Experience for AJO

>[!IMPORTANT]
>
>In order to complete this exercise, you need to have access to an Adobe Journey Optimizer environment that is provisioned for the integration with GenStudio for Performance Marketing, which is currently in beta.

>[!IMPORTANT]
>
>In order to execute all steps in this exercise, you need to have access to an existing Adobe Workfront environment, and in that environment you need to have created a project and an approval workflow. If you follow exercise [Workflow Management with Adobe Workfront](./../../../modules/asset-mgmt/module2.2/workfront.md){target="_blank"} you wil have the required setup available.

## 1.3.4.1 Create & Approve Email Experience

In the left menu, go to **Create**. Select **Email**. 

![GSPeM](./images/gsemail1.png)

Select the **Email** template that you imported before, which is named `--aepUserLdap---citisignal-email-template`. Click **Use**.

![GSPeM](./images/gsemail2.png)

You should then see this. Change the name of your ad to `--aepUserLdap-- - Email Online Gamers Fiber Max`.

![GSPeM](./images/gsemail3.png)

Under **Paramaters**, select the following options:

- **Brand**: `--aepUserLdap-- - CitiSignal`
- **Language**: `English (US)`
- **Persona**: `--aepUserLdap-- - Smart Home Families`
- **Product**: `--aepUserLdap-- - CitiSignal Fiber Max`

Click **Select from Content**.

![GSPeM](./images/gsemail4.png)

Select the asset `--aepUserLdap-- - neon rabbit.png`. Click **Use**.

![GSPeM](./images/gsemail5.png)

Enter the prompt `convince online gamers to start playing online multiplayer games using CitiSignal internet` and click **Generate**.

![GSPeM](./images/gsemail6.png)

You should then see something like this, with 4 email variations being generated. The defautl view shows the **mobile** view, you can switch to the desktop view by clicking the **computer** icon.

![GSPeM](./images/gsemail7.png)

For every email, a compliancy score is automatically calculated. Click the score to see more details.

![GSPeM](./images/gsemail8.png)

Click **View and fix issues**.

![GSPeM](./images/gsemail9.png)

You can then see more detail as to what you can do to optimize the complicancy score.

![GSPeM](./images/gsemail10.png)

Next, click **Request approval**, which will connect to Adobe Workfront.

![GSPeM](./images/gsemail11.png)

Select your Adobe Workfront project, which should be named `--aepUserLdap-- - CitiSignal Fiber Launch`. Enter your own email address under **Invite people** and ensure your role is set to **Approver**.

![GSPeM](./images/gsemail12.png)

Alternatively, you can also use an existing approval workflow in Adobe Workfront. To do that, click **Use template** and select the template `--aepuserLdap-- - Approval Workflow`. Click **Send**.

![GSPeM](./images/gsemail13.png)

Click **View comments in Workfront**, you'll now be sent to the Adobe Workfront Proof UI.

![GSPeM](./images/gsemail14.png)

In the Adobe Workfront Proof UI, click **Make decision**.

![GSPeM](./images/gsemail15.png)

Select **Approved** and click **Make decision**.

![GSPeM](./images/gsemail16.png)

Click **Publish**.

![GSPeM](./images/gsemail17.png)

Select your Campaign `--aepUserLdap-- - CitiSignal Fiber Launch Campaign` and click **Publish**.

![GSPeM](./images/gsemail18.png)

Click **Open in Content**.

![GSPeM](./images/gsemail19.png)

The 4 email experiences are now available under **Content** > **Experiences**.

![GSPeM](./images/gsemail20.png)

## 1.3.4.2 Create a Campaign in AJO

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](./../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxName--`. You'll then be in the **Home** view of your sandbox `--aepSandboxName--`.

![ACOP](./../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

You'll now create a campaign. Unlike the event-based journey of the previous exercise which relies on incoming experience events or audience entries or exits to trigger a journey for 1 specific customer, campaigns target a whole audience once with unique content like newsletters, one-off promotions, or generic information or periodically with similar content sent on a regular basis like for instance birthday campaigns and reminders. 

In the menu, go to **Campaigns** and click **Create campaign**.

![Journey Optimizer](./images/gsemail21.png)

Select **Scheduled - Marketing** and click **Create**.

![Journey Optimizer](./images/gsemail22.png)

On the campaign creation screen, configure the following:

- **Name**: `--aepUserLdap--  - Online Gamers CitiSignal Fiber Max`.
- **Description**: Fiber campaign for Online Gamers

Click **Actions**.

![Journey Optimizer](./images/gsemail23.png)

Click **+ Add Action** and then select **Email**.

![Journey Optimizer](./images/gsemail24.png)

Then, select an existing **Email configuration** and then click **Edit content**.

![Journey Optimizer](./images/gsemail25.png)

You'll then see this. For the **Subject line**, use this: 

```
{{profile.person.name.firstName}}, say goodbye to delays!
```

Next, click **Edit content**.

![Journey Optimizer](./images/gsemail26.png)

Click **Import HTML**.

![Journey Optimizer](./images/gsemail27.png)

Next, click the button for **Adobe GenStudio for Performance Marketing**.

![Journey Optimizer](./images/gsemail28.png)

You should then see a popup window which shows all of the email experiences that were published in GenStudio for Performance Marketing. Select one of the available email experiences and click **Use**.

![Journey Optimizer](./images/gsemail29.png)

Select your own AEM Assets CS repository, which should be named `--aepUserLdap-- - CitiSignal dev`, and click **Import**.

![Journey Optimizer](./images/gsemail30.png)

You should then see this. Select the missing image button and click **Select an asset**.

![Journey Optimizer](./images/gsemail31.png)

Go to the folder that looks like this one, starting with **GenStudio.zip.....** and select the image `--aepUserLdap-- - neon rabbit.png`. CLick **Select**

![Journey Optimizer](./images/gsemail32.png)

You should then see this.

![Journey Optimizer](./images/gsemail33.png)

Scroll down to the footer, select the word **Unsubscribe** and click the **link** icon.

![Journey Optimizer](./images/gsemail38.png)

Set the **Type** to **External Opt-out/Unsubscription** and set the url to `https://techinsiders.org/unsubscribe.html` (it's not allowed to have a blank URL for the unsubscribe link).

Click **Save** and then click the **arrow** in the top lmeft corner of your screen to go back to the campaign configuration.

![Journey Optimizer](./images/gsemail39.png)

Go to **Audience**.

![Journey Optimizer](./images/gsemail34.png)

Click **Select audience**.

![Journey Optimizer](./images/gsemail35.png)

Select the audience of the subscription list for Online Gamers, which should be named `--aepUserLdap--_SL_Interest_Online_Gaming`. Click **Save**.

![Journey Optimizer](./images/gsemail36.png)

Click **Review to activate**.

![Journey Optimizer](./images/gsemail37.png)

If your campaign configuration has no issues, you'll be able to click **Activate**.

![Journey Optimizer](./images/gsemail40.png)

Your campaign will then be activated, which takes a couple of minutes.

![Journey Optimizer](./images/gsemail41.png)

After a couple of minutes, the campaign is live and the email will be sent to the subscription list that you selected.

![Journey Optimizer](./images/gsemail42.png)

You've now completed this exercise.

## Next Steps

Go to [Summary & benefits](./summary.md){target="_blank"}

Go back to [GenStudio for Performance Marketing](./genstudio.md){target="_blank"}

Go back to [All Modules](./../../../overview.md){target="_blank"}
