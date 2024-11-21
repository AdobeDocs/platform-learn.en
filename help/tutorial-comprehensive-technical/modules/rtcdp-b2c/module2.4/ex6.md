---
title: Audience Activation to Microsoft Azure Event Hub - Define an Azure Function
description: Audience Activation to Microsoft Azure Event Hub - Define an Azure Function
kt: 5342
doc-type: tutorial
---
# 2.4.6 Create your Microsoft Azure Project

## Getting familiar with Azure Event Hub functions

Azure Functions allow you to run small pieces of code (called **functions**) without worrying about application infrastructure. With Azure Functions, the cloud infrastructure provides all the up-to-date servers you need to keep your application running at scale.

A function is **triggered** by a specific type of event. Supported triggers include responding to changes in data, responding to messages (for example Event Hubs), running on a schedule, or as the result of an HTTP request.

Azure Functions is a serverless compute service that lets you run event-triggered code without having to explicitly provision or manage infrastructure. 

Azure Event Hubs integrates with Azure Functions for a serverless architecture.

## Open Visual Studio Code and Logon to Azure

Visual Studio Code makes it easy to...

- define and bind Azure functions to Event Hubs
- test locally 
- deploy to Azure
- remote log function execution

### Open Visual Studio Code

### Logon to Azure

When you logon with your Azure account that you used to register in the previous exercise, Visual Studio Code will let you find and bind all Event Hub resources. 

Open Visual Studio Code and click the **Azure** icon. 

Next select **Sign in to Azure**:

![3-01-vsc-open.png](./images/301vscopen.png)

You will be redirected to you browser to login. Remember to select the Azure account that you used to register.

When you see the following screen in your browser, you are logged in with Visual Code Studio:

![3-03-vsc-login-ok.png](./images/303vscloginok.png)

Return to Visual Code Studio (you will see the name of your Azure subscription, for example **Azure subscription 1**):

![3-04-vsc-logged-in.png](./images/304vscloggedin.png)

## Create an Azure Project

Click **Create Function Project...**:

![3-05-vsc-create-project.png](./images/vsc2.png)

Select or create a local folder of your choice to save the project and click **Select**:

![3-06-vsc-select-folder.png](./images/vsc3.png)

You will now enter the project creation wizard. Click **Javascript** as the language for your project:

![3-07-vsc-select-language.png](./images/vsc4.png)

Then select **Model v4**.

![3-07-vsc-select-language.png](./images/vsc4a.png)

Select **Azure Event Hub trigger** as your project's first function template:

![3-08-vsc-function-template.png](./images/vsc5.png)

Enter a name for your function, use the following format `--aepUserLdap---aep-event-hub-trigger` and press enter:
  
![3-09-vsc-function-name.png](./images/vsc6.png)

Select **Create new local app setting**:

![3-10-vsc-function-local-app-setting.png](./images/vsc7.png)

Click to select the Event Hub Namespace that you created earlier, which is named `--aepUserLdap---aep-enablement`.

![3-11-vsc-function-select-namespace.png](./images/vsc8.png)

Next, click to select the Event Hub that you created earlier, which is named `--aepUserLdap---aep-enablement-event-hub`.

![3-12-vsc-function-select-eventhub.png](./images/vsc9.png)

Click to select **RootManageSharedAccessKey** as your Event Hub policy:

![3-13-vsc-function-select-eventhub-policy.png](./images/vsc10.png)

Select **Add to workspace** on how to open your project:

![3-15-vsc-project-add-to-workspace.png](./images/vsc12.png)

You may then get a message like this one. In that case, click **Yes, I trust the authors**.

![3-15-vsc-project-add-to-workspace.png](./images/vsc12a.png)

After you project is created, open the file `--aepUserLdap---aep-event-hub-trigger.js` in the editor:

![3-16-vsc-open-index-js.png](./images/vsc13.png)

The payload sent by Adobe Experience Platform to your Event Hub will look like this:

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

Update the code in your Visual Studio Code's `--aepUserLdap---aep-event-hub-trigger.js` with the code below. This code will be executed each time Real-time CDP sends audience qualifications to your Event Hub destination. In this example, the code is just about displaying incoming payload, but you can imagine any kind of additional function to process audience qualifications in real-time and use thel further down your data pipeline ecosystem.

Line 11 in your file `--aepUserLdap---aep-event-hub-trigger.js` currently shows this:

```javascript
context.log('Event hub message:', message);
```

Change line 11 in `--aepUserLdap---aep-event-hub-trigger.js` to look like this:

```javascript
context.log('Event hub message:', JSON.stringify(message));
```

The total payload should then be like this:

```javascript
const { app } = require('@azure/functions');

app.eventHub('--aepUserLdap---aep-event-hub-trigger', {
    connection: '--aepUserLdap--aepenablement_RootManageSharedAccessKey_EVENTHUB',
    eventHubName: '--aepUserLdap---aep-enablement-event-hub',
    cardinality: 'many',
    handler: (messages, context) => {
        if (Array.isArray(messages)) {
            context.log(`Event hub function processed ${messages.length} messages`);
            for (const message of messages) {
                context.log('Event hub message:', message);
            }
        } else {
            context.log('Event hub function processed message:', messages);
        }
    }
});
```


The result should look like this:

![3-16b-vsc-edit-index-js.png](./images/vsc1.png)

## Run Azure Project

Now it is time to run your project. At this stage we will not deploy the project to Azure. We will run it locally in debug mode. Select the Run icon, click the green arrow. 

![3-17-vsc-run-project.png](./images/vsc14.png)

The first time you run you project in debug mode, you will need to attach a Azure storage account, click **Select storage account**.

![3-17-vsc-run-project.png](./images/vsc14a.png)

and then select the storage account that you created earlier, which is named `--aepUserLdap--aepstorage`.

![3-17-vsc-run-project.png](./images/vsc14b.png)

Your project is now up and running and is listing for events in the Event Hub. In the next exercise you'll demonstrate behavior on the CitiSignal demo website that will qualify you for audiences. As a result you will receive a audience qualification payload in the terminal of your Event Hub trigger function.

![3-24-vsc-application-stop.png](./images/vsc18.png)

## Stop Azure Project

To stop your project, go to the lenu **CALL STACK** in VSC, click on the arrow on your running project and then click **Stop**.

![3-24-vsc-application-stop.png](./images/vsc17.png)

Next Step: [2.4.7 End-to-end scenario](./ex7.md)

[Go Back to Module 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Go Back to All Modules](./../../../overview.md)
