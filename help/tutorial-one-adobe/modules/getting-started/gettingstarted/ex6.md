---
title: Getting Started - Adobe I/O
description: Getting Started - Adobe I/O
kt: 5342
doc-type: tutorial
exl-id: 00f17d4f-a2c8-4e8e-a1ff-556037a60629
---
# Configure your Adobe I/O project 

## Create your Adobe I/O project

In this exercise, Adobe I/O is used to query various Adobe endpoints. Follow these steps to setup Adobe I/O.

Go to [https://developer.adobe.com/console/home](https://developer.adobe.com/console/home){target="_blank"}.

![Adobe I/O New Integration](./images/iohome.png)

Make sure to select the correct instance in the top right corner of your screen. Your instance is `--aepImsOrgName--`. 

>[!NOTE]
>
> The below screenshot shows a specific org being selected. When you are going through this tutorial, it is very likely that your org has a different name. When you signed up for this tutorial, you were provided with the environment details to use, please follow those instructions.

Next, select **Create new project**.

![Adobe I/O New Integration](./images/iocomp.png)

### Firefly Services API

>[!IMPORTANT]
>
>Depending on the learning path that you selected, you may not have access to Firefly Services API. You will only have access to Firefly Services API if you're on the learning path **Firefly**, **Workfront Fusion**, **ALL**, or when you're attending a **live in-person workshop**. You can skip this step if you're not on one of these learning paths.

You should then see this. Select **+ Add to Project** and choose **API**.

![Adobe I/O New Integration](./images/adobe_io_access_api.png)

Your screen should look like this.

![Adobe I/O New Integration](./images/api1.png)

Select **Creative Cloud** and choose **Firefly - Firefly Services**, then select **Next**.

![Adobe I/O New Integration](./images/api3.png)

Provide a name for your credential: `--aepUserLdap-- - One Adobe OAuth credential` and select **Next**.

![Adobe I/O New Integration](./images/api4.png)

Select the default profile **Default Firefly Services Configuration** and select **Save Configured API**.

![Adobe I/O New Integration](./images/api9.png)

You should then see this.

![Adobe I/O New Integration](./images/api10.png)

### Photoshop Services API

>[!IMPORTANT]
>
>Depending on the learning path that you selected, you may not have access to Photoshop Services API. You will only have access to Photoshop Services API if you're on the learning path **Firefly**, **Workfront Fusion**, **ALL**, or when you're attending a **live in-person workshop**. You can skip this step if you're not on one of these learning paths.
>
Select **+ Add to Project** and then select **API**.

![Azure Storage](./images/ps2.png)

Select **Creative Cloud** and choose **Photoshop - Firefly Services**. Select **Next**.

![Azure Storage](./images/ps3.png)

Select **Next**.

![Azure Storage](./images/ps4.png)

Next, you need to select a product profile that defines what permissions are available to this integration.

Select **Default Firefly Services Configuration** and **Default Creative Cloud Automation Services configuration**.

Select **Save Configured API**.

![Azure Storage](./images/ps5.png)

You should then see this.

![Adobe I/O New Integration](./images/ps7.png)

### Adobe Experience Platform API

>[!IMPORTANT]
>
>Depending on the learning path that you selected, you may not have access to Adobe Experience Platform API. You will only have access to Adobe Experience Platform API if you're on the learning path **AEP + Apps**, **ALL**, or when you're attending a **live in-person workshop**. You can skip this step if you're not on one of these learning paths.

Select **+ Add to Project** and then select **API**.

![Azure Storage](./images/aep1.png)

Select **Adobe Experience Platfrom** and choose **Experience Platform API**. Select **Next**.

![Azure Storage](./images/aep2.png)

Select **Next**.

![Azure Storage](./images/aep3.png)

Next, you need to select a product profile that defines what permissions are available to this integration.

Select **Adobe Experience Platform - All Users - PROD**.

>[!NOTE]
>
>The name of the Product Profile for AEP is dependent on how the environment was configured. If you don't see the above mentioned product profile, you may have a product profile that is called **Default Production All Access**. If you're not sure which one to choose, ask your AEP System Admin.

Select **Save Configured API**.

![Azure Storage](./images/aep4.png)

You should then see this.

![Adobe I/O New Integration](./images/aep5.png)

### Frame.io API

>[!IMPORTANT]
>
>Depending on the learning path that you selected, you may not have access to Frame.io API. You will only have access to Frame.io API if you're on the learning path **Workfront Fusion**, **ALL**, or when you're attending a **live in-person workshop**. You can skip this step if you're not on one of these learning paths.

Select **+ Add to Project** and then select **API**.

![Azure Storage](./images/fiops2.png)

Select **Creative Cloud** and choose **Frame.io API**. Select **Next**.

![Azure Storage](./images/fiops3.png)

Select **Server-to-Server Authentication** and then click **Next**.

![Azure Storage](./images/fiops4.png)

Select **OAuth Server-to-Server** and then click **Next**.

![Azure Storage](./images/fiops5.png)

Next, you need to select a product profile that defines what permissions are available to this integration.

Select **Default Frame.io Enterprise - Prime Configuration** and click **Save Configured API**.

![Azure Storage](./images/fiops6.png)

You should then see this.

![Adobe I/O New Integration](./images/fiops7.png)

### Project Name

Click your project name.

![Adobe I/O New Integration](./images/api13.png){zoomable="yes"}

Select **Edit Project**.

![Adobe I/O New Integration](./images/api14.png){zoomable="yes"}

Enter a friendly name for your integration: `--aepUserLdap-- One Adobe tutorial` and select **Save**.

![Adobe I/O New Integration](./images/api15.png){zoomable="yes"}

The setup of your Adobe I/O project is now finished.

![Adobe I/O New Integration](./images/api16.png){zoomable="yes"}

## Next Steps

Go to [Option 1: Postman setup](./ex7.md){target="_blank"}

Go to [Option 2: PostBuster setup](./ex8.md){target="_blank"}

Go back to [Getting Started](./getting-started.md){target="_blank"}

Go back to [All modules](./../../../overview.md){target="_blank"}
