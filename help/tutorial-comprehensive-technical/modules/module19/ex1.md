---
title: Adobe Experience Platform and ServiceNow 
description: Adobe Experience Platform and ServiceNow
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: 
---

# 19.1 Setup your ServiceNow developer instance

## 19.1.1 Create your ServiceNow account and instance

Go to [https://developer.servicenow.com/dev.do#!/home](https://developer.servicenow.com/dev.do#!/home) and select **Create an account**. 

![ServiceNow](./images/snow1.png)

You'll then see this. 

![ServiceNow](./images/snow2.png)

Fill out the fields and click **Sign Up**.

![ServiceNow](./images/snow3.png)

You'll then see this. 

![ServiceNow](./images/snow4.png)

Next, check your email for a link to activate your account. Click the link.

![ServiceNow](./images/snow5.png)

You'll then see this. Click **Sign In**.

![ServiceNow](./images/snow6.png)

Enter your email and click **Next**.

![ServiceNow](./images/snow7.png)

Enter your password and click **Next**.

![ServiceNow](./images/snow8.png)

You'll then see this. Scroll down until you reach the end of the document.

![ServiceNow](./images/snow9.png)

Check the checkbox to accept the ServiceNow Developer Agreement and click **Submit**.

![ServiceNow](./images/snow10.png)

You'll then see the developer homepage of ServiceNow. Click **Request an instance** to get your own personal ServiceNow instance.

![ServiceNow](./images/snow11.png)

In the **Choose your release** window, you have to select **Paris**. Click **Request**.

![ServiceNow](./images/snow12.png)

You'll then see this. Click **Close**.

![ServiceNow](./images/snow13.png)

After a couple of seconds/minutes, you'll see this message. You can see that the username for logging in to your ServiceNow developer instance is **admin**, and you'll also see a default password which you'll need in the next step. You'll have to change that default password in the next step.

Click **Open Instance**.

![ServiceNow](./images/snow14.png)

You then first need to change your password. 

![ServiceNow](./images/snow15.png)

Enter the default password from the previous step in the **Current Password**. After entering your new password and confirming it, click **Submit**.

![ServiceNow](./images/snow16.png)

You've now successfully logged in to your ServiceNow instance. 

![ServiceNow](./images/snow17.png)

## 19.1.2 Activate Customer Service Management in ServiceNow

You now need to activate the **Customer Service Management** plugin in ServiceNow.

To install the **Customer Service Management** plugin, type **System Applications** in the **Filter Navigator**. Then, click **All**.

![ServiceNow](./images/csmplugin1.png)

You'll then see this. Search for the plugin **Customer Service Management** and click **Install**.

![ServiceNow](./images/csmplugin2.png)

In the search field, enter **Adobe Experience Platform**. Next, click **Install**.

You'll then see a confirmation window. Click **Activate**.

![ServiceNow](./images/csmplugin3.png)

You'll then see a progress bar. After a couple of minutes, the **Customer Service Management** plugin will be activated and available.

## 19.1.3 Activate ServiceNow IntegrationHub Enterprise Pack Installer

Go back to [https://developer.servicenow.com/dev.do#!/home](https://developer.servicenow.com/dev.do#!/home). In the **Your Instance** panel, click **Manage** and then click **Activate Plugin**.

![ServiceNow](./images/snow18.png)

In the list of available plugins, search and find the plugin named **ServiceNow IntegrationHub Enterprise Pack Installer**. Click **Activate**.

![ServiceNow](./images/snow19.png)

You'll then see this. Close this window and wait until you receive an email to confirm that the **ServiceNow IntegrationHub Enterprise Pack** plugin has been activated. This may take 10 minutes.

![ServiceNow](./images/snow20.png)

Once you've received this email, you can continue with the next exercise.

![ServiceNow](./images/snow21.png)

Next Step: [19.2 Install and configure the integration between ServiceNow and Adobe Experience Platform through Adobe I/O](./ex2.md)

[Go Back to Module 19](./call-center-servicenow.md)

[Go Back to All Modules](./../../overview.md)
