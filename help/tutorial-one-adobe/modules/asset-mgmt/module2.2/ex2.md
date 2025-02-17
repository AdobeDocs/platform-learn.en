---
title: Proofing with Workfront
description: Proofing with Workfront
kt: 5342
doc-type: tutorial
exl-id: 1b5ca13b-2a32-44a1-a3ae-342bccc6baeb
---
# 1.2.2 Proofing with Workfront

## 1.2.2.1 Create a new Approval Flow

Go to [https://experienceplatform.my.workfront.com/](https://experienceplatform.my.workfront.com/){target="_blank"}.

Click the 9 dots **hamburger** icon and select **Proofing**.

![WF](./images/wfp1.png)

Go to **Workflows**, click **+ New** and then select **New template**.

![WF](./images/wfp2.png)

Set the **Template name** to `--aepUserLdap-- - Approval Workflow` and set the **Template owner** to yourself.

![WF](./images/wfp3.png)

Scroll down, and under **Stages** > **Stage 1**, add **Wouter Van Geluwe** with the **Role** of **Reviewer & Approver**.

Click **Create**.

![WF](./images/wfp4.png)

Your basic approval workflow is now ready to be used.

![WF](./images/wfp5.png)

## 1.2.2.2 Create a new Project

From the Workfront home page, click **New** in the **My Projects** tab. Select **Blank Project**.

![WF](./images/wfp6.png)

You should then see this. Change the name to `--aepUserLdap-- - CitiSignal Fiber Launch`.

![WF](./images/wfp6a.png)

Your project is now created.

![WF](./images/wfp7.png)

## 1.2.2.3 Create a new Task

Enter this name for your task: **Create assets for Fiber campaign**. Click **Create Task**.

![WF](./images/wfp8.png)

You should then see this.

![WF](./images/wfp9.png)

## 1.2.2.4 Add a new Document to your Task go through the approval flow

Click **+ Add new** and then select **Document**.

![WF](./images/wfp10.png)

Download [this file](./images/2048x2048.png) to your desktop.

![WF](./images/2048x2048.png){width="50px" align="left"}

Select the file **2048x2048.png** and click **Open**.

![WF](./images/wfp12.png)

You should then have this. Click **Create proof** and then choose **Advanced Proof**.

![WF](./images/wfp13.png)

In the **new proof** window, select the workflow template that you created before, which should be named `--aepuserLdap-- - Approval Workflow`. Click **Create Proof**.

![WF](./images/wfp14.png)

You'll then be back in your task. Click the **Assign to** button and select **Assign to me**.

![WF](./images/wfp15.png)

Click **Save**.

![WF](./images/wfp16.png)

Click **Work on it**.

![WF](./images/wfp17.png)

Click **Open Proof**

![WF](./images/wfp18.png)

You can now review the proof. Select **Add comment** to add a remark that requires the document to be changed.

![WF](./images/wfp19.png)

Enter your comment and click **Post**. Click **Close**.

![WF](./images/wfp20.png)

Next, you need to change your role from **Reviewer** to **Reviewer & Approver**. To do that, go back to your Task and click **Proofing Workflow**.

![WF](./images/wfp21.png)

Change your role from **Reviewer** to **Reviewer & Approver**.

![WF](./images/wfp22.png)

Go back to your Task and open the proof again. You now see a new button, **Make decision**. Click it.

![WF](./images/wfp23.png)

Select **Changes required** and click **make decision**.

![WF](./images/wfp24.png)

You should then be back here. You now need to upload a second image that takes into account the comments that were provided.

![WF](./images/wfp25.png)

Download [this file](./images/2048x2048_buynow.png) to your desktop.

![this file](./images/2048x2048_buynow.png){width="50px" align="left"}

In your Task view, select the old image file that wasn't approved. Then, click **+ Add new**, select **Version** and then select **Document**.

![WF](./images/wfp26.png)

Select the fle **2048x2048_buynow.png** and click **Open**.

![WF](./images/wfp27.png)

You should then have this. Click **Create proof** and then select **Advanced Proof** again.

![WF](./images/wfp28.png)

You'll then see this. The **Workflow template** is now preselected as Workfront assumes that the previous approval workflow is still valid. Click **Create Proof**.

![WF](./images/wfp29.png)

Select **Open Proof**.

![WF](./images/wfp30.png)

You can now see 2 versions of the file next to eachother.

![WF](./images/wfp31.png)

Click **Make decision**, select **Approved** and click **Make decision** again.

![WF](./images/wfp32.png)

Close the proof preview.

![WF](./images/wfp33.png)

You'll then be back in your Task view, with an approved asset. This asset now needs to be shared towards AEM Assets.

![WF](./images/wfp34.png)

Click the **Share arrow** icon and select your AEM Assets integration, which should be named `--aepUserLdap-- - Citi Signal AEM`.

![WF](./images/wfp35.png)

Double-click the folder you created before, which should be named `--aepUserLdap-- - Workfront Assets`.

![WF](./images/wfp36.png)

Click **Select folder**.

![WF](./images/wfp37.png)

After 1-2 minutes, your document will now be published into AEM Assets. You'll see an AEM icon next to your document name.

![WF](./images/wfp37a.png)

Click **Open summary**.

![WF](./images/wfp38.png)

Go to **Metadata**, you should see this:

![WF](./images/wfp39.png)

Go to **Overview** and click **+ Add** to add a description.

![WF](./images/wfp40.png)

Enter your description. Your proof and document settings are now done.

![WF](./images/wfp41.png)

## 1.2.2.5 View your file in AEM Assets

Go to your folder in AEM Assets, which is named `--aepUserLdap-- - Workfront Assets`.

![WF](./images/wfppaem1.png)

Click the 3 dots under your image, and then select **Details**.

![WF](./images/wfppaem2.png)

You'll then see the Metadata Form your created earlier, with the values that have been populated automatically by the integration between Workfront and AEM Assets.

![WF](./images/wfppaem3.png)

Go Back to [Workflow Management with Adobe Workfront](./workfront.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
