---
title: Test the implementation
description: Test the implementation
exl-id: 66eb1d4e-32eb-45fc-8da4-8d3c04dc3c7a
---
# Test the implementation

Now that you have your webpage set up and your Adobe Experience Platform tag library deployed, it's time to test the implementation.

1. Open up your product page in your browser. You can do this by clicking _File_ then _Open File..._ in your browser or you can host your page on a web server and enter the appropriate URL.

After the page loads, you should see something like this:
    ![Webpage](assets/webpage.png)

It's not pretty, but it does the job.

## Inspect the page view and product view events

1. Open the developer tools in your browser and click on the network panel. Refresh your page.
At this point, you should see four requests:
* product.html - Your web page.
* launch-############-development.js - Your Launch library.
* interact - The page view event being sent to the server.
* interact - The product view event being sent to the server.
Inspect the payload of each request:
1. For the first `interact` request, you should be able to see the payload being sent with an `eventType` of `web.webpagedetails.pageViews`.
    ![Page view request inspection](assets/webpage-page-viewed-inspection.png)
1. For the second `interact` request, you should be able to see the payload being sent with an `eventType` of `commerce.productViews`.
    ![Product view request inspection](assets/webpage-product-view-inspection.png)
1. Review the rest of the data being sent, including the product information.

## Inspect the open cart and add to cart events

1. Now click the **_Add to cart_**button.

You should see two additional requests, the first with an `eventType` of `commerce.productListOpens` (for opening a new cart) and the second with an `eventType` of `commerce.productListAdds` (for adding the product to the cart).

## Inspect the download app link click event

Depending on the browser, clicking a link that navigates you away from the current page may clear out your network panel. Because you want to inspect the network request for the link click event that occurs right before you navigate away from the page, you need to configure your browser to preserve network logs across pages. 

1. Preserve network logs by either checking a **_Preserve log_** checkbox in the network panel (Chrome, Safari, Edge) or clicking a gear icon and checking a **_Persist logs_** item on the displayed menu (Firefox).
1. Click the **_Download the app_** link. You should see one more `interact` request show up in the network panel. 
1. Locate the request with an `eventType` of `web.webinteraction.linkClicks`, and review the details about the link that was clicked.

## Check that data arrives in the Adobe Experience Platform dataset

Now that requests are being sent, check whether the data is safely arriving in the Adobe Experience Platform dataset  you created. 

1. Navigate to the **[!UICONTROL Datasets]** view inside Adobe Experience Platform.
1. Select the [dataset](configure-the-server/create-a-dataset.md) that you created for this tutorial.
You may need to wait a few minutes, but soon you should see indications of data being processed and inserted into your dataset. You should also see whether processing succeeded or failed. If it failed, you see why it failed. Failures typically occur because the data you are sending does not match the schema and you need to adjust your data or schema accordingly.
    ![Dataset ingestion](assets/dataset-ingestion.png)

## Use the Adobe Experience Platform Debugger extension

For greater insight into how your implementation is behaving both on the browser and on Adobe's servers, check out the Adobe Experience Platform Debugger browser extension!

[Adobe Experience Platform Debugger extension for Chrome](https://chrome.google.com/webstore/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob)

[Adobe Experience Platform Debugger extension for Firefox](https://addons.mozilla.org/en-US/firefox/addon/adobe-experience-platform-dbg/)

[Next: **Summary**](summary.md)

>[!NOTE]
>
>Thank you for investing your time in learning about Data Collection. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)