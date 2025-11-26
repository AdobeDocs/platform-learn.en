---
title: Getting started with Agent Orchestrator
description: Getting started with Agent Orchestrator
kt: 5342
doc-type: tutorial
---
# 1.1.1 Getting started with Agent Orchestrator

## 1.1.1.1 Set Context in Agent Orchestrator 

Go to [https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat](https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat).

You should then see this. Make sure you're in the org **Experience Platform International**.

![Agent Orchestrator](./images/ao1.png)

Click the **context** window.

![Agent Orchestrator](./images/ao2.png)

Set the context to:

- **Documentation Source**: **Customer Journey Analytics**
- **Sandbox**: **Accelerate**
- **Dataview**: **Accelerate 2026 B2C**

Click **Set context**.

![Agent Orchestrator](./images/ao3.png)

## 1.1.1.2 Start with overall purchase trends to anchor context and zoom into fiber 

**Intent**

Get a toplevel pulse on category demand—Mobile, Landline, Internet, TV, Fiber—specifically for the most recent 60 days. This sets baselines for seasonality, promo effects, and regional variance after the New York rollout. 

Enter the following **Prompt** and click the **send** button.

```javascript
Show me purchases by mainCategory over the last 2 months.
```

![Agent Orchestrator](./images/ao4.png)

You should then see this:

![Agent Orchestrator](./images/ao5.png)

Enter the following **Prompt** and click the **send** button.

`Show me purchases by mainCategory = Fiber over the last 2 months per week`

![Agent Orchestrator](./images/ao6.png)

You should then see this, which drills down into Fiber-specific trends. 

**Action**: Note the growth curve and regional spikes. 

![Agent Orchestrator](./images/ao7.png)

## 1.1.1.3 Correlate Orders with Content Preferences 

**Intent**

Test the hypothesis that content preference (e.g., SciFi, Sports, Drama) predicts broadband upgrade behavior—especially for highbandwidth needs. 

Enter the following **Prompt** and click the **send** button.

```javascript
Show me ordersYTD by preferredGenre for the last 2 months
```

![Agent Orchestrator](./images/ao8.png)

You should then see this:

![Agent Orchestrator](./images/ao9.png)

## 1.1.1.4 Identify Existing Fiber Journeys

**Intent** 

Discover which active or recently concluded journeys include “Fiber” in the title—e.g., “Fiber Upgrade NYC – Sept”, “Fiber Trial – Streaming Bundle”. 

Enter the following **Prompt** and click the **send** button.

```javascript
What journeys exist? 
```

![Agent Orchestrator](./images/ao12.png)

You should then see this:

![Agent Orchestrator](./images/ao13.png)

List active or past journeys with Fiber messaging. 

Action: Shortlist high-performing journeys for cloning.

Enter the following **Prompt** and click the **send** button.

```javascript
Which of these journeys has 'Fiber' in its name?
```

![Agent Orchestrator](./images/ao14.png)

You should then see this:

![Agent Orchestrator](./images/ao15.png)

## 1.1.1.5 Check the seed

**Intent**:

Understand the seed definition of the “CitiSignal - Fiber Max Launch Promotion” journey—what traits drove targeting (e.g., “SciFi Genre Preference,” “4+ devices,” “stream ≥ 300GB/month”). 

Enter the following **Prompt** and then type in **+CitiSignal fib** to enable autocomplete. Select the journey **CitiSignal - Fiber Max Launch Promotion**.

```javascript
What was the initial audience in the journey named 
```

![Agent Orchestrator](./images/ao16.png)

You should then see this. Click the **send** button.

![Agent Orchestrator](./images/ao17.png)

You should then see this.

![Agent Orchestrator](./images/ao18.png)

## 1.1.1.6 Validate journey performance via fallout analysis 

**Intent**

Build a stepwise funnel in Customer Journey Analytics

Delivered → Opened → Clicked → Landed → Product View → Add to Cart → Checkout → Order Complete 

Include Fiber-related SKU views as a branch. 

Enter the following **Prompt** and click the **send** button.

```javascript
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey
```

![Agent Orchestrator](./images/ao19.png)

## 1.1.1.7 Create a new audience

**Intent**

Based on the above findings, there's a correlation between customers that consume a lot of data and that have a preferred genre of sci-fi or fantasy. You will now combine these attributes in an audience.

Go to [https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat](https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat).

Enter the following **Prompt** and click the **send** button.

>[!NOTE]
>
>Please verify that the context of the assistant is pointing to the sandbox **Accelerate** and the dataview **Accelerate 2026 B2C**

```javascript
Create an audience that combines people with an average download per month of over 2000 GB and a preferred genre of sci-fi or fantasy.
```

![Agent Orchestrator](./images/ao32.png)

Review the plan. Enter `yes` and click **send**.

![Agent Orchestrator](./images/ao33.png)

Review the segment query expression. Enter `yes` and click the **send** button.

![Agent Orchestrator](./images/ao34.png)

Review the segment size estimation. Enter `yes` and click the **send** button.

![Agent Orchestrator](./images/ao35.png)

Click **Review**.

![Agent Orchestrator](./images/ao36.png)

Review the segment definition. Click **Create**.

![Agent Orchestrator](./images/ao37.png)

Your audience has now been created.

![Agent Orchestrator](./images/ao38.png)

