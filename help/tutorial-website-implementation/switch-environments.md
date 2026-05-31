---
title: Switch tag environments with the Adobe Experience Cloud Debugger
description: Learn how to use the Experience Cloud Debugger to load different tag embed codes. This lesson is part of the Implement the Experience Cloud in websites tutorial.
exl-id: 29972a00-e5e0-4fe0-a71c-c2ca106938be
TQID: https://experienceleague.adobe.com/blt3GpsKnHSOCzTwlHtpv6NbPQA54iRmkjvdKpBJk7A
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
# Switch tag environments with the Experience Cloud Debugger

In this lesson you will use the [Adobe Experience Platform Debugger extension](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob) to replace the tag property hardcoded on the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html) with your own property.


>[!WARNING]
>
> This tutorial and its Luma website exercises are no longer maintained and rely on older JavaScript libraries. To learn the current best practice, please use the [Implement Adobe Experience Cloud with Web SDK tutorial](https://experienceleague.adobe.com/en/docs/platform-learn/implement-web-sdk/overview).

This technique is called environment switching and will be helpful later, when you work with tags on your own website. You will be able to load your production website in your browser, but with your *development* tag environment. This enables you to confidently make and validate tags changes independently from your regular code releases.  After all, this separation of marketing tag releases from your regular code releases is one of the main reasons customers use tags in the first place!


## Learning Objectives

At the end of this lesson, you will be able to:

* Use the Debugger to load an alternate tag environment
* Use the Debugger to validate that you have loaded an alternate tag environment
  
## Get the URL of your Development Environment

1. In your tag property, open the `Environments` page

1. In the **[!UICONTROL Development]** row, click the Install icon ![Install icon](images/launch-installIcon.png) to open the modal

1. Click the Copy icon ![Copy icon](images/launch-copyIcon.png) to copy the embed code to your clipboard

1. Click **[!UICONTROL Close]** to close the modal

   ![Install icon](images/launch-copyInstallCode.png)

## Replace the tag URL on the Luma Demo Site

1. Open the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html) in your Chrome browser

1. Open the [Experience Platform Debugger extension](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob) by clicking the ![Debugger Icon](images/icon-debugger.png) icon

   ![Click the Debugger icon](images/switchEnvironments-openDebugger.png)

1. Note that the currently implemented tag property is shown on the Summary tab

   ![tag environment shown in Debugger](images/switchEnvironments-debuggerOnWeRetail-prod.png)

1. Go to the Tools tab
1. Scroll to the section **[!UICONTROL Replace Launch Embed Code]**
1. Make sure the Chrome tab with the Luma site is in focus behind the Debugger (not the tab with this tutorial or the tab with the Data Collection interface).  Paste the embed code that is in your clipboard into the input field
1. Toggle on the "Apply across luma.enablementadobe.com" feature so that all pages on the Luma site will map to your tag property
1. Click the **[!UICONTROL Save]** button

   ![tag environment shown in Debugger](images/switchEnvironments-debugger-save.png)

1. Reload the Luma site and check the Summary tab of the Debugger. Under the Launch section, you should now see your Development Property is being used. Confirm that both the Name of the property matches yours and that the Environment says "development."

   ![tag environment shown in Debugger](images/switchEnvironments-debuggerOnWeRetail.png)

>[!NOTE]
>
>The Debugger will save this configuration and replace the tag embed codes whenever you come back to the Luma site. It will not impact other sites you visit in other open tabs. To stop the Debugger from replacing the embed code, click the **[!UICONTROL Remove]** button next to the embed code in the Tools tab of the Debugger.

As you continue the tutorial, you will use this technique of mapping the Luma site to your own tag property to validate your tag implementation. When you start using tags on your production website, you can use this same technique to validate changes.

[Next "Add the Adobe Experience Platform Identity Service" >](id-service.md)
