---
title: Audience Activation to Microsoft Azure Event Hub - Activate Audience
description: Audience Activation to Microsoft Azure Event Hub - Activate Audience
kt: 5342
doc-type: tutorial
exl-id: 89cfda0e-6c5e-45ab-9506-f0f0f6211e7f
---
# 2.4.5 Activate your audience

## Add audience to Azure Event Hub Destination

In this exercise you will add your audience `--aepUserLdap-- - Interest in Plans` to your `--aepUserLdap---aep-enablement` Azure Event Hub destination.

Log in to Adobe Experience Platform by going to this URL: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./../../../modules/datacollection/module1.2/images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxName--``. After selecting the appropriate sandbox, you'll see the screen change and now you're in your dedicated sandbox.

![Data Ingestion](./../../../modules/datacollection/module1.2/images/sb1.png)

Go to **Destinations**, then click **Browse**. You'll then see all available destinations. Locate your destination and click the 3 dots**...** as indicated below, then click **Activate audiences**.

![5-01-select-destination.png](./images/501selectdestination.png)

You'll then see this. Search for your audience using your ldap and select `--aepUserLdap-- - Interest in Plans` from the list of audiences.

Click **Next**.

![5-04-select-segment.png](./images/504selectsegment.png)

Click **Add new field**, click browse schema and select the field `--aepTenantId--identification.core.ecid` (delete any other field that would be displayed automatically).

Click **Next**.

![5-05-select-attributes.png](./images/505selectattributes.png)

Click **Finish**.

![5-06-destination-finish.png](./images/506destinationfinish.png)

Your audience is now activated towards your Microsoft Event Hub destination.

![5-07-destination-segment-added.png](./images/507destinationsegmentadded.png)

Next Step: [2.4.6 Create your Microsoft Azure Project](./ex6.md)

[Go Back to Module 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Go Back to All Modules](./../../../overview.md)
