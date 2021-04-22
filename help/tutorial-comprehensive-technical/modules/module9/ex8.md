---
title: Data Ingestion using Google Tag Manager and Google Analytics - Verify Data Ingestion from website into Platform
description: Data Ingestion using Google Tag Manager and Google Analytics - Verify Data Ingestion from website into Platform
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: fbabb928-5bfb-4302-81e6-3da090744ae8
---
# 9.8 Verify Data Ingestion from website into Platform

Open a new, clean incognito window and navigate to [https://public.aepdemo.net](https://public.aepdemo.net). Enter your Configuration ID and save it.

After updating the configuration of your Configuration ID and loading the AEP Demo website in a new, clean incognito browser window, you should start to see requests being sent towards Adobe Experience Platform.

These requests are sent to the DCS Endpoint that you configured in Exercise 9.4.

To verify if requests are being sent, open your website by going to [https://public.aepdemo.net/index.html](https://public.aepdemo.net/index.html) in Chrome and at the same time open the Chrome Developer Tools.

![Verify Calls](./images/devtools.png)

Open the Chrome Developer Tools on the **Network** view and then refresh your page.

![Verify Calls](./images/sitedevtools.png)

By refreshing your page, you'll see all the requests being sent from the page to various servers, including the requests to the DCS Endpoint of Platform.

![Verify Calls](./images/sitecalls.png)

Go to the **Console** view.

![Verify Calls](./images/sitecallsconsole.png)

In the **Filter**, type `GA`.

![Verify Calls](./images/sitecallsconsolega.png)

You should now see a log entry that says `>>>>> GA - All General Pages - Sending PageView to DCS`. This indicates that the request from your Google Tag Manager tag `All General Pages` has fired.

Go back to the **Network** view.

![Verify Calls](./images/sitecalls.png)

To easily find the requests to Platform, you can apply a filter by entering `dcs` in the Filter field.

![Verify Calls](./images/dcsfilter.png)

This should give you two requests to Platform, which are the requests that sends in ExperienceEvent data on every page load, now sent by Adobe Experience Platform Launch and also, Google Tag Manager.

The first request is the request sent by Google Tag Manager. Click on it and scroll down until you see **Request Payload**.

![Verify Calls](./images/payload.png)

Click on **view source** to view the full raw request to Platform. Select the full raw text and copy it.

![Verify Calls](./images/rawcall.png)

Go to [https://jsonformatter.org/json-pretty-print](https://jsonformatter.org/json-pretty-print) and paste the copied raw text in the left window.

![Verify Calls](./images/makepretty.png)

Click on **Make Pretty** to see a readable version of the request to Platform. You now see the full payload as sent by Google Tag Manager to Adobe Experience Platform, and you can also see that the only identifier on this request, the Primary Identifier, is the Google `GAID`. This also means that with Platform, the presence of the ECID isn't a hard requirement anymore. Any identifier, including non-Adobe identifiers, can be the Primary Identifier, it's up to the customer to choose.

![Verify Calls](./images/prettycall.png)

Next, click on any Product like the **Nadia Elements Shell**. Keep the Chrome Developer Console open.

Go to the **Console** view. In the **Filter**, type `GA`.

![Verify Calls](./images/sitecallsconsolegapp.png)

You should now see a log entry that says `>>>>> GA - All Product Pages - Sending PageView to DCS`. This indicates that the request from your Google Tag Manager Tag `All Product Pages` has fired.

Go back to the **Network** view. To easily find the requests to Platform, you can apply a filter by entering `dcs` in the Filter field.

This should give you two requests to Platform, which are the requests that sends in ExperienceEvent-data for a Product View, now sent by Adobe Experience Platform Launch and also, Google Tag Manager.

The first request is the request sent by Google Tag Manager. Click on it and scroll down until you see **Request Payload**.

Click on **view source** to view the full raw request to Platform. Select the full raw text and copy it.

![Verify Calls](./images/rawcallpp.png)

Go to [https://jsonformatter.org/json-pretty-print](https://jsonformatter.org/json-pretty-print) and paste the copied raw text in the left window.

![Verify Calls](./images/makepretty.png)

Click on **Make Pretty** to see a readable version of the request to Platform. You now see the full Product Page  payload as sent by Google Tag Manager to Adobe Experience Platform, and you can also see that the only identifier on this request, the Primary Identifier, is the Google `GAID`. This also means that with Platform, the presence of the ECID isn't a hard requirement anymore. Any identifier, including non-Adobe identifiers, can be the Primary Identifier, it's up to the customer to choose.

![Verify Calls](./images/prettycallpp.png)

Next, go to to the Login/Register-page [https://public.aepdemo.net/login-register.html](http://public.aepdemo.net/login-register.html).

Fill out all the fields and click **Create Account**.

![Verify Calls](./images/createaccount.png)

After clicking the **Create Account** button, you're sent to the homepage.

In the Chrome Developer Console, go to the **Console** view. In the **Filter**, type `GA`.

![Verify Calls](./images/sitecallsconsolegauth.png)

You should now see a log entry that says `>>>>> GA - All General Pages - Sending PageView to DCS` and also another log entry that says `>>>>> GA - All Authenticated Pages - Sending PageView to DCS`. This indicates that the request from your Google Tag Manager Tag `All General Pages` and the GTL Tag for `All Authenticated Pages` has fired.

Go back to the **Network** view. To easily find the requests to Platform, you can apply a filter by entering `dcs` in the Filter field.

This should give you four requests to Platform, which are two requests that send in ExperienceEvent-data for a General Page View and two requests that send in Profile-data, now sent by Adobe Experience Platform Launch and also, Google Tag Manager.

The 3rd request is the request sent by Google Tag Manager containing Profile Data. Click on it and scroll down until you see **Request Payload**.

Click on **view source** to view the full raw request to Platform. Select the full raw text and copy it.

![Verify Calls](./images/rawcallauth.png)

Go to [https://jsonformatter.org/json-pretty-print](https://jsonformatter.org/json-pretty-print) and paste the copied raw text in the left window, then click on **Make Pretty** to see the full payload in a readable format.

![Verify Calls](./images/prettyprofile.png)

Again you notice that the identifiers-object contains a Google `GAID`. In this case, for Profile data, the Primary Identifier is `emailId`, with `GAID` being a secondary identifier. By having both of these identities on the same request, including the `mobilenr`, ID-syncs have now been done and have connected these 3 identities to each other in Adobe Experience Platform's Unified Identity Service.

If you see all these requests going out to the DCS Endpoint from GTM, that means that GTM is correctly configured.

Now we need to verify whether these requests are successfully received by Platform.

To log in to Platform, go to [https://experience.adobe.com/platform/home](https://experience.adobe.com/platform/home).

Go to **Datasets** and locate your two Datasets. As a reminder, the shared datasets we're using are called:

* Website Interaction Dataset name:
  
  * `AEP Demo - GA Website Interactions`
      ![Platform Setup](./images/ee.png)

* Website Registration Dataset name:
  
  * `AEP Demo - GA Website Registrations`
      ![Platform Setup](./images/p.png)

Datasets in the UI of Platform are usually updated every 15 minutes.

You can immediately see if the ingestion of the last batch of data for this dataset was successful:

![Verify Calls](./images/datasetstatus.png)

And by opening the `AEP Demo - GA Website Interactions`-dataset you can see all individual ingested batches for this dataset.

![Verify Calls](./images/alleebatches.png)

By clicking on **Preview**, you can see a preview of the ingested data.

![Verify Calls](./images/previewbtn.png)

![Verify Calls](./images/eepreview.png)

You can do the same thing for the `AEP Demo - GA Website Registrations` dataset:

![Verify Calls](./images/profilebatches.png)

Also have a look at the **Preview** of Profile Data to retrieve your ingested data.

![Verify Calls](./images/profilepreviewdata.png)

Next Step: [Summary and benefits](./summary.md)

[Go Back to Module 9](./data-ingestion-using-google-tag-manager-and-google-analytics.md)

[Go Back to All Modules](../../overview.md)
