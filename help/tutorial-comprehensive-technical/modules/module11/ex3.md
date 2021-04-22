---
title: Real-time CDP - Build a segment and take action - Send your segment to DV360
description: Real-time CDP - Build a segment and take action - Send your segment to DV360
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 3180ea5d-e028-40fd-a572-1725fefcc7bb
---
# 11.3 - Take Action: send your segment to DV360

Log in to Adobe Experience Platform by going to this URL: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./images/home.png)

In the left menu, go to **Destinations**.

You'll then see the **Destinations** homepage.

![RTCDP](./images/rtcdpmenudest.png)

In **Destinations**, click on **Google Display & Video 360**.

![RTCDP](./images/rtcdpgoogleseg.png)

Click on **Browse Destinations**.

You'll then see all available **Google Display & Video 360** destinations.

![RTCDP](./images/rtcdpgoogledest.png)

Click the **Destination Name** of `DV360 - Advertiser ID: 5701635`.

You'll then see this screen:

![RTCDP](./images/rtcdpgoogledest1.png)

Click **Edit Activation**.

![RTCDP](./images/rtcdpactivate.png)

You'll then see all available segments in your Adobe Experience Platform instance. Search and select the segment you created in 1.

![RTCDP](./images/rtcdpactivateseg.png)

Click **Next**.

![RTCDP](./images/rtcdpnext.png)

On the next page, click **Next**.

![RTCDP](./images/rtcdpnext1.png)

On the next page, click **Finish**.

![RTCDP](./images/rtcdpnext2.png)

Your segment is now linked to Google DV360. Every time a customer qualifies for this segment, a signal will be sent to Google DV360 to include that customer in the Audience at Google DV360 side.

![RTCDP](./images/rtcdpnext3.png)

Next Step: [11.4 Take Action: Send your segment to Google AdWords RLSA using Adobe Audience Manager](./ex4.md)

[Go Back to Module 11](./real-time-cdp-build-a-segment-take-action.md)

[Go Back to All Modules](../../overview.md)
