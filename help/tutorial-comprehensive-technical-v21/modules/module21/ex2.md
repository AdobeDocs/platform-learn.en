---
title: Data Collection & Real-time Server Side Forwarding: Update your Edge Configuration to make data available to your Launch Server Side property
description: Update your Edge Configuration to make data available to your Launch Server Side property
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
---

# 21.2 Update your Edge Configuration to make data available to your Launch Server Side property

>[!NOTE]
>
>The Adobe Experience Platform Edge mobile extension is currently in BETA. Use of this extension is by invitation only. Please contact your Adobe Customer Success Manager to learn more and get access to the materials for this tutorial.

## 21.2.1 Update your Edge Configuration ID

In [Exercise 0.2](./../../modules/module0/ex2.md), you created your own **[!UICONTROL Edge Configuration ID]**. You then used the name **ldap - Demo System Edge Configuration** and replaced **ldap** with your ldap.

In this exercise, you need to configure that **[!UICONTROL Edge Configuration ID]** to work with **[!DNL Launch Server Side Forwarding]**.

To do that, go to [https://launch.adobe.com/](https://launch.adobe.com/). You'll then see this. 

![WebSDK](./images/websdk0.png)

Click **[!UICONTROL Client Side]**. In the dropdown menu, click **[!UICONTROL Edge Configurations]**.

![WebSDK](./images/websdk1.png)

Search for your **[!UICONTROL Edge Configuration]**. Click your **[!UICONTROL Edge Configuration]** to open it.

![WebSDK](./images/websdk2.png)

You'll then see this. Click **[!UICONTROL Development Environment]**.

![WebSDK](./images/websdk3.png)

In the **[!UICONTROL Development Environment]**, you'll see your Adobe Experience Platform configuration. 

![WebSDK](./images/websdk4.png)

Scroll down to **[!DNL Launch Server Side]** and toggle the button to turn [!DNL Launch Server Side] on.

![WebSDK](./images/websdk4a.png)

You can then select your **[!DNL Launch Server Side property ID]** from the dropdown list.

![WebSDK](./images/websdk5.png)

Seach and select the **[!DNL Launch Server Side property]** you created in the previous step.

![WebSDK](./images/websdk6.png)

After selecting the **[!DNL Launch Server Side property]**, you need to select the Environment ID. Select **[!DNL Development]**.

![WebSDK](./images/websdk7.png)

Click **[!DNL Save]**.

![WebSDK](./images/websdk8.png)

You'll then be back here.

![WebSDK](./images/websdk8a.png)

Next, repeat the above steps for the other environments.

This should be your configuration for the **[!DNL Staging Environment]**.

![WebSDK](./images/websdk9.png)

And this should be your configuration for the **[!DNL Production Environment]**.

![WebSDK](./images/websdk10.png)

Your Edge Configuration is now ready to work with your **[!DNL Launch Server Side property]**.

Next Step: [21.3 Create and configure a custom webhook](./ex3.md)

[Go Back to Module 21](./aep_data_collection_ssf.md)

[Go Back to All Modules](./../../overview.md)
