---
title: Foundation - Setup of Adobe Experience Platform Data Collection and the Web SDK extension - XDM Schema requirements in Adobe Experience Platform
description: Foundation - Setup of Adobe Experience Platform Data Collection and the Web SDK extension - XDM Schema requirements in Adobe Experience Platform
kt: 5342
doc-type: tutorial
---
# 1.1.7 XDM schema requirements in Adobe Experience Platform

To ensure the Web SDK is able to ingest data into Adobe Experience Platform, there is a requirement for a specific XDM mixin to be part of the XDM schema in Adobe Experience Platform.

Go to [https://experience.adobe.com/platform](https://experience.adobe.com/platform) and log in.

![AEP Debugger](./images/exp1.png)

After logging in, select the appropriate sandbox by clicking the text **Production Prod** in the blue line on top of your screen. Select the sandbox `--aepSandboxName--`.

After selecting your sandbox, you'll see the screen change and now you're in your sandbox.

![AEP Debugger](./images/exp2.png)

In the left menu, go to **Schemas** and open the **Demo System - Event Schema for Website (Global v1.1)** Schema.

![AEP Debugger](./images/exp3.png)

In that schema, you'll see that the field group **AEP Web SDK ExperienceEvent** field group has been added. This field group adds all the minimally required fields to the Schema. Every Experience Event Schema in Adobe Experience Platform that will be used by Web SDK will always require that field group to be part of the Schema.

![AEP Debugger](./images/exp4.png)

In [Module 1.2 Data Ingestion](./../dc1.2/data-ingestion.md) you'll learn how to add field groups to schemas.

Next Step: 

## Next Steps

Go to [Summary and benefits](./summary.md){target="_blank"}

Go back to [Setup of Adobe Experience Platform Data Collection and the Web SDK tag extension](./data-ingestion-launch-web-sdk.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}