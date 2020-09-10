---
title: Segment Activation to Microsoft Azure Event Hub - Action
description: Segment Activation to Microsoft Azure Event Hub - Action
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: 
---

# Exercise 18.6: Action

## Objectives

- Activate "Luma Telco Sports Fan" to our Azure Event Hub RT-CDP destination 

## Exercise 18.6.1 - Start Azure Event Hub trigger

To show the payload send by Adobe Experience Platform Real-time CDP to our Azure Event Hub upon segment qualification, we need to start our simple Azure Event Hub trigger function. This function will simple "dump" the payload to the console in Visual Studio Code. Buttt remember this function can be extended in any way to interface with all sorts of environments using dedicated API's and protocols.

### Launch Visual Studio Code and start project

Refer to [Exercise 3 - Create Azure Project](exercises/3-create-azure-project.md) to start Visual Code Studio, logon to Azure and start your function:

* Exercise 18.3.2 - Open Visual Studio Code and Logon to Azure
* Exercise 18.3.4 - Run Azure Project

To stop/restart your Azure function in Visual Studio Code:

* Exercise 18.3.5 - Stop Azure Project
* Exercise 18.3.4 - Run Azure Project

Your Visual Studio Code's "Terminal" should mention:

```code
Hosting environment: Production
Content root path: /Users/mmeewis/Projects/adobe.node/azure.function/event-hub-enablement
Now listening on: http://0.0.0.0:7071
Application started. Press Ctrl+C to shut down.
[22/06/2020 12:55:03] Host lock lease acquired by instance ID '0000000000000000000000006A61AFA2'.
[22/06/2020 12:55:03] Debugger attached.
```

![6-01-vsc-ready.png](../resources/6-01-vsc-ready.png)

## Exercise 18.6.2 - Start Luma Telco

Navigate to https://public.aepdemo.net/, select your &lt;ldap&gt; (1), select "Luma Telco" (2) as your brand and launch (3) Luma Telco:

![6-02-start-luma-telco.png](../resources/6-02-start-luma-telco.png)

When you open **Adobe Experience Platform X-RAY** you should be anonymous (you only have an ECID identity) and you should be member of only one segment **Homepage Visitors**:

![6-03-start-luma-telco-xray.png](../resources/6-03-start-luma-telco-xray.png)

Switch back to Visual Studio Code and look at your 'TERMINAL' tab, nothing changed. This is normal because our destination will only trigger when your profile will qualify for **Luma Telco Sports Fan**.

![6-03b-visual-studio-code.png](../resources/6-03b-visual-studio-code.png)


## Exercise 18.6.3 - Let's qualify for Luma Telco Sports Fan

Navigate (1) to the **Sports** page once, and do not reload/refresh it. This action should qualify us for **Luma Telco Sports Fan**. 

![6-04-luma-telco-nav-sports.png]

To verify let's open another page to make sure that the X-Ray panel refreshes. If we would reload the **Sports** page to refresh the X-Ray panel, the segment qualification status would change and that is not what we want at this moment.  but 

Instead open 'BROADBAND DEALS' and open the X-Ray panel, you should now be a member of both the **Luma Telco Sports Fan**  and the **Homepage Visitor** segments. If you segment memberships are not yet updated in your X-Ray panel, reload the page.  

![6-05-luma-telco-nav-broadband.png](../resources/6-05-luma-telco-nav-broadband.png)

Switch back to Visual Studio Code and look at your 'TERMINAL' tab, you should see a list of segments for your specific **ECID**. This activation payload is delivered to your event hub as soon as you qualify for the **Luma Telco Sports Fan** streaming segment. Note that the segment name in the payload has been added by our Azure function because Adobe Experience Platform Real-time CDP only includes the segmentId.

When you take a closer look a the segment payload, you can see that **Homepage Visitor** is in status **existing** and **Luma Telco Sports Fan** is in status **realized**. 

A segment status of **realized** means that our profile is entering the segment. While the **existing** status means that our profile continues to be in the segment.

Although this is our first activation, **Homepage Visitors** already is in status **existing**. The reason is that **Luma Telco Sports Fan** is triggering the activation because we are entering the segment. When a segment triggers an  activation, all segments for which our profile qualifies are included into the activation payload. The segments for which we already qualified before are listed with a status **existing** because our profile continues to be in the segment.

![6-06-vsc-activation-realized.png](../resources/6-06-vsc-activation-realized.png)

## Exercise 18.6.4 - Let's visit the Sports page for a second time

From the **Broadband deals** page navigate back to the **Sports** page.

![6-07-back-to-sports.png](../resources/6-07-back-to-sports.png)

And Switch back to Visual Studio Code and verify your 'TERMINAL' tab. You will see that we still have our two segments, but now in status **existing** which means that our profile continues to be in the segment.

![6-08-vsc-activation-existing.png](../resources/6-08-vsc-activation-existing.png)

## Exercise 18.6.5 - Let's visit the Home page for a third time

If you would revisit the **Sports** page for a third time, no activation will take place, because there is no state change from a segment point of view. 

Segment activations only happen when the segment's status changes:

![6-09-segment-state-change.png](../resources/6-09-segment-state-change.png)

## Exercise 18.6.6 - Activation payload for a known profile

In the previous exercises we did activations for anonymous profiles, as a result only the **ECID** was included as part of teh identity map in the activation payload delivered to our azure event hub function. In this last exercise we will take a look at the activation paylaod for an known profile.

Close you browser and open Luma Telco again in an incognito window.

Navigate to **Login/Register** and create a profile:

![6-10-create-profile.png](../resources/6-10-create-profile.png)

Navigate to the **Sports** page, this will make your known profile qualify for **Luma Telco Sports Fan**. After the page loaded, navigate to the home page and open X-Ray to validate your segment qualifications:

![6-11-check-segment-qualif.png](../resources/6-11-check-segment-qualif.png)

If you see the qualifications, switch to Visual Studio Code and look at your 'TERMINAL' tab. The output of the azure function will include the segments and a full identity map of your profile. These identities can be used by teh azure function to link the segments to customer in a thrird party application using that application's customer identifier:

![6-12-profile-identities.png](../resources/6-12-profile-identities.png)

Payload detail:

```json
[{
	"segmentMembership": {
		"ups": {
			"ca114007-4122-4ef6-a730-4d98e56dce45": {
				"lastQualificationTime": "2020-08-31T15:25:40Z",
				"status": "existing",
				"segmentName": "all - Homepage Visitors"
			},
			"39f0feef-a8f2-48c6-8ebe-3293bc49aaef": {
				"lastQualificationTime": "2020-08-31T15:25:36Z",
				"status": "realized",
				"segmentName": "mmeewis - Luma Telco Sports Fan"
			}
		}
	},
	"identityMap": {
		"ecid": [{
			"id": "34053798168136392521859077594127725521"
		}],
		"email_lc_sha256": [{
			"id": "81dcaeb579a699d7a5f8a59b921b8c7901365193bc55ef38f2770208ff940626"
		}],
		"mobilenr": [{
			"id": "+32476892710-31082020-1"
		}],
		"email": [{
			"id": "mmeewis+marc-31082020-1@adobetest.com"
		}]
	}
}]
```

Next Step: [Exercise 7 - Key take-aways!](./summary.md)

[Go Back to Module 18](./segment-activation-microsoft-azure-eventhub.md)

[Go Back to All Modules](./../../overview.md)