---
title: Foundation - Setup of Adobe Experience Platform Data Collection and the Web SDK extension - Implement Adobe Target
description: Foundation - Setup of Adobe Experience Platform Data Collection and the Web SDK extension - Implement Adobe Target
kt: 5342
doc-type: tutorial
exl-id: 31cdde2f-011d-442d-8e47-15a318a6c89d
TQID: https://experienceleague.adobe.com/19a4RrHvx-W3rRCNAaCDWxdX5r8AW-a-E1yqtpfMbdU
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: acc16deb-1d7f-4ec9-9ce3-6cdf355afde6
    internal-label: XDM
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: ca3d6bf4-a4af-4944-936b-8de1eb09f149
    internal-label: Datastreams
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# 1.1.6 Implement Adobe Target

## Update your datastream to use Adobe Target

In case you want to send data collected by Web SDK to Adobe Target and get a response from Adobe Target with a personalized experience for every customer, follow these steps.

Go to [https://experience.adobe.com/launch/](https://experience.adobe.com/launch/) and go to **Datastreams**. 

In the top right corner of your screen, select your sandbox name, which should be `--aepSandboxName--`. Open your specific datastream, which is named `--aepUserLdap-- - Demo System Datastream`.

![Click Edge Configuration icon in the left navigation](./images/edgeconfig1b.png)

You'll then see this. To enable Adobe Target, click **Add Service**.

![AEP Debugger](./images/aa2.png)

You'll then see this. Select the service **Adobe Target**, after which you can optionally provide additional information. Click **Save**.

![AEP Debugger](./images/at1.png)

## Next Steps

Go to [1.1.7 XDM Schema requirements in Adobe Experience Platform](./ex7.md){target="_blank"}

Go back to [Setup of Adobe Experience Platform Data Collection and the Web SDK tag extension](./data-ingestion-launch-web-sdk.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
