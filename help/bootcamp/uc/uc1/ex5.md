---
title: Bootcamp - Real-time CDP - Build a segment and take action - Send your segment to DV360
description: Bootcamp - Real-time CDP - Build a segment and take action - Send your segment to DV360
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
---
# 1.5 Take Action: send your segment to Facebook

Go to [Adobe Experience Platform](https://experience.adobe.com/platform). After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``Bootcamp``. You can do this by clicking the text **[!UICONTROL Production Prod]** in the blue line on top of your screen. After selecting the appropriate [!UICONTROL sandbox], you'll see the screen change and now you're in your dedicated [!UICONTROL sandbox].

![Data Ingestion](./images/sb1.png)

In the left menu, go to **Destinations**, then go to **Catalog**. You'll then see the **Destinations Catalog**. In **Destinations**, click **Activate Segments** on the **Facebook Custom Audience** card.

![RTCDP](./images/rtcdpgoogleseg.png)

Select the destination **bootcamp-facebook** and click **Next**.

![RTCDP](./images/rtcdpcreatedest2.png)

In the list of available segments, select the segment you created in the previous exercise. Click **Next**.

![RTCDP](./images/rtcdpcreatedest3.png)

On the **Mapping** page, accept the default settings and click **Next**.

![RTCDP](./images/rtcdpcreatedest4a.png)

On the **Segment Schedule** page, select the **Origin of your audience** and set it to **Directly from customers**. Click **Next**.

![RTCDP](./images/rtcdpcreatedest4.png)

Finally, on the **Review** page, click **Finish**.

![RTCDP](./images/rtcdpcreatedest5.png)

Your segment is now linked to Facebook Custom Audiences. Every time a customer qualifies for this segment, a signal will be sent to Facebook server-side to include that customer in the Custom Audience at Facebook side.

In Facebook, you'll find your segment from Adobe Experience Platform under Custom Audiences :

![RTCDP](./images/rtcdpcreatedest5b.png)

You can now see your custom audience appear in Facebook:

![RTCDP](./images/rtcdpcreatedest5a.png)

[Go Back to User Flow 1](./uc1.md)

[Go Back to All Modules](../../overview.md)
