---
title: Project Firefly and Adobe Experience Platform
description: Connect EXP News data collection to your EXP News real-time dashboard
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
---

# 22.4 Connect EXP News data collection to your EXP News real-time dashboard

## Objectives

- Understand how to connect our Project Firefly EXP News Realtime dashboard app to real-time streaming information, from the EXP News website, using Adobe Launch Server Side Forwarding.

## Prerequisites

Before you start this exercise, ensure you have installed and setup NodeJS and Adobe I/O CLI on your machine. See [Exercise 22.1 - Setting up your environment](./ex1.md) for details.

## 22.4.1 Discover the Project Firefly app webhook

We need to figure out the webhook we can connect streaming events from the EXP News website to our dashboard app. Actually, you should already have spotted it as output of your `aio app deploy` from exercise 22.3.2. You can copy it straight from here; it is the first line in the list of **Your deployed action**; the one ending with **webhook**. ![Deploy](images/deploy.png) E.g. `https://133309-rmaurexpnews-development.adobeio-static.net/api/v1/web/poc-platform-realtime-0.0.1/webhook`. Copy the URL for **webhook** and save it somewhere so you can use it later.

## 22.4.2 Set up Adobe Launch Server Side Forwarding

We will now set up the server side forwarding for our Project Firefly EXP News Firefly dashboard app using the webhook we discovered in the previous exercise.

Go to [https://launch.adobe.com](https://launch.adobe.com). Ensure you are in the correct organization. at the right top: `--envName--`. 

![Launch SSF](./images/launchhome.png)

In the top left corner, click **Client Side** and in the dropdown menu, select **Server Side**. You will see an overview  of the server side properties. 

![Launch SSF](./images/launchhomeserverside.png) 

Search for your server side property you created as part of Module 21 (e.g. **rmaur - Demo System (21/01/2021) (Edge)**) and click to open it.

Click on **Data Elements** in the left rail, and then click on **Add Data Element** to add a new data element. In the data element definition screen provide the following information:
   
- **Name**: `brandName`
- **Extension**: select `Core` from the list.
- **Data Element Type**: select `Path` from the list.
- **Path (required)**: `arc.event.xdm.--aepTenantId--.demoEnvironment.brandName`

![Launch SSF data element](./images/launchssfdataelement.png)

Click on **Save** to save the data element.

Click on **Rules** in the left rail. You will see an overview of the rules created for this property, with the **All Pages** rule from Exercise 21 listed. 

![Launch Rules](images/rule1.png)

Click on **Add Rule**. 

In the **Create Rule** screen:

Provide a **Name**, e.g. `All Pages EXP News`. 

![Launch Rule Name](images/launchrulename.png)

Click on **Add** below **CONDITIONS**. In the **Condition Configuration** screen and provide the following information:

- **Logic Type**: select `Regular`
- **Extension**: select `Core`
- **Condition** Type: select `Value Comparison`
- **Name**: `Core - Value Comparison`
- **Left Operand (required)**: select `brandName` from the dialog that shows up by clicking on the three cylinder icon. The field is populated with `{{brandName}}`.
- **Operator**: select `Equals`
- **Right Operand**: type `EXP News`.
      
![Launch SSF Rule](./images/rule2.png)

Click on **Keep Changes** to return to the **Create Rule** screen.
  
Click on **Add** below **ACTIONS**. In the **Action Configuration** screen provide the following information on the left panel.

- **Extension**: select `Adobe Cloud Connector`
- **Action Type**: select `Make Fetch Call`
- **Name**: `Adobe Cloud Connector - Make Fetch Call`
- **Method (required)**: select `POST`
- **URL (required)**: paste here the webhook you copied and saved from exercise 22.4.1, e.g. `https://133309-rmaurexpnews-development.adobeio-static.net/api/v1/web/poc-platform-realtime-0.0.1/webhook`
      
![Launch SSF Rule 3](images/rules3a.png)
  
Click on **Body** tab

- Ensure **Raw** is selected as **Body Format**
- select **XDM Event** from the dialog that shows up when clicking the three cylinder icon behind the field below **Body (Raw)**. This will insert `{{XDM Event}}`.

![Launch SSF Rule 3b](images/rule3b.png) 
  
Click on **Keep Changes**. Your screen should look like
  
![Launch SSF Rule 4](images/rule4.png)
  
Click on **Save** to save the rule.

Click on **Publishing Flow** on the left to deploy the changes in your Launch Server Side configuration.

![Launch SSF Rule 5](images/publishing.png)

Click on **...** right from **v1** in your **Development** column. ![Launch SSF Rule 5](images/pubedit.png) 

Click on **Edit**.

In the **Edit Library** screen 

![Launch SSF Rule 6](images/resourcechanges.png) 

click on **Add All Changed Resources**. You will see an overview of the latest changes. 

![Launch SSF Rule 7](images/changedresources.png)

Click on **Save & Build for Development**. After a while you will return to the previous screen. Wait until the circle before **v1** stops spinning and turns solid green. Your updated server side forwarding rules for EXP News pages are now deployed. ![Launch SSF Rule 7](images/rulesdeployed.png)

## 22.4.3 Demonstrate the EXP News Real-time dashboard

We will now demonstrate how interactions in the EXP News website will be updated in real time in our EXP News dashboard app.

To do this:

Go to https://public.aepdemo.net.

Enter your configuration ID and click **Load Configuration**.

At the bottom of the page, click **Save Configuration**

Click on **Select LDAP** and pick your LDAP name from the list. Click **Save**. ![LDAP](images/ldap.png)

Click on **Select Brand** and select `EXP News (Demo brand for mediaent)` from the list. 

Click on **Save**. 

![Brand](images/brand.png)

From the **Environment Status** screen 

![Status](images/status.png) 

Click on the EXP News logo. This will take you to the EXP News website.!

![EXP News](images/expnews.png) 

On the EXP News website, click around to read articles and look at videos.

Return to your EXP News Real-time Dashboard Firefly app; it should refresh your interactions with the EXP News site in real time. 

![Realtime](images/realtime.png)

Have fun further exploring this. If you are more of a developer and adventurous and do have spare time, explore the source code of the dashboard app and make changes as you see fit.

You have now finished this exercise and this  module.

Next Step: [Summary and benefits](./summary.md)

[Go Back to Module 22](./adobe-io-firefly.md)

[Go Back to All Modules](../../overview.md)