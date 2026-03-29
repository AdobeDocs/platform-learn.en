---
title: Adobe Marketing Agent for Google Gemini Enterprise
description: Adobe Marketing Agent for Google Gemini Enterprise
kt: 5342
doc-type: tutorial
exl-id: 62b0b307-599b-4165-819b-cac61a8c5d28
---
# 1.1.4 Adobe Marketing Agent for Google Gemini Enterprise

[!BADGE Beta]

+++Beta Details
By using the Adobe Marketing Agent with Google Gemini Enterprise Beta, You hereby acknowledge that the Beta is provided “as is” without warranty of any kind. Adobe shall have no obligation to maintain, correct, update, change, modify or otherwise support the Beta. You are advised to use caution and not to rely in any way on the correct functioning or performance of such Beta and/or accompanying materials. The Beta is considered Confidential Information of Adobe.  Any “Feedback” (information regarding the Beta including but not limited to problems or defects you encounter while using the Beta, suggestions, improvements, and recommendations) provided by You to Adobe is hereby assigned to Adobe including all rights, title, and interest in and to such Feedback.

+++

## Prerequisites

In order to follow the steps in this lab as documented below, the following access is required:

- Access to Real-Time CDP, Journey Optimizer and Customer Journey Analytics
- Access to AI Assistant in Adobe Experience Cloud
- Access to AEP Agent Orchestrator
- Access to Google Gemini Enterprise

## Video

In this video, you'll get an explanation and demonstration of all the steps involved in this exercise.

