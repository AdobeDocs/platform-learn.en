---
title: Create a sandbox
seo-title: Create a sandbox | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Create a sandbox
description: In this lesson, you will create a development environment sandbox that you can use for the rest of the tutorial.
role: Data Architect, Data Engineer
feature: Sandboxes
jira: KT-4348
thumbnail: 4348-create-a-sandbox.jpg
exl-id: a04afada-52a1-4812-8fa2-14be72e68614
---
# Create a sandbox

<!--25min-->

In this lesson, you will create a development environment sandbox that you will use for the rest of the tutorial.

Sandboxes provide isolated environments where you can try out functionality without mixing resources and data with your Production environment. For more details, see the [sandboxes documentation](https://experienceleague.adobe.com/docs/experience-platform/sandbox/home.html).

**Data Architects** and **Data Engineers** will need to create sandboxes outside of this tutorial.

Before you begin the exercises, watch this short video to learn more about sandboxes:
>[!VIDEO](https://video.tv.adobe.com/v/29838/?learn=on&enablevpops)

## Permissions required

In the [Configure Permissions](configure-permissions.md) lesson, you set up all the access controls required to complete this lesson.

<!--
* Permission items **[!UICONTROL Sandbox Administration]** > **[!UICONTROL View Sandboxes]** and **[!UICONTROL Manage Sandboxes]**
* Permission item **[!UICONTROL Sandboxes]** > **[!UICONTROL Prod]**
* User-role access to the `Luma Tutorial Platform` product profile
* Admin-level access to the `Luma Tutorial Platform` product profile
-->

## Create a Sandbox

Let's create a sandbox:

1. Log into the [Adobe Experience Platform](https://experience.adobe.com/platform) interface
1. Go to **[!UICONTROL Sandboxes]** in the left navigation
1. Select **[!UICONTROL Create sandbox]** on the top right
   ![Select Create sandbox](assets/sandbox-createSandbox.png)

1. Select **[!UICONTROL Development]** as the **[!UICONTROL Type]**
1. Name your sandbox `luma-tutorial` (consider adding your name to the end)
1. Title your tutorial `Luma Tutorial` (consider adding your name to the end)
1. Select the **[!UICONTROL Create]** button
   ![Create your sandbox](assets/sandbox-nameSandbox.png)
   >[!NOTE]
   >
   >While you could use any arbitrary values for your sandbox name and title, sticking to the values suggested is recommended as we will refer to these labels throughout the tutorial. If there are multiple people at your organization completing this tutorial, consider adding your name at the end of the sandbox title and name, for example luma-tutorial-ignatiusjreilly.

Sandboxes take approximately 30 seconds to create, during which time a "[!UICONTROL Creating]" status displays. When the sandbox is fully created, it shows as "[!UICONTROL Active]":
   ![Active status](assets/sandbox-active.png)

Wait until your sandbox is "[!UICONTROL Active]" before continuing to the next exercise.

## Add the new sandbox to the role

Once the sandbox is active, you must include it in your role in order to use it. To add it to your role (requires System Admin or Product Admin privileges):

1. Go to the [!UICONTROL Permissions] screen
1. Open the `Luma Tutorial Platform` role
1. Optionally _remove_ the `Prod` sandbox from the role
1. Add the `Luma Tutorial` sandbox
1. Select **[!UICONTROL Save]**
1. On the [!UICONTROL Sandboxes] row, select **[!UICONTROL Edit]**

    ![Add the Luma Tutorial](assets/sandbox-addLumaTutorial.png)

1. Reload (or Shift-reload) the page and you should now either be in the `Luma Tutorial` sandbox or it should appear in your sandbox dropdown
1. Switch to the `Luma Tutorial` sandbox if you aren't already in it

   ![Confirm Sandbox](assets/sandbox-confirmDropdown.png)

Great, you've created your sandbox and are ready to [Set up Developer Console and Postman](set-up-developer-console-and-postman.md)!
