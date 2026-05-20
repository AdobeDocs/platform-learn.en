---
title: Publish your tag property
description: Learn how to publish your tag property from the Development environment to the Staging and Production environments. This lesson is part of the Implement the Experience Cloud in websites tutorial.
exl-id: dec70472-cecc-4630-b68e-723798f17a56
TQID: https://experienceleague.adobe.com/4Zv6xcAbI69Z38vlow-3zjAMD2RhXPr5-gQEp6RhAKs
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
    internal-label: Acrobat Sign
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
  - id: ed0d8d0e-04b9-4326-be72-a0fbca265377
    internal-label: Integrations
  - id: fc7979f3-56c3-43ca-9784-f1ea3dc69c4b
    internal-label: Integrations
subfeature_v2:
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: ca3d6bf4-a4af-4944-936b-8de1eb09f149
    internal-label: Datastreams
  - id: d9830f6f-ceb6-4faa-9744-f281fe4439f9
    internal-label: Tags
  - id: dc6ebdf7-9a94-43eb-9184-759cfdd0cf1c
    internal-label: Event forwarding
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
# Publish your tag property

Now that you have implemented some key solutions of the Adobe Experience Cloud in your Development environment, it's time to learn the publishing workflow.


>[!WARNING]
>
> This tutorial and its Luma website exercises are no longer maintained and rely on older JavaScript libraries. To learn the current best practice, please use the [Implement Adobe Experience Cloud with Web SDK tutorial](https://experienceleague.adobe.com/en/docs/platform-learn/implement-web-sdk/overview).


## Learning Objectives

At the end of this lesson, you will be able to:

1. Publish a Development library to the Staging environment
1. Map a Staging library to your production website using the Debugger
1. Publish a Staging library to the Production environment

## Publish to Staging

 Now that you have created and validated your library in the Development environment, it is time to publish it to Staging.

1. Go to the **[!UICONTROL Publishing Flow]** page

1. Open the dropdown next to your library and select **[!UICONTROL Submit for Approval]**

   ![Submit for Approval](images/publishing-submitForApproval.png)

1. Click the **[!UICONTROL Submit]** button in the dialog:

   ![Click Submit in the Modal](images/publishing-submit.png)

1. Your library will now appear in the [!UICONTROL Submitted] column in an unbuilt state:

1. Open the dropdown and select **[!UICONTROL Build for Staging]**:

   ![Build for Staging](images/publishing-buildForStaging.png)

1. Once the green-dot icon appears, the library can be previewed in the Staging environment.

In a real-life scenario, the next step in the process would typically be to have your QA team validate the changes in the Staging library. They can do this using the Debugger.

**To Validate the Changes in the Staging Library**

1. In your tag property, open the [!UICONTROL Environments] page

1. In the [!UICONTROL Staging] row, click the Install icon ![Install icon](images/launch-installIcon.png) to open the modal

   ![Go to the Environments page and click to open the modal](images/publishing-getStagingCode.png)

1. Click the Copy icon ![Copy icon](images/launch-copyIcon.png) to copy the embed code to your clipboard

1. Click **[!UICONTROL Close]** to close the modal

   ![Install icon](images/publishing-copyStagingCode.png)

1. Open the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html) in your Chrome browser

1. Open the [Experience Platform Debugger extension](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob) by clicking the ![Debugger Icon](images/icon-debugger.png) icon

   ![Click the Debugger icon](images/switchEnvironments-openDebugger.png)

1. Go to the Tools Tab

1. In the **[!UICONTROL Adobe Launch > Replace Launch Embed Code]** section paste the Staging embed code that is in your clipboard
1. Turn on the **[!UICONTROL Apply across luma.enablementadobe.com]** switch

1. Click the disk icon to save

   ![tag environment shown in Debugger](images/switchEnvironments-debugger-save.png)

1. Reload and check the Summary tab of the Debugger. Under the Launch section, you should now see your Staging Property is implemented, showing your property name (I.e. "tags Tutorial" or whatever you named your property)!

   ![tag environment shown in Debugger](images/publishing-debugger-staging.png)

In real-life, once your QA team has signed off by reviewing the changes in the Staging environment it is time to publish to production.

## Publish to Production

1. Go to the [!UICONTROL Publishing] page

1. From the dropdown, click **[!UICONTROL Approve for Publishing]**:

   ![Approve for Publishing](images/publishing-approveForPublishing.png)

1. Click the **[!UICONTROL Approve]** button in the dialog box:

   ![Click Approve](images/publishing-approve.png)

1. The library will now appear in the [!UICONTROL Approved] column in the unbuilt state (yellow dot):

1. Open the dropdown and select **[!UICONTROL Build and Publish to Production]**:

   ![Click Build &amp; Publish to Production](images/publishing-buildAndPublishToProduction.png)

1. Click the **[!UICONTROL Publish]** in the dialog box:

   ![Click Publish](images/publishing-publish.png)

1. The library will now appear in the [!UICONTROL Published] column:

   ![Published](images/publishing-published.png)

That's it! You've completed the tutorial and published your first property in tags!
