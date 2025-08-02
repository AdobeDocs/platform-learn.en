---
title: Proofing with Workfront
description: Proofing with Workfront
kt: 5342
doc-type: tutorial
---
# 1.2.2 Proofing with Workfront

>[!IMPORTANT]
>
>If you have previously configured an AEM CS Program with an AEM Assets CS environment, it may be that your AEM CS sandbox was hibernated. Given that dehibernating such a sandbox takes 10-15 minutes, it would be a good idea to start the dehibernation process now so that you don't have to wait for it at a later time.

## 1.2.2.1 Create a new Approval Flow

Go back to **Adobe Workfront**. Click the **menu** icon and select **Proofing**.

![WF](./images/wfp1.png)

Go to **Workflows**, click **+ New** and then select **New template**.

![WF](./images/wfp2.png)

Set the **Template name** to `--aepUserLdap-- - Approval Workflow` and set the **Template owner** to yourself.

![WF](./images/wfp3.png)

Scroll down, and under **Stages** > **Stage 1**, add yourself with the **Role** of **Reviewer & Approver**.

Click **Create**.

![WF](./images/wfp4.png)

Your basic approval workflow is now ready to be used.

![WF](./images/wfp5.png)

## 1.2.2.2 Create a new Project

Open the **menu** and go to **Programs**.

![WF](./images/wfp6a.png)

Click to the program you created before, which is named `--aepUserLdap-- CitiSignal Fiber Launch`.

>[!NOTE]
>
>You created a program as part of the exercise on [Workfront Planning](./../module1.1/ex1.md) with the automation you created and ran. If you haven't done that yet, you can find the instructions there.

![WF](./images/wfp6b.png)

In your program, go to **Projects**. Click **+ New Project** and then select **New Project**.

![WF](./images/wfp6.png)

You should then see this. Change the name to `--aepUserLdap-- - CitiSignal Fiber Launch`.

![WF](./images/wfp6c.png)

Go to **Project Details**. Click **+Add** under **Description**.

![WF](./images/wfp6d.png)

Set the description to `The CitiSignal Fiber Launch project is used to plan the upcoming launch of CitiSignal Fiber.`

Click **Save Changes**.

![WF](./images/wfp6e.png)

Your project is now created.

![WF](./images/wfp7.png)

## 1.2.2.3 Create a new Task

Go to **Tasks** and click **+ New Task**.

![WF](./images/wfp7a.png)

Enter this name for your task: `Create assets for Fiber campaign`. 

Set the field **Description** to: `This task is used to track the progress of the creation of the assets for the CitiSignal Fiber Launch Campaign.`

Click **Create Task**.

![WF](./images/wfp8.png)

You should then see this.

![WF](./images/wfp9.png)

In the column **Assignment**, add your own name.

![WF](./images/wfp9a.png)

The task will then be assigned to you.

![WF](./images/wfp9b.png)

## 1.2.2.4 Add a new Document to your Task go through the approval flow

Click the **Workfront** logo to go back to the overview page. You should then see the project you just created appear in the overview. Click your project to open it.

![WF](./images/wfp9c.png)

In **Tasks**, click to open the task.

![WF](./images/wfp9d.png)

Go to **Documents**. Click **+ Add new** and then select **Document**.

![WF](./images/wfp10.png)

Download [this file](./images/2048x2048.png) to your desktop.

![WF](./images/2048x2048.png){width="50px" align="left"}

Select the file **2048x2048.png** and click **Open**.

![WF](./images/wfp12.png)

You should then have this. Hover over the uploaded document. Click **Create proof** and then choose **Advanced Proof**.

![WF](./images/wfp13.png)

In the **new proof** window, select **Automated** and then select the workflow template that you created before, which should be named `--aepUserLdap-- - Approval Workflow`. Click **Create Proof**.

![WF](./images/wfp14.png)

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

Go back to your **Task** and the **Document**. You now need to upload a second image that takes into account the comments that were provided.

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

Click the **Task Name** to go back to the Task overview.

![WF](./images/wfp33.png)

You'll then be back in your Task view, with an approved asset. This asset now needs to be shared towards AEM Assets.

![WF](./images/wfp34.png)

Select the approved document. Click the **Share arrow** icon and select your AEM Assets integration, which should be named `--aepUserLdap-- - CitiSignal AEM`.

![WF](./images/wfp35.png)

Double-click the folder you created before, which should be named `--aepUserLdap-- - CitiSignal Fiber Launch Assets`.

![WF](./images/wfp36.png)

Click **Select folder**.

![WF](./images/wfp37.png)

After 1-2 minutes, your document will now be published into AEM Assets. You'll see an AEM icon next to your document name.

![WF](./images/wfp37a.png)

Click **Mark as done** to finish this task.

![WF](./images/wfp37b.png)

You should then see this.

![WF](./images/wfp37c.png)

## 1.2.2.5 View your file in AEM Assets

Go to your folder in AEM Assets CS, which is named `--aepUserLdap-- - CitiSignal Fiber Launch Assets`.

![WF](./images/wfppaem1.png)

Select the image, and then choose **Details**.

![WF](./images/wfppaem2.png)

You'll then see the Metadata Form your created earlier, with the values that have been populated automatically by the integration between Workfront and AEM Assets.

![WF](./images/wfppaem3.png)

Go Back to [Workflow Management with Adobe Workfront](./workfront.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
