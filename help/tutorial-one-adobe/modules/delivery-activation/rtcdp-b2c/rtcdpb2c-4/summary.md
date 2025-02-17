---
title: Audience Activation to Microsoft Azure Event Hub - Summary & benefits
description: Audience Activation to Microsoft Azure Event Hub - Summary & benefits
kt: 5342
doc-type: tutorial
---
# Summary & benefits

Congratulations and thank you for investing your time in learning about Microsoft Azure Event Hub and Adobe Experience Platform! 
In this module, you learnt how to set up an Azure Event Hub instance and how to connect that to Adobe Experience Platform.

## Benefits

Let's highlight the benefits of integrating Adobe Experience Platform with Microsoft Azure Event Hub:

- Microsoft Azure Event Hubs as an Adobe Experience Platform Destination lets you capture audience qualification in realtime and process them using an Azure Event Hub function. With such an Azure Event Hub function you can build any kind of custom audience activation handler and as such integrate any kind of third party destination.

- Although destinations are triggered only by specified audiences, the activation payload will include all audiences for which given profile qualifies.

- An audience only triggers an activation when its status changes. For example a profile that qualifies four times for a audience in a period of three months, only the first two will be activated. The first one is a status change from to **realized**, the second one is triggered by a status change from **realized** to **existing**.

- When activating audiences for known profiles, a full identity map is included into the activation payload. Your Azure function can use any of the available identities to map the audiences to a profile managed in a third party application, while using the application's customer identifier.

- In this module, the event hub function was deployed locally (debug mode in Visual Studio Code), offering you lots of troubleshooting and debug options.

## Check this out

- N/A

## Next Steps

Go back to [Real-Time CDP: Audience Activation to Microsoft Azure Event Hub](./segment-activation-microsoft-azure-eventhub.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}