---
title: Configure permissions
seo-title: Configure permissions | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Configure permissions
description: In this lesson, you will configure Adobe Experience Platform user permissions using Adobe's Admin Console.
role: Developer
feature: Access Control
jira: KT-4348
thumbnail: 4348-configure-permissions.jpg
exl-id: ca01f99e-f10c-4bf0-bef2-b011ac29a565
TQID: https://experienceleague.adobe.com/GWWEjcIp8RZY-PeLiKSbxskxc7EBffI7LAT1quubOrw
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: adf04a6a-050f-44bc-a52c-db79ccb22ebf
    internal-label: Administration
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: a16ec9c0-4484-4842-b9a0-5504cde38e6a
    internal-label: Access control
  - id: a230274e-7e6e-49eb-b817-514495a710ac
    internal-label: query service
  - id: a7150a74-b8a9-4042-b066-147c5f0ca505
    internal-label: Alerts
  - id: a9b953c0-98db-499b-97f5-a0dc3290bda3
    internal-label: Adobe Admin Console
  - id: a9eb38d5-9d89-492f-af4e-b968a07f2d91
    internal-label: Permissions
  - id: abc02dd6-664f-446a-9aaa-675bc0f2fe4a
    internal-label: Sources
  - id: d175cb4c-5781-454e-a826-bf6dff786265
    internal-label: Roles
  - id: d1a87129-ba05-4f15-98b1-233618f1774a
    internal-label: Data ingestion
  - id: f5efb499-54f9-432b-ac5c-599dbac103af
    internal-label: Data management
  - id: f6ff4d13-7b5c-4533-8556-95e76673d4cb
    internal-label: Properties
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: b23e006f-0a29-4f1d-8fd0-77aa56f3d12b
    internal-label: Data modeling
  - id: c7d04a2c-412a-4c9d-9d7a-4456eaa5adeb
    internal-label: Governance
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
    internal-label: Data management
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
---
# Configure permissions

<!--30min-->

