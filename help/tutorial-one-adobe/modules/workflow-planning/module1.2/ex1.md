---
title: Getting started with Workfront
description: Getting started with Workfront
kt: 5342
doc-type: tutorial
---
# 1.2.1 Workfront + AEM Assets CS Metadata Integration

Go to [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Click to open **Workfront**.

![Workfront Planning](./../module1.1/images/wfpl1.png)

You'll then see this.

![WF](./images/wfb1.png)

## 1.2.1.1 Configure your AEM Assets Integration

Click the **menu** icon and then select **Setup**.

![WF](./images/wfb2.png)

In the left menu, scroll down to **Documents** and then click **Experience Manager Assets**. Click **+ Add Experience Manager integration**.

![WF](./images/wfb3.png)

For the name of your integration, use `--aepUserLdap-- - CitiSignal AEM`.

Open the **Experience Manager repository** dropdown and select your AEM CS instance, which should be named `--aepUserLdap-- - CitiSignal`.

![WF](./images/wfb5.png)

Under **Metadata**, configure the following mapping:

| Workfront Field | Experience Manager Assets field|
| --------------- | ------------------------------ | 
| **Document** > **Name** | **wm:documentName** | 
| **Project** > **Name** | **wm:projectName** | 
| **Project** > **Description** | **wm:projectDescription** | 
| **Document Request** > **Status** | **wm:wm:documentStatus** | 
| **Task** > **Name** | **wm:taskName** | 
| **Task** > **Description** | **wm:taskDescription** | 
| **Project** > **ID** | **wm:projectId** | 

Enable the switch for **Sync object metadata**.

Click **Save**.

![WF](./images/wfb6.png)

Your integration from Workfront to AEM Assets CS is now configured.

![WF](./images/wfb7.png)

## 1.2.1.2 Configure Metadata integration with AEM Assets

Next, you need to configure AEM Assets CS so that the metadata fields from the asset in Workfront will be shared with AEM Assets CS.

To do that, go to [https://experience.adobe.com/](https://experience.adobe.com/). Click **Experience Manager Assets**.

![WF](./images/wfbaem1.png)

Click to select your AEM Assets environment, which should be named `--aepUserLdap-- - CitiSignal dev`.

![WF](./images/wfbaem2.png)

You should then see this. In the left menu, go to **Assets**.

![WF](./images/wfbaem3.png)

Next, click **Create Folder**.

![WF](./images/wfbaem3a.png)

Name your folder `--aepUserLdap-- - CitiSignal Fiber Launch Assets` and click **Create**.

![WF](./images/wfbaem4.png)

Next, go to **Metadata Forms** in the left menu and then click **Create**.

![WF](./images/wfbaem5.png)

Use the name `--aepUserLdap-- - Metadata Form` and click **Create**.

![WF](./images/wfbaem6.png)

Add 7 new **Single Line Text** fields to the form and select the first field. Then, click the **Schema** icon next to the **Metadata property** field for the first field.

![WF](./images/wfbaem7.png)

You'll then see this popup. In the search field, enter `wm:project` and then select the field **Project Name**. Click **Select**.

![WF](./images/wfbaem11.png)

Change the label of the field to `Project Name`. Click **Save**.

![WF](./images/wfbaem12.png)

Go to the second field and click the **Schema** icon next to the **Metadata property** field.

![WF](./images/wfbaem12a.png)

In the search field, enter `wm:project` and then select the field **Project Description**. Click **Select**.

![WF](./images/wfbaem8.png)

Change the label of the field to `Project Description`.

![WF](./images/wfbaem9.png)

Next, select the third field and click the **Schema** icon next to the **Metadata property** field again. 

![WF](./images/wfbaem10b.png)

You'll then see this popup again. In the search field, enter `wm:project` and then select the field **Project ID**. Click **Select**.

![WF](./images/wfbaem10.png)

Change the label of the field to `Project ID`.

![WF](./images/wfbaem10a.png)

Next, select the fourth field and click the **Schema** icon next to the **Metadata property** field again. 

![WF](./images/wfbaem11a.png)

You'll then see this popup again. In the search field, enter `wm:document` and then select the field **Project ID**. Click **Select**.

![WF](./images/wfbaem101.png)

Change the label of the field to `Document Status`.

![WF](./images/wfbaem102.png)

Next, select the fifth field and click the **Schema** icon next to the **Metadata property** field again. 

![WF](./images/wfbaem103.png)

You'll then see this popup again. In the search field, enter `wm:document` and then select the field **Project ID**. Click **Select**.

![WF](./images/wfbaem104.png)

Change the label of the field to `Document Name`.

![WF](./images/wfbaem105.png)

Next, select the sixth field and click the **Schema** icon next to the **Metadata property** field again. 

![WF](./images/wfbaem106.png)

You'll then see this popup again. In the search field, enter `wm:task` and then select the field **Task Name**. Click **Select**.

![WF](./images/wfbaem107.png)

Change the label of the field to `Task Name`.

![WF](./images/wfbaem108.png)

Next, select the seventh field and click the **Schema** icon next to the **Metadata property** field again. 

![WF](./images/wfbaem109.png)

You'll then see this popup again. In the search field, enter `wm:task` and then select the field **Task Description**. Click **Select**.

![WF](./images/wfbaem110.png)

Change the label of the field to `Task Description`.

![WF](./images/wfbaem111.png)

Change the **Tab name** on the form to `--aepUserLdap-- - Workfront Metadata`. 

![WF](./images/wfbaem13.png)

Click **Save** and **Close**.

![WF](./images/wfbaem13a.png)

Your **Metadata Form** is now configured.

![WF](./images/wfbaem14.png)

Next, you need to assign the Metadata Form to the folder you created before. Check the checkbox for your Metadata Form and click **Assign to Folder(s)**.

![WF](./images/wfbaem15.png)

Select your folder, which should be named `--aepUserLdap-- - CitiSignal Fiber Launch Assets`. Click **Assign**.

![WF](./images/wfbaem16.png)

The Metadata Form is now assigned to your folder successfully.

![WF](./images/wfbaem17.png)

Next Step: [1.2.2 Proofing with Workfront](./ex2.md){target="_blank"}

Go Back to [Workflow Management with Adobe Workfront](./workfront.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
