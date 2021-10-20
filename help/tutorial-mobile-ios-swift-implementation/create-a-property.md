---
title: Create a tag property for a mobile app
description: Learn how to log into the Data Collection interface and create a mobile tag property. This lesson is part of the Implement the Experience Cloud in Mobile iOS Swift Applications tutorial.
exl-id: 658f3c4c-c5e6-4aef-8511-833b7a813d77
---
# Create a tag property

Data Collection is the next generation of mobile SDK and website tag management capabilities. The tags feature gives customers a simple way to deploy and manage all of the analytics, marketing, and advertising solutions necessary to power relevant customer experiences. There is no additional charge for tags. It is available to any Adobe Experience Cloud customer.

In this lesson, you will create a tag property for mobile apps.


>[!NOTE]
>
>Adobe Experience Platform Launch is being integrated into Adobe Experience Platform as a suite of data collection technologies. Several terminology changes have rolled out in the interface which you should be aware of while using this content:
>
> * Platform Launch (Client Side) is now **[[!DNL tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)** 
> * Platform Launch Server Side is now **[[!DNL event forwarding]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html)** 
> * Edge configurations  are now **[[!DNL datastreams]](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)**

## Prerequisites

In order to complete the next few lessons, you must have permission to Develop, Approve, Publish, Manage Extensions, and Manage Environments in tags. If you are unable to complete any of these steps because the user interface options are not available to you, reach out to your Experience Cloud Administrator to request access. For more information on tag user permissions, see [the documentation](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html).

## Learning Objectives

At the end of this lesson, you will be able to:

* Log into the Data Collection user interface
* Create a new mobile tag property
* Configure a mobile tag property

## Go to Data Collection

**To get to Data Collection**

1. Log into the [Adobe Experience Cloud](https://experiencecloud.adobe.com)

1. Click the ![Solution Switcher Icon](images/mobile-launch-solutionSwitcher.png) icon to open the solution switcher

1. Select **[!UICONTROL Launch/Data Collection]** from the menu

    ![Open the solution switcher using the icon and click Activation](images/mobile-launch-solutionSwitcherActivation.png)



You should now see the `Tags Properties` screen (if no properties have ever been created in the account, this screen might be empty):

![Properties Screen](images/mobile-launch-propertiesScreen.png)

## Create a Property

A property is basically a container that you fill with extensions, rules, data elements, and libraries as you deploy tags to your app. A single mobile property can be used across multiple app platforms (e.g. iOS and Android™) provided the apps contain similar functionality and require the same solutions to be implemented. For more information on creating properties, see ["Set up a mobile property"](https://aep-sdks.gitbook.io/docs/getting-started/create-a-mobile-property) in the product documentation.

**To Create a Property**

1. Click the **[!UICONTROL New Property]** button:

    ![Click New Property](images/mobile-launch-addNewProperty.png)

1. Name your property (e.g. `Mobile Tutorial`)
1. As the platform, click **[!UICONTROL Mobile]**
1. Click the **[!UICONTROL Save]** button

   ![Create a new Property](images/mobile-launch-newProperty.png)

Your new property should display on Properties page. Note that if you check the box next to the property name, options to **[!UICONTROL Configure]** or **[!UICONTROL Delete]** the property appear above the property list. Click on the name of your property (e.g. `Mobile Tutorial`) to open the `Overview` screen.
![Click the name of the property to open it](images/mobile-launch-openProperty.png)

[Next "Add Extensions" >](add-extensions.md)