In this lesson, you will configure Adobe Experience Platform user permissions using [!DNL Adobe's Admin Console] and the [!UICONTROL Permissions] screen in the Platform interface. 

Access control is a key privacy capability in Experience Platform and we recommend limiting permissions to the minimum required for people to perform their job functions. See the [Access Control documentation](https://experienceleague.adobe.com/docs/experience-platform/access-control/home.html) for more information.

Data Architects and Data Engineers are  power users of Adobe Experience Platform and you will need many permissions in order to complete this tutorial and later in your day-to-day work. Data Architects are likely be involved in the administration of *other Platform users* at their company such as marketers, analysts, and data scientists. As you complete this lesson, think about how you might use these features to manage other users at your company.

**Data Architects** often configure permissions for other users outside of this tutorial.

>[!IMPORTANT]
>
>A System Administrator of Adobe Experience Cloud products must complete some of the steps in this lesson, which is called out in the section headings. If you are not System Administrator, please reach out to one at your company and ask them complete these tasks. There is also a task they need to complete during the [Set up Developer Console and Postman](set-up-developer-console-and-postman.md) lesson.

## About the Admin Console

The [!DNL Admin Console] is the interface used to administer user access to all Adobe Experience Cloud products. For access to Platform, a user or must be added in the Admin Console and then all of their granular permission items are managed in the Permissions screen of Adobe Experience Platform.


Here is a quick summary of the roles that exist for Platform:

* **Users** of a product profile can complete tasks in Platform's user interface according to the permissions assigned in the product profile.
* **Developers** can create API credentials and projects in the Adobe Developer Console, in order to begin using Experience Platform API
* **Product Admins** can add users and developers to the Adobe Experience Platform product in the Adobe Admin Console, as well as manage granular user access in the Permissions screen of the Platform interface.
* **System Administrators** can add product admins and administer essentially any permissions for all Adobe Experience Cloud products.

## Add a User and Developer to the `AEP-Default-All-Users` product profile (requires a system administrator or product admin)

In this exercise, you or a System Administrator or Product Admin will add you as a User and Developer in the Adobe Experience Platform product of the Adobe Admin Console.

>[!NOTE]
>
>If you are a System Administrator assisting a colleague taking this tutorial, consider adding your colleague as a *Product Administrator* for Adobe Experience Platform. As a Product Administrator, they would be able to complete these steps on their own and administrate other Experience Platform users in the future.

To add the tutorial participant as a [!UICONTROL User] and [!UICONTROL Developer]:

1. Log into the [Adobe Admin Console](https://adminconsole.adobe.com)
1. Select **[!UICONTROL Products]** on the top navigation
1. Select **Adobe Experience Platform**
    ![Select Adobe Experience Platform](assets/adminconsole-experiencePlatform.png)
1. You may have several profiles in your Experience Platform instance already. Select the `AEP-Default-All-Users` profile
    ![Select Add New Profile](assets/adminconsole-newProfile.png)

1. Go to the **[!UICONTROL Users]** tab
1. Select the **[!UICONTROL Add User]** button
    ![Select Add User](assets/adminconsole-addUser.png)
1. Complete the workflow to add the tutorial participant as a user to the product profile

1. Go to the **[!UICONTROL Developers]** tab
1. Select the **[!UICONTROL Add Developer]** button
    ![Select Add User](assets/adminconsole-addDeveloper.png)
1. Complete the workflow to add the tutorial participant as a developer to the product profile


## Add a Role in Adobe Experience Platform (requires a system administrator or product admin)

Granular permissions to Experience Platform are managed in the Permissions screen of the Platform interface. Only System and Product Admins have access to this screen, so if you do not have Admin privileges, you will need assistance from someone who does.

Permissions are managed in Roles. Create a Role for the tutorial:

1. Log into [Adobe Experience Platform](https://platform.adobe.com)
1. Select **[!UICONTROL Permissions]** in the left navigation which will take you to the [!UICONTROL Roles] screen
1. Select **[!UICONTROL Create role]**

    ![Create a role in Experience Platform](assets/permissions-addRole.png)
1. Name the role `Luma Tutorial Platform` (add the tutorial participant's name to the end, if multiple people from your company are taking this tutorial) and select **[!UICONTROL Confirm]**

    ![Create a role in Experience Platform](assets/permissions-nameRole.png)


1. Add all of the permission items for the following resources using  **[!UICONTROL +]** and **[!UICONTROL Add all]**:

    1. Data Modeling
    1. Data Management
    1. Profile Management
    1. Identity Management
    1. Sandbox Administration
    1. Query Service
    1. Data Collection
    1. Data Governance
    1. Dashboards
    1. Alerts

        ![Add Permission items](assets/permissions-addPermissionItems.png)

1. Under Data Ingestion, add the Manage Sources and View Sources permission items.

1. After adding all of the permission items, be sure to select the Save button
    ![Save permission items](assets/permissions-savePermissions.png)

You will make a few small updates to this role after the [Create a sandbox](create-a-sandbox.md) and [Set up Developer Console and Postman](set-up-developer-console-and-postman.md) lessons.

## Create a Data Collection product profile (requires a system administrator or product admin)

In this exercise, you or a System Administrator at your company will create a product profile for Data Collection (formerly known as Adobe Experience Platform Launch) and add you as a product profile admin.

>[!NOTE]
>
>If you are a System Administrator assisting a colleague with this tutorial, consider adding them as a *Product Administrator* for Data Collection. As a Product Administrator, they will be able to complete these steps on their own and administrate other users of Data Collection in the future.

To create the product profile:

1. In the [!DNL Adobe Admin Console] go to the Adobe Experience Platform Data Collection product
1. Add a new profile named `Luma Tutorial Data Collection` (add the tutorial participant's name to the end, if multiple people from your company are taking this tutorial)
1. Turn off the **[!UICONTROL Properties]** > **[!UICONTROL Auto-include]** setting
1. Don't assign any properties or permissions at this point
1. Add the tutorial participant as an admin of this profile

After completing these steps, you should see that the `Luma Tutorial Data Collection` profile is set up with one admin.
![Data Collection profile created](assets/adminconsole-dc-profileCreated.png)

## Configure the Data Collection product profile

Now that you are an admin of the `Luma Tutorial Data Collection` product profile you can configure the permissions and roles you will need to complete the tutorial.

### Add permissions

Now you will add the individual permission items to the profile:

1. In the [Adobe Admin Console](https://adminconsole.adobe.com), go to **[!UICONTROL Products]** > **[!UICONTROL Data Collection]**
1. Open the `Luma Tutorial Data Collection` profile
1. Go to the **[!UICONTROL Permissions]** tab
1. Open **[!UICONTROL Platforms]**
1. Make sure that all of the available platforms are selected (you may see different options based on your license)
1. **[!UICONTROL Save]** any changes
    ![Add platforms](assets/adminconsole-launch-addPlatforms.png)
1. Open **[!UICONTROL Properties]**
1. Make sure the **[!UICONTROL Auto-Include]** toggle is Off so that you don't have access to any properties (we will add one later)
1. **[!UICONTROL Save]** any changes
    ![Remove properties](assets/adminconsole-launch-removeProperties.png)
1. Open **[!UICONTROL Property Rights]**
1. Select **[!UICONTROL Add all]** to add all of the property permissions
1. **[!UICONTROL Save]**
    ![Remove properties](assets/adminconsole-launch-addPropertyRights.png)
1. Open **[!UICONTROL Company Rights]** 
1. Add **[!UICONTROL Manage Properties]**
1. Select **[!UICONTROL Save]**
    ![Remove properties](assets/adminconsole-launch-companyRights.png)


### Add yourself as a user

Now add yourself as a user to the Data Collection profile:

1. Go to the **[!UICONTROL Users]** tab
1. Select the **[!UICONTROL Add User]** button
    ![Select Add User](assets/adminconsole-launch-addUser.png)
1. Complete the workflow to add yourself as a user to the product profile

You do not need to add yourself as a Developer for Data Collection.

Now you have almost all the permissions required to complete the tutorial! There will be just two more tweaks that you will make inside the [!DNL Adobe Admin Console], including one after you [create a sandbox](create-a-sandbox.md)!
