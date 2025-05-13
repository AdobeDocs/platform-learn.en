---
title: Audience Activation to Microsoft Azure Event Hub - Action
description: Audience Activation to Microsoft Azure Event Hub - Action
kt: 5342
doc-type: tutorial
exl-id: bff4d2ee-eaff-4b56-9fa0-4ffc3c368141
---
# 2.4.7 End-to-end scenario

## Start Azure Event Hub trigger

To show the payload send by Adobe Experience Platform Real-time CDP to our Azure Event Hub upon audience qualification, we need to start our simple Azure Event Hub trigger function. This function will simple "dump" the payload to the console in Visual Studio Code. But remember this function can be extended in any way to interface with all sorts of environments using dedicated API's and protocols.

### Launch Visual Studio Code and start project

Make sure to have your Visual Studio Code project opened and running

To start/stop/restart your Azure function in Visual Studio Code, refer to the previous exercise.

Your Visual Studio Code's **Terminal** should mention something similar to this:

```code
[2024-11-20T20:07:12.316Z] Debugger listening on ws://127.0.0.1:9229/86c8e251-8e2f-4c65-a063-cda77edbf2ca
[2024-11-20T20:07:12.318Z] For help, see: https://nodejs.org/en/docs/inspector
[2024-11-20T20:07:12.343Z] Worker process started and initialized.
[2024-11-20T20:07:12.359Z] Debugger attached.

Functions:

        vangeluw-aep-event-hub-trigger: eventHubTrigger

For detailed output, run func with --verbose flag.
[2024-11-20T20:07:18.150Z] Host lock lease acquired by instance ID '000000000000000000000000000C19D8'.
```

## Load your Citi Signal website

Go to [https://dsn.adobe.com](https://dsn.adobe.com). After logging in with your Adobe ID, you'll see this. Click the 3 dots **...** on your website project and then click **Run** to open it.

![DSN](./../../datacollection/dc1.1/images/web8.png)

You'll then see your demo website open up. Select the URL and copy it to your clipboard.

![DSN](../../../getting-started/gettingstarted/images/web3.png)

Open a new incognito browser window.

![DSN](../../../getting-started/gettingstarted/images/web4.png)

Paste the URL of your demo website, which you copied in the previous step. You'll then be asked to login using your Adobe ID.

![DSN](../../../getting-started/gettingstarted/images/web5.png)

Select your account type and complete the login process.

![DSN](../../../getting-started/gettingstarted/images/web6.png)

You'll then see your website loaded in an incognito browser window. For every exercise, you'll need to use a fresh, incognito browser window to load your demo website URL.

![DSN](../../../getting-started/gettingstarted/images/web7.png)

## Qualify for your audience

Navigate to the **Plans** page. This action will qualify you for the `--aepUserLdap-- - Interest in Plans` audience. 

![6-04-luma-telco-nav-sports.png](./images/cs1.png)

To verify, open the Profile Viewer panel. You should now be a member of the `--aepUserLdap-- - Interest in Plans`. If your audience memberships are not yet updated in your Profile Viewer panel, click the reload button.  

![6-05-luma-telco-nav-broadband.png](./images/cs2.png)

Switch back to Visual Studio Code and look at your **TERMINAL** tab, you should see a list of audiences for your specific **ECID**. This activation payload is delivered to your event hub as soon as you qualify for the `--aepUserLdap-- - Interest in Plans` audience. 

![6-06-vsc-activation-realized.png](./images/cs3.png)

When you take a closer look a the audience payload, you can see that `--aepUserLdap-- - Interest in Plans` is in status **realized**. 

```json
{
  "identityMap": {
    "ecid": [
      {
        "id": "36281682065771928820739672071812090802"
      }
    ]
  },
  "segmentMembership": {
    "ups": {
      "94db5aed-b90e-478d-9637-9b0fad5bba11": {
        "createdAt": 1732129904025,
        "lastQualificationTime": "2024-11-21T07:33:52Z",
        "mappingCreatedAt": 1732130611000,
        "mappingUpdatedAt": 1732130611000,
        "name": "vangeluw - Interest in Plans",
        "status": "realized",
        "updatedAt": 1732129904025
      }
    }
  }
}
```

An audience status of **realized** means that your profile is part of the audience, while the **exited** status means that our profile has been removed from the audience.

## Next Steps

Go to [Summary and benefits](./summary.md){target="_blank"}

Go back to [Real-Time CDP: Audience Activation to Microsoft Azure Event Hub](./segment-activation-microsoft-azure-eventhub.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
