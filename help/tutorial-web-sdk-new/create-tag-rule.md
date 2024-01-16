---
title: Create a tag rule
description: Learn how to send an event to the Platform Edge Network with your XDM object using a tag rule. This lesson is part of the Implement Adobe Experience Cloud with Web SDK tutorial.
feature: Tags
---
# Create a tag rule

Learn how to send an event to the Platform Edge Network with your XDM object using a tag rule. A tag rule is a combination of events, conditions, and actions that tells the tag property to do something.

>[!NOTE]
>
> For demonstration purposes, the exercises in this lesson build upon the example used during the [Create identities](create-identities.md) step; sending an XDM event action to capture content and identities from users on the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html).

 
## Learning objectives

At the end of this lesson, you are able to:

* Use a naming convention for managing rules within tags
* Send an XDM event by using Update Variable and Send Event action types in a tag rule
* Publish a tag rule to a development library


## Prerequisites

You are familiar with Data Collection tags and the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html), and you must have completed the following previous lessons in the tutorial:

* [Configure an XDM schema](configure-schemas.md)
* [Configure an identity namespace](configure-identities.md)
* [Configure a datastream](configure-datastream.md)
* [Web SDK extension installed in the tag property](install-web-sdk.md)
* [Create data elements](create-data-elements.md)
* [Create identities](create-identities.md)

## Naming Conventions

To better manage rules in tags, it is recommended to follow a standard naming convention. This tutorial uses a three-part naming convention:

* [**location**] - [**event**] - [**tool**] (**sequence**)

where;

1. **location** is the page or pages on the site where the rule fires
1. **event** is the trigger for the rule
1. **tool** is the specific application or applications used in the action step for that rule
1. **sequence** is the order in which the rule should fire in relation to other rules
<!-- minor update --> 

## Create tag rule

In tags, rules are used to execute actions (fire calls) under various conditions. The Platform Web SDK tags extension includes two actions which will be used in this lesson:

* **[!UICONTROL Update variable]** maps data elements to XDM fields
* **[!UICONTROL Send Event]** sends the XDM object to Experience Platform Edge Network

### Update variable

Create this first rule as a "global configuration" to set all the essential content variables in the XDM object using Platform Web SDK's **[!UICONTROL Update Variable]** action. Then create a second rule, sequenced to trigger after the first one, to send the XDM object to Platform Edge Network using the **[!UICONTROL Send Event]** action. Later in this tutorial, you send different XDM fields based on the type of page the visitor is on (for example product SKUs on product pages). You accomplish this by sequencing the rules containing **[!UICONTROL Update Variable]** actions before the rule that uses the **[!UICONTROL Send Event]** action.

To create a tag rule:

1. Open the tag property that you are using for this tutorial

1. Go to **[!UICONTROL Rules]** in the left navigation

1. Select the **[!UICONTROL Create New Rule]** button

    ![Create a rule](assets/rules-create.png)
    
1. Name the rule `all pages global content variables - page bottom - AA (order 1)`

1. In the **[!UICONTROL Events]** section, select **[!UICONTROL Add]**

    ![Name the rule and add an event](assets/rule-name-new.png)   

1. Use the **[!UICONTROL Core Extension]** and select `Page Bottom` as the **[!UICONTROL Event Type]** 

1. Under the **[!UICONTROL Name]** field, name it `Core - Page Bottom - order 1`. This helps you describe the trigger with a meaningful name.

1. Select **[!UICONTROL Advanced]** dropdown and enter `1` in **[!UICONTROL Order]**

    >[!NOTE]
    >
    > The higher the number you enter, the later in the overall order of operations it triggers.

1. Select **[!UICONTROL Keep Changes]** to return to the main rule screen
    ![Select Page Bottom Trigger](assets/create-tag-rule-trigger-bottom.png)

1. In the **[!UICONTROL Actions]** section, select **[!UICONTROL Add]**

1. As the **[!UICONTROL Extension]**, select **[!UICONTROL Adobe Experience Platform Web SDK]** 

1. As the **[!UICONTROL Action Type]**, select **[!UICONTROL Update variable]** 

1. As the **[!UICONTROL Data element]**, select the `xdm.variable.content` you created in the [Create data elements](create-data-elements.md) lesson

    ![Update Variable Schema](assets/create-rule-update-variable.png)

Now map your [!UICONTROL data elements] to the [!UICONTROL schema] used by your XDM object.  

>[!NOTE] 
> 
> You can map to individual properties or entire objects. In this example, you map to individual properties.


