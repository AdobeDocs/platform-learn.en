---
title: Real-time CDP - Build a segment and take action - Configure an Advertising Destination like Google DV360
description: Real-time CDP - Build a segment and take action - Configure an Advertising Destination like Google DV360
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: c2cb3bb8-08d1-42a8-aa65-5d9da72ea023
---
# 11.2 Configure an Advertising Destination like Google DV360

>[!IMPORTANT]
>
>The below content is intended as FYI - You do **NOT** have to configure a new destination for DV360. The destination has already been created and you can use it in the next exercise.

Log in to Adobe Experience Platform by going to this URL: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./images/home.png)

Before you continue, make sure you are in the `Production Prod` environment in the blue line on top of your screen.

In the left menu, go to **Destinations**.

![RTCDP](./images/rtcdpmenudest.png)

You'll then see the **Destinations** homepage.

![RTCDP](./images/rtcdp.png)

Set the **Type** switcher to **Connections**.

![RTCDP](./images/rtcdpconn.png)

You'll now see this:

![RTCDP](./images/rtcdpconn1.png)

In **Destinations**, click on **Google Display & Video 360**.

![RTCDP](./images/rtcdpgoogle.png)

Click on **Connect Destination**.

![RTCDP](./images/rtcdpgooglecreate.png)

You'll then see this:

![RTCDP](./images/rtcdpgooglecreate1.png)

Click **Connect to destination**.

![RTCDP](./images/rtcdpgooglecreate2.png)

You'll then see a visual confirmation.

![RTCDP](./images/rtcdpgooglecreate3.png)

Click **Next**.

![RTCDP](./images/next.png)

In the next screen, you'll see the Self-Service UI to configure your destination to Google DV360.

![RTCDP](./images/rtcdpgooglecreatedest.png)

Enter a value in the fields **Name** and **Description**.

The field **Account ID** is the **Advertiser ID** of the DV360 Account. You can find that here:

![RTCDP](./images/rtcdpgoogledv360advid.png)

The **Account Type** should be set to **Invite Advertiser**.

Now you have something like this:

![RTCDP](./images/rtcdpgoogldv360new.png)

FYI - If you have configured DV360/DBM integrations in the past for Adobe Audience Manager projects, it was also required to contact Google for this setup and request Google to **allow-list** Adobe to send segments to DV360/DBM. This step is still required and as such, Google needs to allow-list Adobe in order for Adobe Experience Platform to speak with Google DV360.

Click **Create** to create your destination.

![RTCDP](./images/rtcdpcreatedest.png)

After creating the destination, you'll see this:

![RTCDP](./images/rtcdpcreatedest1.png)

Click **Next**.

![RTCDP](./images/next.png)

You can then select segments to be sent to this destination:

![RTCDP](./images/rtcdpselseg.png)

Click **Next**.

![RTCDP](./images/next.png)

On the **Segment Schedule** page, click **Next**.

![RTCDP](./images/rtcdpselseg1.png)

![RTCDP](./images/next.png)

Finally, on the **Review** page, click **Finish**.

![RTCDP](./images/rtcdpselseg2.png)

![RTCDP](./images/finish.png)

In the next exercise, you'll connect the segment you built in the previous to the Google DV360 destination.

Next Step: [11.3 Take Action: send your segment to DV360](./ex3.md)

[Go Back to Module 11](./real-time-cdp-build-a-segment-take-action.md)

[Go Back to All Modules](../../overview.md)
