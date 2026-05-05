---
title: AI Harness
description: AI Harness
kt: 5342
doc-type: tutorial
---
# 1.1.6 AI Harness

## Prerequisites

In order to follow the steps in this lab as documented below, the following access is required:

- Access to Real-Time CDP, Journey Optimizer and Customer Journey Analytics
- Access to AI Assistant in Adobe Experience Cloud
- Access to AEP Agent Orchestrator
- Node.js 18+ needs to be installed on your system

## 1.1.6.1 Access Agent Orchestrator

Go to [https://ao.adobe.io/](https://ao.adobe.io/). Log in using your Adobe account. After logging in, make sure you've selected the correct instance and sandbox by changing selecting them as indicated below.

![AO](./images/aov2lab1.png)

## 1.1.6.2 Set your context

Enter the following command and click **Send**.

```
list dataviews
```

![AO](./images/aov2lab18.png)

You may get this request. Provide the required permissions. 

![AO](./images/aov2lab19.png)

You may get this request. Provide the required permissions. 

![AO](./images/aov2lab19a.png)

You should then see this. Enter the following command and click **Send**.

```
switch to dataview AdobeOne - Unified Customer Data View
```

![AO](./images/aov2lab20.png)

You should then see this.

![AO](./images/aov2lab21.png)

## 1.1.6.3 Start with overall purchase trends to anchor context and zoom into fiber 

**Intent**

Get a toplevel pulse on category demand—Mobile, Landline, Internet, TV, Fiber—specifically for the most recent 60 days. This sets baselines for seasonality, promo effects, and regional variance after the New York rollout. 

Enter the following **Prompt** and click the **send** button.

```javascript
Show me purchases by mainCategory over the last 2 months.
```

![Agent Orchestrator](./images/aotechlab4.png)

You should then see this:

![Agent Orchestrator](./images/aotechlab5.png)

Enter the following **Prompt** and click the **send** button.

```javascript
Show me purchases by mainCategory = Fiber over the last 2 months per week
```

![Agent Orchestrator](./images/aotechlab6.png)

You should then see this, which drills down into Fiber-specific trends. 

![Agent Orchestrator](./images/aotechlab7.png)

## 1.1.6.4 Correlate Orders with Content Preferences 

**Intent**

Test the hypothesis that a preference for a specific genre (e.g., SciFi, Sports, Drama) predicts broadband upgrade behavior—especially for high bandwidth needs. 

First, you need to find out which field is used to store the genre preference.

Enter the following **Prompt** and click the **send** button.

```javascript
Which field is used to store the favourite genre?
```

![Agent Orchestrator](./images/aotechlab7a.png)

You should then see this, which shows that the field used for genre is **`--aepTenantId--.individualCharacteristics.telco.mediaPreferences.favouriteGenre`**.

![Agent Orchestrator](./images/aotechlab7b.png)

With that information, you can start drilling down in the purchase data.

Enter the following **Prompt** and click the **send** button.

```javascript
Show me purchases by favourite genre for the last 2 months
```

![Agent Orchestrator](./images/aotechlab8.png)

You should then see this.

![Agent Orchestrator](./images/aotechlab9.png)

## 1.1.6.5 Identify Existing Fiber Journeys

**Intent** 

Discover which active or recently concluded journeys include “Fiber” in the title—e.g., “Fiber Upgrade NYC – Sept”, “Fiber Trial – Streaming Bundle”. 

Enter the following **Prompt** and click the **send** button.

```javascript
What journeys exist? 
```

![Agent Orchestrator](./images/aotechlab12.png)

You should then see something like this. 

![Agent Orchestrator](./images/aotechlab13.png)

Enter the following **Prompt** and click the **send** button.

```javascript
Which of these journeys has 'Fiber' in its name?
```

![Agent Orchestrator](./images/aotechlab14.png)

You should then see this. Click the link on one of the journeys.

![Agent Orchestrator](./images/aotechlab15.png)

A new window will be opened, and you'll be taken to the journey details overview immediately.

![Agent Orchestrator](./images/aotechlab15a.png)

## 1.1.6.6 Check which audience is used

**Intent**:

Understand the seed definition of the “CitiSignal - Fiber Max Launch Promotion” journey—what traits drove targeting (e.g., “SciFi Genre Preference,” “4+ devices,” “stream ≥ 300GB/month”). 

Enter the following **Prompt** and click the **send** button.

```javascript
What was the initial audience in the journey named CitiSignal - Fiber Max Launch Promotion?
```

![Agent Orchestrator](./images/aotechlab16.png)

You should then see this.

![Agent Orchestrator](./images/aotechlab18.png)

## 1.1.6.7 Validate journey performance via fallout analysis 

**Intent**

You want to understand journey performance fallout to know if there are any nodes or conditions within the journey that are experiencing a large percentage of profiles being dropped. This is helpful in understanding if additional adjustments are needed in the journey.

Enter the following **Prompt** and click the **send** button.

```javascript
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey
```

![Agent Orchestrator](./images/aotechlab19.png)

You should then see this.

![Agent Orchestrator](./images/aotechlab20.png)

## 1.1.6.8 Create a new audience

**Intent**

Based on the above findings and research, there's a correlation between customers that consume a lot of data and that have a preferred genre of sci-fi or fantasy. You will now combine these attributes in an audience.

Enter the following **Prompt** and click the **send** button.

```javascript
Create an audience that combines people with an average download usage per month of over 2000 GB and a preferred genre of sci-fi or fantasy.
```

![Agent Orchestrator](./images/aotechlab32.png)

If similar, already existing audiences are already available, you should see a similar message.

![Agent Orchestrator](./images/aotechlab32a.png)

Review the plan. Click **Approve plan**.

![Agent Orchestrator](./images/aotechlab33.png)

Your audience has now been created.

![Agent Orchestrator](./images/aotechlab38.png)

>[!NOTE]
>
>When creating a new audience, it will take 24 hours before the audience is available to AI Assistant for further usage.

## 1.1.6.9 Find existing audiences aligned to high usage and check if they are in use

**Intent**: 

Locate any audience named with "heavy downloaders", defined by monthly data usage thresholds.

>[!NOTE]
>
>In the previous step you created a new audience, please remember that it will take 24 hours before the audience is available to AI Assistant for further usage. You should now use another, already existing audience instead.

Enter the following **Prompt** and click the **send** button.

```javascript
Is there an audience that has "heavy downloaders" in the title?
```

![Agent Orchestrator](./images/ao30.png)

You should then see this. You now want to see all your audiences and how much they have changed over the last few days.

Enter the following **Prompt** and click the **send** button.

```javascript
List how much these audiences changed over the last few days.
```

![Agent Orchestrator](./images/ao31.png)

You should then see this. Click **Show more**.

![Agent Orchestrator](./images/ao31a.png)

You should then see this. Click to close the right pane.

![Agent Orchestrator](./images/ao31b.png)

Scroll down a little bit to review the steps taken by AI Assistant.

![Agent Orchestrator](./images/ao31c.png)

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
Are these journeys active? 
```

![Agent Orchestrator](./images/ao52.png)

You should then see something similar to this. None of these journeys are currently running.

![Agent Orchestrator](./images/ao53.png)

For the upcoming launch of Fiber Max, you should now create a new journey.

## 1.1.6.10 Create New Journey for Fiber Max Launch 

**Intent**: 

Build a new journey targeting the compound audience: 

Heavy Downloaders ∩ SciFi Preference. 

Enter the following **Prompt** and click the **send** button.

```javascript
Create a  journey towards the audience Heavy Downloaders - Sci-Fi Preference_kbaa_5207bf. The journey is for the rollout of fiber broadband. There will 2 versions of an email  based on  a split of the audience based on who is in the "Eligble for Fiber upgrade" audience.  After 3 days, profiles from both email treatments who have not purchased fibre max will be sent a follow up email. 
```

![Agent Orchestrator](./images/aocj1.png)

You should then see this. Enter `yes` and click generate.

![Agent Orchestrator](./images/aocj2.png)

You should then see this. Enter `yes` and click generate.

![Agent Orchestrator](./images/aocj3.png)

You should then see this. Enter `The first one` and click send.

![Agent Orchestrator](./images/aocj4.png)

You should then see this. Enter `yes` and click send.

![Agent Orchestrator](./images/aocj5.png)

Review the response. Enter `yes` and click send.

![Agent Orchestrator](./images/aocj6.png)

Click **Review**.

![Agent Orchestrator](./images/aocj7.png)

Update the journey name with your LDAP to make it unique. Click **Save**.

![Agent Orchestrator](./images/aocj8.png)

Your journey has now been created in draft mode.

![Agent Orchestrator](./images/aocj9.png)

## 1.1.6.11 Journey Conflict Management

Enter the following **Prompt** and click the **send** button.

```javascript
How can I manage journey conflicts?
```

![Agent Orchestrator](./images/aocj80.png)

Review the information.

![Agent Orchestrator](./images/aocj81.png)

Scroll down and select the **Sources** to find that the information is sourced from Experience League.

![Agent Orchestrator](./images/aocj82.png)

Enter the following **Prompt** and click the **send** button.

```javascript
List any conflicts for the journey +CitiSignal Fiber Max
```

Then manually select the journey **CitiSignal - Fiber Max Launch Promotion** from the list.

![Agent Orchestrator](./images/aocj70.png)

You should then see this. Click **send**.

![Agent Orchestrator](./images/aocj70a.png)

Review the journey conflict information.

![Agent Orchestrator](./images/aocj71.png)

Scroll down to find more journey conflict details.

![Agent Orchestrator](./images/aocj72.png)

## 1.1.6.12 Experiments

Enter the following **Prompt** and click the **send** button.

```javascript
How are the experiments performing for the journey named 'CitiSignal - Fiber Max Launch Promotion'?
```

![Agent Orchestrator](./images/aoea0.png)

You should then see this:

![Agent Orchestrator](./images/aoea1.png)

Scroll down and click one of the suggestions. Click **send**.

>[!NOTE]
>
>Suggestions are dynamic so you should expect to see different suggestions each time a response is generated. Your suggestions will likely be different than the suggestions shown in this screenshot.

![Agent Orchestrator](./images/aoea2.png)

You should then see a detailed answer related to the suggestion that was chosen.

![Agent Orchestrator](./images/aoea4.png)

You've now completed this lab.

## Next Steps

Go back to [Agent Orchestrator](./agentorchestrator.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}

