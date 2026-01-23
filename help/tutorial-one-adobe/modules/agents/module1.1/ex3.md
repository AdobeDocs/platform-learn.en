---
title: Adobe Marketing Agent with Microsoft 365 Copilot
description: Adobe Marketing Agent with Microsoft 365 Copilot
kt: 5342
doc-type: tutorial
---
# 1.1.3 Adobe Marketing Agent with Microsoft 365 Copilot

>[!IMPORTANT]
>
>This lab uses a feature that hasn't been released yet. The feature is still being developed so it isn't generally available yet.

## Prerequisites

>[!NOTE]
>
>In order to follow the steps in this lab as documented below, the following access is required:

>- Access to Real-Time CDP, Journey Optimizer and Customer Journey Analytics
>- Access to AI Assistant in Adobe Experience Cloud
>- Access to AEP Agent Orchestrator
>- Access to Microsoft 365 Copilot

## Video

In this video, you'll get an explanation and demonstration of all the steps involved in this exercise.

>[!VIDEO](https://video.tv.adobe.com/v/3479158?quality=12&learn=on)

## 1.1.3.1 Add Adobe Marketing Agent to Microsoft Teams & Copilot

Open Microsoft Teams and log in using your account details. Once you're logged in, you should see this. 

Click **Apps**.

![ChatGPT](./images/copilot1.png)

Select **Manage your apps**.

![ChatGPT](./images/copilot2.png)

Select **Upload an app**.

![ChatGPT](./images/copilot3.png)

Select **Upload a custom app**.

![ChatGPT](./images/copilot4.png)

Select the manifest file that was given to you by your instructor and click **Open**.

![ChatGPT](./images/copilot5.png)

Click **Add**.

![ChatGPT](./images/copilot6.png)

Click **Open with Copilot**.

![ChatGPT](./images/copilot7.png)

Adobe Marketing Agent is now loaded successfully.

![ChatGPT](./images/copilot8.png)

Enter the prompt `login` and click the **send** button.

![ChatGPT](./images/copilotlogin1.png)

Click **Sign in to Adobe Marketing Agent**.

![ChatGPT](./images/copilotlogin2.png)

A new window will open up, asking you to login using your Adobe account credentials.

![ChatGPT](./images/copilotlogin3.png)

After successful authentication, you may need to select the specific instance you want to use. If you see this screen, please select the instance --aepImsOrgName--.

![ChatGPT](./images/copilotlogin4.png)

You will then see a similar code being generated. Click **Copy** to copy the code.

![ChatGPT](./images/copilotlogin5.png)

Paste the code in the Adobe Marketing Agent window in Copilot and click the **send** button.

![ChatGPT](./images/copilotlogin6.png)

You should then see something similar to this. You're now successfully signed in to Adobe Marketing Agent in Microsoft Copilot.

![ChatGPT](./images/copilotlogin7.png)

## 1.1.3.2 Set context in Adobe Marketing Agent 

Before interacting further with Adobe Marketing Agent through Copilot, the context needs to be set.

For this exercise, the context needs to be set to use:

- **Sandbox**: **Prod - Accelerate (VA7)**

  The sandbox setting helps to identify which sandbox AI Assistant should look at when asking questions.

- **Dataview**: **Accelerate 2026 B2C**
  
  The dataview setting helps to identify which dataview AI Assistant should look at when asking questions.

![Agent Orchestrator](./images/copilotlogin7.png)

To change the sandbox, enter the following command and click the **send** button.

```javascript
change sandbox
```

![Agent Orchestrator](./images/copilot9.png)

You should then see something similar to this. Select the sandbox you need to use and click **select**.

![Agent Orchestrator](./images/copilot10.png)

You should then see this. To change the dataview, enter the following command and click the **send** button.

```javascript
change dataview
```

![Agent Orchestrator](./images/copilot11.png)

You should then see something similar to this. Select the dataview you need to use and click **select**.

![Agent Orchestrator](./images/copilot12.png)

You should then see this. The context is now set correctly so you can start sending specific prompts next.

![Agent Orchestrator](./images/copilot13.png)

## 1.1.3.3 Start with overall purchase trends to anchor context and zoom into fiber 

**Intent**

Get a toplevel pulse on category demand—Mobile, Landline, Internet, TV, Fiber—specifically for the most recent 60 days. This sets baselines for seasonality, promo effects, and regional variance after the New York rollout. 

Enter the following **Prompt** and click the **send** button.

```javascript
Show me purchases by mainCategory over the last 4 months.
```

![Agent Orchestrator](./images/copilot18.png)

You should then see this:

![Agent Orchestrator](./images/copilot19.png)

Enter the following **Prompt** and click the **send** button.

```javascript
Show me purchases by mainCategory = Fiber over the last 4 months broken down by week
```

![Agent Orchestrator](./images/copilot20.png)

You should then see this, which drills down into Fiber-specific trends. 

![Agent Orchestrator](./images/copilot21.png)

## 1.1.3.4 Correlate Orders with Content Preferences 

**Intent**

Test the hypothesis that a preference for a specific genre (e.g., SciFi, Sports, Drama) predicts broadband upgrade behavior—especially for high bandwidth needs. 

First, you need to find out which field is used to store the genre preference.

Enter the following **Prompt** and click the **send** button.

```javascript
Which field is used to store the preferred genre
```

![Agent Orchestrator](./images/copilot22.png)

You should then see this, which shows that the field used for genre is **_experienceplatform.individualCharacteristics.preferences.preferredGenre**.

![Agent Orchestrator](./images/copilot23.png)

With that information, you can start drilling down in the purchase data.

Enter the following **Prompt** and click the **send** button.

```javascript
Show me ordersYTD by preferredGenre for the last 4 months
```

![Agent Orchestrator](./images/copilot24.png)

You should then see this. Click **View Data**.

![Agent Orchestrator](./images/copilot25.png)

You should then see this.

![Agent Orchestrator](./images/copilot26.png)

## 1.1.3.5 Identify Existing Fiber Journeys

**Intent** 

Discover which active or recently concluded journeys include “Fiber” in the title—e.g., “Fiber Upgrade NYC – Sept”, “Fiber Trial – Streaming Bundle”. 

Enter the following **Prompt** and click the **send** button.

```javascript
What journeys exist? 
```

![Agent Orchestrator](./images/copilot28.png)

You should then see a list of journeys.

![Agent Orchestrator](./images/copilot29.png)

Enter the following **Prompt** and click the **send** button.

```javascript
Which of these journeys has 'Fiber' in its name?
```

![Agent Orchestrator](./images/copilot31.png)

You should then see this.

![Agent Orchestrator](./images/copilot33.png)

Enter the following **Prompt** and click the **send** button.

```javascript
Show me the details of the journey 'CitiSignal - Fiber Max Launch Promotion'
```

![Agent Orchestrator](./images/copilot35.png)

You should then see this.

![Agent Orchestrator](./images/copilot36.png)

## 1.1.3.6 Validate journey performance via fallout analysis 

**Intent**

You want to understand journey performance fallout to know if there are any nodes or conditions within the journey that are experiencing a large percentage of profiles being dropped. This is helpful in understanding if additional adjustments are needed in the journey.

Enter the following **Prompt** and click the **send** button.

```javascript
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey
```

![Agent Orchestrator](./images/copilot37.png)

You should then see this.

![Agent Orchestrator](./images/copilot38.png)

Scroll down a little bit more to see observations and recommendations. Click the 3 dots **...** and then select **Journey Details** to open the specific journey in Adobe Journey Optimizer.

![Agent Orchestrator](./images/copilot40.png)

You should then see this.

![Agent Orchestrator](./images/copilot41.png)

You've now completed this lab.

Go Back to [Agent Orchestrator](./agentorchestrator.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}