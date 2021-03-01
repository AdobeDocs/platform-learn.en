---
title: Getting Started - Install the Chrome extension for the Experience League documentation
description: Getting Started - Install the Chrome extension for the Experience League documentation
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
---

# 0.2 Create your Edge Configuration ID

Go to [https://launch.adobe.com/](https://launch.adobe.com/). After the previous exercise, you now have two Launch properties: one for web and one for mobile.

![DSN](./images/launchprop.png)

These properties are almost ready to be used, but before you can start collecting data using these properties you need to set up an Edge Configuration ID. You'll get more information around the concept of what an Edge Configuration ID is and what it means in Exercise 1.2.

For now, please follow these steps.

Open the dropdown menu and click **[!UICONTROL Edge Configuration]**.

![Click Edge Configuration icon in the left navigation](./images/edgeconfig1a.png)

Click **[!UICONTROL New Edge Configuration]**.

![Click Edge Configuration icon in the left navigation](./images/edgeconfig1.png)

For the **[!UICONTROL Friendly Name]**, and for the optional description, enter **ldap - Demo System Edge Configuration** and replace **ldap** with your ldap.

![Name the Edge Configuration and save](./images/edgeconfig2.png)

Click the **[!UICONTROL Save]** button

![Name the Edge Configuration and save](./images/save.png)

You'll then see this:

![Name the Edge Configuration and save](./images/edgeconfig3.png)

Toggle on **[!UICONTROL Adobe Experience Platform]** which will expose additional fields. You'll then see this:

![Name the Edge Configuration and save](./images/edgeconfig4.png)

For **[!UICONTROL Sandbox]**, select your sandbox name.

>[!NOTE]
>
> You can find your IMS Org ID, Org Name and your Adobe Experience Platform sandbox name on your company's github repository that was set up by your Adobe contact. If you don't know which sandbox to use, verify if you can see a sandbox named **AEP Enablement FY21**. If you can see that sandbox, please select it.

![Name the Edge Configuration and save](./images/edgeconfig5.png)

For Event Dataset, select **Demo System - Event Dataset for Website (Global v1.1)** and for Profile Dataset, select **Demo System - Profile Dataset for Website (Global v1.1)**.

![Name the Edge Configuration and save](./images/edgeconfig7.png)

That's it for now. In [Module 1](./../module1/data-ingestion-launch-web-sdk.md) you'll learn more about Web SDK and how to configure all of its capabilities.

You now have this. Click **Save**.

![Name the Edge Configuration and save](./images/edgeconfig8.png)

You'll then see that your Edge Configuration consists of 3 environments.

![Name the Edge Configuration and save](./images/edgeconfig9.png)

Open the dropdown menu and click **[!UICONTROL Client Side]**.

![Name the Edge Configuration and save](./images/edgeconfig10a.png)

Filter the search results to see your two Launch properties.

![Name the Edge Configuration and save](./images/edgeconfig10.png)

Open the Launch property for **Web** by clicking it. You'll then see this.

![Name the Edge Configuration and save](./images/edgeconfig11.png)

In the left menu, go to **Extensions**. On the AEP Web SDK, click **Configure**.

![Name the Edge Configuration and save](./images/edgeconfig12.png)

You'll then see this. For the **Edge Configurations**, you'll currently see a dummy value set to 1. You now need to click the **Choose from list** radio-button. In the dropdown list, select the Edge Configuration ID you created earlier.

![Name the Edge Configuration and save](./images/edgeconfig13.png)

Make sure to have selected your **Edge Configuration ID**. 

![Name the Edge Configuration and save](./images/edgeconfig14.png)

Scroll down until you see **Data Collection**.

![Name the Edge Configuration and save](./images/edgeconfig14a.png)

Uncheck the checkbox for **Enable click data collection**.

![Name the Edge Configuration and save](./images/edgeconfig14b.png)

Click **Save** to save your changes.

Go to **Publishing Flow**.

![Name the Edge Configuration and save](./images/edgeconfig15.png)

Click the **...** for the **Content Library**, then click **Edit**.

![Name the Edge Configuration and save](./images/edgeconfig16.png) 

Click **Add All Changed Resources**.

![Name the Edge Configuration and save](./images/edgeconfig17.png)

Finally, click **Save & Build for Development**.

![Name the Edge Configuration and save](./images/edgeconfig18.png) 

Your changes are now being published and will be ready in a couple of minutes.

Next Step: [0.3 Create your Enablement Configuration ID](./ex3.md)

[Go Back to Module 0](./getting-started.md)

[Go Back to All Modules](./../../overview.md)