---
title: Getting started with Workfront
description: Getting started with Workfront
kt: 5342
doc-type: tutorial
---
# 1.2.1 Getting started with Workfront

Log in to Adobe Workfront by going to [https://experienceplatform.my.workfront.com/](https://experienceplatform.my.workfront.com/){target="_blank"}.

You then see this.

![WF](./images/wfb1.png)

## 1.2.1.1 Configure your AEM Assets Integration

Click the 9 dots **hamburger** icon and then select **Setup**.

![WF](./images/wfb2.png)

In the left menu, scroll down to **Documents** and then click **Experience Manager Assets**.

![WF](./images/wfb3.png)

Click **+ Add Experience Manager integration**.

![WF](./images/wfb4.png)

For the name of your integration, use `--aepUserLdap-- - Citi Signal AEM`.

Open the **Experience Manager repository** dropdown and select your AEM CS instance, which should be named `--aepUserLdap-- - Citi Signal`.

![WF](./images/wfb5.png)

Under **Metadata**, configure the following mapping:

| Workfront Field | Experience Manager Assets field|
| --------------- | ------------------------------ | 
| **Document** > **Name** | **wm:documentName** | 
| **Project** > **Description** | **wm:projectDescription** | 
| **Task** > **Name** | **wm:taskName** | 
| **Task** > **Description** | **wm:taskDescription** | 

Enable the switch for **Sync object metadata**.

Click **Save**.

![WF](./images/wfb6.png)

Your integration from Workfront to AEM Assets CS is now configured.

![WF](./images/wfb7.png)

## 1.2.1.2 Configure Metadata integration with AEM Assets

Next, you need to configure AEM Assets so that the metadata fields from the asset in Workfront will be shared with AEM.

To do that, go to [https://experience.adobe.com/](https://experience.adobe.com/). Click **Experience Manager Assets**.

![WF](./images/wfbaem1.png)

Click to select your AEM Assets environment, which should be named `--aepUserLdap-- - Citi Signal dev`.

![WF](./images/wfbaem2.png)

You should then see this. In the left menu, go to **Assets** and click **Create Folder**.

![WF](./images/wfbaem3.png)

Name your folder `--aepUserLdap-- - Workfront Assets` and click **Create**.

![WF](./images/wfbaem4.png)

Next, go to **Metadata Forms** in the left menu and then click **Create**.

![WF](./images/wfbaem5.png)

Use the name `--aepUserLdap-- - Metadata Form` and click **Create**.

![WF](./images/wfbaem6.png)

Add 3 new **Single Line Text** fields to the form and select the first field. Then, click the **Schema** icon next to the **Metadata property** field.

![WF](./images/wfbaem7.png)

In the search field, enter `wm:project` and then select the field **Project Description**. Click **Select**.

![WF](./images/wfbaem8.png)

Change the label of the field to **Project Description**.

![WF](./images/wfbaem9.png)

Next, select the 2nd **Single Line Text** field and click the **Schema** icon next to the **Metadata property** field again. 

![WF](./images/wfbaem10b.png)

You'll then see this popup again. In the search field, enter `wm:project` and then select the field **Project ID**. Click **Select**.

![WF](./images/wfbaem10.png)

Change the label of the field to **Project ID**.

![WF](./images/wfbaem10a.png)

Select the 3rd **Single Line Text** field and click the **Schema** icon next to the **Metadata property** field again. 

![WF](./images/wfbaem11a.png)

You'll then see this popup again. In the search field, enter `wm:project` and then select the field **Project Name**. Click **Select**.

![WF](./images/wfbaem11.png)

Change the label of the field to **Project Name**. Click **Save**.

![WF](./images/wfbaem12.png)

Change the **Tab name** on the form to `--aepUserLdap-- - Workfront Metadata`. Click **Save** and **Close**.

![WF](./images/wfbaem13.png)

Your **Metadata Form** is now configured.

![WF](./images/wfbaem14.png)

Next, you need to assign the Metadata Form to the folder you created before. Check the checkbox for your Metadata Form and click **Assign to Folder(s)**.

![WF](./images/wfbaem15.png)

Select your folder, which should be named `--aepUserLdap-- - Workfront Assets`. Click **Assign**.

![WF](./images/wfbaem16.png)

The Metadata Form is now assigned to your folder successfully.

![WF](./images/wfbaem17.png)

## 1.2.1.2 Configure your AEM Sites Integration

>[!NOTE]
>
>This plugin is currently in **Early Access** mode and isn't generally available yet. 
>
>This plugin may already be installed in the Workfront instance your using. If it is already installed, you can review the below instructions but there's no need to change anything in your configuration then.

Go to [https://experience.adobe.com/#/@experienceplatform/aem/extension-manager/universal-editor](https://experience.adobe.com/#/@experienceplatform/aem/extension-manager/universal-editor){target="_blank"}.

Make sure the **toggle** for this plugin is set to **Enabled**. Then, click the **gear** icon.

![WF](./images/wfb8.png)

You'll see an **Extension configuration** popup. Configure the following fields to use this plugin.

| Key | Value|
| --------------- | ------------------------------ | 
| **`IMS_ENV`** | **PROD** | 
| **`WORKFRONT_INSTANCE_URL`** | **https://experienceplatform.my.workfront.com** | 
| **`SHOW_CUSTOM_FORMS`** | **'{"previewUrl": true, "publishUrl": true}'** | 

Click **Save**.

![WF](./images/wfb8.png)

Go back to your Workfront UI and click the 9 dots **hamburger** icon. Select **Setup**.

![WF](./images/wfb9.png)

In the left menu, go to **Custom Forms** and select **Form**. Click **+ New custom form**.

![WF](./images/wfb10.png)

Select **Task** and click **Continue**.

![WF](./images/wfb11.png)

You'll then see an empty custom form. Enter the form name `Content Fragment & Integration ID`.

![WF](./images/wfb12.png)

Drag and drop a new **Single line text** field onto the canvas.

![WF](./images/wfb13.png)

Configure the new field like this:

- **Label**: **Content Fragment**
- **Name**: **`aem_workfront_integration_content_fragment`**

![WF](./images/wfb14.png)

Add a new **Single line text** field onto the canvas and configure the new field like this:

- **Label**: **Integration ID**
- **Name**: **`aem_workfront_integration_id`**

Click **Apply**.

![WF](./images/wfb15.png)

You now need to configure a second custom form. Click **+ New custom form**.

![WF](./images/wfb10.png)

Select **Task** and click **Continue**.

![WF](./images/wfb11.png)

You'll then see an empty custom form. Enter the form name `Preview & Publish URL`.

![WF](./images/wfb16.png)

Drag and drop a new **Single line text** field onto the canvas.

![WF](./images/wfb17.png)

Configure the new field like this:

- **Label**: **Preview URL**
- **Name**: **`aem_workfront_integration_preview_url`**

![WF](./images/wfb18.png)

Add a new **Single line text** field onto the canvas and configure the new field like this:

- **Label**: **Publish URL**
- **Name**: **`aem_workfront_integration_publish_url`**

Click **Apply**.

![WF](./images/wfb19.png)

You should then have 2 custom forms available.

![WF](./images/wfb20.png)

Next Step: [1.2.2 Proofing with Workfront](./ex2.md){target="_blank"}

Go Back to [Workflow Management with Adobe Workfront](./workfront.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
