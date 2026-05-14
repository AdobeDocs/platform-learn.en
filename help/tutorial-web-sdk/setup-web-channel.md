---
title: Set up Journey Optimizer web channel with Platform Web SDK
description: Learn how to implement Journey Optimizer web channel using Platform Web SDK. This lesson is part of the Implement Adobe Experience Cloud with Web SDK tutorial.
solution: Data Collection,Experience Platform,Journey Optimizer
feature-set: Journey Optimizer
feature: Web Channel,Web SDK
jira: KT-15411
exl-id: ab83ce56-7f54-4341-8750-b458d0db0239
TQID: https://experienceleague.adobe.com/UED9NNShLICBB-E4AB7G0Ez2yUL0EGR1LegDVqbkM0I
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
    internal-label: Journey Optimizer
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: a653cc2e-bc85-4353-a306-399e5b247978
    internal-label: Journey Optimizer campaigns
  - id: b49ca41f-eb7a-4f4b-abeb-a97c06fd0c04
    internal-label: Track and monitor
  - id: baecb07f-ce89-4ebb-9cd9-0f7c053f944f
    internal-label: Journey management
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: c20d46e7-1c7d-476c-a50e-3961d4dce35f
    internal-label: Reporting
  - id: d556b755-390a-43f0-be32-a08cf6236126
    internal-label: Configuration
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
  - id: fe338112-e2ce-4876-8989-fc4d497613f1
    internal-label: Email
subfeature_v2:
  - id: a9f73820-6899-47c2-a597-3fec28ab756a
    internal-label: Journey Optimizer reporting
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: b32bb433-f8c6-4931-8e52-e657230a3bf2
    internal-label: Audiences
  - id: b3a93754-a8b8-46eb-9421-7eccaeeb3dff
    internal-label: Best practices
  - id: b572b7ff-a413-4173-b2b4-d7d3874f1b9b
    internal-label: Best practices
  - id: c1f1ac67-ccab-4be9-a93a-b7faba1192c4
    internal-label: Assurance
  - id: ca3d6bf4-a4af-4944-936b-8de1eb09f149
    internal-label: Datastreams
  - id: d9830f6f-ceb6-4faa-9744-f281fe4439f9
    internal-label: Tags
  - id: da923278-9c80-47b0-bebd-b68c341e76fb
    internal-label: ""
  - id: e5329d1b-e590-4e24-a3fb-ef3fe0f2c721
    internal-label: Subdomains
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
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: bcc5edb5-84c3-4940-9f84-ed88b6c16274
    internal-label: Experimentation
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: e9001ce2-5245-4a8e-8601-dd958009072f
    internal-label: Web experience
  - id: f8667931-f646-4dd3-af2a-b9d0cb8098ad
    internal-label: Taxonomy
---
# Set up Journey Optimizer web channel with Web SDK

Learn how to implement the Adobe Journey Optimizer [web channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/web/get-started-web) using Adobe Experience Platform Web SDK. This lesson covers the foundational web channel prerequisites, detailed steps for configuration, and a deep dive into a use case centered on loyalty status.

By following this lesson, Journey Optimizer users are equipped to use the web channel for advanced online personalization using the Journey Optimizer web designer.



![Web SDK and Adobe Analytics diagram](assets/dc-websdk-ajo.png)  

## Learning Objectives

At the end of this lesson, you are able to:

* Understand the function and significance of Web SDK in delivering the web channel experience.
* Understand the process of creating a web channel campaign from start to finish utilizing the sample Luma Loyalty Rewards use case.
* Configure campaign properties, actions, and schedules within the interface.
* Understand the functionality and benefits of the Adobe Experience Cloud Visual Editing Helper extension.
* Learn to edit web page content, including images, headers, and other elements, using the web designer.
* Learn how to insert offers into a web page using the Offer decision component.
* Familiarize yourself with best practices for ensuring the quality and success of a web channel campaign.

## Prerequisites

To complete the lessons in this section, you must first:

