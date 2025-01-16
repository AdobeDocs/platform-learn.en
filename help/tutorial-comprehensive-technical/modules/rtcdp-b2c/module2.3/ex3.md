---
title: Real-time CDP - Build an audience and take action - Send your audience to DV360
description: Real-time CDP - Build an audience and take action - Send your audience to DV360
kt: 5342
doc-type: tutorial
exl-id: bb76524e-52c1-4c2c-8bcd-33cd39d12741
---
# 2.3.3 Take Action: send your audience to DV360

Go to [Adobe Experience Platform](https://experience.adobe.com/platform). After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./../../../modules/datacollection/module1.2/images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxName--``. After selecting the appropriate [!UICONTROL sandbox], you'll see the screen change and now you're in your dedicated [!UICONTROL sandbox].

![Data Ingestion](./../../../modules/datacollection/module1.2/images/sb1.png)

In the left menu, go to **Destinations**, then go to **Browse**. You'll then see the **DV360** destination. Click the 3 dots **...** and click **Activate Audiences**.

![RTCDP](./images/rtcdpmenudest.png)

In the list of available audiences, select the audience you created in the previous exercise. Click **Next**.

![RTCDP](./images/rtcdpcreatedest3.png)

On the **Audience Schedule** page, click **Next**.

![RTCDP](./images/rtcdpcreatedest4.png)

Finally, on the **Review** page, click **Finish**.

![RTCDP](./images/rtcdpcreatedest5.png)

Your audience is now linked to Google DV360. Every time a customer qualifies for this audience, a signal will be sent to Google DV360 to include that customer in the audience at Google DV360 side.

Next Step: [2.3.4 Take Action: send your audience to an S3-destination](./ex4.md)

[Go Back to Module 2.3](./real-time-cdp-build-a-segment-take-action.md)

[Go Back to All Modules](../../../overview.md)
