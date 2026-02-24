---
title: Monitor Events in Slack
description: Learn how to receive Experience Platform notifications in Slack by integrating with an Adobe App Builder webhook proxy.
feature: Monitoring
role: Developer, Admin
level: Intermediate
duration: 519
last-substantial-update: 2026-02-24
jira: KT-20339
---

# Monitor Experience Platform events in Slack

Learn how to receive Experience Platform notifications in Slack by integrating with an Adobe App Builder webhook proxy. Data engineers and administrators may want to receive proactive notifications in Slack from Adobe Experience Platform to monitor the health of their Platform implementations. This tutorial outlines the architecture and implementation steps to connect Adobe I/O Events to Slack using Adobe App Builder.


>[!VIDEO](https://video.tv.adobe.com/v/3480183?learn=on)

## Why a webhook proxy?

Directly connecting Adobe I/O Events to a Slack Incoming Webhook is not possible due to a protocol mismatch in the verification process.

* **The Challenge**: When you register a webhook with Adobe I/O Events, Adobe sends a "Challenge" request (either a `GET` or `POST`) to your endpoint. Your endpoint must successfully process this challenge and return the specific value to confirm ownership.

* **The Limitation**: Slack's Incoming Webhooks are designed only to ingest JSON payloads for messaging. They do not have logic to recognize or respond to Adobe's verification challenge handshake.

* **The Solution**: Deploy an intermediary webhook proxy using Adobe App Builder. This proxy sits between Adobe and Slack to:
    1. Intercept the request from Adobe and respond to the verification challenge.
    1. Format the payload into a Slack-compatible message and forward it to Slack.

* **Delivery method**: Runtime Actions.  Runtime actions come packaged with Adobe App Builder. When using a Runtime Action (non-web action) as the event handler, Adobe I/O Events automatically handles signature verification and challenge responses. Runtime actions are the recommended approach as it requires less code and provides built-in security.

## Architecture overview

### What is Adobe Developer Console?

Adobe Developer Console is the central portal for managing your Adobe projects, APIs, and credentials. It is where you create your project, configure authentication, and register your webhooks.

### What is App Builder?

Adobe App Builder is a complete framework that enables enterprise developers to build cloud-native applications.

* **Provisioning**: App Builder is not enabled by default; it must be provisioned for your organization as a feature. Ensure that your organization has the **[!DNL App Builder]** entitlement.

* **Project Template**: App Builder projects are created specifically using the **[!UICONTROL App Builder]** template in the [!DNL Developer Console] ([!UICONTROL Project from Template] > [!UICONTROL App Builder]). The template automatically sets up the necessary workspaces and runtime environments.

* **App Builder Getting Started Guide**: Refer to the documentation [to provision and create your first project from the template](https://developer.adobe.com/app-builder/docs/get_started/app_builder_get_started/first-app){target=_blank}.

### What is Adobe I/O Runtime?

Adobe I/O Runtime is the serverless platform that powers App Builder. It allows developers to deploy code (Functions-as-a-Service) that runs in response to HTTP requests without managing server infrastructure.

In this implementation, we use an **Action**. An Action is a stateless function (written in Node.js) that runs on the Adobe I/O Runtime. Our Action serves as the public HTTP endpoint that Adobe I/O Events talk to.

For more information, see the [Adobe I/O Runtime documentation](https://developer.adobe.com/runtime/){target=_blank}.

## Implementation guide

### Prerequisites

Before starting, ensure you have the following:

* **Adobe Developer Console Access**: You must have access to a System Admin or [Developer role](../admin/add-developers.md) within an organization that has App Builder enabled.

    >[!TIP]
    > To verify App Builder provisioning, log into [Adobe Developer Console](https://developer.adobe.com/console/){target=_blank}, make sure you are in the desired organization, select **[!UICONTROL Create project from template]**, and verify that the App Builder template is available. If it is not, please review the App Builder FAQ section "[How to get App Builder](https://developer.adobe.com/app-builder/docs/intro_and_overview/faq#how-to-get-app-builder){target=_blank}"


* **Node.js & npm**: This project requires Node.js, which includes NPM (Node Package Manager). NPM is used to install the Adobe CLI and manage project dependencies.

    * [Download Node.js (LTS version recommended)](https://nodejs.org/){target=_blank}
    * [npm Getting Started Guide](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm){target=_blank} - A guide on how to verify your installation.

* **`aio CLI`**: Installed via your terminal: `npm install -g @adobe/aio-cli`
* **Slack App Configuration**: You need a Slack App set up in your workspace with an **Incoming Webhook** activated.

    * [Create a Slack App](https://api.slack.com/apps){target=_blank}
    * [Slack Incoming Webhooks Guide](https://docs.slack.dev/messaging/sending-messages-using-incoming-webhooks/){target=_blank} - Follow this guide to create your app and generate the Webhook URL (starts with `https://hooks.slack.com/`...).

### Step 1: Create a project in Adobe Developer Console

First, create a project with the App Builder template in Adobe Developer Console:

1. Log into [Adobe Developer Console](https://developer.adobe.com/console)
1. Select **[!UICONTROL Create project from template]**
1. Select the App Builder template
1. Enter a Project Title, for example `Slack webhook integration`
1. Select **[!UICONTROL Save]**

### Initialize the runtime environment

Run the following commands in your terminal to create the project structure:

#### Log into `aio`

```
aio login
```

#### Step 2: Initialize a new App Builder project

```
aio app init slack-webhook-proxy
```
 
1. Select your Organization and press **Enter**
1. Select the Project that you created in the previous step (for example, `Slack webhook integration`) and press **Enter**
1. Select the **[!UICONTROL Only Templates Supported By My Org]** option
1. Skip the sample section by pressing **Enter**
1. When prompted, make sure that the following components are selected (circle should be filled in) and press **Enter**:
    1. **[!UICONTROL Actions: Deploy Runtime actions]**
    1. **[!UICONTROL Events: Publish to Adobe I/O Events]**
    1. **[!UICONTROL Web Assets: Deploy to hosted static assets]**
1. With your 'Up' and 'Down' arrows, navigate the incoming list and choose **[!UICONTROL Adobe Experience Platform: Realtime Customer Profile]** and press **Enter**
1. **[!UICONTROL Generic]** actions are generated automatically
1. Choose the **[!UICONTROL Pure HTML/JS]** for the UI and press **Enter**
1. Keep **[!UICONTROL generic]** as the sample action to showcase how to access an external API name and press **Enter**
1. Keep the **[!UICONTROL publish-events]** as the sample action name to create messages in cloud events format and press **Enter**

Your app initialization should complete.
 
#### Navigate to the project directory

```
cd slack-webhook-proxy
```

#### Add the web action

```
aio app add action
```

1. Choose **[!UICONTROL Only Templates Supported By My Org]** and press **Enter**
2. See the **[!UICONTROL publish-events]** action in the table that is presented; press **Space** to select the action. If the circle next to the name is filled as shown in the video tutorial, press **Enter**
3. Name the action `webhook-proxy`

### Step 3: Update the proxy action code

In an IDE or text editor, create/modify the file `actions/webhook-proxy/index.js` with the following code. This implementation forwards events to Slack. Signature verification and challenge handling are automatic when using Runtime Action registration.

```javascript

const fetch = require("node-fetch");
const { Core } = require("@adobe/aio-sdk");
 
/**
 * Adobe I/O Events to Slack Runtime Proxy
 *
 * Receives events from Adobe I/O Events and forwards them to Slack.
 * Signature verification and challenge handling are automatic when
 * using Runtime Action registration (non-web action).
 */
async function main(params) {
  const logger = Core.Logger("webhook-proxy", { level: params.LOG_LEVEL || "info" });
 
  try {
    logger.info(`Event received: ${JSON.stringify(params)}`);
 
    // Forward to Slack
    return forwardToSlack(params, params.SLACK_WEBHOOK_URL, logger);
 
  } catch (error) {
    logger.error(`Error: ${error.message}`);
    return { statusCode: 500, body: { error: "Internal server error" } };
  }
}
 
/**
 * Forwards the event payload to Slack
 */
async function forwardToSlack(payload, webhookUrl, logger) {
  if (!webhookUrl) {
    logger.error("SLACK_WEBHOOK_URL not configured");
    return { statusCode: 500, body: { error: "Server configuration error" } };
  }
 
  // Extract Adobe headers passed to runtime action
  const headers = {
    "x-adobe-event-code": payload["x-adobe-event-code"],
    "x-adobe-event-id": payload["x-adobe-event-id"],
    "x-adobe-provider": payload["x-adobe-provider"]
  };
 
  const slackMessage = buildSlackMessage(payload, headers);
 
  const response = await fetch(webhookUrl, {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify(slackMessage)
  });
 
  if (!response.ok) {
    const errorText = await response.text();
    logger.error(`Slack API error: ${response.status} - ${errorText}`);
    return { statusCode: response.status, body: { error: errorText } };
  }
 
  logger.info("Event forwarded to Slack");
  return { statusCode: 200, body: { success: true } };
}
 
/**
 * Builds a Slack Block Kit message from the event payload
 */
function buildSlackMessage(payload, headers) {
  // Adobe passes event code as x-adobe-event-code header (available in params for runtime actions)
  const eventType = headers["x-adobe-event-code"] ||
                    payload["x-adobe-event-code"] ||
                    payload.event_code ||
                    payload.type ||
                    payload.event_type ||
                    "Adobe Event";
  const eventId = headers["x-adobe-event-id"] || payload["x-adobe-event-id"] || payload.event_id || payload.id || "N/A";
  const eventData = payload.data || payload.event || payload;
 
  return {
    blocks: [
      {
        type: "header",
        text: { type: "plain_text", text: `Event: ${eventType}`, emoji: true }
      },
      {
        type: "section",
        fields: formatDataFields(eventData)
      },
      { type: "divider" },
      {
        type: "context",
        elements: [{
          type: "mrkdwn",
          text: `*Event ID:* ${eventId}  |  *Time:* ${new Date().toISOString()}`
        }]
      }
    ]
  };
}
 
/**
 * Formats event data as Slack mrkdwn fields
 */
function formatDataFields(data, maxFields = 10) {
  if (typeof data !== "object" || data === null) {
    return [{ type: "mrkdwn", text: `*Payload:*\n${String(data)}` }];
  }
 
  const entries = Object.entries(data);
  if (entries.length === 0) {
    return [{ type: "mrkdwn", text: "_No data provided_" }];
  }
 
  return entries.slice(0, maxFields).map(([key, value]) => ({
    type: "mrkdwn",
    text: `*${key}:*\n${typeof value === "object" ? `\`\`\`${JSON.stringify(value)}\`\`\`` : value}`
  }));
}
 
exports.main = main;
```

### Step 4: Configure the action

The action configuration in `app.config.yaml` is critical. Use web: no to create a non-web action that can be registered as a Runtime Action in the Developer Console.

```yaml
application:
  runtimeManifest:
    packages:
      slack-webhook-proxy:
        license: Apache-2.0
        actions:
          webhook-proxy:
            function: actions/webhook-proxy/index.js
            web: no
            runtime: nodejs:22
            inputs:
              LOG_LEVEL: info
              SLACK_WEBHOOK_URL: $SLACK_WEBHOOK_URL
            annotations:
              require-adobe-auth: false
              final: true
```

#### Why `web: no?`

When you use a non-web action and register it via the "Runtime Action" option in the Developer Console, Adobe I/O Events automatically:

* Handles challenge verification (both `GET` and `POST`)
* Verifies digital signatures before invoking your action
* Chains a signature validator action in front of your action

This means that your code only needs to handle the business logic (forwarding to Slack).

### Step 4: Update the environment variables

To securely manage credentials, we use environment variables. Create/modify the `.env` file in the root of your project to add your Slack webhook URL. Be sure to show hidden files on your system if you don't see the `.env` file:

```
# ... other .env file content ...
 
SLACK_WEBHOOK_URL=https://hooks.slack.com/services/YOUR/WEBHOOK/URL
```

### Step 5: Deploy the action

Once the environment variables are set, deploy the action. Make sure to be in the root of your project, namely `slack-webhook-proxy`, when running this command in the terminal.

```
aio app deploy
```

Your action is deployed to Adobe I/O Runtime and is available in the Developer Console for registration.

### Step 6: Register the action in Adobe Developer Console

Now that your action is deployed, register it as the destination for Adobe Events.

1. Navigate to the [Adobe Developer Console](https://developer.adobe.com/console){target=_blank} and open your App Builder project.
1. Choose your **[!UICONTROL Workspace]**
1. Select **[!UICONTROL Add Service]** and select **[!UICONTROL Event]**.
1. Select **[!UICONTROL Adobe Experience Platform]** as the product.
1. Select **[!UICONTROL Platform Notifications]** as the type of events.
1. Select the specific events (or all) you would like to be notified of in Slack and select **[!UICONTROL Next]**.
1. Select or [create your OAuth credential](https://experienceleague.adobe.com/en/docs/platform-learn/tutorials/api/platform-api-authentication){target=_blank}.
1. Configure **[!UICONTROL Event registration details]**:
    1. **[!UICONTROL Registration Name]**: Give your registration a descriptive name.
    1. **[!UICONTROL Registration Description]**: Make sure this is explicit so that other contributors can be aware of what it does.
    1. Select **[!UICONTROL Next]**
    1. **[!UICONTROL Delivery Method]**: Select **[!UICONTROL Runtime Action]** (not "Webhook").
    1. **[!UICONTROL Runtime Action]**: Choose `webhook-proxy` from the dropdown (refresh the page if you don't see it).
1. Select **[!UICONTROL Save Configured Events]**.


### Step 7: Validate with a sample event

You can test the entire flow end-to-end by clicking the 'Send sample event' icon next to any configured event.

The sample event is sent on the channel that you have configured when making your Slack app and creating the webhook; You should see something similar to the following:

![Example of a monitoring event in Slack](../assets/slack-monitor.png)

Congratulations, you have successfully integrated Slack with Experience Platform events!

### Common Issues

Here are some issues that you may run into when configuring the proxy and some potential ways to address them.

* **Unable to see IMS orgs**: If you don't see your list of IMS orgs when running `aio app init` try the following. Run `aio logout` in your Terminal, log out of Experience Cloud on your default web browser, and run  `aio login` again.
* **Action not appearing in dropdown**: Ensure `web: no` is set in `app.config.yaml`. Only non-web actions appear in the Runtime Action dropdown. Refresh the Developer Console page after deploying.
* **Signature verification failed**: If you see this in the activation logs, it means that Adobe's built-in validator rejected the request. This shouldn't happen for legitimate Adobe events. Check that the event registration is correctly configured.
* **Slack not receiving messages**: Check that `SLACK_WEBHOOK_URL` is correctly set in your `.env` file and that the Slack app has the Incoming Webhook enabled.
* **Action timeout**: Runtime actions have a 60-second timeout. If your action takes longer, consider using the journaling approach instead.