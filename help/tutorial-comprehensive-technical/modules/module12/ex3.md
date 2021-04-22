---
title: Journey Orchestration - External Weather API, SMS Action & more - Define Custom Actions
description: Journey Orchestration - External Weather API, SMS Action & more - Define Custom Actions
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 8652b8a7-8304-41fb-a3ff-26113b29affc
---
# 12.3 Define Custom Actions

In this exercise, you'll create two custom Actions by making use of Journey Orchestration in combination with Adobe Experience Platform.

Go to [https://experience.adobe.com/](https://experience.adobe.com/)

You'll see the **Adobe Experience Cloud** homepage.

![Demo](./images/aec.png)

Click on **Journey Orchestration**.

![Demo](./images/aecjo.png)

Next, you'll see the **Journey Orchestration** homepage.

![Demo](./images/aecjoh.png)

In the menu, click on **Actions**.

![Demo](./images/menuactions.png)

You'll then see the **Actions** list.

![Demo](./images/acthome.png)

You'll define two actions:

* One action that sends an SMS using an external application, Twilio
* One action that sends a text to a Slack channel

## Action: Send SMS using Twilio

Twilio is a 3rd party provider of SMS Messages. It has an easy-to-use API and we'll use Journey Orchestration to trigger their API.

![Demo](./images/twilio.png)

Click **Add** to start adding your action.

![Demo](./images/add.png)

You'll see an empty Action popup.

![Demo](./images/emptyact.png)

As a Name for the Action, use `smsTwilioLdap` and replace `Ldap` with your LDAP. In this example, the Action Name is `smsTwilioVangeluw`.

Set Description to: `Send SMS using Twilio`.

![Demo](./images/twilioname.png)

For the **URL Configuration**, use this:

* URL: `https://l1uikl5kog.execute-api.us-west-2.amazonaws.com/prod/`
* Method: **POST**

You don't need to change the Header Fields.

![Demo](./images/twiliourl.png)

(For transparency, we're using an AWS API Gateway and AWS Lambda function that sits behind the above URL to handle the authentication and sending of SMSs to Twilio.)

**Authentication** should be set to **No Authentication**.

![Demo](./images/twilioauth.png)

For the **Message Parameters**, you need to define which fields should be sent towards Twilio. Logically, we want Journey Orchestration and Adobe Experience Platform to be the brain of personalization, so the SMS Message Text and the Mobile Number to send the SMS towards should be defined by Journey Orchestration and then sent to Twilio for execution.

So for the **Message Parameters**, click the **Edit Payload** icon.

![Demo](./images/twiliomsgp.png)

You'll then see an empty popup-window.

![Demo](./images/twiliomsgpopup.png)

Copy the below text and paste it in the empty popup-window.

```json
{
 "body": {
  "textMessage": {
   "toBeMapped": true,
   "dataType": "string",
   "label": "textMessage"
  },
  "to": {
   "toBeMapped": true,
   "dataType": "string",
   "label": "mobileNr"
  }
 }
}
```

FYI: by specifying the below fields, these fields will become accessible from your Customer Journey and you'll be able to populate them dynamically from the Journey:

**"toBeMapped": true,**

**"dataType": "string",**

**"label": "textMessage"**

You'll then see this:

![Demo](./images/twiliomsgpopup1.png)

Click **Save**.

![Demo](./images/twiliomsgpopup2.png)

Scroll up and click **Save** one more time to save your custom Action.

![Demo](./images/twiliomsgpopup3.png)

Your custom Action is now part of the **Actions** list.

![Demo](./images/twiliodone.png)

Let's define your second action now.

## Action: Send Text to Slack Channel

We'll now use an existing Slack Channel and send messages to that Slack Channel. Slack has an easy-to-use API and we'll use Journey Orchestration to trigger their API.

![Demo](./images/slack.png)

Click **Add** to start adding your action.

![Demo](./images/add.png)

You'll see an empty Action popup.

![Demo](./images/emptyact.png)

As a Name for the Action, use `textSlackLdap` and replace `Ldap` with your LDAP. In this example, the Action Name is `textSlackVangeluw`.

Set Description to: `Send Text to Slack`.

![Demo](./images/slackname.png)

For the **URL Configuration**, use this:

* URL: `https://hooks.slack.com/services/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`
* Method: **POST**

You don't need to change the Header Fields.

![Demo](./images/slackurl.png)

**Authentication** should be set to **No Authentication**.

![Demo](./images/slackauth.png)

For the **Message Parameters**, you need to define which fields should be sent towards Slack. Logically, we want Journey Orchestration and Adobe Experience Platform to be the brain of personalization, so the text to send to Slack should be defined by Journey Orchestration and then sent to Slack for execution.

So for the **Message Parameters**, click the **Edit Payload** icon.

![Demo](./images/slackmsgp.png)

You'll then see an empty popup-window.

![Demo](./images/slackmsgpopup.png)

Copy the below text and paste it in the empty popup window.

```json
{
 "text": {
  "toBeMapped": true,
  "dataType": "string",
  "label": "textToSlack"
 }
}
```

FYI: by specifying the below fields, these fields will become accessible from your Customer Journey and you'll be able to populate them dynamically from the Journey:

**"toBeMapped": true,**

**"dataType": "string",**

**"label": "textToSlack"**

You'll then see this:

![Demo](./images/slackmsgpopup1.png)

Click **Save**.

![Demo](./images/twiliomsgpopup2.png)

Scroll up and click **Save** one more time to save your custom Action.

![Demo](./images/slackmsgpopup3.png)

Your custom Action is now part of the **Actions** list.

![Demo](./images/slackdone.png)

You've defined Events, Data Sources and Actions. Now let's consolidate all of that in one Orchestrated Journey.

Next Step: [12.4 Design a trigger-based Customer Journey](./ex4.md)

[Go Back to Module 12](journey-orchestration-external-weather-api-sms.md)

[Go Back to All Modules](../../overview.md)
