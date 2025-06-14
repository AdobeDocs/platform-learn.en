---
title: Validate Web SDK implementations with Experience Platform Debugger
description: Learn how to validate your Platform Web SDK implementation with Adobe Experience Platform Debugger. This lesson is part of the Implement Adobe Experience Cloud with Web SDK tutorial.
feature: Web SDK,Tags,Debugger
jira: KT-15405
exl-id: 150bb1b1-4523-4b44-bd4e-6cabc468fc04
---
# Validate Web SDK implementations with Experience Platform Debugger

Learn how to validate your Adobe Experience Platform Web SDK implementation with Adobe Experience Platform Debugger.

The Experience Platform Debugger is an extension available for Chrome and Firefox browsers, which helps you see the Adobe technology implemented in your web pages. Download the version for your preferred browser:

* [Firefox extension](https://addons.mozilla.org/en-US/firefox/addon/adobe-experience-platform-dbg/)
* [Chrome extension](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob)

If you have never used the debugger before, you might want to watch this five-minute overview video:

>[!VIDEO](https://video.tv.adobe.com/v/32156?learn=on&enablevpops)

In this lesson, you use the [Adobe Experience Platform Debugger extension](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob) to replace the tag property hardcoded on the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html) with your own property.

This technique is called environment switching and will be helpful later, when you work with tags on your own website. It allows you to to load your production website in your browser, but with your *development* tags library. This ability enables you to confidently make and validate tags changes independently from your regular code releases. After all, this separation of marketing tag releases from your regular code releases is one of the main reasons customers use tags in the first place!

## Learning objectives

At the end of this lesson, you will be able to use the debugger to:

* Load an alternate tag library
* Validate the client-side XDM event is capturing and sending data as expected to Platform Edge Network
* Enable Edge Trace to view server-side requests sent by Platform Edge Network

## Prerequisites

You are familiar with Data Collection tags and the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} and have completed the previous lessons in the tutorial:

* [Configure an XDM schema](configure-schemas.md)
* [Configure an identity namespace](configure-identities.md)
* [Configure a datastream](configure-datastream.md)
* [Web SDK extension installed in the tag property](install-web-sdk.md)
* [Create data elements](create-data-elements.md)
* [Create identities](create-identities.md)
* [Create tag rules](create-tag-rule.md)

## Load alternate tag libraries with Debugger

The Experience Platform Debugger has a cool feature that allows you to replace an existing tag library with a different one. This technique is useful for validation and allows us to skip many implementation steps in this tutorial.

1. Make sure you have the [Luma demo website](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} open and select the Experience Platform Debugger extension icon
1. The Debugger will open and show some details of the hardcoded implementation (you may need to reload the Luma site after opening the Debugger)
1. Confirm that the Debugger is "**[!UICONTROL Connected to Luma]**" as pictured below and then select the "**[!UICONTROL lock]**" icon to lock the Debugger to the Luma site.
1. Select the **[!UICONTROL Sign In]** button and sign into Adobe Experience Cloud using your Adobe Id.
1. Now, go to **[!UICONTROL Experience Platform Tags]** in the left navigation

    ![Debugger tag Screen](assets/validate-launch-screen.png)

1. Select the **[!UICONTROL Configuration]** tab
1. To the right of where it shows you the **[!UICONTROL Page Embed Codes]**, open the **[!UICONTROL Actions]** dropdown, and select **[!UICONTROL Replace]**

    ![Select Actions > Replace](assets/validate-switch-environment.png)

1. Since you are authenticated, the Debugger is going to pull in your available tag properties and environments. Select your property
1. Select your `Development` environment
1. Select the **[!UICONTROL Apply]** button

    ![Select the alternate tag property](assets/validate-switch-selection.png)

1. The Luma website will now reload _with your own tag property_.

    ![tag property replaced](assets/validate-switch-success.png)

As you continue the tutorial, you use this technique of mapping the Luma site to your own tag property to validate your Platform Web SDK implementation. When using tags on your own website, you can use this same technique to validate development tag libraries on your production website.

## Validate client-side network requests with Experience Platform Debugger

You can use the Debugger to validate client-side beacons triggered from your Platform Web SDK implementation to view the data sent to Platform Edge Network:

1. Go to **[!UICONTROL Summary]** in the left navigation, to see the details of your tag property

    ![Summary tab](assets/validate-summary.png)