>[!VIDEO](https://video.tv.adobe.com/v/3481322?quality=12&learn=on)

## 1.1.4.1 Access to Google Gemini Enterprise

Go to [https://cloud.google.com/gemini-enterprise](https://cloud.google.com/gemini-enterprise). Click **Start 30-day free trial**.

![Gemini](./images/gemini1.png)

Enter your Google account's email address and click **Continue with email**.

![Gemini](./images/gemini2.png)

Provide your first and last name and then click **Agree & get started**.

![Gemini](./images/gemini3.png)

Click **I'll do this later**.

![Gemini](./images/gemini4.png)

You should then see this.

![Gemini](./images/gemini5.png)

Go to [https://cloud.google.com/gemini-enterprise](https://cloud.google.com/gemini-enterprise).

You should then see something like this. You may also have to first create your billing account, to then select it here afterwards.

![Gemini](./images/gemini6.png)

Click **Start 30-day cost-free trial**.

![Gemini](./images/gemini7.png)

Click **Continue and activate the API**.

![Gemini](./images/gemini8.png)

Click **Create**.

![Gemini](./images/gemini9.png)

You should then see this.

![Gemini](./images/gemini10.png)

## 1.1.4.2 Create your custom agent using A2A

Go to [https://console.cloud.google.com/gemini-enterprise](https://console.cloud.google.com/gemini-enterprise). Click **Agents**.

![Gemini](./images/gemini10a.png)

Click **+Add agent**.

![Gemini](./images/gemini11.png)

Select **Custom agent via A2A**.

![Gemini](./images/gemini12.png)

Paste the **Agent Card JSON**.

>[!NOTE]
>
>Check with your Adobe representative to get the **Agent Card JSON** information.

![Gemini](./images/gemini13.png)

After pasting the **Agent Card JSON**, click **Preview agent details**.

![Gemini](./images/gemini14.png)

You should then see something like this. Scroll down and click **Next**.

![Gemini](./images/gemini15.png)

You should then see something like this. 

![Gemini](./images/gemini16.png)

Fill out the fields for your instance.

- **Client ID**:

```
--aepImsOrgId--
```

- **Client Secret**:

```
AdobeMarketingAgent
```

- **Authorization URL**:

```
https://XXX.adobe.io/authorize
```

- **Token URL**:

```
https://XXX.adobe.io/token
```

- **Scopes**:

```
openid email profile
```

Click **Finish**.

![Gemini](./images/gemini17.png)

You should then see this.

![Gemini](./images/gemini18.png)

## 1.1.4.3 Login to Adobe Marketing Agent

Go to **Overview** and then click **Preview**.

![Gemini](./images/gemini19.png)

Click **Get Started**

![Gemini](./images/gemini20.png)

Go to **Agents**. You should see **Adobe Marketing Agent** there.

![Gemini](./images/gemini21.png)

Click the 3 dots **...** and then select **Pin**.

![Gemini](./images/gemini22.png)

Go to **New chat** and enter the symbol **@** in the chat. Click **Adobe Marketing Agent**.

![Gemini](./images/gemini23.png)

Enter the command `login` and then click **Send**.

![Gemini](./images/gemini24.png)

You should then see this. Click **Authorize**.

![Gemini](./images/gemini25.png)

Click **Allow Access** and complete the login using your Adobe ID, and select the instance `--aepImsOrgName--` when prompted.

![Gemini](./images/gemini26.png)

You should then see this.

![Gemini](./images/gemini27.png)

## 1.1.4.4 Set context in Adobe Marketing Agent 

Before interacting further with Adobe Marketing Agent through Copilot, the context needs to be set.

For this exercise, the context needs to be set to use:

- **Sandbox**: **Prod - Accelerate (VA7)**

  The sandbox setting helps to identify which sandbox AI Assistant should look at when asking questions.

- **Dataview**: **Accelerate 2026 B2C**
  
The dataview setting helps to identify which dataview AI Assistant should look at when asking questions.

To change the sandbox, enter the following command and click the **send** button.

```javascript
list sandboxes
```

![Agent Orchestrator](./images/gemini28.png)

You should then see something similar to this. Enter the command `switch to sandbox accelerate` and click the **Send** button.

![Agent Orchestrator](./images/geminilab10.png)

You should then see this. To change the dataview, enter the following command and click the **send** button.

```javascript
list dataviews
```

![Agent Orchestrator](./images/geminilab11.png)

You should then see something similar to this. Enter the command `switch dataview to Accelerate 2026 B2C` and click the **Send** button.

![Agent Orchestrator](./images/geminilab12.png)

You should then see this. The context is now set correctly so you can start sending specific prompts next.

![Agent Orchestrator](./images/geminilab13.png)

## 1.1.4.5 Start with overall purchase trends to anchor context and zoom into fiber 

**Intent**

Get a toplevel pulse on category demand—Mobile, Landline, Internet, TV, Fiber—specifically for the most recent 60 days. This sets baselines for seasonality, promo effects, and regional variance after the New York rollout. 

Enter the following **Prompt** and click the **send** button.

```javascript
Show me purchases by mainCategory over the last 7 months.
```

![Agent Orchestrator](./images/geminilab18.png)

You should then see this:

![Agent Orchestrator](./images/geminilab19.png)

Enter the following **Prompt** and click the **send** button.

```javascript
Show me purchases by mainCategory = Fiber over the last 7 months broken down by week
```

![Agent Orchestrator](./images/geminilab20.png)

You should then see this, which drills down into Fiber-specific trends. 

![Agent Orchestrator](./images/geminilab21.png)

## 1.1.4.6 Correlate Orders with Content Preferences 

**Intent**

Test the hypothesis that a preference for a specific genre (e.g., SciFi, Sports, Drama) predicts broadband upgrade behavior—especially for high bandwidth needs. 

First, you need to find out which field is used to store the genre preference.

Enter the following **Prompt** and click the **send** button.

```javascript
Which field is used to store the preferred genre
```

![Agent Orchestrator](./images/geminilab22.png)

You should then see this, which shows that the field used for genre is **_experienceplatform.individualCharacteristics.preferences.preferredGenre**.

![Agent Orchestrator](./images/geminilab23.png)

With that information, you can start drilling down in the purchase data.

Enter the following **Prompt** and click the **send** button.

```javascript
Show me ordersYTD by preferredGenre for the last 7 months
```

![Agent Orchestrator](./images/geminilab24.png)

You should then see this. 

![Agent Orchestrator](./images/geminilab25.png)

## 1.1.4.7 Identify Existing Fiber Journeys

**Intent** 

Discover which active or recently concluded journeys include “Fiber” in the title—e.g., “Fiber Upgrade NYC – Sept”, “Fiber Trial – Streaming Bundle”. 

Enter the following **Prompt** and click the **send** button.

```javascript
What journeys exist? 
```

![Agent Orchestrator](./images/geminilab28.png)

You should then see a list of journeys.

![Agent Orchestrator](./images/geminilab29.png)

Enter the following **Prompt** and click the **send** button.

```javascript
Which of these journeys has 'Fiber' in its name?
```

![Agent Orchestrator](./images/geminilab31.png)

You should then see this.

![Agent Orchestrator](./images/geminilab33.png)

Enter the following **Prompt** and click the **send** button.

```javascript
Show me the details of the journey 'CitiSignal - Fiber Max Launch Promotion'
```

![Agent Orchestrator](./images/geminilab35.png)

You should then see this.

![Agent Orchestrator](./images/geminilab36.png)

## 1.1.4.8 Validate journey performance via fallout analysis 

**Intent**

You want to understand journey performance fallout to know if there are any nodes or conditions within the journey that are experiencing a large percentage of profiles being dropped. This is helpful in understanding if additional adjustments are needed in the journey.

Enter the following **Prompt** and click the **send** button.

```javascript
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey
```

![Agent Orchestrator](./images/geminilab37.png)

You should then see this.

![Agent Orchestrator](./images/geminilab38.png)

You've now completed this lab.

## Next Steps

Go to [1.1.5 Adobe Marketing Agent for Claude](./ex5.md){target="_blank"}

Go back to [Agent Orchestrator](./agentorchestrator.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
