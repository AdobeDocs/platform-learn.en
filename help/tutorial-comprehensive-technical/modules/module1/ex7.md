---
title: Foundation - Setup of Adobe Experience Platform Launch and the Web SDK extension - Implement Adobe Target
description: Foundation - Setup of Adobe Experience Platform Launch and the Web SDK extension - Implement Adobe Target
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: ac49edb9-262d-4db0-8bc6-01b760698fb8
---
# 1.7 XDM Schema requirements in Adobe Experience Platform

To ensure Web SDK and alloy.js are able to ingest data into Adobe Experience Platform, there is a requirement for a specific XDM Mixin to be part of the XDM Schema in Adobe Experience Platform.

Go to [https://experience.adobe.com/platform](https://experience.adobe.com/platform) and log in.

![AEP Debugger](./images/exp1.png)

After logging in, select the appropriate sandbox by clicking the text **Production Prod** in the blue line on top of your screen. Select the sandbox `--aepSandboxId--`.

After selecting your sandbox, you'll see the screen change and now you're in your sandbox.

![AEP Debugger](./images/exp2.png)

In the left menu, go to **Schemas** and open the **AEP Demo - Website Interactions** Schema.

![AEP Debugger](./images/exp3.png)

On that Schema, you'll see that the Mixin **AEP Web SDK ExperienceEvent Mixin** has been added. This Mixin adds all the minimally required fields to the Schema. Every Experience Event Schema in Adobe Experience Platform that will be used by Web SDK will always require that Mixin to be part of the Schema.

![AEP Debugger](./images/exp4.png)

In [Module 2](./../module2/data-ingestion.md) you'll learn how to add Mixins to Schemas.

Next Step: [Summary and benefits](./summary.md)

[Go Back to Module 1](./data-ingestion-launch-web-sdk.md)

[Go Back to All Modules](./../../overview.md)
