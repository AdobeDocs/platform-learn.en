---
title: Create a Sandbox | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
description: 
feature: sandbox
topics: 
kt: 4348
audience: data architect,data engineer
doc-type: tutorial
activity: implement
---

# Create a sandbox

Sandboxes provide isolated environments where you can try out functionality without mixing resources and data with your Production environment.

In this lesson, you will create a development environment sandbox that you can use for the rest of the tutorial.

<!--include note on extent of sandbox support-->

First, watch this short video to learn more about sandboxes:
>[!VIDEO](https://video.tv.adobe.com/v/29838/?quality=12&learn=on)

## Permissions required

In the [Configure Permissions](configure-permissions.md) lesson, you setup all the access controls you need to complete this lesson, specifically:

* Permission item Sandbox Management > View Sandboxes
* Permission item Sandbox Management > Manage Sandboxes
* Permission item Sandboxes > (any sandbox)
* User-role access to the `Luma Tutorial` product profile
* Admin-level access to the `Luma Tutorial` product profile

## Create a Sandbox

So let's create a sandbox

1. Click **[!UICONTROL Sandboxes]** in the left navigation
   
   ![](assets/sandbox-clickSandboxes.png)

1. Click **[!UICONTROL Create sandbox]** on the top right
   ![](assets/sandbox-createSandbox.png)

1. Name your sandbox `luma-tutorial` 
1. Title your tutorial `Luma Tutorial`
   ![](assets/sandbox-nameSandbox.png)

   >[!NOTE]
   >
   >While you could use any arbitrary values for your sandbox name and title, sticking to the values suggested is recommended as we will refer to these labels throughout the tutorial

Sandboxes take approximately fifteen minutes to create and "[!UICONTROL Creating]" status will display:
   ![](assets/sandbox-creating.png)

Wait until your sandbox is "[!UICONTROL Active]" before continuing to the next steps:
   ![](assets/sandbox-active.png)



## Add the new sandbox to the product profile

Although the sandbox is now active, you will not be able to start using it until you have included it in your product profile via the Admin Console.

### Update the product profile

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

1. If you reload the You should now be able to see the new sandbox appear in the sandbox dropdown in the Platform interface:

   ![Confirm Sandbox](assets/sandbox-confirmDropdown.png)

## Additional Resources

* [Sandboxes documentation](https://docs.adobe.com/content/help/en/experience-platform/sandbox/home.html)
* [Sandbox API reference](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/sandbox-api.yaml)