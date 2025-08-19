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

Scroll down, and under **Stages** > **Stage 1**, change the **Proof Creator** role to **Reviewer & Approver**. You can also add anyone else, so as an example, add yourself by selecting your user and set the **Role** of **Reviewer & Approver**.

Click **Create**.

![WF](./images/wfp4.png)

Your basic approval workflow is now ready to be used.

![WF](./images/wfp5.png)

## 1.2.2.2 Enable Workfront Blueprint

In the next step, you will create a new project using a template. Adobe Workfront provides you with a number of available blueprints that just require to be activated.

For CitiSignal's use case, the blueprint **Integrated Campaign Execution** is the one you need to use.

In order to install that blueprint, open the menu and select **Blueprints**.

![WF](./images/blueprint1.png)

Select the filter **Marketing** and then scroll down to find the blueprint **Integrated Campaign Execution**. Click **Install**.

![WF](./images/blueprint2.png)

Click **Continue**.

![WF](./images/blueprint3.png)

Click **Install as is...**.

![WF](./images/blueprint4.png)

You should then see this. Installing may take a couple of minutes.

![WF](./images/blueprint5.png)

After a couple of minutes, the blueprint will be installed.

![WF](./images/blueprint6.png)

## 1.2.2.3 Create a new Project

Open the **menu** and go to **Programs**.

![WF](./images/wfp6a.png)

Click to the program you created before, which is named `--aepUserLdap-- CitiSignal Fiber Launch`.

>[!NOTE]
>
>You created a program as part of the exercise on [Workfront Planning](./../module1.1/ex1.md) with the automation you created and ran. If you haven't done that yet, you can find the instructions there.

![WF](./images/wfp6b.png)

In your program, go to **Projects**. Click **+ New Project** and then select **New Project from Template**.

![WF](./images/wfp6.png)

Select the template **Integrated Campaign Execution** and click **Use template**.

![WF](./images/wfp6g.png)

You should then see this. Change the name to `--aepUserLdap-- - CitiSignal Fiber Launch Winter 2026` and click **Create project**.

![WF](./images/wfp6c.png)

Your project is now created. Go to **Project Details**.

![WF](./images/wfp6h.png)

Go to **Project Details**. Click to select the current text under **Description**.

![WF](./images/wfp6d.png)

Set the description to `The CitiSignal Fiber Launch project is used to plan the upcoming launch of CitiSignal Fiber.`

Click **Save Changes**.

![WF](./images/wfp6e.png)

Your project is now ready to be used.

![WF](./images/wfp7.png)

The tasks and dependencies in the project have been created based on the template that you chose and you have been set as the. owner of the project. The status of the project has been set to **Planning**. You can change the status of the project by selecting another value in the list.

![WF](./images/wfp7z.png)

## 1.2.2.4 Create a new Task

Hover over the task **Begin to Create Design Templates** and click the 3 dots **...**.

![WF](./images/wfp7a.png)

Select the option **Insert Task Below**.

![WF](./images/wfp7x.png)

Enter this name for your task: `Create layout using approved assets and copy`. 

Set the field **Assignments** to the role **Designer**.
Set the field **Duration** to **5 days**.
Set the field predecessor to **9**.
Enter a date for the fields **Start on** and **Due on**.

Click somewhere else in the screen to save the new task.

![WF](./images/wfp8.png)

You should then see this. Click the task to open it.

![WF](./images/wfp9.png)

Go to **task Details** and set the field **Description** to: `This task is used to track the progress of the creation of the assets for the CitiSignal Fiber Launch Campaign.`

Click **Save Changes**.

![WF](./images/wfp9a.png)

You should then see this. Click on the **Project** field to go back to your project.

![WF](./images/wfp9b.png)

In the **Project** view, go to **Workload Balancer**.

![WF](./images/wfpwlb1.png)

Click **Bulk Assignments**.

![WF](./images/wfpwlb2.png)

Select the **Role assignment** of **Designer** and then click in the field **User to assign**. This will show all users that have a **Designer** role in your Workfront instance. In this case, select the fictitious user **Melissa Jenkins**.

![WF](./images/wfpwlb3.png)

Click **Assign**. The user you selected will now be assigned to the tasks in the project that are linked to the **Designer** role.

![WF](./images/wfpwlb4.png)

The tasks are now assigned. Click **Tasks** to go back to the **Tasks** overview page.

![WF](./images/wfpwlb5.png)

Click the task you created, which is named 
**Create layout using approved assets and copy**.

![WF](./images/wfpwlb6.png)

You will now start working on this task as part of this exercise. You can see that Melissa Jenkins is assigned to this task at the moment. To change that to yourself, click the **Assignments** field and select **Assign to me**.

![WF](./images/wfpwlb7.png)

Click **Save**.

![WF](./images/wfpwlb8.png)

Click **Work on it**.

![WF](./images/wfpwlb9.png)

You should then see this.

![WF](./images/wfpwlb10.png)

As part of this task, you need to create a new image and then upload it as a document in Workfront. You'll now create that asset yourself using Adobe Express.

## 1.2.2.5 Create Asset with Adobe Firefly Services and Adobe Express

