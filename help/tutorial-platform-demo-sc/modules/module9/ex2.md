---
title: Module 9, Exercise
description: 
kt: 5342
audience: 
doc-type: tutorial
activity: 
---

# Exercise 9.2 - Setup Google Analytics & link it to GTM

Go to [https://analytics.google.com/](https://analytics.google.com/) and login with your Google Account.

If this is the first time you do this, your screen will look like this.

![GA setup](./images/ga1-blank.png)

Click on ``Start measuring``.

![GA setup](./images/ga1-blank-start.png)

You'll need to fill in some Account details about the website you want to analyze. Please use ``SYTYCD - ldap``, and leave the fields checked, unless you have a specific reason to uncheck them.

![GA setup](./images/ga2-accountdetails.png)

Click ``Next`` to proceed to ``What do you want to measure?``.

![GA setup](./images/ga3-next.png)

Select ``Web``.

![GA setup](./images/ga3-whattomeasure.png)

Click ``Next`` to proceed to ``Property setup``.

![GA setup](./images/ga3-next.png)

You can fill in these fields:

| Form field                | Value               |
|:-------------------------------------------| :------------------ |
|Website Name|SYTYCD - **ldap**|
|Website URL|www.platformdemo.net|
|Industry Category|Shopping|
|Reporting Time Zone|the timezone where you work|

![GA setup](./images/ga4-property.png)

Click ``Create``.

![GA setup](./images/ga4-create.png)

Accept the Terms & Conditions by checking the 2 checkboxes.

![GA setup](./images/ga4-create-accepttc.png)

Then click ``I accept``.

![GA setup](./images/ga4-create-accepttci.png)

You'll now see the ``Admin`` - page of your Google Analytics - property.

![GA setup](./images/ga5-homescreen.png)

Click on ``Property Settings``.

![GA setup](./images/ga8-property.png)

You now need to copy the value of ``Tracking ID``.

![GA setup](./images/ga9-trackingidd.png)

![GA setup](./images/ga9-trackingid.png)

Google Tag Manager is able to manage the Google Analytics tags by using this Tracking ID.
So let's go back to GTM to store the Tracking ID there.

Go to [https://tagmanager.google.com/](https://tagmanager.google.com/) by following the URL of by clicking the ``Product Switcher`` - item at the top right of the screen.

![GA setup](./images/ga10-switchproducts.png)

Next choose Tag Manager at the bottom of the list.

![GA setup](./images/ga11-gtm.png)

You might need to login again, then choose the container in GTM for ``www.platformdemo.net``.

![GA setup](./images/ga12-gtmstart.png)

You are now on the overview page of GTM where nothing has been added yet.

![GA setup](./images/ga12-gtmoverviewsstart.png)

If you're familiar to Adobe Launch you use ``Extensions``, ``Data elements`` and ``Rules``. In GTM you use in more or less the same way ``Tags``, ``Variables`` and ``Triggers``.
We're going to create a ``Tag`` for GA, then a ``Trigger`` when to fire the GA-tag.

Create the tag by clicking ``New Tag``.

![GA setup](./images/ganewtag.png)

You'll then see this screen:

![GA setup](./images/ga13-gtmnewtagempty.png)

Give this tag a name by changing ``Untitled Tag`` into ``Universal Analytics``:

| Form field                | Value               |
|:-------------------------------------------| :------------------ |
|Tag Name|Universal Analytics|

Then press ``Tag Configuration``, where you can choose from a list of available tags.

![GA setup](./images/ga14-choosetag1.png)

Choose ``Google Analytics: Universal Analytics``. You'll then see this screen:

![GA setup](./images/ga14-choosetag2.png)

Click the ``Google Analytics Settings`` - dropdown list and choose ``New Variable``.

![GA setup](./images/ga14-choosetag.png)

Then add the following fields:

| Form field                | Value               |
|:-------------------------------------------| :------------------ |
|Track Type|Page View|
|Google Analytics settings|New Variable|

This selection gives you a next screen where you can enter as a Tracking ID the one you copied earlier from Google Analytics.
Name this one ``GA Tracking ID``. By doing that, you've also automatically created a new GTM Variable.

![GA setup](./images/ga15-yourtrackingid.png)

Click ``Save`` to proceed.

![GA setup](./images/gasave.png)

You now see the name of the newly created data element appearing. You're now ready with the Tag Configuration, now it's time to tell GTM, that this tag should be triggered on each page view. You do that by clicking the ``Triggering`` element in your screen.

![GA setup](./images/ga15-garesult.png)

Currently there's only the default trigger ``All Pages``. Later we'll define new triggers for specific pages. Choose this one by selecting it with your mouse.

![GA setup](./images/ga16-addtriggerA.png)

Your screen will now show a checked box, proceed by clicking ``Add``.

![GA setup](./images/gaadd.png)

![GA setup](./images/ga16-addtriggerB.png)

You are now ready to save the Universal Analytics Tag by clicking ``Save``.

![GA setup](./images/gasave.png)

![GA setup](./images/ga16-addtriggerC.png)

You are now again on the overview page, but here you see that there are two changes to be published in the workflow.
Click ``Submit``.

![GA setup](./images/gasubmit.png)

![GA setup](./images/ga12-gtmoverview.png)

First you see this screen where you can fill in descriptive information about the change you're going to publish. Add a short description and a more describing one.

![GA setup](./images/ga17-publish2.png)

Now click ``Publish``.

![GA setup](./images/gapublish.png)

You're then seeing the versions tab in GTM, showing you the summary of what you just published. This will not be active yet, since we have not yet implemented the GTM tag on the SYTYCD-website. We'll be doing that in a later exercise.

![GA setup](./images/ga-publish3.png)

From here you can click back to the ``Workspace`` tab, where you can add more Tags, Triggers and Variables, which we'll be doing in the next Exercise.

![GA setup](./images/gaworkspace.png)

Next Step: [Exercise 9.3 - Configure GTM Variables](./ex3.md)

[Go Back to Module 9](./README.md)

[Go Back to All Modules](../../README.md)
