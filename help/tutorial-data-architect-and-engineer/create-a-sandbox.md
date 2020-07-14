---
title: Create a Sandbox | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
description: 
feature: sandbox
topics: 
kt: 4348
audience: data-architect,data-engineer
doc-type: tutorial
activity: implement
---

# Create a Sandbox

In this tutorial you will be uploading sample data into your Platform account. In order to segregate this sample data from your company's actual production data, we will use the Sandbox feature in Adobe Experience Platform.

Sandboxes provide isolated environments where you can try out functionality and then delete them when you are done.

## Pre-requisites

## Create a Sandbox

1. Click **[!UICONTROL Sandboxes]** in the left navigation
   
   ![](assets/sandbox-clickSandboxes.png)

1. Click **[!UICONTROL Create sandbox]** on the top right
   ![](assets/sandbox-createSandbox.png)

1. Give your sandbox a **[!UICONTROL Name]** and a **[!UICONTROL Title]**. The **[!UICONTROL Name]** must be all lowercase, alphanumeric characters and hyphens.
   ![](assets/sandbox-nameSandbox.png)

Sandboxes take approximately fifteen minutes to create and will display a "[!UICONTROL Creating]" status:
   ![](assets/sandbox-creating.png)

Wait until your sandbox is "[!UICONTROL Active]" before continuing to the next steps:
   ![](assets/sandbox-active.png)



## Get Access to the Sandbox

Although the sandbox is now active, you will not be able to start using it  until you have been assigned access in the Admin Console.

To get access rights to the new sandbox you will need Administrative privileges or you will need the assistance of an administrator at your company. Here is what those the basic steps look like, although the configuration of Product Profiles and users might be different at your company.

### Select the Product Profile

1. Log into the [Admin Console](https://adminconsole.adobe.com)
1. Select **[!UICONTROL Products > Adobe Experience Platform]**
1. Click on the [!UICONTROL Product Profile] containing the users who need access to the Sandbox (you may wish to create a new one)

    ![Select the Product Profile](assets/sandbox-selectProfile.png)

1. Click on the **[!UICONTROL Permissions]** tab

1. On the [!UICONTROL Sandboxes] row, click **[!UICONTROL Edit]**

    ![Click Edit](assets/sandbox-selectSandboxes.png)

1. Click the **[!UICONTROL +]** icon to add the new sandbox to the right hand column

    ![Move the Sandbox to the other column](assets/sandbox-moveToOtherColumn.png)

1. Click **[!UICONTROL Save]** to save the updated permissions  

    ![Save Permissions](assets/sandbox-savePermissions.png)

1. You should now be able to see the new sandbox appear in the sandbox dropdown in the Platform interface:

   ![Confirm Sandbox](assets/sandbox-confirmDropdown.png)