Go to [https://firefly.adobe.com/](https://firefly.adobe.com/){target="_blank"}. Enter the prompt `a neon rabbit running very fast through space` and click **Generate**.

![GSPeM](./images/gsasset1.png)

You will then see several images being generated. Choose the image you like the most, click the **Share** icon on the image and then select **Open in Adobe Express**.

![GSPeM](./images/gsasset2.png)

You will then see the image you just generated become available in Adobe Express for editing. You now need to add the CitiSignal logo on the image. To do that, go to **Brands**.

![GSPeM](./images/gsasset3.png)

You should then see a CitiSignal brand template. that was created in GenStudio for Performance Marketing appear in Adobe Express. Click to select a brand template which has `CitiSignal` in its name.

![GSPeM](./images/gsasset4.png)

Go to **Logos** and click the **white** Citisignal logo to drop it on the image.

![GSPeM](./images/gsasset5.png)

Position the CitiSignal logo at the top of your image, not too far from the middle.

![GSPeM](./images/gsasset6.png)

Go to **Text**.

![GSPeM](./images/gsasset6a.png)

Click **Add your text**.

![GSPeM](./images/gsasset6b.png)

Enter the text `Timetravel now!`, change the font color and font size, set the text to **Bold** so that you have an image similar to this one.

![GSPeM](./images/gsasset6c.png)

Next, click **Share**.

![GSPeM](./images/gsasset7.png)

Select **AEM Assets**.

![GSPeM](./images/gsasset8.png)

Change the file name to `CitiSignal - Neon Rabbit - Timetravel now!`.
Click **Select folder**.

![GSPeM](./images/gsasset9.png)

Select your AEM Assets CS repository, which should be named `--aepUserLdap-- - CitiSignal` and then select the folder `--aepUserLdap-- - CitiSignal Fiber Campaign`. Click **Select**.

![GSPeM](./images/gsasset11.png)

You should then see this. Click **Upload 1 asset**. Your image will now be uploaded to AEM Assets CS.

![GSPeM](./images/gsasset12.png)

## 1.2.2.6 Add a new Document to your Task and start the approval flow

Go back to the **Task Detail** screen. Go to **Documents**. Click **+ Add new** and then select your AEM Assets CS repository, which should be named `--aepUserLdap-- - CitiSignal`.

![WF](./images/wfp10.png)

Double-click to open the folder `--aepUserLdap-- CitiSignal Fiber Campaign`.

![WF](./images/wfp10a.png)

Select the file you created in the previous step, which is named **CitiSignal - Neon rabbit - Timetravel Now!.png**. Click **Select**.

![WF](./images/2048x2048.png){width="50px" align="left"}

You should then have this. Hover over the uploaded document. Click **Create proof** and then choose **Advanced Proof**.

![WF](./images/wfp13.png)

In the **new proof** window, select **Automated** and then select the workflow template that you created before, which should be named `--aepUserLdap-- - Approval Workflow`. Click **Create Proof**.

![WF](./images/wfp14.png)

Click **Open Proof**

![WF](./images/wfp18.png)

You can now review the proof. Select **Add comment** to add a remark that requires the document to be changed.

![WF](./images/wfp19.png)

Enter your comment and click **Post**. Next, click **Make a decision**.

![WF](./images/wfp20.png)

Select **Changes required** and click **make decision**.

![WF](./images/wfp24.png)

Go back to your **Task** and the **Document**. You'll see the text **Changes required** also appear there..

![WF](./images/wfp25.png)

You now need to make design changes, which you will do in Adobe Express.

## 1.2.2.7 Make design changes in Adobe Express

Go to [https://new.express.adobe.com/your-stuff/files](https://new.express.adobe.com/your-stuff/files) and open the image you created earlier again.

![WF](./images/wfp25a.png)

Change the CTA text to `Get On Board Now!`.

![WF](./images/wfp25b.png)

Click **Share** and then select **AEM Assets**.

![WF](./images/wfp25c.png)

Enter the name `CitiSignal - Neon Rabbit - Get On Board Now!` and then click **Select Folder** to select a destination folder.

![WF](./images/wfp25d.png)

Select your AEM Assets CS repository, which should be named `--aepUserLdap-- - CitiSignal` and then select the folder `--aepUserLdap-- - CitiSignal Fiber Campaign`. Click **Select**.

![WF](./images/wfp25e.png)

Click **upload 1 asset**.

![WF](./images/wfp25f.png)

Your new asset is now created and stored in AEM Assets.

## 1.2.2.8 Add a new version of your Document to your Task

In your Task view in Adobe Workfront, select the old image file that wasn't approved. Then, click **+ Add new**, select **Version** and then select your AEM Assets CS repository, which should be named `--aepUserLdap-- - CitiSignal`.

![WF](./images/wfp26.png)

Navigate to the folder `--aepUserLdap-- CitiSignal Fiber Campaign` and select the file `CitiSignal - Neon Rabit - Get On Board Now!.png`. Click **Select**.

![WF](./images/wfp26a.png)

You should then have this. Click **Create proof** and then select **Advanced Proof** again.

![WF](./images/wfp28.png)

You'll then see this. The **Workflow template** is now preselected as Workfront assumes that the previous approval workflow is still valid. Click **Create Proof**.

![WF](./images/wfp29.png)

Select **Open Proof**.

![WF](./images/wfp30.png)

You can now see 2 versions of the file next to eachother. Click the **Compare Proofs** button.

![WF](./images/wfp31.png)

You should then see both versions of the image next to eachother. Click **Make decision**. 

![WF](./images/wfp32.png)

Select **Approved** and click **Make decision** again.

![WF](./images/wfp32a.png)

Close the **Compare Proofs** view by closing the left version of the image. Click the **Task Name** to go back to the Task overview.

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

## 1.2.2.9 View your file in AEM Assets

Go to your folder in AEM Assets CS, which is named `--aepUserLdap-- - CitiSignal Fiber Launch Assets`.

![WF](./images/wfppaem1.png)

Select the image, and then choose **Details**.

![WF](./images/wfppaem2.png)

You'll then see the Metadata Form your created earlier, with the values that have been populated automatically by the integration between Workfront and AEM Assets.

![WF](./images/wfppaem3.png)

Go Back to [Workflow Management with Adobe Workfront](./workfront.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
