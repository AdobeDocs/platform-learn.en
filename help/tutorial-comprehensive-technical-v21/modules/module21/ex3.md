---
title: Data Collection & Real-time Server Side Forwarding - Create and configure a custom webhook
description: Create and configure a custom webhook
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 294e6557-9243-4486-a5d5-e77beb46703c
---
# 21.3 Create and configure a custom webhook

>[!NOTE]
>
>The Adobe Experience Platform Edge mobile extension is currently in BETA. Use of this extension is by invitation only. Please contact your Adobe Customer Success Manager to learn more and get access to the materials for this tutorial.

## 21.3.1 Create your custom webhook

Go to [https://webhook.site/](https://webhook.site/). You'll see something like this:

![demo](./images/webhook1.png)

You'll see your unique URL, which looks like this: https://webhook.site/f02f2c22-44f9-40d8-8188-dc60fd03e3ec.

This website has now created this webhook for you, and you'll be able to configure this webhook in your **[!DNL Launch Server Side property]** to start testing the forwarding of events.

## 21.3.2 Update your Launch Server Side property: Create a Data Element

Go to [https://launch.adobe.com](https://launch.adobe.com).

![Launch SSF](./images/launchhome.png)

In the top left corned, click **Client Side** and in the dropdown menu, click **Server Side**.

![Launch SSF](./images/launchhome1.png)

You'll then see an overview of all available Server Side Launch properties. Click to open the property you created in [exercise 21.1](./ex1.md).

![Launch SSF](./images/webhookssf1.png)

In the left menu, go to **Data Elements**. Click **Create New Data Element**.

![Launch SSF](./images/de1.png)

You'll then see a new data element to configure.

![Launch SSF](./images/de2.png)

Make the following selection:

- As the **Name**, enter **XDM Event**.
- As the **Extension**, select **Core**.
- As the **Data Element Type**, select **Path**.
- As the **Path**, enter **arc.event.xdm**. By entering this path, you'll be filtering out the **XDM** section from the event payload that is sent by the website or mobile app into the Adobe Edge.

You'll now have this. Click **Save**.

![Launch SSF](./images/de3.png)

>[!NOTE]
>
>In the above path, a reference is made to **arc**. **arc** stands for Adobe Resource Context and **arc** always stands for the highest available object that is available in the Server Side context. Enrichments and transformations may be added to that **arc** object using Launch Server Side functions.
>
>In the above path, a reference is made to **event**. **event** stands for a unique event and Launch Server Side will always evaluate every event individually. Sometimes, you may see a reference to **events** in the payload sent by Web SDK Client Side, but in Launch Server Side, every event is evaluated individually.

## 21.3.3 Update your Launch Server Side property: Create a Rule

In the left menu, go to **Rules**. Click **Create New Rule**.

![Launch SSF](./images/rl1.png)

You'll then see a new rule to configure. 

![Launch SSF](./images/rl2.png)

Enter the **Name**: **All Pages**.

For this exercise, you won't need to configure a condition. Instead, you'll setup an action. Click the **+ Add** button under **Actions**.

![Launch SSF](./images/rl3.png)

You'll then see this.

![Launch SSF](./images/rl4.png)

Make the following selection:

- Select the **Extension**: **Adobe Cloud Connector**.
- Select the **Action Type**: **Make Fetch Call**.

That should give you this **Name**: **Adobe Cloud Connector - Make Fetch Call**. You should now see this:

![Launch SSF](./images/rl5.png)

Next, configure the following:

- Change the request protocol from GET to **POST**
- Enter the URL of the custom webhook you created in one of the previous steps on the [https://webhook.site/](https://webhook.site/) website, which looks like this: https://webhook.site/f02f2c22-44f9-40d8-8188-dc60fd03e3ec

You should now have this. Next, go to **Body**.

![Launch SSF](./images/rl6.png)

You'll then see this. Click the Data Element icon as indicated below.

![Launch SSF](./images/rl7.png)

In the popup, select the data element **XDM Event** which you created in the previous step. Click **Select**.

![Launch SSF](./images/rl8.png)

You'll then see this. Click **Keep Changes**.

![Launch SSF](./images/rl9.png)

You'll then see this. Click **Save**.

![Launch SSF](./images/rl10.png)

You've now configured your first rule in a Launch Server Side property. Go to **Publishing Flow** to publish your changes.

![Launch SSF](./images/rl11.png)

Open your Development library **v1** by clicking **Edit** as indicated.

![Launch SSF](./images/rl12.png)

Click the **Add All Changed Resources** button, after which you'll see your Rule and Data Element appear in this library. Next, click **Save & Build for Development**. Your changes are now being deployed.

![Launch SSF](./images/rl13.png)

After a couple of minutes, you'll see that the deployment is done and ready to be tested.

![Launch SSF](./images/rl14.png)

## 21.3.4 Test your configuration

Open a new, clean incognito browser window and go to [https://public.aepdemo.net](https://public.aepdemo.net). 

You'll then see this. 

![Launch Setup](./images/demo1.png)

Enter your Configuration ID and click **Load Configuration**. Your configuration is then loaded.

![Launch Setup](./images/demo2.png)

Scroll down and click **Save Configuration**.

![Launch Setup](./images/demo3.png)

You'll then be redirected to the Admin homepage. Go to **Select LDAP**. Select your LDAP and click **Save**.

![Launch Setup](./images/demo5.png)

You'll then be redirected to the Admin homepage. Go to **Select Brand** and select the brand **Luma**, click **Save**.

![Launch Setup](./images/demo7.png)

You'll then be redirected to the Admin homepage. Click the **Luma** logo.

![Launch Setup](./images/demo8.png)

You'll then see the Luma homepage.

![Launch Setup](./images/demo9.png)

When you open up your browser Developer View, you can inspect Network requests as indicated below. When you use the filter **interact**, you'll see the network requests that are sent by Launch Client Side to the Adobe Edge.

![Launch Setup](./images/hook1.png)

If you select the raw payload, go to [https://jsonformatter.org/json-pretty-print](https://jsonformatter.org/json-pretty-print) and paste the payload. Click **Make Pretty**. You'll then see the JSON payload, the **events** object and the **xdm** object. In one of the previous steps, when you defined the Data Element, you used the reference **arc.event.xdm**, which will result in you parsing out the **xdm** object of this payload.

![Launch Setup](./images/hook2.png)

Switch your view to the website [https://webhook.site/](https://webhook.site/) which you used in one of the previous steps. You should now have a view similar to this one, with network requests being shown in the left menu. You're seeing the **xdm** payload that was filter out of the network request that was shown above. 

![Launch Setup](./images/hook3.png)

Scroll down a bit in the payload to find the page name, which in this case is **Luma Home**.

![Launch Setup](./images/hook4.png)

If you now navigate across the website, you'll see additional network requests becoming available on this custom webhook in real-time.

![Launch Setup](./images/hook5.png)

You've now configured the Server Side Forwarding of Web SDK/XDM payloads to an external custom webhook. In the next exercises, you'll configure a similar approach, and you'll be sending that same data towards Google and Microsoft Azure environments.

Next Step: [21.4 Create and configure a Google Cloud Function](./ex4.md)

[Go Back to Module 21](./aep-data-collection-ssf.md)

[Go Back to All Modules](./../../overview.md)
