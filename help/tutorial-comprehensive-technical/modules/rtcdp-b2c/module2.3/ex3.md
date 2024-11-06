---
title: Real-time CDP - Build a segment and take action - Send your segment to DV360
description: Real-time CDP - Build a segment and take action - Send your segment to DV360
kt: 5342
doc-type: tutorial
---
# 2.3.3 Take Action: send your segment to DV360

Go to [Adobe Experience Platform](https://experience.adobe.com/platform). After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./../../../modules/datacollection/module1.2/images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxId--``. You can do this by clicking the text **[!UICONTROL Production Prod]** in the blue line on top of your screen. After selecting the appropriate [!UICONTROL sandbox], you'll see the screen change and now you're in your dedicated [!UICONTROL sandbox].

![Data Ingestion](./../../../modules/datacollection/module1.2/images/sb1.png)

In the left menu, go to **Destinations**, then go to **Catalog**. You'll then see the **Destinations Catalog**.

![RTCDP](./images/rtcdpmenudest.png)

In **Destinations**, click the **Activate Segments** on the **Google Display & Video 360** card.

![RTCDP](./images/rtcdpgoogleseg.png)

Select your destination and click **Next**.

![RTCDP](./images/rtcdpcreatedest2.png)

In the list of available segments, select the segment you created in the previous exercise. Click **Next**.

![RTCDP](./images/rtcdpcreatedest3.png)

On the **Segment Schedule** page, click **Next**.

![RTCDP](./images/rtcdpcreatedest4.png)

Finally, on the **Review** page, click **Finish**.

![RTCDP](./images/rtcdpcreatedest5.png)

Your segment is now linked to Google DV360. Every time a customer qualifies for this segment, a signal will be sent to Google DV360 to include that customer in the Audience at Google DV360 side.

Next Step: [2.3.4 Take Action: send your segment to an S3-destination](./ex4.md)

[Go Back to Module 2.3](./real-time-cdp-build-a-segment-take-action.md)

[Go Back to All Modules](../../../overview.md)
