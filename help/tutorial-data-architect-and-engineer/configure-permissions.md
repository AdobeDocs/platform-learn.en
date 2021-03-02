---
title: Configure permissions
seo-title: Configure permissions | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Configure permissions
description: In this lesson, you will configure Adobe Experience Platform user permissions using Adobe's Admin Console. 
role: Data Architect, Data Engineer
feature: Access Control
kt: 4348
thumbnail: 4348-configure-permissions.jpg
---

# Configure permissions

<!--30min-->

In this lesson, you will configure Adobe Experience Platform user permissions using [!DNL Adobe's Admin Console]. 

Access control is a key privacy capability in Experience Platform and we recommend limiting permissions to the minimum required for people to perform their job functions. 

Data Architects and Data Engineers are  power users of Adobe Experience Platform and you will need almost all permissions in order to complete this tutorial, and later in your day-to-day work. Data Architects are likely be involved in the administration of *other Platform users* at their company such as marketers, analysts, and data scientists. As you complete this lesson, think about how you might use these features to manage other users at your company.

**Data Architects** typically need to configure permissions for other users outside of this tutorial.

>[!IMPORTANT]
>
>A System Administrator of Adobe Experience Cloud products will need to complete some of the steps in this lesson, which we have called out in the section headings.  If you are not System Administrator, please reach out to one at your company and have them complete these tasks.

## About the Admin Console

The [!DNL Admin Console] is the interface used to administer user access to all Adobe Experience Cloud products. Some key [!DNL Admin Console] concepts to be aware of:

* A **product profile** is a combination of permissions, roles, and sandbox environments tied to a specific Adobe product. Multiple product profiles can be created for a single Adobe product. For example, a "Marketer" profile could limit permissions to what a typical marketer would need to complete key tasks in the production instance, while a "Data Architect" profile could be used to grant different permissions in multiple environments. In this lesson, we will create a "Luma Tutorial" product profile with all the permissions a Data Architect and Data Engineer would need to complete this tutorial in a sandbox environment. 
* An **integration** is a connection to a _project_ in the Adobe Developer Console. The Adobe Developer Console is the heart of authentication and configuration of Adobe APIs. You will configure an integration in the Developer Console and [!DNL Postman] lesson.

Also, here is a quick summary of the roles that exist for Platform, as well as any Adobe Experience Cloud application:

* **Users** must be a member of a product profile can complete tasks in Platform's user interface according to the permissions in their product profile(s). Users can also be assigned to User Groups, to streamline management.
* **Developers** must also be a member of product profile can complete the tasks using Platform's API according to the permissions in the product profile.
* **Product Profile Admins** can edit *that specific profile's* permissions and services as well as add users, additional profile admins, and developers. Potentially a product profile admin can give themselves access to all capabilities of the product, with the exception of administering other product profiles.
* **Product Admins** can administer *all product profiles* for that Adobe product and add new product profiles.
* **System Administrators** can add product admins and administer essentially any permissions for all Adobe Experience Cloud products.

## Create an Experience Platform product profile (requires a system administrator or product admin)

In this exercise you or a System Administrator at your company will create a product profile for Adobe Experience Platform and add you as an admin for that product profile.

>[!NOTE]
>
>If you are a System Administrator facilitating the enablement of a colleague, consider adding them as a *Product Administrator* for Adobe Experience Platform, in which case they would be able to complete these steps on their own and administrate other users of Experience Platform in the future.

To create the product profile:

1. Log into the [Adobe Admin Console](https://adminconsole.adobe.com)
1. Click **[!UICONTROL Products]** on the top navigation
1. Click **[!UICONTROL Adobe Experience Platform]** on the left navigation
1. You probably already have several profiles in your Experience Platform instance. Click the **[!UICONTROL New Profile]** button to add another
    ![Click Add New Profile](assets/adminconsole-newProfile.png)
1. Name the profile `Luma Tutorial Platform` (add the tutorial taker's name to the end, if multiple people from your company are taking this tutorial) and click the **[!UICONTROL Next]** button
    ![Name the profile Luma Tutorial Platform](assets/adminconsole-nameProfile.png)
1. Depending on the details of your product license, you may or may not see this second **[!UICONTROL Services]** screen. We will not be using any of these services in this tutorial, so click the **[!UICONTROL All on]** checkbox to *remove* all services and click **[!UICONTROL Done]**.
    ![Disable services](assets/adminconsole-createProfile-services.png)
1. At this point the profile is created. Permission items will be added in a later exercise, so on the **[!UICONTROL Configure profile]** screen, just hit the **[!UICONTROL Cancel]** button.
    ![Add permissions](assets/adminconsole-configureProfileCancel.png)


Now you need to add the tutorial participant as an admin of the newly created product profile. If you yourself are the tutorial participant, you can skip ahead to the "Configure Experience Platform product profile" exercise:

1. Click on the `Luma Tutorial Platform` product profile:
   
    ![Open the profile](assets/adminconsole-newProfileInList.png)

1. Click on the **[!UICONTROL Admin]** tab and then click the **[!UICONTROL Add Admin]** button:

    ![Go to the Admins tab and click Add Admin](assets/adminconsole-addAdmin.png)

1. Complete the workflow to add the tutorial participant as an admin.

After completing these steps you should see that the `Luma Tutorial Platform` profile is set up with 1 admin.
![Platform profile created](assets/adminconsole-platform-profileCreated.png)

## Configure Experience Platform product profile

Now that you are an admin of the `Luma Tutorial Platform` product profile you can configure the permissions and roles you will need to complete the tutorial.
   
### Add permissions

Now you will add the individual permission items to the profile:

1. Open the `Luma Tutorial Platform` product profile
1. Click the **[!UICONTROL Permissions]** tab
1. Under **[!UICONTROL Sandboxes]**, add the **[!UICONTROL Prod]** sandbox to the profile. It is necessary to have access to the [!DNL Prod] sandbox in order to create additional sandboxes. Once we have added the tutorial sandbox in the next lesson, we will remove the [!DNL Prod] sandbox from the product profile.
1. Add all of the permission items for the categories highlighted in the screenshot below, by opening a category and moving the items to the right column. The [!UICONTROL Destinations], [!UICONTROL Decisioning] and [!UICONTROL Data Science Workspace] features are not covered in  this tutorial
1. After adding all of the permission items, be sure to click the **[!UICONTROL Save]** button

After saving, your screen should look like this:
![Click settings](assets/adminconsole-platform-enablePermissions.png)

### Add yourself as a user

At this point, if `Luma Tutorial Platform` was your _only_ Experience Platform product profile, you still would not be able to log into Experience Platform's user interface. To do that you need to be a _user_ in the product profile. Fortunately, since you are an _admin_ of a product profile, you can add yourself as a _user_!  

1. Go to the **[!UICONTROL Users]** tab
1. Click the **[!UICONTROL Add User]** button
    ![Click Add User](assets/adminconsole-addUser.png)
1. Complete the workflow to add yourself as a user to the product profile

### Add yourself as a developer

In order to use the Platform API, you will need add yourself as a developer:

1. Go to the **[!UICONTROL Developers]** tab
1. Click the **[!UICONTROL Add Developer]** button
    ![Click Add User](assets/adminconsole-addDeveloper.png)
1. Complete the workflow to add yourself as a developer to the product profile

## Create a Launch product profile (requires a system administrator or product admin)

In this exercise you or a System Administrator at your company will create a product profile for Adobe Experience Platform Launch and add you as a product profile admin.

>[!NOTE]
>
>If you are a System Administrator facilitating the enablement of a colleague with this tutorial, consider adding them as a *Product Administrator* for Launch, in which case they would be able to complete these steps on their own and administrate other users of Launch in the future.

To create the product profile:

1. In the [!DNL Adobe Admin Console] go to the Adobe Experience Platform Launch product
1. Add a new profile and name it `Luma Tutorial Launch` (add the tutorial taker's name to the end, if multiple people from your company are taking this tutorial)
1. Turn off the **[!UICONTROL Properties]** > **[!UICONTROL Auto-include]** setting
1. Don't assign any properties or permissions at this point
1. Add the tutorial participant as an admin of this profile

After completing these steps you should see that the `Luma Tutorial Launch` profile is set up with 1 admin.
![Launch profile created](assets/adminconsole-launch-profileCreated.png)

## Configure the Launch product profile

Now that you are an admin of the `Luma Tutorial Launch` product profile you can configure the permissions and roles you will need to complete the tutorial.

### Add permissions

Now you will add the individual permission items to the profile. From the product profile screen:

1. In the [Adobe Admin Console](https://adminconsole.adobe.com), go to **[!UICONTROL Products]** > **[!UICONTROL Adobe Experience Platform Launch]** (you might need to SHIFT-Reload to see [!UICONTROL Adobe Experience Platform Launch] show up after your permissions were just updated)
1. Open the `Luma Tutorial Launch` profile
    ![Open Products > Adobe Experience Platform Launch > Luma Tutorial Launch](assets/adminconsole-launch-openProfile.png)
1. Click on the Permissions tab
1. Click to open **[!UICONTROL Platforms]**
1. Click **[!UICONTROL Add all]** so you can create both [!UICONTROL Web] and [!UICONTROL Mobile] properties.
    ![Add platforms](assets/adminconsole-launch-addPlatforms.png)
1. Click **[!UICONTROL Save]**
1. Click to open **[!UICONTROL Properties]**
1. Make sure the **[!UICONTROL Auto-Include]** toggle so that it is in the Off state so that you don't have access to any properties (we will add one later).
1. Click **[!UICONTROL Save]**
    ![Remove properties](assets/adminconsole-launch-removeProperties.png)
1. Click to open the **[!UICONTROL Property Rights]** row
1. Click **[!UICONTROL Add all]** to add all of the property rights
1. Click **[!UICONTROL Save]**
    ![Remove properties](assets/adminconsole-launch-addPropertyRights.png)
1. Click to open the **[!UICONTROL Company Rights]** row
1. Add **[!UICONTROL Manage Properties]**
1. Click **[!UICONTROL Save]**
    ![Remove properties](assets/adminconsole-launch-companyRights.png)


### Add yourself as a user

Now add yourself as a user to the Launch profile:

1. Go to the **[!UICONTROL Users]** tab
1. Click the **[!UICONTROL Add User]** button
    ![Click Add User](assets/adminconsole-launch-addUser.png)
1. Complete the workflow to add yourself as a user to the product profile

You will not need to add yourself as a Developer for Launch.

## Additional Resources

* [Adobe Admin Console documentation](https://helpx.adobe.com/enterprise/using/admin-console.html)
* [Access Control documentation](https://experienceleague.adobe.com/docs/experience-platform/access-control/home.html)
* [Access Control API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/access-control.yaml)

Now you have almost all the permissions required to complete the tutorial! There will be just two more tweaks that you will make inside the [!DNL Adobe Admin Console], including one after you [create a sandbox](create-a-sandbox.md)!