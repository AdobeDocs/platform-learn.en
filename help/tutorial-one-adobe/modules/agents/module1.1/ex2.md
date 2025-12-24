---
title: Adobe Marketing Agent with ChatGPT
description: Adobe Marketing Agent with ChatGPT
kt: 5342
doc-type: tutorial
---
# 1.1.2 Adobe Marketing Agent with ChatGPT

## Video

In this video, you'll get an explanation and demonstration of all the steps involved in this exercise.

>[!VIDEO](https://video.tv.adobe.com/v/3478410?quality=12&learn=on)

## 1.1.2.1 Create custom app in ChatGPT for Adobe Marketing Agent 

>[!NOTE]
>
>Using Adobe Marketing Agent in ChatGPT requires the following:
>- a paid version of OpenAI's ChatGPT
>- using the ChatGPT web client

Go to https://chatgpt.com/ and log in using your account details. Once you're logged in, you should see this. Click your username.

![ChatGPT](./images/chatgpt1.png)

Select **Settings**.

![ChatGPT](./images/chatgpt2.png)

Go to **Apps** and then select **Advanced settings**.

![ChatGPT](./images/chatgpt3.png)

Turn on **Developer mode** and then click **Back**.

![ChatGPT](./images/chatgpt4.png)

Click **Create app**.

![ChatGPT](./images/chatgpt5.png)

Fill out the fields like this:

- **Name**: `Adobe Marketing Agent`
- **MCP Server URL**: check with your Adobe representative
- **Authentication**: `OAuth`

Check the checkbox for **I understand and want to continue**.

Click **Create**.

![ChatGPT](./images/chatgpt6.png)

ChatGPT will now attempt to connect to your Adobe account. Select **Allow Access** and then you'll have to log in with your Adobe account.

![ChatGPT](./images/chatgpt7.png)

Once you've logged in successfully, you should see that your Adobe Marketing Agent is now connected successfully.

![ChatGPT](./images/chatgpt8.png)

## 1.1.2.2 Set context in Adobe Marketing Agent 

Close this window.

![Agent Orchestrator](./images/chatgpt9.png)

You should then see this. Click the **+** icon, go to **More** and then select **Adobe Marketing Agent**.

![Agent Orchestrator](./images/chatgpt10.png)

Before interacting further with Adobe Marketing Agent through ChatGPT, the context needs to be set.

For this exercise, the context needs to be set to use:

- **Sandbox**: **Prod - Accelerate (VA7)**

The Sandbox setting helps to identify which sandbox AI Assistant should look at when asking questions.

- **Dataview**: **Accelerate 2026 B2C**

The Dataview setting helps to identify which dataview AI Assistant should look at when asking questions.

Enter the following **Prompt** and click the **send** button.

```javascript
list sandboxes
```

![Agent Orchestrator](./images/chatgpt11.png)

You should then see a similar list of available sandboxes. The current sandbox in this example is set to **prod**. 

To change that to the sandbox that needs to be used, enter the following **Prompt** and click the **send** button.

```javascript
switch to sandbox accelerate
```

![Agent Orchestrator](./images/chatgpt12.png)

You should then see this. Click **Set Context**.

![Agent Orchestrator](./images/chatgpt13.png)

You should then see this. Enter the following **Prompt** and click the **send** button to set the dataview to use.

```javascript
list dataviews
```

![Agent Orchestrator](./images/chatgpt14.png)

You should then see a similar list of available sandboxes. The current sandbox in this example is set to **prod**. 

To change that to the sandbox that needs to be used, enter the following **Prompt** and click the **send** button.

```javascript
switch to Accelerate 2026 B2C
```

![Agent Orchestrator](./images/chatgpt15.png)

You should then see this. Click **Set Context**.

![Agent Orchestrator](./images/chatgpt16.png)

You should then see this.

![Agent Orchestrator](./images/chatgpt17.png)

Your context is now propermy set, so you can start sending specific prompts next.

## 1.1.2.3 Start with overall purchase trends to anchor context and zoom into fiber 

**Intent**

Get a toplevel pulse on category demand—Mobile, Landline, Internet, TV, Fiber—specifically for the most recent 60 days. This sets baselines for seasonality, promo effects, and regional variance after the New York rollout. 

Enter the following **Prompt** and click the **send** button.

```javascript
Show me purchases by mainCategory over the last 2 months.
```

![Agent Orchestrator](./images/chatgpt18.png)

You should then see this:

![Agent Orchestrator](./images/chatgpt19.png)

Enter the following **Prompt** and click the **send** button.

```javascript
Show me purchases by mainCategory = Fiber over the last 2 months per week
```

![Agent Orchestrator](./images/chatgpt20.png)

You should then see this, which drills down into Fiber-specific trends. 

![Agent Orchestrator](./images/chatgpt21.png)

## 1.1.2.4 Correlate Orders with Content Preferences 

**Intent**

Test the hypothesis that a preference for a specific genre (e.g., SciFi, Sports, Drama) predicts broadband upgrade behavior—especially for high bandwidth needs. 

First, you need to find out which field is used to store the genre preference.

Enter the following **Prompt** and click the **send** button.

```javascript
Which field is used to store the preferred genre in the sandbox accelerate?
```

![Agent Orchestrator](./images/chatgpt22.png)

You should then see this, which shows that the field used for genre is **_experienceplatform.individualCharacteristics.preferences.preferredGenre**.

![Agent Orchestrator](./images/chatgpt23.png)

With that information, you can start drilling down in the purchase data.

Enter the following **Prompt** and click the **send** button.

```javascript
Show me ordersYTD by preferredGenre for the last 2 months
```

![Agent Orchestrator](./images/chatgpt24.png)

You should then see this. Click **Research**.

![Agent Orchestrator](./images/chatgpt25.png)

You should then see this.

![Agent Orchestrator](./images/chatgpt26.png)

Scroll down to see more information.

![Agent Orchestrator](./images/chatgpt27.png)

## 1.1.2.5 Identify Existing Fiber Journeys

**Intent** 

Discover which active or recently concluded journeys include “Fiber” in the title—e.g., “Fiber Upgrade NYC – Sept”, “Fiber Trial – Streaming Bundle”. 

Enter the following **Prompt** and click the **send** button.

```javascript
What journeys exist? 
```

![Agent Orchestrator](./images/chatgpt28.png)

You should then see this. Click **Research**.

![Agent Orchestrator](./images/chatgpt29.png)

You should then see a list of journeys.

![Agent Orchestrator](./images/chatgpt30.png)

Enter the following **Prompt** and click the **send** button.

```javascript
Which of these journeys has 'Fiber' in its name?
```

![Agent Orchestrator](./images/chatgpt31.png)

You should then see this. Click **Research**.

![Agent Orchestrator](./images/chatgpt32.png)

You should then see this.

![Agent Orchestrator](./images/chatgpt33.png)

Scroll down to see more details.

![Agent Orchestrator](./images/chatgpt34.png)

Enter the following **Prompt** and click the **send** button.

```javascript
show me the details of the journey 'CitiSignal - Fiber Max Launch Promotion'
```

![Agent Orchestrator](./images/chatgpt35.png)

You should then see this.

![Agent Orchestrator](./images/chatgpt36.png)

## 1.1.2.6 Validate journey performance via fallout analysis 

**Intent**

You want to understand journey performance fallout to know if there are any nodes or conditions within the journey that are experiencing a large percentage of profiles being dropped. This is helpful in understanding if additional adjustments are needed in the journey.

Enter the following **Prompt** and click the **send** button.

```javascript
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey
```

![Agent Orchestrator](./images/chatgpt37.png)

You should then see this.

![Agent Orchestrator](./images/chatgpt38.png)

Scroll down a little bit. You can now review the table by inspecting each node and its respective enter numbers, fallout numbers, and fallout rate. 

![Agent Orchestrator](./images/chatgpt39.png)

Scroll down a little bit more to see observations and recommendations. 

![Agent Orchestrator](./images/chatgpt40.png)

You've now completed this lab.

Go Back to [Agent Orchestrator](./agentorchestrator.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}