---
title: Data Ingestion using Google Tag Manager and Google Analytics - Setup Google Analytics & link it to GTM
description: Data Ingestion using Google Tag Manager and Google Analytics - Setup Google Analytics & link it to GTM
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 92bd76a8-d3fc-4d33-81d8-b3da70a6ac94
---
# 9.2 Setup Google Analytics & link it to GTM

Go to [https://analytics.google.com/](https://analytics.google.com/) and login with your Google Account.

If this is the first time you do this, your screen will look like this.

![Google Analytics setup](./images/ga1-blank.png)

Click on **Start measuring**.

![Google Analytics setup](./images/ga1-blank-start.png)

You'll need to fill in some Account details about the website you want to analyze. Please use **SYTYCD - ldap**, and leave the fields checked, unless you have a specific reason to uncheck them.

![Google Analytics setup](./images/ga2-accountdetails.png)

Click **Next** to proceed to **What do you want to measure?**.

![Google Analytics setup](./images/ga3-next.png)

Select **Web**.

![Google Analytics setup](./images/ga3-whattomeasure.png)

Click **Next** to proceed to **Property setup**.

![Google Analytics setup](./images/ga3-next.png)

You can fill in these fields:

| Form field                | Value               |
|:-------------------------------------------| :------------------ |
|Website Name|SYTYCD - **ldap**|
|Website URL|www.aepdemo.net|
|Industry Category|Shopping|
|Reporting Time Zone|the timezone where you work|

![Google Analytics setup](./images/ga4-property.png)

Click **Create**.

![Google Analytics setup](./images/ga4-create.png)

Accept the Terms & Conditions by checking the 2 checkboxes.

![Google Analytics setup](./images/ga4-create-accepttc.png)

Then click **I accept**.

![Google Analytics setup](./images/ga4-create-accepttci.png)

You'll now see the **Admin** - page of your Google Analytics - property.

![Google Analytics setup](./images/ga5-homescreen.png)

Click on **Property Settings**.

![Google Analytics setup](./images/ga8-property.png)

You now need to copy the value of **Tracking ID**.

![Google Analytics setup](./images/ga9-trackingidd.png)

![Google Analytics setup](./images/ga9-trackingid.png)

Google Tag Manager is able to manage the Google Analytics tags by using this Tracking ID.
So let's go back to GTM to store the Tracking ID there.

Go to [https://tagmanager.google.com/](https://tagmanager.google.com/) by following the URL of by clicking the **Product Switcher** item at the top right of the screen.

![Google Analytics setup](./images/ga10-switchproducts.png)

Next choose Tag Manager at the bottom of the list.

![Google Analytics setup](./images/ga11-gtm.png)

You might need to login again, then choose the container in GTM for **www.platformdemo.net**.

![Google Analytics setup](./images/ga12-gtmstart.png)

You are now on the overview page of GTM where nothing has been added yet.

![Google Analytics setup](./images/ga12-gtmoverviewsstart.png)

If you're familiar to Adobe Launch you use **Extensions**, **Data elements** and **Rules**. In GTM you use in more or less the same way **Tags**, **Variables** and **Triggers**.
We're going to create a **Tag** for Google Analytics, then a **Trigger** when to fire the Google Analytics tag.

Create the tag by clicking **New Tag**.

![Google Analytics setup](./images/ganewtag.png)

You'll then see this screen:

![Google Analytics setup](./images/ga13-gtmnewtagempty.png)

Give this tag a name by changing **Untitled Tag** into **Universal Analytics**:

| Form field                | Value               |
|:-------------------------------------------| :------------------ |
|Tag Name|Universal Analytics|

Then press **Tag Configuration**, where you can choose from a list of available tags.

![Google Analytics setup](./images/ga14-choosetag1.png)

Choose **Google Analytics: Universal Analytics**. You'll then see this screen:

![Google Analytics setup](./images/ga14-choosetag2.png)

Click the **Google Analytics Settings** - dropdown list and choose **New Variable**.

![Google Analytics setup](./images/ga14-choosetag.png)

Then add the following fields:

| Form field                | Value               |
|:-------------------------------------------| :------------------ |
|Track Type|Page View|
|Google Analytics settings|New Variable|

This selection gives you a next screen where you can enter as a Tracking ID the one you copied earlier from Google Analytics.
Name this one **Google Analytics Tracking ID**. By doing that, you've also automatically created a new GTM Variable.

![Google Analytics setup](./images/ga15-yourtrackingid.png)

Click **Save** to proceed.

![Google Analytics setup](./images/gasave.png)

You now see the name of the newly created data element appearing. You're now ready with the Tag Configuration, now it's time to tell GTM, that this tag should be triggered on each page view. You do that by clicking the **Triggering** element in your screen.

![Google Analytics setup](./images/ga15-garesult.png)

Currently there's only the default trigger **All Pages**. Later we'll define new triggers for specific pages. Choose this one by selecting it with your mouse.

![Google Analytics setup](./images/ga16-addtriggerA.png)

Your screen will now show a checked box, proceed by clicking **Add**.

![Google Analytics setup](./images/gaadd.png)

![Google Analytics setup](./images/ga16-addtriggerB.png)

You are now ready to save the Universal Analytics Tag by clicking **Save**.

![Google Analytics setup](./images/gasave.png)

![Google Analytics setup](./images/ga16-addtriggerC.png)

You are now again on the overview page, but here you see that there are two changes to be published in the workflow.
Click **Submit**.

![Google Analytics setup](./images/gasubmit.png)

![Google Analytics setup](./images/ga12-gtmoverview.png)

First you see this screen where you can fill in descriptive information about the change you're going to publish. Add a short description and a more describing one.

![Google Analytics setup](./images/ga17-publish2.png)

Now click **Publish**.

![Google Analytics setup](./images/gapublish.png)

You're then seeing the versions tab in GTM, showing you the summary of what you just published. This will not be active yet, since we have not yet implemented the GTM tag on the Platform Demo website. We'll be doing that in a later exercise.

![Google Analytics setup](./images/ga-publish3.png)

From here you can click back to the **Workspace** tab, where you can add more Tags, Triggers and Variables, which we'll be doing in the next Exercise.

![Google Analytics setup](./images/gaworkspace.png)

Next Step: [9.3 Configure GTM Variables](./ex3.md)

[Go Back to Module 9](./data-ingestion-using-google-tag-manager-and-google-analytics.md)

[Go Back to All Modules](../../overview.md)