1. Scroll down until you reach the **`web`** object

1. Select to open it

1. Map the following data elements to the corresponding `web` XDM variables

    * **`web.webPageDetials.name`** to `%page.pageInfo.pageName%`
    * **`web.webPageDetials.server`** to `%page.pageInfo.server%`
    * **`web.webPageDetials.siteSection`** to `%page.pageInfo.hierarchie1%`

    ![Update variable content](assets/create-rule-xdm-variable-content.png)

1. Next, find the `identityMap` object in the schema and select it
 
1. Map to the `identityMap.loginID` data element

   ![Update variable identity map](assets/create-rule-variable-identityMap.png)

1. Next, find the eventType field and select it 

1. Enter the value `web.webpagedetails.pageViews`

    >[!WARNING]
    >
    > This dropdown populates the **`xdm.eventType`** variable in the XDM object. While you are also able to type free-form labels in this field, it is highly recommended you **do not** as it has averse effects with Platform.

    >[!TIP]
    >
    > To understand what values to populate in the `eventType` field, you must go to the schema page and select the `eventType` field to view the suggested values on the right rail. 

    ![Update variable identity map](assets/create-tag-rule-eventType.png)
    

1. Select **[!UICONTROL Keep Changes]** and then **[!UICONTROL Save]** the rule in the next screen to finish creating the rule

### Send event

Now that you have set the variables, you can create the second rule to send the XDM object to Platform Edge Network with the **[!UICONTROL Send event]** action type.

1. On the right, select to **[!UICONTROL Add Rule]** to create another rule

1. Name the rule `all pages send event - page bottom - AA (order 50)`

1. In the **[!UICONTROL Events]** section, select **[!UICONTROL Add]**

1. Use the **[!UICONTROL Core Extension]** and select `Page Bottom` as the **[!UICONTROL Event Type]** 

1. Under the **[!UICONTROL Name]** field, name it `Core - Page Bottom - order 50`. This helps you describe the trigger with a meaningful name.

1. Select **[!UICONTROL Advanced]** dropdown and enter `50` in **[!UICONTROL Order]**. This will ensure the second rule triggers after the first rule you set to trigger as `1`.

1. Select **[!UICONTROL Keep Changes]** to return to the main rule screen
    ![Select Page Bottom Trigger](assets/create-tag-rule-trigger-bottom-send.png)

1. In the **[!UICONTROL Actions]** section, select **[!UICONTROL Add]**

1. As the **[!UICONTROL Extension]**, select  **[!UICONTROL Adobe Experience Platform Web SDK]** 

1. As the  **[!UICONTROL Action Type]**, select  **[!UICONTROL Send event]** 

1. As the **[!UICONTROL XDM]**, select the `xdm.variable.content` data element created in the previous lesson

1. Select **[!UICONTROL Keep Changes]** to return to the main rule screen

    ![Add the Send Event action](assets/create-rule-send-event-action.png)
1. Select **[!UICONTROL Save]** to save the rule    

    ![Save the rule](assets/create-rule-save-rule.png)   

## Publish the rule in a library

Next, publish the rule to your development environment so you can verify it works.

To create a library:

1. Go to **[!UICONTROL Publishing Flow]** in the left navigation

1. Select **[!UICONTROL Add Library]**

    ![Select Add Library](assets/rule-publish-library.png)
1. For the **[!UICONTROL Name]**, enter `Luma Web SDK Tutorial`
1. For the **[!UICONTROL Environment]**, select `Development`
1. Select  **[!UICONTROL Add All Changed Resources]** 

    >[!NOTE]
    >
    >    In addition to the Adobe Experience Platform Web SDK extension and the `all pages global content variables - page bottom - AA (order 50)` rule, you see the tag components created in previous lessons. The Core extension contains the base JavaScript required by all web tag properties.

1. Select **[!UICONTROL Save & Build for Development]**

    ![Create and build the library](assets/create-tag-rule-library-changes.png)

The library may take a few minutes to build and when it is complete it displays a green dot to the left of the library name:

![Build complete](assets/create-rule-development-success.png)   

As you can see on the [!UICONTROL Publishing Flow] screen, there is a lot more to the publishing process which is beyond the scope of this tutorial. This tutorial just uses a single library in your Development environment.

Now you are ready to validate the data in the request using the Adobe Experience Platform Debugger.

[Next **Validate with Debugger**](validate-with-debugger.md)

>[!NOTE]
>
>Thank you for investing your time in learning about Adobe Experience Platform Web SDK. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
