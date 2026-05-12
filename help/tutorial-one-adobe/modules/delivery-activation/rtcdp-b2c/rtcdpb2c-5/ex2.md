---
title: Adobe Experience Platform Data Collection & Real-time Server Side Forwarding - Update your Datastream to make data available to your Adobe Experience Platform Data Collection Server property
description: Update your Datastream to make data available to your Adobe Experience Platform Data Collection Server property
kt: 5342
doc-type: tutorial
exl-id: f4bb0673-d553-4027-8bfd-53d2608efaf5
TQID: https://experienceleague.adobe.com/2-ZpJYMf6d8MxUpgIxasHcjKSkpfHb0-OpQe70BcyCk
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: ca3d6bf4-a4af-4944-936b-8de1eb09f149
    internal-label: Datastreams
  - id: dc6ebdf7-9a94-43eb-9184-759cfdd0cf1c
    internal-label: Event forwarding
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# 2.5.2 Update your Datastream to make data available to your Adobe Experience Platform Data Collection Server property

## Update your Datastream

In [Getting Started](./../../../getting-started/gettingstarted/ex2.md), you created your own **[!UICONTROL Datastream]**. You then used the name `--aepUserLdap-- - Demo System Datastream`.

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

## Next Steps

Go to [2.5.3 Create and configure a custom webhook](./ex3.md){target="_blank"}

Go back to [Real-Time CDP Connections: Event Forwarding](./aep-data-collection-ssf.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
