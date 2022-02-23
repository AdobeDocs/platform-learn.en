---
title: Adobe Experience Platform Data Collection & Real-time Server Side Forwarding - Update your Datastream to make data available to your Adobe Experience Platform Data Collection Server property
description: Update your Datastream to make data available to your Adobe Experience Platform Data Collection Server property
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 0c42350c-c38a-410e-bdab-41aff6024f81
---
# 14.2 Update your Datastream to make data available to your Adobe Experience Platform Data Collection Server property

## 14.2.1 Update your Datastream

In [Exercise 0.2](./../../modules/module0/ex2.md), you created your own **[!UICONTROL Datastream]**. You then used the name `--demoProfileLdap-- - Demo System Datastream`.

In this exercise, you need to configure that **[!UICONTROL Datastream]** to work with your **[!DNL Data Collection Server property]**.

To do that, go to [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). You'll then see this. In the left menu, click **[!UICONTROL Datastreams]**.
Search for your **[!UICONTROL Datastream]**. Click your **[!UICONTROL Datastream]** to open it.

![WebSDK](./images/websdk0.png)

You'll then see this. Click **[!UICONTROL Development Environment]**.

![WebSDK](./images/websdk3.png)

In the **[!UICONTROL Development Environment]**, you'll see your current datastream configuration. 

![WebSDK](./images/websdk4.png)

Scroll down to **[!DNL Launch Server Side]** and toggle the button to turn [!DNL Launch Server Side] on.
You can then select your **[!DNL Event Forwarding property]** from the dropdown list. Search and select the **[!DNL Event Forwarding property]** you created in the previous step. After selecting the **[!DNL Event Forwarding property]**, you need to select the Environment ID. Select **[!DNL Development]**.

Click **[!DNL Save]**.

![WebSDK](./images/websdk4a.png)

You'll then be back here.

![WebSDK](./images/websdk8a.png)

Your datastream is now ready to work with your **[!DNL Event Forwarding property]**.

Next Step: [14.3 Create and configure a custom webhook](./ex3.md)

[Go Back to Module 14](./aep-data-collection-ssf.md)

[Go Back to All Modules](./../../overview.md)
