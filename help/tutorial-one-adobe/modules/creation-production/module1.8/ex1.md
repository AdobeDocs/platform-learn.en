---
title: Getting started with Workfront, Frame.io & Adobe Cloud Storage
description: Getting started with Workfront, Frame.io & Adobe Cloud Storage
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 2f9a3eef-16ef-497c-97f7-377ff9ed2f82
---
# 1.8.1 Getting started with Workfront, Frame.io & Adobe Cloud Storage

>[!IMPORTANT]
>
>Your AEM CS sandbox may be hibernated. Given that dehibernating a sandbox takes 10-15 minutes, it would be a good idea to start the dehibernation process now so that you don't have to wait for it at a later time.

>[!IMPORTANT]
>
>Before you begin, read the below instructions!

## Instructions: Partner Lab New Orleans

For this exercise, you need to use:

- **Instance**: **Adobe Tech Insiders**
- **Username**: **adobetechinsiders-XXX@adobeeventlab.com**
- **Password**: use the password that was shared with you
- **AEM Program**: **Tech Insiders - AEM + ACCS XXX** which you can access through [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)
- **Workfront URL**: [https://experience.adobe.com/#/@experienceplatform/so:experienceplatformworkfrontplanningv2-Production/workfront](https://experience.adobe.com/#/@experienceplatform/so:experienceplatformworkfrontplanningv2-Production/workfront)

## 1.8.1.1 Workfront Workflow Terminology

The following are the main Workfront objects and concepts:

| Name                   | Last Update |
| ---------------------- | ------------ |
| Portfolio | A collection of projects that have unifying characteristics. Those projects usually compete for the same resources, budget, or time slot.   |
| Program | A subset within a portfolio, where similar projects can be grouped together in order to achieve a well-defined benefit. |
| Project | A large amount of work that must be completed within a specific timeframe and must use a specific budget and number of resources. To make it manageable, you divide the project into a series of tasks. Completing all the tasks results in the completion of the project. |
| Project Template | You can use project templates to capture most of the repeatable processes, information, and settings associated with the projects in your organization. After creating templates, you can attach them to existing projects, or you can use them to build new projects.  |
| Task | An activity that must be performed as a step toward achieving a final goal (completing the Project). Tasks can never exist independently. They are always part of a project.|
| Assignment | A user, job role, or team assigned to an issue or a task. Projects, portfolios, or programs cannot have assignments. |
| Document/Version | Any file that is attached to an object within Workfront. Each time the same document is uploaded to the same object, it is assigned a version number. Users can view and change several options for a previous version of a document. |
| Approval | A given work item, such as a task, document, or timesheet, may require that a supervisor or other user sign off on the work item. This process of signing off is called approval. |


Go to [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Click to open **Workfront**.

![Workfront Planning](./images/wfpl1.png)

You'll then see this.

![WF](./images/wfb1.png)

## 1.8.1.2 Enable Workfront Blueprint

In the next step, you will create a new project using a template. Adobe Workfront provides you with a number of available blueprints that just require to be activated.

For CitiSignal's use case, the blueprint **Integrated Campaign Execution** is the one you need to use.

In order to install that blueprint, open the menu and select **Blueprints**.

![WF](./images/blueprint1a.png)

Select the filter **Marketing** and then scroll down to find the blueprint **Integrated Campaign Execution**. Click **Install**.

![WF](./images/blueprint1.png)

Click **Continue**.

![WF](./images/blueprint2.png)

Change the **Project Template Name** to `--aepUserLdap-- - Integrated Campaign Execution`.

Click **Install Blueprint**.

![WF](./images/blueprint3.png)

After a couple of minutes, the blueprint will be installed.

![WF](./images/blueprint6.png)

## 1.8.1.3 Configure your AEM Assets Integration

Click the **menu** icon and then select **Setup**.

![WF](./images/wfb2.png)

In the left menu, scroll down to **Documents** and then click **Experience Manager Assets**. Click **+ Add Experience Manager integration**.

![WF](./images/wfb3.png)

For the name of your integration, use `--aepUserLdap-- - CitiSignal AEM + ACCS`.

Open the **Experience Manager repository** dropdown and select your AEM CS instance, which should be named `Tech Insiders - AEM + ACCS XXX dev author`.

Click **Save**.

![WF](./images/wfb5.png)

Your integration from Workfront to AEM Assets CS is now configured.

![WF](./images/wfb7.png)

## 1.8.1.4 Create a new Project

Open the **menu** and go to **Porftolios**.

![WF](./images/wfp6a.png)

Click **+ New Portfolio**.

![WF](./images/wfpfolio1.png)

Enter the portfolio name `--aepUserLdap-- - CitiSignal`.

![WF](./images/wfpfolio2.png)

Go to **Programs** and click **+ New Program**. Select **New Program**.

![WF](./images/wfnp1.png)

Enter the program name: `--aepUserLdap-- - CitiSignal Fiber Launch`.

![WF](./images/wfp6b.png)

In your program, go to **Projects**. Click **+ New Project** and then select **New Project from Template**.

![WF](./images/wfp6.png)

Select the template `--aepUserLdap-- - Integrated Campaign Execution` and click **Use template**.

![WF](./images/wfp6g.png)

You should then see this. Change the name to `--aepUserLdap-- - CitiSignal Fiber Launch Winter 2026` and click **Create project**.

![WF](./images/wfp6c.png)

Your project is now created. Go to **Project Details**.

![WF](./images/wfp6h.png)

Go to **Project Details**. Click to select the current text under **Description**.

Set the description to `The CitiSignal Fiber Launch project is used to plan the upcoming launch of CitiSignal Fiber.`

Click **Save Changes**.

![WF](./images/wfp6e.png)

Your project is now ready to be used.

![WF](./images/wfp7.png)

The tasks and dependencies in the project have been created based on the template that you chose and you have been set as the. owner of the project. The status of the project has been set to **Planning**. You can change the status of the project by selecting another value in the list.

![WF](./images/wfp7z.png)

## 1.8.1.5 Project view in Frame.io

Go to [https://next.frame.io/](https://next.frame.io/). Log in, and select the instance to use, in this example **Adobe Tech Insiders**. You'll notice that a folder already exists in Frame.io for the project that you just created. The folder is named after the project name that you entered earlier.

This is a feature of Adobe Cloud Storage, a cloud-based storage solution that serves as the central repository for assets across Adobe enterprise products, including Workfront and Frame.io.

Key benefits of Adobe Cloud Storage include:

- Unified storage layer for creative and work management assets
- Centralized permissions via Adobe Identity Management system (IMS) for secure access control
- End-to-end asset visibility across Workfront and Frame.io
- Scalable storage and quota management for enterprise needs

![WF](./images/fio1.png)

## 1.8.1.6 Create a new Task

Go back to Workfront. Go to **Tasks**, hover over the task **Begin to Create Design Templates** and click the 3 dots **...**.

![WF](./images/wfp7a.png)

Select the option **Insert Task Below**.

![WF](./images/wfp7x.png)

Enter this name for your task: `Create layout using approved assets and copy`. 

Set the field **Assignments** to the role **Designer**.
Set the field **Duration** to **5 days**.
Set the field predecessor to **9**.

Click somewhere else in the screen to save the new task.

![WF](./images/wfp8.png)

You should then see this. Click the task to open it.

![WF](./images/wfp9.png)

Go to **Task Details** and set the field **Description** to: `This task is used to track the progress of the creation of the assets for the CitiSignal Fiber Launch Campaign.`

Click **Save Changes**.

![WF](./images/wfp9a.png)

You should then see this. Click the **Assignments** field and select **Assign to me**.

![WF](./images/wfpwlb7.png)

Click **Save**.

![WF](./images/wfpwlb8.png)

Click **Work on it**.

![WF](./images/wfpwlb9.png)

You should then see this.

![WF](./images/wfpwlb10.png)

As part of this task, a new asset needs to be created. In the next step, first you'll provide reference images in Workfront so that the designer knows what is expected. Then, you'll change into the role of Designer and create that asset yourself using Adobe Express.

## 1.8.1.7 Upload reference images

Download the reference images [here](./assets/reference_images.zip) to your desktop and unzip them.

![WF](./images/wfrefimg1.png)

Go to **Documents**, click **+ Add new** and then select **Document**.

![WF](./images/wfrefimg3.png)

Navigate to the folder that you downloaded which contains the reference images. Select all images and click **Open**.

![WF](./images/wfrefimg4.png)

After a couple of minutes, all images will be uploaded and a new folder will be created using the name of the task. Click that new folder to open it.

![WF](./images/wfrefimg5.png)

With the reference images in place, the designer can now create the new asset for this campaign.

You should then see this.

![WF](./images/wfrefimg6.png)

Next, click **+** and then select **New Folder**.

![WF](./images/wfrefimg7.png)

Enter the name `Final Deliverables` and click **Create**.

![WF](./images/wfrefimg8.png)

You should then see this. This folder will be used to store the final images for approval.

![WF](./images/wfrefimg9.png)

## Next Steps

Next Step: [Create a new asset, review & approve it](./ex2.md){target="_blank"}

Go back to [Unified Review & Approval with Workfront, Frame.io and Adobe Cloud Storage](./esm.md){target="_blank"}

Go back to [All Modules](./../../../overview.md){target="_blank"}