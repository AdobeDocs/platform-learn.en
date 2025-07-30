---
title: GenStudio for Performance Marketing Campaign Activation to Meta
description: GenStudio for Performance Marketing Campaign Activation to Meta
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
---
# 1.3.3 Campaign Activation to Meta

>[!IMPORTANT]
>
>In order to complete this exercise, you need to have access to a working AEM Assets CS Author environment with AEM Content Hub enabled. If you follow exercise [Adobe Experience Manager Cloud Service & Edge Delivery Services](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"} you wil have access to such an environment.

>[!IMPORTANT]
>
>In order to execute all steps in this exercise, you need to have access to an existing Adobe Workfront environment, and in that environment you need to have created a project and an approval workflow. If you follow exercise [Workflow Management with Adobe Workfront](./../../../modules/workflow-planning/module1.2/workfront.md){target="_blank"} you wil have the required setup available.

>[!IMPORTANT]
>
>If you have previously configured an AEM Assets CS Program with an Author and AEM Assets environment, it may be that your AEM CS sandbox was hibernated. Given that dehibernating such a sandbox takes 10-15 minutes, it would be a good idea to start the dehibernation process now so that you don't have to wait for it at a later time.

## 1.3.3.1 Create campaign

In **GenStudio for Performance Marketing**, go to **Campaigns** in the left menu. Click **+ Add campaign**.

![GSPeM](./images/gscampaign1.png)

You should then see an empty campaign overview.

![GSPeM](./images/gscampaign2.png)

For the field name, use `--aepUserLdap-- - CitiSignal Fiber Launch Campaign`.

For the field **Description**, use the below text.

```
The CitiSignal Fiber Launch campaign introduces CitiSignal’s flagship fiber internet service—CitiSignal Fiber Max—to key residential markets. This campaign is designed to build awareness, drive sign-ups, and establish CitiSignal as the go-to provider for ultra-fast, reliable, and future-ready internet. The campaign will highlight the product’s benefits for remote professionals, online gamers, and smart home families, using persona-driven messaging across digital and physical channels.
```

For the field **Objective**, use the below text.

```
Generate brand awareness in target regions
Drive early sign-ups and pre-orders for CitiSignal Fiber Max
Position CitiSignal as a premium, customer-first fiber internet provider
Educate consumers on the benefits of fiber over cable or DSL
```

For the field **Key Messaging**, use the below text.

```
Supporting Points:
Symmetrical speeds up to 2 Gbps
Whole-home Wi-Fi 6E coverage
99.99% uptime guarantee
24/7 concierge support
No data caps or throttling
 Channels:
Digital Advertising: Google Display, YouTube pre-roll, Meta (Facebook/Instagram), TikTok (for gamers)
Email Marketing: Persona-segmented drip campaigns
Social Media: Organic and paid posts with testimonials, speed demos, and influencer partnerships
Out-of-Home (OOH): Billboards, transit ads in suburban commuter corridors
Local Events: Pop-up booths at tech expos, family festivals, and gaming tournaments
Direct Mail: Personalized flyers with QR codes for early sign-up discounts
 
Target Regions:
Primary Launch Markets:
Denver Metro Area, CO
Austin, TX
Raleigh-Durham, NC
Salt Lake City, UT
Demographic Focus:
Suburban neighborhoods with high remote work density
Areas with high smart home adoption
Zip codes with underserved or dissatisfied cable customers
```

You should then have this:

![GSPeM](./images/gscampaign3.png)

Scroll down to see more fields:

![GSPeM](./images/gscampaign4.png)

For the field **Start**, set it to today's date.

For the field **End**, set it to a date 1 month from now.

For the field **Status**, set it to **Active**.

For the field **Channels**, set it to **Meta**, **Email**, **Paid Media**, **Display**.

For the field **Regions**, select a region of choice.

For the field For the field **References** > **Products**: choose the product `--aepUserLdap-- - CitiSignal Fiber Max`.

**References** > **Personas**: choose the personas `--aepUserLdap-- - Remote Professionals`, `--aepUserLdap-- - Online Gamers`, `--aepUserLdap-- - Smart Home Families`

You should then see this:

![GSPeM](./images/gscampaign5.png)

Your campaign is now ready. Click the **arrow** to go back.

![GSPeM](./images/gscampaign6.png)

You will then see your campaign in the list. Click the calendar view icon to change the view to the campaign calendar.

![GSPeM](./images/gscampaign7.png)

You should then see a campaign calendar which gives a more visual idea of which campaigns are active at which moment.

![GSPeM](./images/gscampaign8.png)

## 1.3.3.2 Setup connection to Meta

>[!IMPORTANT]
>
>In order to setup your connection to Meta, you need to have a Meta user account available and that user account needs to be added to a Meta Business account.

To setup the connection to Meta, click the 3 dots **...** and select **Settings**.

![GSPeM](./images/gsconnection1.png)

Click **Connect** for **Meta Ads**.

![GSPeM](./images/gsconnection2.png)

Log in using your Meta account. Click **Continue**.

![GSPeM](./images/gsconnection3.png)

If your account is linked to a Meta Business Account, you'll be able to select  the business portfolio that has been configured in Meta.

![GSPeM](./images/gsconnection5.png)

Once the connection has been successfully established, click the line that says **X connected account(s)**.

![GSPeM](./images/gsconnection4.png)

You should then see the details of the Meta Business Account that is connected to GenStudio for Performance Marketing.

![GSPeM](./images/gsconnection6.png)

## 1.3.3.3 Create new asset

Go to [https://firefly.adobe.com/](https://firefly.adobe.com/){target="_blank"}. Enter the prompt `a neon rabbit running very fast through space` and click **Generate**.

![GSPeM](./images/gsasset1.png)

You will then see several images being generated. Choose the image you like the most, click the **Share** icon on the image and then select **Open in Adobe Express**.

![GSPeM](./images/gsasset2.png)

You will then see the image you just generated become available in Adobe Express for editing. You now need to add the CitiSignal logo on the image. To do that, go to **Brands**.

![GSPeM](./images/gsasset3.png)

You should then see the CitiSignal brand template that you created in GenStudio for Performance Marketing appear in Adobe Express. Click to select your brand template which should be named `--aepUserLdap-- - CitiSignal`.

![GSPeM](./images/gsasset4.png)

Go to **Logos** and click the **white** Citisignal logo to drop it on the image.

![GSPeM](./images/gsasset5.png)

Position the CitiSignal logo at the top of your image, not too far from the middle.

![GSPeM](./images/gsasset6.png)

Next, click **Share**.

![GSPeM](./images/gsasset7.png)

Select **AEM Assets**.

![GSPeM](./images/gsasset8.png)

Click **Select folder**.

![GSPeM](./images/gsasset9.png)

Select your AEM Assets CS repository, which should be named `--aepUserLdap-- - CitiSignal` and then select the folder `--aepUserLdap-- - CitiSignal Fiber Campaign`. Click **Select**.

![GSPeM](./images/gsasset11.png)

You should then see this. Click **Upload 1 asset**. Your image will now be uploaded to AEM Assets CS.

![GSPeM](./images/gsasset12.png)

Go to [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Open **Experience Manager Assets**.

![GSPeM](./images/gsasset13.png)

Select your AEM Assets CS environment, which should be named `--aepUserLdap-- - CitiSignal dev`.

![GSPeM](./images/gsasset14.png)

Go to **Assets** and then double-click the folder `--aepUserLdap-- - CitiSignal Fiber Campaign`.

![GSPeM](./images/gsasset15.png)

You should then see something similar to this. Double-click the image `--aepUserLdap-- - neon rabbit`.

![GSPeM](./images/gsasset16.png)

The image `--aepUserLdap-- - neon rabbit` will then be shown. Change the **Status** to **Approved** and then click **Save**

>[!IMPORTANT]
>
>If the status of an image isn't set to **Approved**, then the image will not be visible in GenStudio for Performance Marketing. Only approved assets are accessible in GenStudio for Performance Marketing.

![GSPeM](./images/gsasset17.png)

Switch back to GenStudio for Performance Marketing. In the left menu, go to **Assets** and select your AEM Assets CS repository, which should be named `--aepUserLdap-- - CitiSignal`. You will then see the image that you just created and approved become available inside GenStudio for Performance Marketing.

![GSPeM](./images/gsasset18.png)

## 1.3.3.4 Create & Approve Meta ad

In the left menu, go to **Create**. Select **Meta**. 

![GSPeM](./images/gsad1.png)

Select the **Meta ad** template that you imported before, which is named `--aepUserLdap---citisignal-meta-ad`. Click **Use**.

![GSPeM](./images/gsad2.png)

You should then see this. Change the name of your ad to `--aepUserLdap-- - Meta Ad Fiber Max`.

Under **Paramaters**, select the following options:

- **Brand**: `--aepUserLdap-- - CitiSignal`
- **Language**: `English (US)`
- **Persona**: `--aepUserLdap-- - Smart Home Families`
- **Product**: `--aepUserLdap-- - CitiSignal Fiber Max`

Click **Select from Content**.

![GSPeM](./images/gsad3.png)

Select the asset `--aepUserLdap-- - neon rabbit.png`. Click **Use**.

![GSPeM](./images/gsad4.png)

Enter the prompt `focus on lightning fast internet for big families` and click **Generate**.

![GSPeM](./images/gsad5.png)

You should then see something like this. Your ads are now ready to be reviewed and approved. To do that, click **Request approval**, which will connect to Adobe Workfront.

![GSPeM](./images/gsad6.png)

Select your Adobe Workfront project, which should be named `--aepUserLdap-- - CitiSignal Fiber Launch`. Enter your own email address under **Invite people** and ensure your role is set to **Approver**.

![GSPeM](./images/gsad7.png)

Alternatively, you can also use an existing approval workflow in Adobe Workfront. To do that, click **Use template** and select the template `--aepuserLdap-- - Approval Workflow`. Click **Send**.

![GSPeM](./images/gsad8.png)

Click **View comments in Workfront**, you'll now be sent to the Adobe Workfront Proof UI.

![GSPeM](./images/gsad9.png)

In the Adobe Workfront Proof UI, click **Make decision**.

![GSPeM](./images/gsad10.png)

Select **Approved** and click **Make decision**.

![GSPeM](./images/gsad11.png)

Click **Publish**.

![GSPeM](./images/gsad12.png)

Select your Campaign `--aepUserLdap-- - CitiSignal Fiber Launch Campaign` and click **Publish**.

![GSPeM](./images/gsad13.png)

Click **Open in Content**.

![GSPeM](./images/gsad14.png)

The 4 Meta ads are now available under **Content** > **Experiences**.

![GSPeM](./images/gsad15.png)

## 1.3.3.5 Publish ad to Meta

Select one of the ads and then click **Activate**.

![GSPeM](./images/gsmetaad1.png)

Choose a **Call to action** out of the list and enter an example URL. Click **Next**.

![GSPeM](./images/gsmetaad3.png)

Select the Meta account, the linked Facebook page, the Meta Campaign and the Meta Ad Set.

Give your add a name, use `--aepUserLdap-- Fiber Max Ad`.

Click **Next**.

![GSPeM](./images/gsmetaad4.png)

Click **Publish**.

![GSPeM](./images/gsmetaad5.png)

Click **OK**.

![GSPeM](./images/gsmetaad6.png)

The status of your ad is now set to **Publishing**, which may take a couple of minutes.

![GSPeM](./images/gsmetaad7.png)

After a couple of minutes, the status of the ad will change to **Published**. This means that the ad has been sent from GenStudio for Performance Marketing to Meta. It doesn't mean that the ad is published in Meta already! There are still a numbers of steps to take in the Meta Business Account to take the ad and publish it so that it can be seen by users on the various Meta platforms.

Click **View details**.

![GSPeM](./images/gsmetaad8.png)

Click **Open**, which will take you to your Meta Business Account.

>[!IMPORTANT]
>
>If you don't have access to the Meta Business Account that is connected to your environment, then you won't be able to visualize this ad in Meta.

![GSPeM](./images/gsmetaad9.png)

Here's an overview of the ad you just created, but now in Meta.

![GSPeM](./images/gsmetaad10.png)

You've now completed this exercise.

## Next Steps

Go to [Summary & benefits](./summary.md){target="_blank"}

Go back to [GenStudio for Performance Marketing](./genstudio.md){target="_blank"}

Go back to [All Modules](./../../../overview.md){target="_blank"}