1. Now, go to **[!UICONTROL Experience Platform Web SDK]** in the left navigation to see the **[!UICONTROL Network Requests]**
1. Open the **[!UICONTROL events]** row

    ![Adobe Experience Platform Web SDK request](assets/validate-aep-screen.png)

1. Note how you can see the `web.webpagedetails.pageView` event type you specified in your [!UICONTROL Update variable] action, and other, out-of-the-box variables adhering to the `AEP Web SDK ExperienceEvent` field group

    ![Event details](assets/validate-event-pageViews.png)   
    
1. Scroll down to the `web` object, select to open it and inspect the `webPageDetails.name`, `webPageDetails.server`, and `webPageDetails.siteSection`. They should match the corresponding `digitalData` data layer variables on the homepage

>[!TIP]
>
> To view and compare the `digitalData` data layer on the homepage:
>
> 1. While on the Luma homepage, open the browser developer tools. In the case of Chrome, select button `F12` on your keyboard
> 1. Select the **[!UICONTROL Console]** tab
> 1. Enter `digitalData` and select `Enter` on your keyboard to bring up the data layer values

![Network tab](assets/validate-xdm-content.png)

You can also validate the Identity Map details:

1. Log in to the Luma site using the credentials `test@test.com`/`test`

1. Return to the [Luma homepage](https://luma.enablementadobe.com/content/luma/us/en.html)

1. Open the **[!UICONTROL Experience Platform Web SDK]** section in the left navigation 

   ![Web SDK in Debugger](assets/identity-debugger-websdk-dark.png)

1. Select the **[!UICONTROL events]** row to open details in a pop-up

   ![Web SDK in Debugger](assets/identity-deugger-websdk-event-dark.png)

1. Search for the **identityMap** within the pop-up. Here you should see `lumaCrmId` with three keys of authenticatedState, id, and primary:
    ![Web SDK in Debugger](assets/identity-deugger-websdk-event-lumaCrmId-dark.png)

### Validate client-side requests with browser dev tools

These types of request details are also visible in the browser's web developer tools **Network** tab (assuming the website is loading your tag library). 

1. Open the browser's web developer tools **Network** tab and reload the page. Filter for calls with `/ee` to locate the call, select it, and then look in the **Headers** tab, and **Payload** tab

    ![Network tab](assets/validate-dev-console.png)

1. Go to the **Response** tab and note how the ECID value is included in the response.

    ![Network tab](assets/validate-dev-console-ecid.png)   

    >[!NOTE]
    >
    > The ECID value is visible in the network response. It is not included in the `identityMap` portion of the network request, nor is it stored in this format in a cookie.

## Validate server-side network requests with Experience Platform Debugger

As you learned in the [Configure a datastream](configure-datastream.md) lesson, Platform Web SDK first sends data from your digital property to Platform Edge Network. Then, Platform Edge Network makes additional server-side requests to the corresponding services enabled in your datastream. You can validate the server-side requests made by Platform Edge Network by using Edge Trace in the Debugger. 

<!--Furthermore, you can also validate the fully processed payload after it reaches an Adobe application by using [Adobe Experience Platform Assurance](https://experienceleague.adobe.com/en/docs/experience-platform/assurance/home). -->


### Enable Edge Trace

To enable Edge Trace:

1. In the left navigation of **[!UICONTROL Experience Platform Debugger]** select **[!UICONTROL Logs]**
1. Select the **[!UICONTROL Edge]** tab, and select **[!UICONTROL Connect]**

    ![Connect Edge Trace](assets/analytics-debugger-edgeTrace.png)

1. It is empty for now

    ![Connected Edge Trace](assets/analytics-debugger-edge-connected.png)    

1. Refresh the [Luma home page](https://luma.enablementadobe.com/) and check **[!UICONTROL Experience Platform Debugger]** again, to see data come through. 

    ![Analytics beacon Edge Trace](assets/validate-edge-trace.png)

At this point, you are not able to view any Platform Edge Network requests going to Adobe applications because you have not enabled any in the datastream. In future lessons, you use Edge Trace to view the outgoing server-side requests to Adobe applications and event forwarding. But first, learn about another tool to validate server-side requests made by Platform Edge Network&mdash;Adobe Experience Platform Assurance!

[Next: **Validate with Assurance**](validate-with-assurance.md)

>[!NOTE]
>
>Thank you for investing your time in learning about Adobe Experience Platform Web SDK. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
