---
title: Create a new asset, review & approve it
description: Create a new asset, review & approve it
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 39854816-4572-46e5-8fe4-861da1eb41cf
---
# 1.8.2 Create a new asset, review & approve it

>[!IMPORTANT]
>
>Before you begin, read the below instructions!

## Instructions for in-person workshops

- **Instance**: **Adobe Tech Insiders**
- **Username**: **adobetechinsiders-XXX@adobeeventlab.com**
- **Password**: use the password that was shared with you
- **AEM Program**: **Tech Insiders - AEM + ACCS XXX** which you can access through [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)
- **Workfront URL**: [https://experience.adobe.com/#/@experienceplatform/so:experienceplatformworkfrontplanningv2-Production/workfront](https://experience.adobe.com/#/@experienceplatform/so:experienceplatformworkfrontplanningv2-Production/workfront)

## 1.8.2.1 Verify reference images in Frame.io

Go to [https://next.frame.io/](https://next.frame.io/). Click to open the folder of your project.

![WF](./images/wffio1.png)

Click to open the folder of your task.

![WF](./images/wffio1a.png)

You should now see all the reference images that were provided in Workfront. The designer now has access to all files that were uploaded in Workfront, in a secure environment, automatically.

![WF](./images/wffio2.png)

## 1.8.2.2 Adobe Cloud Drive

>[!NOTE]
>
>Adobe Cloud Drive isn't generally available yet. Contact your instructor for installation instructions.

After installing Adobe Cloud Drive, you need to sign in. Click the **Adobe Cloud Drive** icon in your task bar and then click **Sign in**.

![WF](./images/acd1.png)

Use the email address linked to your Adobe account to log in.

![WF](./images/acd2.png)

When prompted, ensure you select the organization **`--aepImsOrgName--`**.

![WF](./images/acd3.png)

You should then see this. Click **Open**.

![WF](./images/acd4.png)

You should now see the folder for your project and task being synchronized to your computer.

![WF](./images/acd5.png)

## 1.8.2.3 Create a new asset with Adobe Firefly and Adobe Photshop

>[!NOTE]
>
>In case you prefer not to create the new asset yourself, you can download the finished version [here](./images/timetravelnow.png).

Open **Adobe Photoshop**. Click **New File**.

![WF](./images/ps1.png)

Go to **Web** and then select **Web Most Common**. Click **Create**.

![WF](./images/ps2.png)

Click **Generate image**.

![WF](./images/ps3.png)

Enter the prompt `a neon rabbit running very fast through space` and click **Generate**.

![WF](./images/ps4.png)

You should then see something like this.

![WF](./images/ps5.png)

Click the **text** icon.

![WF](./images/ps6.png)

Add a text field onto your image.

![WF](./images/ps7.png)

Chaneg the text to `Timetravel now!`.

![WF](./images/ps8.png)

Add the CitiSignal logo, which you can download [here](./assets/Logo-White.png).

![WF](./images/ps9.png)

Go to **File** and then select **Save as...**.

![WF](./images/ps10.png)

Use the following name for the file. Click **Save**.

```
CitiSignal-Fiber-Campaign-Winter-2026.psd
```

![WF](./images/ps11.png)

Click **Allow**.

![WF](./images/ps12.png)

Click **OK**.

![WF](./images/ps14.png)

Go to **File**, select **Export** and then choose **Save for Web...**.

![WF](./images/ps15.png)

Click **Save...**.

![WF](./images/ps16.png)

Use the following name for the file. Click **Save**.

```
CitiSignal-Fiber-Campaign-Winter-2026.png
```

![WF](./images/ps17.png)

Go back to your **Adobe Cloud Drive** folder, you should now see both files in the **Final Deliverables** folder.

![WF](./images/ps18.png)

## 1.8.2.4 Approve the asset 

Go back to Workfront, to your Task, to the **Documents** folder. You should now see both files in Workfront.

Select the file **CitiSignal-Fiber-Campaign-Winter-2026.png** and choose **Request approval**.

![WF](./images/ps19.png)

Add yourself as an approver and then click **Request approval**.

![WF](./images/ps20.png)

You should then see this. Click the **approval** icon and then click **Open review**.

![WF](./images/ps21.png)

You should then see this.

![WF](./images/ps22.png)

You can also see that same asset in **Frame.io** by going to [https://next.frame.io/](https://next.frame.io/). Click to open the folder of your project.

![WF](./images/ps23.png)

Click to open the folder of your task.

![WF](./images/ps24.png)

Click to open the folder **Final Deliverables**.

![WF](./images/ps25.png)

You should then see this.

![WF](./images/ps26.png)

Go back to the approval and click **Approved**.

![WF](./images/ps27.png)

Your asset will now be marked as approved in Workfront.

![WF](./images/ps28.png)

## 1.8.2.5 Send the asset to AEM Assets CS 

In Workfront, select your asset and click **Send to**.

![WF](./images/wffio16.png)

Select the AEM Assets environment that you created in the previous exercise. Clck **Send**.

![WF](./images/aemas1.png)

Select the folder **citisignal** and then click **Select Folder**.

![WF](./images/aemas2.png)

After a couple of minutes, your asset is now sent to AEM Assets.

![WF](./images/aemas3.png)

You can now find your assets in AEM Assets.

![WF](./images/aemas4.png)

## Next Steps

Go back to [Unified Review & Approval with Workfront, Frame.io and Adobe Cloud Storage](./esm.md){target="_blank"}

Go back to [All Modules](./../../../overview.md){target="_blank"}
