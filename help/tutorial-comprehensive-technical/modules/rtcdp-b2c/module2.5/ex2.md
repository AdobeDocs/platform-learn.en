---
title: Adobe Experience Platform Data Collection & Real-time Server Side Forwarding - Update your Datastream to make data available to your Adobe Experience Platform Data Collection Server property
description: Update your Datastream to make data available to your Adobe Experience Platform Data Collection Server property
kt: 5342
doc-type: tutorial
---
# 2.5.2 Update your Datastream to make data available to your Adobe Experience Platform Data Collection Server property

## Update your Datastream

In [Getting Started](./../../gettingstarted/gettingstarted/ex2.md), you created your own **[!UICONTROL Datastream]**. You then used the name `--aepUserLdap-- - Demo System Datastream`.

In this exercise, you need to configure that **[!UICONTROL Datastream]** to work with your **Data Collection Server property**.

To do that, go to [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). You'll then see this. In the left menu, click **[!UICONTROL Datastreams]**.

In the top right corner of your screen, select your sandbox name, which should be `--aepSandboxName--`.

![Click Edge Configuration icon in the left navigation](./images/edgeconfig1b.png)

Search for your **[!UICONTROL Datastream]**, which is named `--aepUserLdap-- - Demo System Datastream`. Click your **[!UICONTROL Datastream]** to open it.

![WebSDK](./images/websdk0.png)

You'll then see this. Click **[!UICONTROL + Add Service]**.

![WebSDK](./images/websdk3.png)

Select the service **Event Forwarding**. This will show you 2 additional settings. Select your Event Forwarding property, which you created in the previous exercise and which is named `--aepUserLdap-- - Demo System (DD/MM/YYYY) (Edge)`. Then select **Development** under **Environment**. Click **Save**. 

![WebSDK](./images/websdk4.png)

Your datastream has now been updated and is ready for usage.

![WebSDK](./images/websdk8a.png)

Your datastream is now ready to work with your **[!DNL Event Forwarding property]**.

Next Step: [2.5.3 Create and configure a custom webhook](./ex3.md)

[Go Back to Module 2.5](./aep-data-collection-ssf.md)

[Go Back to All Modules](./../../../overview.md)
