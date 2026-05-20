---
title: Adobe Marketing Agent for ChatGPT Enterprise
description: Adobe Marketing Agent for ChatGPT Enterprise
kt: 5342
doc-type: tutorial
exl-id: 0aa0cef5-bc1d-4cb6-be09-a5964686c963
---
# 1.1.2 Adobe Marketing Agent for ChatGPT Enterprise

## Video

In this video, you'll get an explanation and demonstration of all the steps involved in this exercise.

>[!VIDEO](https://video.tv.adobe.com/v/3478410?quality=12&learn=on)

## 1.1.2.1 Create custom app in ChatGPT Enterprise for Adobe Marketing Agent 

>[!NOTE]
>
>Using Adobe Marketing Agent in ChatGPT requires the following:
>- a paid version of OpenAI's ChatGPT Enterprise
>- using the ChatGPT Enterprise web client

Go to [https://chatgpt.com/](https://chatgpt.com/){target="_blank"} and log in using your account details. Once you're logged in, you should see this. Go to **Apps**.

![ChatGPT](./images/chatgpt1.png)

Search for **Adobe Marketing Agent** and then click **Adobe Marketing Agent**.

![ChatGPT](./images/chatgpt2.png)

Click **Connect**.

![ChatGPT](./images/chatgpt3.png)

Click **Sign in with Adobe Marketing Agent**.

![ChatGPT](./images/chatgpt4.png)

ChatGPT will now attempt to connect to your Adobe account. Select **Allow Access** and then you'll have to log in with your Adobe account.

![ChatGPT](./images/chatgpt5.png)

Once you've logged in successfully, you should see that your Adobe Marketing Agent is now connected successfully. Click **Start chat**.

![ChatGPT](./images/chatgpt8.png)

## 1.1.2.2 Set context in Adobe Marketing Agentd

Before interacting further with Adobe Marketing Agent through ChatGPT, the context needs to be set.

For this exercise, the context needs to be set to use:

- **IMS Org**: `--aepImsOrgName--`.

- **Sandbox**: **Prod - One Adobe**

The Sandbox setting helps to identify which sandbox ChatGPT should look at when asking questions.

- **Dataview**: **AdobeOne - Unified Customer Data View**

The Dataview setting helps to identify which dataview ChatGPT should look at when asking questions.

Enter the following **Prompt** and click the **send** button.

```
change context
```

![Agent Orchestrator](./images/chatgpt11.png)

You should then see a similar window, showing the current organization, sandbox and dataview selection. Change these fields to the correct organization, sandbox and dataview based on the above information.

![Agent Orchestrator](./images/chatgpt12.png)

Your context is now properly set, so you can start sending specific prompts next.

## 1.1.2.3 Start with overall purchase trends to anchor context and zoom into fiber 

**Intent**

Get a toplevel pulse on category demand—Mobile, Landline, Internet, TV, Fiber—specifically for the most recent 60 days. This sets baselines for seasonality, promo effects, and regional variance after the New York rollout. 

Enter the following **Prompt** and click the **send** button.

```
Show me purchases by mainCategory over the last 2 months.
```

![Agent Orchestrator](./images/chatgpt18.png)

You should then see this:

![Agent Orchestrator](./images/chatgpt19.png)

Enter the following **Prompt** and click the **send** button.

```
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

```
Which field is used to store the preferred genre?
```

![Agent Orchestrator](./images/chatgpt22.png)

You should then see this, which shows that the field used for genre is **`--aepTenantId--.individualCharacteristics.telco.mediaPreferences.favouriteGenre`**.

![Agent Orchestrator](./images/chatgpt23.png)

With that information, you can start drilling down in the purchase data.

Enter the following **Prompt** and click the **send** button.

```
Show me purchases by favouriteGenre for the last 2 months
```

![Agent Orchestrator](./images/chatgpt24.png)

You should then see this.

![Agent Orchestrator](./images/chatgpt25.png)

## 1.1.2.5 Identify Existing Fiber Journeys

**Intent** 

Discover which active or recently concluded journeys include “Fiber” in the title—e.g., “Fiber Upgrade NYC – Sept”, “Fiber Trial – Streaming Bundle”. 

Enter the following **Prompt** and click the **send** button.

```
What journeys exist? 
```

![Agent Orchestrator](./images/chatgpt28.png)

You should then see this.

![Agent Orchestrator](./images/chatgpt29.png)

Enter the following **Prompt** and click the **send** button.

```
Which of these journeys has 'Fiber' in its name?
```

![Agent Orchestrator](./images/chatgpt31.png)

You should then see this.

![Agent Orchestrator](./images/chatgpt32.png)

Enter the following **Prompt** and click the **send** button.

```
show me the details of the journey 'CitiSignal - Fiber Max Launch Promotion'
```

![Agent Orchestrator](./images/chatgpt35.png)

You should then see this.

![Agent Orchestrator](./images/chatgpt36.png)

## 1.1.2.6 Validate journey performance via fallout analysis 

**Intent**

You want to understand journey performance fallout to know if there are any nodes or conditions within the journey that are experiencing a large percentage of profiles being dropped. This is helpful in understanding if additional adjustments are needed in the journey.

Enter the following **Prompt** and click the **send** button.

```
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

## Next Steps

Go to [Adobe Marketing Agent for Microsoft 365 Copilot](./ex3.md){target="_blank"}

Go back to [Agent Orchestrator](./agentorchestrator.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
