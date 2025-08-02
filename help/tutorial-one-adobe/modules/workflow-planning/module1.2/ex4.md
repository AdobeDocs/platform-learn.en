---
title: Getting started with Workfront
description: Getting started with Workfront
kt: 5342
doc-type: tutorial
---
# 1.2.4 Workfront + AEM Sites

Log in to Adobe Workfront by going to [https://experienceplatform.my.workfront.com/](https://experienceplatform.my.workfront.com/){target="_blank"}.

You then see this.

![WF](./images/wfb1.png)

## 1.2.4.1 Configure your AEM Sites Integration

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