* Complete all lessons for initial configuration of the Platform Web SDK, including setting up data elements and rules.
* Ensure that your Adobe Experience Platform Web SDK tags extension version is 2.16 or above.
* Complete the Set up Experience Platform lesson, including the exercise to create the `Luma Loyalty Rewards – Gold Status` audience.
* Downloaded and enable the [Adobe Experience Cloud Visual Editing Helper browser extension](https://chromewebstore.google.com/detail/adobe-experience-cloud-vi/kgmjjkfjacffaebgpkpcllakjifppnca).
* If you are using the Journey Optimizer web designer to author your web channel experience, ensure you are using either the Google Chrome or Microsoft&reg; Edge browsers.
* Ensure that third-party cookies are allowed in your browser. It may be necessary to disable any ad blockers in your browser as well.

    >[!CAUTION]
    >
    > In the Journey Optimizer web designer, certain websites may not reliably open due to one of the following reasons:
    > 
    > 1. The website has stringent security policies.
    > 1. The website is embedded within an iframe.
    > 1. The customer's QA or stage site is not externally accessible (it is an internal site).

* When creating web experiences and including content from the Adobe Experience Manager Assets Essentials library, it's necessary to [configure the subdomain for publishing this content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/web/configure-web-channel/web-delegated-subdomains).
* If using the content experimentation feature, ensure that your web dataset is also included in your reporting configuration.
* Currently, two types of implementations are supported for enabling the authoring and delivery of web channel campaigns on your web properties:
    * Client-side only: To modify your website, you must implement the Adobe Experience Platform Web SDK.
    * Hybrid mode: You can utilize the Platform Edge Network Server API to request personalization server-side. The response from the API is then provided to the Adobe Experience Platform Web SDK for rendering modifications on the client-side. For more information, refer to the Adobe Experience Platform Edge Network Server API documentation. Additional details and implementation samples for the hybrid mode can be found in this blog post.

    >[!NOTE]
    >
    >Server-side only implementation is not currently supported.




## Terminology

First, you should understand the terminology used within web channel campaigns.

* **Web channel**: A medium for communication or the delivery of content via the web. In the context of this guide, it refers to the mechanism through which personalized content is delivered to website visitors using the Platform Web SDK, within Adobe Journey Optimizer.
* **Web surface**: Refers to a web property identified by a URL where content is delivered. It can encompass a single or multiple web pages.
* **Journey Optimizer web designer**: A specific tool or interface within the Journey Optimizer where users can design their web channel experiences.
* **Adobe Experience Cloud Visual Editing Helper**: A browser extension that assists in visually editing and designing web channel experiences.
* **Datastream**: A configuration within the Adobe Experience Platform service that ensures web channel experiences can be delivered.
* **Merge policy**: A configuration that ensures the accurate activation and publication of inbound campaigns.
* **Audience**: A specific segment of users or site visitors who meet certain criteria.
* **Web designer**: An interface or tool that aids in visually editing and designing web experiences without diving deep into code.
* **Expression editor**: A tool within the web designer that allows users to add personalization to web content, potentially based on data attributes or other criteria.
* **Offer decision component**: A component in the web designer that helps in deciding which offer is best suited to be displayed to a specific visitor based on decision management.
* **Content experiment**: A method to test different content variations to find out which one performs best in terms of the desired metric, such as inbound clicks.
* **Treatment**: In the context of content experiments, a treatment refers to a specific variation of content being tested against another.
* **Simulation**: A preview mechanism to visualize the web channel experience before activating it for live audiences.

## Configure the datastream

You have already added the Adobe Experience Platform service to your datastream. Now you need to enable the Adobe Journey Optimizer option so you can deliver web channel experiences.

To configure Adobe Journey Optimizer in the datastream:

1. Go to the [Data Collection](https://experience.adobe.com/#/data-collection){target="blank"} interface.
1. On the left navigation, select **[!UICONTROL Datastreams]**.
1. Select the previously created Luma Web SDK datastream.

    ![Select datastream](assets/web-channel-select-datastream.png)

1. Select **[!UICONTROL Edit]** within the Adobe Experience Platform service.
    
    ![Edit datastream](assets/web-channel-edit-datastream.png)

1. Check the **[!UICONTROL Adobe Journey Optimizer]** box.

1. **[!UICONTROL Save]** the updated configuration.

    ![Check AJO box](assets/web-channel-check-ajo-box.png)


This ensures that inbound events for Journey Optimizer are correctly handled by the Adobe Experience Platform Edge Network.

## Configure the merge policy

Ensure that a merge policy is defined with the **[!UICONTROL Active-On-Edge Merge Policy]** option enabled. This merge policy option is employed by Journey Optimizer inbound channels to ensure the accurate activation and publication of inbound campaigns on the edge.

To configure the option in the merge policy:

1. Go to the **[!UICONTROL Customer]** > **[!UICONTROL Profiles]** page in either the Experience Platform or Journey Optimizer interface.
1. Make sure you are in the sandbox used for the  tutorial
1. Select the **[!UICONTROL Merge Policies]** tab.
1. Select your policy (it's usually best to use the [!UICONTROL Default Timebased] policy), and toggle the **[!UICONTROL Active-On-Edge Merge Policy]** option within the **[!UICONTROL Configure]** step.

   ![Toggle merge policy](assets/web-channel-active-on-edge-merge-policy.png)

## Configure the web dataset for content experimentation

To use content experiments within web channel campaigns, you must ensure the web dataset used is also included in your reporting configuration. The Journey Optimizer reporting system uses the dataset in a read-only fashion to populate out-of-the-box content experimentation reports.

[Adding datasets for content experiment reporting is detailed in this section](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting-configuration#add-datasets).

## Use Case Overview – Loyalty Rewards

In this lesson, a sample Loyalty Rewards use case is used to detail implementation of a web channel experience using the Web SDK.

This use case enables you to better understand how Journey Optimizer can help deliver the best inbound experiences to your customers, utilizing Journey Optimizer campaigns, and the web designer.

As this tutorial is aimed at implementers, it's worth noting that this lesson involves substantial interface work in Journey Optimizer. While such interface tasks are typically handled by marketers, it can be beneficial for implementers to gain insight into the process, even if they are not typically responsible for web channel campaign creation.

### Create Loyalty Rewards Campaign

Now that you have ingested our sample loyalty data and created our segment, create the Loyalty Rewards web channel campaign in Adobe Journey Optimizer.

To create the sample campaign:

1. Open the [Journey Optimizer](https://experience.adobe.com/journey-optimizer/home){target="_blank"} interface
 
    >[!NOTE]
    >
    > Schema, datasets, and audiences can also be built in the Journey Optimizer interface as they are all common Experience Platform constructs.

1. Navigate to **[!UICONTROL Journey Management]** > **[!UICONTROL Campaigns]** in the left navigation
1. Click **[!UICONTROL Create campaign]** in the upper right.
1. Choose the type of campaign. For the Loyalty Rewards use case, choose **Scheduled - Marketing**.

    ![Scheduled campaign](assets/web-channel-campaign-properties-scheduled.png)

1. Add some additional details to the new web channel campaign. First, name the campaign. Call it `Luma Loyalty Rewards – Gold Status`. Optionally, you can add a description to the campaign. Also add **[!UICONTROL Tags]** to improve the overall campaign taxonomy.

    ![Name the campaign](assets/web-channel-campaign-name.png)

1. Go to the **[!UICONTROL Actions]** tab 
1. Choose the **[!UICONTROL Web]** as the **[!UICONTROL Action name]**.
1. Select **[!UICONTROL Create new configuration]** as the **[!UICONTROL Web configuration]**.
1. As the Channel Configuration details, enter the following:
    1. `LumaHomepage` as the **[!UICONTROL Name]**.
    1. **[!UICONTROL Web]** as the **[!UICONTROL Channel]**.
    1. **[!UICONTROL Onsite Personalization]** as the **[!UICONTROL Marketing action]**.
    1. **[!UICONTROL Single page]** as the **[!UICONTROL Web settings]**.
    1. `https://luma.enablementadobe.com/index.html` as the **[!UICONTROL Page URL]**.
1. **[!UICONTROL Submit]** the new channel configuration

    ![Configure the Web Channel](assets/web-channel-configuration.png)
1. In the browser tab with your Campaign, select the new `LumaHomepage` configuration

    >[!TIP]
    >
    > If the new configuration doesn't appear in the dropdown, go to the [!UICONTROL Properties] tab and then return to the [!UICONTROL Actions] tab and check the dropdown again.


## Experiment with Loyalty Rewards Content

Now that you have selected your [!UICONTROL Web configuration], in the **[!UICONTROL Action]** section, you can optionally create an experiment to test out which content works better for the `Luma Loyalty Rewards – Gold Status` audience. Let's create and test two treatments as a component of the campaign configuration.

To create the content experiment:

1. Click **[!UICONTROL Create experiment]**.

    ![Create experiment](assets/web-channel-create-content-experiment.png)

1. First choose a **[!UICONTROL Success metric]**. This is the metric for determining content effectiveness. Choose **[!UICONTROL Unique Clicks]**, to see which content treatment generates more clicks on the web experience CTA.

1. Optionally, you can designate a **[!UICONTROL Holdout]** that does not receive either of the two treatments. Leave this unchecked for now.

1. Also optionally, choose to **[!UICONTROL Distribute evenly]**. Check this option to ensure the treatment splits are always evenly split.

1. Select **[!UICONTROL Add treatment]** so you have two treatments in the experiment.

1. Select **[!UICONTROL Create]**.

    ![Choose success metric](assets/web-channel-content-experiment-metric.png)


[Learn more about content experiments in Adobe Journey Optimizer web channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/get-started-experiment).



### Edit Content using the Visual Helper

Now, let's author the web channel experience. First, install the [Adobe Experience Cloud Visual Editing Helper](https://chromewebstore.google.com/detail/adobe-experience-cloud-vi/kgmjjkfjacffaebgpkpcllakjifppnca) browser extension for Google Chrome and Microsoft&reg; Edge, if you haven't already. Once installed, proceed with the steps in the Journey Optimizer interface:

1. Select **[!UICONTROL Edit Content]** (or navigate to the Cotnent tab of the campaign). Since you entered a single page URL as the surface, you should be ready to begin working in the composer.

    ![Edit content](assets/web-channel-edit-content.png)

1. Now, click **[!UICONTROL Edit web page]** to begin authoring Treatment A of your experiement.

    ![Edit web page](assets/web-channel-edit-web-page.png)

1. Start by editing some elements using the web composer. Use the contextual menu to edit the Luma hero image header. Adjust the style of the contextual pane on the right.

    ![Add contextual edits](assets/web-channel-some-contextual-edit.png)



1. Also add personalization to the container using the **[!UICONTROL Expression editor]**.
    
    ![Open the expression editor](assets/web-channel-open-expression-editor.png)
    ![Add personalization](assets/web-channel-add-basic-personalization.png)

1. Ensure that the experience is properly tracked for clicks. Choose **[!UICONTROL Click track element]** from the contextual menu.

    ![Click track](assets/web-channel-click-tracking.png)

There are many options available to personalize the messaging.

### HTML Design Changes

There are a few methods available if you want to make more advanced, or custom changes to the site as a component of the Loyalty Rewards campaign. Explore some of these in Treatment B.

Use the **[!UICONTROL Components]** pane to add HTML, or other content directly to the Luma site.

![Explore the components pane](assets/web-channel-components-pane.png)

Add a new HTML component at the top of the page. Open the **[!UICONTROL expression editor]** again to edit the HTML.

![Open the expression editor](assets/web-channel-open-expression-editor-html.png)


Alternatively, add HTML edits from the **[!UICONTROL Modifications]** pane. This pane allows you to select a component on the page and edit it from the designer interface.

Within the editor, add the HTML for the `Luma Loyalty Rewards – Gold Status` audience. Select **[!UICONTROL Validate]**.

![Validate HTML](assets/web-channel-add-custom-html-validate.png)

Now, review the new custom HTML component for fit and feel.

### Target the campaign to an audience

By default, the campaign is active for all site visitors. For the purposes of this use case, only gold status reward members should see the experience. To target the content to this audience:

1. Navigate to the **[!UICONTROL Audience]** tab

1. In the **[!UICONTROL Identity namespace]** field, select the namespace for identifying individuals within the chosen segment. Since you are deploying the campaign on the Luma site, you can choose the ECID namespace. Profiles within the `Luma Loyalty Rewards – Gold Status` audience lacking the ECID namespace among their various identities are not targeted by the web channel campaign.

1. **[!UICONTROL Select audience]**

    ![Select audience](assets/web-channel-select-audience.png)

1. Choose the `Luma Loyalty Rewards - Gold Status` audience you created in the [Set up Experience Platform](setup-experience-platform.md) lesson.
1. **[!UICONTROL Save]** the audience to the campaign

    ![Save audience](assets/web-channel-save-audience.png)


<!--
### Simulate Loyalty Rewards Content

Look at a preview of the modified web page before activating the campaign. Keep in mind that you must have test profiles configured to simulate web channel experiences.

To simulate the experience:

1. Select **[!UICONTROL Simulate content]** within the campaign.

    ![Simulate content](assets/web-channel-simulate-content.png)

1. Choose a test profile to receive the simulation. Keep in mind that the test profile should be in the `Luma Loyalty Rewards – Gold Status` audience to receive the proper treatment.

1. The preview is displayed for the test profile.

1. Select the [!UICONTROL Content] tab

1. Choose the **[!UICONTROL Page URL]** web surface option to deploy the experience on one page for this campaign. Enter the URL for the Luma page, `https://luma.enablementadobe.com`

1. Once the web surface is defined, select **[!UICONTROL Create]**.

    ![Select web surface](assets/web-channel-web-surface.png)
-->

### Schedule the campaign

By default, campaigns will start and stop when you manually activate and deactivat them. However you have the option to schedule them to start and stop on specific dates and times. Leave the default settings and select **Review to activate**:

![Campaign schedule](assets/web-channel-campaign-schedule.png)

>[!NOTE]
>
>Keep in mind that for web channel campaigns, the web experience is shown when the visitor opens the page. Therefore, unlike other types of campaigns in Adobe Journey Optimizer, the **[!UICONTROL Action triggers]** section is not configurable.



### Activating the Loyalty Rewards Campaign

You are prompted to confirm the campaign details one final time. Select **[!UICONTROL Activate]**. It can take up to 15 minutes for the campaign to become live on the site.

![Activate the campaign](assets/web-channel-campaign-activate.png)

### Loyalty Rewards QA

There are a few logins you can use to simulate "gold status" users and qualify for your campaign. You must have uploaded the sample data in the [Set up Experience Platform](setup-experience-platform.md) and create accounts using these credentials on the website for these to work.

1. `cleavlandeuler@emailsim.io`/`test`
1. `leftybeagen@emailsim.io`/`test`
1. `jenimartinho@emailsim.io`/`test`

As a best practice, monitor the **[!UICONTROL Web]** campaign statistics on the campaign overview screen after launching or click **[!UICONTROL Reports]** for deeper reporting:

![View web report](assets/web-channel-web-report.png)

### Web channel validation using Adobe Experience Platform Debugger

The Adobe Experience Platform Debugger extension, available for both Chrome and Firefox, analyzes your web pages to identify issues in the implementation of Adobe Experience Cloud solutions.

You can use the debugger on the Luma site to validate the web channel experience in production. This is a best practice once the Loyalty Rewards use case is up and running, to ensure that that everything is configured correctly.

[Learn how to configure the debugger in your browser using the guide here](https://experienceleague.adobe.com/en/docs/platform-learn/data-collection/debugger/overview).

To begin validation using the debugger:

1. Navigate to the Luma web page with the web channel experience.
    <!--
    ![ADD SCREENSHOT](#)
    -->
1. While on the web page, open the **[!UICONTROL Adobe Experience Platform Debugger]**.
    <!--
    ![ADD SCREENSHOT](#)
    -->
1. Navigate to **Summary**. Verify that the **[!UICONTROL Datastream ID]** matches the **[!UICONTROL datastream]** in **[!UICONTROL Adobe Data Collection]** for which you enabled Adobe Journey Optimizer.
    <!--
    ![ADD SCREENSHOT](#)
    -->
1. You can then log in to the site with various Luma loyalty accounts, and use the debugger to validate the requests sent to the Adobe Experience Platform Edge Network.
    <!--
    ![ADD SCREENSHOT](#)
    -->
1. Under **[!UICONTROL Solutions]** navigate to the **[!UICONTROL Experience Platform Web SDK]**.
    <!--
    ![ADD SCREENSHOT](#)
    -->
1. Within the **Configuration** tab, Toggle on **[!UICONTROL Enable Debugging]**. This enables logging for the session within an **[!UICONTROL Adobe Experience Platform Assurance]** session.
    <!--
    ![ADD SCREENSHOT](#)
    -->
1. Log in to the site with various Luma loyalty accounts, and use the debugger to validate the requests sent to the **[!UICONTROL Adobe Experience Platform Edge network]**. All of these requests should be captured in **[!UICONTROL Assurance]** for log tracking.
<!--
   ![ADD SCREENSHOT](#)
-->

>[!NOTE]
>
>Thank you for investing your time in learning about Adobe Experience Platform Web SDK. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/adobe-experience-platform-18/tutorial-discussion-implement-adobe-experience-cloud-with-web-sdk-tutorial-248848)
