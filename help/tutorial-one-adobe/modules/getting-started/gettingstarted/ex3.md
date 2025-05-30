---
title: Getting Started - Create your Datastream
description: Getting Started - Create your Datastream
kt: 5342
doc-type: tutorial
exl-id: d36057b4-64c6-4389-9612-d3c9cf013117
---
# Create your Datastream

Go to [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/){target="_blank"}. 

![DSN](./images/launchprop.png)

Before you continue, make sure that you have selected the correct environment by using the environment switcher in the top right corner of your screen. The right environment to use is called `--aepImsOrgName--`.

>[!NOTE]
>
> The below screenshot shows a specific org being selected. When you are going through this tutorial, it is very likely that your org has a different name. When you signed up for this tutorial, you were provided with the environment details to use, please follow those instructions.


![DSN](./images/org.png)

In the left menu, click **[!UICONTROL Tags]**. After the previous exercise, you now have 3 Data Collection properties: one for web, one for mobile and one for the CX app.

![DSN](./images/launchprop1.png)

These properties are almost ready to be used, but before you can start collecting data using these properties you need to set up a datastream. You'll get more information around the concept of what a datastream is and what it means in a later exercise in the Data Collection module.

For now, please follow these steps.

## Create your Datastream for Web

Click **[!UICONTROL Datastreams]**.

![Click Edge Configuration icon in the left navigation](./images/edgeconfig1a.png)

In the top right corner of your screen, select your sandbox name, which should be `--aepSandboxName--`.

>[!NOTE]
>
> The below screenshot shows a specific sandbox being selected. When you are going through this tutorial, it is very likely that your sandbox has a different name. When you signed up for this tutorial, you were provided with the environment details to use, please follow those instructions.

![Click Edge Configuration icon in the left navigation](./images/edgeconfig1b.png)

Click **[!UICONTROL New Datastream]**.

![Click Edge Configuration icon in the left navigation](./images/edgeconfig1.png)

For the **Name**, and for the optional description, enter `--aepUserLdap-- - One Adobe Datastream`. For **Mapping Schema**, select **Demo System - Event Schema for Website (Global v1.1)**. Click **Save**.

![Name the Edge Configuration and save](./images/edgeconfig2.png)

You'll then see this. Click **Add Service**.

![Name the Edge Configuration and save](./images/edgeconfig3.png)

Select the service **[!UICONTROL Adobe Experience Platform]**, which will expose additional fields. You'll then see this. 

For Event Dataset, select **Demo System - Event Dataset for Website (Global v1.1)** and for Profile Dataset, select **Demo System - Profile Dataset for Website (Global v1.1)**. Click **Save**.

![Name the Edge Configuration and save](./images/edgeconfig4.png)

You'll now see this.

![Name the Edge Configuration and save](./images/edgeconfig5.png)

In the left menu, clik **[!UICONTROL Tags]**.

Filter the search results to see your Data Collection properties. Open the property for **Web** by clicking it.

![Name the Edge Configuration and save](./images/edgeconfig10a.png)

You'll then see this. Click **Extensions**.

![Name the Edge Configuration and save](./images/edgeconfig11.png)

First, click the Adobe Experience Platform Web SDK extension and then click **Configure**.

![Name the Edge Configuration and save](./images/edgeconfig12.png)

You'll then see this. Have a look at the **Datastreams** menu and make sure the right sandbox is selected, which in you case should be `--aepSandboxName--`.

![Name the Edge Configuration and save](./images/edgeconfig12a.png)

Open the **Datastreams** dropdown, and select the Datastream you created earlier.

![Name the Edge Configuration and save](./images/edgeconfig13.png)

Make sure to have selected your **Datastream** in all three different environments. Then, click **Save**.

![Name the Edge Configuration and save](./images/edgeconfig14.png)

Go to **Publishing Flow**.

![Name the Edge Configuration and save](./images/edgeconfig15.png)

Click the **...** for **Main**, then click **Edit**.

![Name the Edge Configuration and save](./images/edgeconfig16.png)

Click **Add All Changed Resources** and then click **Save & Build for Development**.

![Name the Edge Configuration and save](./images/edgeconfig17.png)

Your changes are now being published and will be ready in a couple of minutes, after which you'll see the green dot next to **Main**.

![Name the Edge Configuration and save](./images/edgeconfig17a.png)

## Create your Datastream for Mobile

Go to [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/){target="_blank"}. 

Click **[!UICONTROL Datastreams]**.

![Click Datastream icon in the left navigation](./images/edgeconfig1a.png)

In the top right corner of your screen, select your sandbox name, which should be `--aepSandboxName--`.

>[!NOTE]
>
> The below screenshot shows a specific sandbox being selected. When you are going through this tutorial, it is very likely that your sandbox has a different name. When you signed up for this tutorial, you were provided with the environment details to use, please follow those instructions.

![Click Edge Configuration icon in the left navigation](./images/edgeconfig1b.png)

Click **[!UICONTROL New Datastream]**.

![Click Datastream icon in the left navigation](./images/edgeconfig1.png)

For the **[!UICONTROL Friendly Name]**, and for the optional description, enter `--aepUserLdap-- - One Adobe Datastream (Mobile)`. For **Mapping Schema**, select **Demo System - Event Schema for Mobile App (Global v1.1)**. Click **Save**.

Click **[!UICONTROL Save]**.

![Name the Datastream and save](./images/edgeconfig2m.png)

You'll then see this. Click **Add Service**.

![Name the Datastream and save](./images/edgeconfig3m.png)

Select the service **[!UICONTROL Adobe Experience Platform]**, which will expose additional fields. You'll then see this.

For Event Dataset, select **Demo System - Event Dataset for Mobile App (Global v1.1)** and for Profile Dataset, select **Demo System - Profile Dataset for Mobile App (Global v1.1)**. Click **Save**.

![Name the Datastream Configuration and save](./images/edgeconfig4m.png)

You'll then see this.

![Name the Datastream Configuration and save](./images/edgeconfig5m.png)

Your datastream is now ready to be used in your Adobe Experience Platform Data Collection Client property for Mobile.

Go to **Tags** and filter the search results to see your two Data Collection properties. Open the property for **Mobile** by clicking it. 

![Name the Edge Configuration and save](./images/edgeconfig10am.png)

You'll then see this. Click **Extensions**.

![Name the Edge Configuration and save](./images/edgeconfig11m.png)

Click the **Adobe Experience Platform Edge Network** extension and then click **Configure**.

![Name the Edge Configuration and save](./images/edgeconfig12m.png)

You'll then see this. You now need to select the correct sandbox and datastream that you just configured. The sandbox to use is `--aepSandboxName--` and the datastream is called `--aepUserLdap-- - One Adobe Datastream (Mobile)`. 

For the **Edge Network domain**, please use the default domain.

Click **Save** to save your changes.

![Name the Edge Configuration and save](./images/edgeconfig13m.png)

Go to **Publishing Flow**.

![Name the Edge Configuration and save](./images/edgeconfig15m.png)

Click the **...** next to **Main**, then click **Edit**.

![Name the Edge Configuration and save](./images/edgeconfig16m.png)

Click **Add All Changed Resources**, then click **Save & Build for Development**.

![Name the Edge Configuration and save](./images/edgeconfig17m.png)

Your changes are now being published and will be ready in a couple of minutes, after which you'll see the green dot next to **Main**.

![Name the Edge Configuration and save](./images/edgeconfig17ma.png)

## Next Steps

Go to [Use the website](./ex4.md){target="_blank"}

Go back to [Getting Started](./getting-started.md){target="_blank"}

Go back to [All modules](./../../../overview.md){target="_blank"}