---
title: Create a tag property
description: Learn how to log into the Data Collection interface and create a tag property. This lesson is part of the Implement the Experience Cloud in websites tutorial.
exl-id: f83d374a-a831-4598-b9d3-6f183224b589
---
# Create a tag property

In this lesson, you will create your first tag property.

A property is basically a container that you fill with extensions, rules, data elements, and libraries as you deploy tags to your site.

## Prerequisites

In order to complete the next few lessons, you must have permission to Develop, Approve, Publish, Manage Extensions, and Manage Environments in tags. If you are unable to complete any of these steps because the user interface options are not available to you, reach out to your Experience Cloud Administrator to request access. For more information on tag user permissions, see [the documentation](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html).

>[!NOTE]
>
>Adobe Experience Platform Launch is being integrated into Adobe Experience Platform as a suite of data collection technologies. Several terminology changes have rolled out in the interface which you should be aware of while using this content:
>
> * Platform Launch (Client Side) is now **[[!DNL tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)** 
> * Platform Launch Server Side is now **[[!DNL event forwarding]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html)** 
> * Edge configurations  are now **[[!DNL datastreams]](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)**

## Learning Objectives

At the end of this lesson, you will be able to:

* Log into the Data Collection user interface
* Create a new tag property
* Configure a tag property

## Go to the Data Collection interface

**To get to Data Collection**

1. Log into the [Adobe Experience Cloud](https://experiencecloud.adobe.com)

1. Click the ![Solution Switcher Icon](images/launch-solutionSwitcher.png) icon to open the app switcher

1. Select **[!UICONTROL Launch/Data Collection]** from the menu ![Open the solution switcher using the icon and click Launch/Data Collection](images/launch-solutionSwitcherActivation.png)

You should now see the `Tags Properties` screen (if no properties have ever been created in the account, this screen might be empty):

![Properties Screen](images/launch-propertiesScreen.png)

## Create a Property

A property is basically a container that you fill with extensions, rules, data elements, and libraries as you deploy tags to your site. A property can be any grouping of one or more domains and subdomains. You can manage and track these assets similarly. For example, suppose that you have multiple websites based on one template, and you want to track the same assets on all of them. You can apply one property to multiple domains. For more information on creating properties, see ["Companies and Properties"](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/companies-and-properties.html) in the product documentation.

**To Create a Property**

1. Click the **[!UICONTROL New Property]** button:

    ![Click New Property](images/launch-addNewProperty.png)

1. Name your property (e.g. `Luma Tutorial` or `Luma Tutorial - Daniel`)
1. As the domain, enter `enablementadobe.com` since this is the domain where the Luma demo site is hosted. Although the "Domain" field is required, the tag property will work on any domain where it's implemented. The main purpose of this field is to pre-populate menu options in the Rule builder.
1. Expand the **[!UICONTROL Advanced Options]** section and check the box to **[!UICONTROL Run rule components in sequence]**
1. Click the **[!UICONTROL Save]** button

   ![Create a new Property](images/launch-newProperty.png)

Your new property should display on the Properties page. Note that if you check the box next to the property name, options to **[!UICONTROL Configure]** or **[!UICONTROL Delete]** the property appear above the property list. Click on the name of your property (e.g. `Luma Tutorial`) to open the `Overview` screen.
![Click the name of the property to open it](images/launch-openProperty.png)

[Next "Add the Embed Code" >](add-embed-code.md)
