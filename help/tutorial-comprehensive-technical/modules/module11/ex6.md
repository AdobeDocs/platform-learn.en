---
title: Real-time CDP - Build a segment and take action - Send your segment to Adobe Target
description: Real-time CDP - Build a segment and take action - Send your segment to Adobe Target
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: b514313a-9c11-42f5-b925-bb2c7a222126
---
# 11.6 Take Action: send your segment to Adobe Target

Adobe Experience Platform also has the ability to share Audiences directly with the Adobe Experience Cloud **People Core Service - Audience Library**.

This means that all segments built in Adobe Experience Platform will popup in the Experience Cloud **People Core Service - Audience Library**.

Go to the Adobe Experience Cloud homepage by going to [http://experiencecloud.adobe.com/](http://experiencecloud.adobe.com/).

![RTCDP](./images/excl.png)

Open the menu by clicking the **nine dots** icon in the upper right corner of your screen. Then click **People** in the menu.

![RTCDP](./images/excl1.png)

On the next page, you'll see the **Audience Library**, which will show all available segments, including the Adobe Experience Platform segments. You can also see the segment you created in Exercise 11.1.

![RTCDP](./images/excl2.png)

Now that all Adobe Experience Platform segments are available in the Adobe Experience Cloud **Audience Library**, this also means that they can be used by Adobe Experience Cloud solutions for activation.

Let's go back to the Adobe Experience Cloud homepage by going to [http://experiencecloud.adobe.com/](http://experiencecloud.adobe.com/).

![RTCDP](./images/excl.png)

Click **Adobe Target** to open it.

![RTCDP](./images/exclat.png)

On the **Adobe Target** homepage, you'll see all existing Activities.

![RTCDP](./images/exclatov.png)

Click **+ Create Activity** to create a new Activity.

![RTCDP](./images/exclatcr.png)

Select **Experience Targeting**.

![RTCDP](./images/exclatcrxt.png)

>[!IMPORTANT]
>
> Due to the nature of the Platform Demo - website, which always redirects every visit to the Admin-page, it's important to already have the Platform Demo - website open and your brand already selected in another tab in the same browser-window as the one where you're going to define your Adobe Target Activity. If you don't have the Brand already selected in another tab in the same browser window, you won't be able to continue with the next step.

Fill out the details, like the **Activity URL**. 

>[!TIP]
>
>Adobe Target doesn't like localhost connections, so for this use-case, please use a publicly available website as Activity URL.

![RTCDP](./images/exclatcrxtdtl.png)

Click **Next**.

![RTCDP](./images/exclatcrxtdtlnext.png)

You're now in the Visual Experience Composer, and should see the Platform Demo website with the Brand that you already selected.

![RTCDP](./images/exclatvec.png)

The default audience is currently **All Visitors**. Click on the **3 dots** next to **All Visitors** and click **Change Audience**.

![RTCDP](./images/exclatveccha.png)

You're now seeing the Adobe Experience Cloud **Audience Library**, and all Adobe Experience Platform segments are part of this list. Select the segment you previously created in Adobe Experience Platform.

![RTCDP](./images/exclatvecchaud.png)

Click **Done**.

![RTCDP](./images/exclatvecchadone.png)

Your Adobe Experience Platform segment is now part of this Experience Targeting Activity.

![RTCDP](./images/exclatvecchaok.png)

Let's now change the Hero Image. Click the Hero Image, go to **Replace Content**, then click **Image**.

![RTCDP](./images/exclatveccta.png)

You'll then see all available images. Pick an image.

![RTCDP](./images/exclatvecctaimg.png)

Click **Save**.

![RTCDP](./images/exclatvecctaimgsave.png)

You'll then see the new experience with the new image, for your selected Audience.

![RTCDP](./images/exclatvecctaimgsaved.png)

Click the title of your Activity in the upper left corner to rename it.

![RTCDP](./images/exclatvecname.png)

As a naming convention, we'll use:

* `ldap - Module 11 - XT`

Replace **ldap** with your ldap.

![RTCDP](./images/exclatvecnamen.png)

Click **Next**.

![RTCDP](./images/exclatvecnamenext.png)

On the next screen, click **Next**.

![RTCDP](./images/vec1.png)

On the **Goals & Settings** - page, go to **Goal Metrics**.

![RTCDP](./images/vec2.png)

Set the Primary Goal to **Engagement** - **Time On Site**.

![RTCDP](./images/vec3.png)

Click **Save & Close**.

![RTCDP](./images/vecsave.png)

You're now on the **Activity Overview** page.

![RTCDP](./images/vecsave.png)

You still need to activate your Activity.

![RTCDP](./images/vec5.png)

Click on the field **Inactive** and select **Activate**.

![RTCDP](./images/vec6.png)

You'll then get a visual confirmation that your activity is now live.

![RTCDP](./images/veclive.png)

Next Step: [Summary and benefits](./summary.md)

[Go Back to Module 11](./real-time-cdp-build-a-segment-take-action.md)

[Go Back to All Modules](../../overview.md)
