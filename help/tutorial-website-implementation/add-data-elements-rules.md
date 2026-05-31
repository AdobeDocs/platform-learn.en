---
title: Add a data element, a rule and a library
description: Learn how to create Data Elements, Rules, and a Library in tags. This lesson is part of the Implement the Experience Cloud in websites tutorial.
exl-id: 4d9eeb52-144a-4876-95d3-83d8eec4832f
TQID: https://experienceleague.adobe.com/-biwG69zfW5Mt9Z5y1Kcq-l-7v9Fpn0KhPxM-siuXNQ
product_v2:
  - id: a829a185-511f-4bf8-8dcf-9e684f8011cf
    internal-label: Advertising
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
    internal-label: Acrobat Sign
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
    internal-label: Target
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
    internal-label: Implementation
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
  - id: e9dbdbc5-3e52-40f0-a7bc-e18542967b7a
    internal-label: Implementations
  - id: fd307ce7-56f5-4ee3-af68-a7833ff6e85e
    internal-label: API
subfeature_v2:
  - id: abc02dd6-664f-446a-9aaa-675bc0f2fe4a
    internal-label: Sources
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: ca3d6bf4-a4af-4944-936b-8de1eb09f149
    internal-label: Datastreams
  - id: d9830f6f-ceb6-4faa-9744-f281fe4439f9
    internal-label: Tags
  - id: dc6ebdf7-9a94-43eb-9184-759cfdd0cf1c
    internal-label: Event forwarding
  - id: df312454-73c4-43f6-a90e-18f5043f074c
    internal-label: Tags
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
# Add a data element, a rule and a library

In this lesson, you will create your first Data Element, Rule, and Library.

Data Elements and Rules are the basic building blocks of tags. Data Elements store the attributes you want to send to your marketing and advertising solutions, while Rules fire the requests to those solutions under the right conditions.  Libraries are the JavaScript files that load on the page to do all of the work. In this lesson, you will use all three to make our sample page do something.