>[!NOTE]
>
>When creating a new audience, it will take 24 hours before the audience is available to the assistant for further usage.

## 1.1.1.8 Find existing audiences aligned to high usage and check if they are in use

**Intent**: 

Locate any audience named with "heavy downloaders", defined by monthly data usage thresholds.

>[!NOTE]
>
>In the previous steo you created a new audience, please remember that it will take 24 hours before the audience is available to the assistant for further usage. You should now use another, already existing audience instead.

Go to [https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat](https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat).

You should then see this. Make sure you're in the org **Experience Platform International**.

Enter the following **Prompt** and click the **send** button.

>[!NOTE]
>
>Please verify that the context of the assistant is pointing to the sandbox **Accelerate** and the dataview **Accelerate 2026 B2C**

```javascript
Is there an audience that has "heavy downloaders" in the title?
```

![Agent Orchestrator](./images/ao30.png)

You should then see this.

![Agent Orchestrator](./images/ao31.png)

There are some existing audiences already for "heavy downloaders". Let's see if they are in use already.

Enter the following **Prompt** and click the **send** button.

```javascript
Which of the above are used in a journey? 
```

![Agent Orchestrator](./images/ao50.png)

You should then see something similar to this.

![Agent Orchestrator](./images/ao51.png)

You should now verify if that journey is active. Enter the following **Prompt** and click the **send** button.

```javascript
Which of the above are used in a journey? 
```

![Agent Orchestrator](./images/ao52.png)

You should then see something similar to this. That journey isn't running at the moment.

![Agent Orchestrator](./images/ao53.png)

For the upcoming launch of Fiber Max, you should now create a new journey.

## 1.1.1.9 Create New Journey for Fiber Max Launch 

**Intent**: 

Build a new journey targeting the compound audience: 

Heavy Downloaders ∩ SciFi Preference (kbaa_5207bf audience key). 

Go to [https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat](https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat).

You should then see this. Make sure you're in the org **Experience Platform International**.

Enter the following **Prompt** and click the **send** button.

>[!NOTE]
>
>Please verify that the context of the assistant is pointing to the sandbox **Accelerate** and the dataview **Accelerate 2026 B2C**

```javascript
Create a  journey towards the audience Heavy Downloaders - Sci-Fi Preference_kbaa_5207bf. The journey is for the rollout of fiber broadband. There will 2 versions of an email  based on  a split of the audience based on who is in the "Eligble for Fiber upgrade" audience.  After 3 days, profiles from both email treatments who have not purchased fibre max will be sent a follow up email. 
```

![Agent Orchestrator](./images/aocj1.png)

You should then see this. Enter `yes` and click generate.

![Agent Orchestrator](./images/aocj2.png)

You should then see this. Enter `yes` and click generate.

![Agent Orchestrator](./images/aocj3.png)

You should then see this. Enter `The first one` and click generate.

![Agent Orchestrator](./images/aocj4.png)

You should then see this. Enter `yes` and click generate.

![Agent Orchestrator](./images/aocj5.png)

Review the response. Enter `yes` and click generate.

![Agent Orchestrator](./images/aocj6.png)

Click **Review**.

![Agent Orchestrator](./images/aocj7.png)

Update the journey name with your LDAP to make it unique. Click **Save**.

![Agent Orchestrator](./images/aocj8.png)

Your journey has now been created in draft mode.

![Agent Orchestrator](./images/aocj9.png)

## 1.1.1.10 Conflicts

Go to [https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat](https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat).

You should then see this. Make sure you're in the org **Experience Platform International**.

Enter the following **Prompt** and click the **send** button.

>[!NOTE]
>
>Please verify that the context of the assistant is pointing to the documentation source **Journey Optimizer**, the sandbox **Accelerate** and the dataview **Accelerate 2026 B2C**

```javascript
How can I manage journey conflicts?
```

![Agent Orchestrator](./images/aocj80.png)

Review the information.

![Agent Orchestrator](./images/aocj81.png)

Scroll down and select the **Sources** to find that the information is sourced frm Experience League.

![Agent Orchestrator](./images/aocj82.png)

Enter the following **Prompt** and click the **send** button.

```javascript
List any conflicts for "CitiSignal - Fiber Max Launch Promotion" journey
```

![Agent Orchestrator](./images/aocj70.png)

Review the journey conflict information.

![Agent Orchestrator](./images/aocj71.png)

Scroll down to find more journey conflict details.

![Agent Orchestrator](./images/aocj72.png)

## 1.1.1.11 Experiments

Go to [https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat](https://experience.adobe.com/#/@experienceplatform/ai-assistant/chat).

You should then see this. Make sure you're in the org **Experience Platform International**.

Enter the following **Prompt** and click the **send** button.

>[!NOTE]
>
>Please verify that the context of the assistant is pointing to the sandbox **Accelerate** and the dataview **Accelerate 2026 B2C**

```javascript
How are the experiments performing for the journey named 'CitiSignal - Fiber Max Launch Promotion'?
```

![Agent Orchestrator](./images/aoea0.png)

You should then see this:

![Agent Orchestrator](./images/aoea1.png)

Click the suggestion to compare the conversion rates of each treatment and then click **send**.

![Agent Orchestrator](./images/aoea2.png)

You should then see a detailed comparison like this:

![Agent Orchestrator](./images/aoea4.png)

Go Back to [Agent Orchestrator](./agentorchestrator.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}