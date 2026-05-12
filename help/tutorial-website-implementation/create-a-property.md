---
title: Create a tag property
description: Learn how to log into the Data Collection interface and create a tag property. This lesson is part of the Implement the Experience Cloud in websites tutorial.
exl-id: f83d374a-a831-4598-b9d3-6f183224b589
TQID: https://experienceleague.adobe.com/iQSxmRyXcWv5UhhRqaDdJM2KF1nEUbAWxFvQZr41bLQ
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: ca3d6bf4-a4af-4944-936b-8de1eb09f149
    internal-label: Datastreams
  - id: d9830f6f-ceb6-4faa-9744-f281fe4439f9
    internal-label: Tags
  - id: dc6ebdf7-9a94-43eb-9184-759cfdd0cf1c
    internal-label: Event forwarding
  - id: f6ff4d13-7b5c-4533-8556-95e76673d4cb
    internal-label: Properties
  - id: f9a2105e-7a47-4e85-9193-31a519a2cb83
    internal-label: Data elements
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# Create a tag property

In this lesson, you will create your first tag property.

A property is basically a container that you fill with extensions, rules, data elements, and libraries as you deploy tags to your site.


>[!WARNING]
>
> This tutorial and its Luma website exercises are no longer maintained and rely on older JavaScript libraries. To learn the current best practice, please use the [Implement Adobe Experience Cloud with Web SDK tutorial](https://experienceleague.adobe.com/en/docs/platform-learn/implement-web-sdk/overview).

## Prerequisites

In order to complete the next few lessons, you must have permission to Develop, Approve, Publish, Manage Extensions, and Manage Environments in tags. If you are unable to complete any of these steps because the user interface options are not available to you, reach out to your Experience Cloud Administrator to request access. For more information on tag user permissions, see [the documentation](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html).


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