>[!WARNING]
>
> This tutorial and its Luma website exercises are no longer maintained and rely on older JavaScript libraries. To learn the current best practice, please use the [Implement Adobe Experience Cloud with Web SDK tutorial](https://experienceleague.adobe.com/en/docs/platform-learn/implement-web-sdk/overview).


## Learning Objectives

At the end of this lesson, you will be able to:

* Create a data element
* Create a rule
* Create a library
* Add changes to a library
* Validate that your library is loading in your web browser
* Use the "Working Library" feature to work more efficiently

## Create a Data Element for Page Name

Data elements are tags' version of a data layer. They can store values from your own data layer object, cookies, local storage objects, query string parameters, page elements, meta tags, etc. In this exercise, you will create a data element for Page Name, which you will use later in your Target and Analytics implementations.

**To create a data element**

1. In the left navigation, click **[!UICONTROL Data Elements]**

1. Since you haven't created any data elements yet in this property, a brief video appears with additional information on this topic. Watch this video, if you like.

1. Click the **[!UICONTROL Create New Data Element]** button:

   ![Click the Create New Data Element button](images/launch-newDataElement.png)

1. Name the data element, e.g. `Page Name`

1. Use the [!UICONTROL JavaScript Variable] Data Element type to point to a value in your sample page's data layer: `digitalData.page.pageInfo.pageName`

1. Check the boxes for **[!UICONTROL Force lowercase value]** and **[!UICONTROL Clean text]** to standardize the case and remove extraneous spaces

1. Leave **[!UICONTROL None]** as the **[!UICONTROL Storage Duration]** setting since this value will typically be different on every page

1. Click the **[!UICONTROL Save]** button to save the data element

   ![Create the Page Name data element](images/launch-dataElement.png).

>[!NOTE]
>
>Data element capabilities _can be extended with Extensions_. For example, the ContextHub extension allows you to add data elements using features of the extension.

## Create a Rule

Next you will use this data element in a simple rule. Rules are one of the most powerful features in tags and allow you to specify what should happen as the visitor interacts with your website. When the criteria outlined in your rules are met, the rule triggers the action you have specified.

You are going to create a rule that outputs the Page Name data element value to the browser console.

**To create a rule**

1. In the left navigation, click **[!UICONTROL Rules]**

1. Since you haven't created any rules yet in this property, a brief video appears with additional information on the topic. Watch this video, if you like.

1. Click the **[!UICONTROL Create New Rule]** button:

   ![Click the Create New Rule button](images/launch-newRule.png)

1. Name the Rule `All Pages - Library Loaded`. This naming convention indicates where and when the rule will fire, making it easier to identify and re-use as your tag property matures.

1. Under Events, click **[!UICONTROL Add]**. The Event tells tags when the rule should fire and can be many things, including a page load, a click, a custom JavaScript event, etc.

   ![Name the Rule and Add an event](images/launch-addEventToRule.png)
  
   1. As the Event Type, select **[!UICONTROL Library Loaded (Page Top)]**. Note that when you select the Event Type, tags pre-populates a name for the event using your selection. Also note that the default order for the event is 50. Ordering is a powerful feature in tags which gives you precise control over the sequence of actions when you have multiple rules that are triggered by the same event. You will use this feature later in the tutorial.

   1. Click the **[!UICONTROL Keep Changes]** button
  
   ![Select an Event](images/launch-ruleSelectEvent.png)

1. Since this rule should fire on all pages, leave **[!UICONTROL Conditions]** blank. If you open the Conditions modal, you will see that conditions can add both restrictions and exclusions based on a large variety of options, including URLs, data element values, date ranges, and more.

1. Under Actions, click **[!UICONTROL Add]**

1. Select **[!UICONTROL Action Type > Custom Code]**, which at this point is the only option. Later in the tutorial, as you add extensions, more options will become available.

1. Select **[!UICONTROL </> Open Editor]** to open the code editor

   ![Select an Action](images/launch-selectAction.png)

1. Add the following to the code editor. This code will output the value of the Page Name data element to the browser console so you can confirm it's working:

    ```javascript
    console.log('The page name is '+_satellite.getVar('Page Name'));
    ```

1. Save the code editor

   ![Enter custom code](images/launch-customCodeAction.png)

1. On the Action configuration screen click **[!UICONTROL Keep Changes]**

1. Click **[!UICONTROL Save]** to save the rule

On the Rules page, you should see your new rule:
![Rule appears on page](images/launch-savedRule.png)

## Save Your Changes to a Library

After configuring a collection of extensions, data elements, and rules in the Data Collection interface, you need to package these capabilities and logic into a set of JavaScript code that you can deploy on your website so that marketing tags will fire when visitors come to the site. A library is the set of JavaScript code that will do this.

In an earlier lesson, you implemented the embed code of your development environment on the sample page. When you loaded the sample page a 404 error was returned for the embed code URL because a tag library had not been built yet and assigned to the environment. Now you will put your new data element and rule in a library so that your sample page can do something.

**To add and build a library**

1. In the left navigation, click **[!UICONTROL Publishing Flow]**

1. Click **[!UICONTROL Add New Library]**

   ![Add New Library](images/launch-addNewLibrary.png)

1. Name the Library, e.g. `Initial Setup`

1. Select **[!UICONTROL Environment > Development]**

1. Click **[!UICONTROL Add All Changed Resources]**

   ![Add All Changed Resources](images/launch-addAllChangedResources.png)

1. Note that after clicking **[!UICONTROL Add All Changed Resources]** tags summarizes the changes you just made.

1. Click **[!UICONTROL Save & Build for Development]**

   ![Save and Build for Development](images/launch-saveAndBuild.png)

After a few moments, the status dot will turn green indicating the library successfully built.

![Library Built](images/launch-libraryBuilt.png)

## Validate Your Work

Now validate that your rule is working as expected.

Reload your sample page. If you look at the Developer Tools -> Network tab, you should now see a 200 response for your tag library!

![Library loads with 200 response](images/samplepage-200.png)

If you look at the Developer Tools -> Console, you should see the text "The page name is home"

![Console Message](images/samplepage-console.png)

Congratulations, you created your first data element and rule and built your first tag library!

## Use the Working Library Feature

When you are making a lot of changes in tags, it is inconvenient to have to come to the Publishing tab, add changes, and build the library each time you want to see the result.  Now that you have created your "Initial Setup" library, you can use a feature called "Working Library" to rapidly save your changes and rebuild the library in a single step.

Make a small change to your "All Pages - Library Loaded" rule. In the left navigation, click **[!UICONTROL Rules]** and then click on the `All Pages - Library Loaded` rule to open it up.

![Reopen the rule](images/launch-reopenRule.png)

On the `Edit Rule` page, click the ***[!UICONTROL Working Library]*** dropdown and select your `Initial Setup` library.

![Select Initial Setup as the Working Library](images/launch-setWorkingLibrary.png)

Once you've selected the library, you should see that the **[!UICONTROL Save]** button now defaults to **[!UICONTROL Save to Library]**. When you make a change in tags, you can use this option to automatically add the change directly to your working library and/or rebuild it.

Test it out. Open your Custom Code action and just add a colon after the text "The page name is" so the entire code block reads:

```javascript
console.log('The page name is: '+_satellite.getVar('Page Name'));
```

Save the code, keep the changes in the action, and now click the **[!UICONTROL Save to Library and Build]** button.

![The Save and Build option now exists](images/launch-workingLibrary-saveAndBuild.png)

Wait a moment until the green dot reappears next to the [!UICONTROL Working Library] dropdown. Now, reload your sample page and you should see your change reflected in the console message (you may have to clear your browser cache and reload, in order to see the change to the page):

![Console Message with Colon](images/samplepage-consoleWithColon.png)

This is a much faster way of working and you will use this approach for the rest of the tutorial.

[Next "Switch Environments with the Experience Cloud Debugger" >](switch-environments.md)
