---
title: CX Enterprise Coworker with Microsoft 365 Copilot
description: CX Enterprise Coworker with Microsoft 365 Copilot
kt: 5342
doc-type: tutorial
---
# 1.2.4 CX Enterprise Coworker with Microsoft 365 Copilot

## 1.2.4.1 Installing CX Enterprise Coworker in Microsoft 365 Copilot

Open Microsoft Teams and go to **Copilot**. In the left menu, click **More agents**.

![Coworker](./images/cwmsft1.png)

Search for **Coworker** and click **CX Enterprise Coworker**.

![Coworker](./images/cwmsft2.png)

Click **Add**.

![Coworker](./images/cwmsft3.png)

Go to **Copilot** and then click **CX Enterprise Coworker**. You're now ready to start using **CX Enterprise Coworker**.

![Coworker](./images/cwmsft4.png)

## 1.2.4.2 Sign in to CX Enterprise Coworker in Microsoft M365 Copilot

Enter the following **Prompt** and click the **send** button.

```
login
```

![Coworker](./images/cwmsftl1.png)

Click **Sign in to Adobe CX Enterprise Coworker**.

![Coworker](./images/cwmsftl2.png)

Copy the number you received after logging in using your Adobe account.

![Coworker](./images/cwmsftl3.png)

Paste the code that you just copied and click the **send** button.

![Coworker](./images/cwmsftl4.png)

You're now successfully logged in to CX Enterprise Coworker in Microsoft M365 Copilot.

![Coworker](./images/cwmsftl5.png)

## 1.2.4.3 Set context in CX Enterprise Coworker

Before interacting further with CX Enterprise Coworker through Microsoft M365 Copilot, the context needs to be set.

For this exercise, the context needs to be set to use:

- **Sandbox**: **Prod - One Adobe (VA7)**

  The sandbox setting helps to identify which sandbox AI Assistant should look at when asking questions.

- **Dataview**: **AdobeOne - Unified Customer Data View**
  
  The dataview setting helps to identify which dataview AI Assistant should look at when asking questions.

First, change the sandbox to the correct sandbox. If the sandbox isn't already set to **Prod - one-adobe (VA7)**, then use the following command and click **send**.
  
```
change sandbox to one-adobe
```

![Agent Orchestrator](./images/copilotlogin7a.png)

Then, enter the following **prompt** and click the **send** button.

```
list dataviews
```

![Agent Orchestrator](./images/copilotlogin9.png)

Enter the following **prompt** and click the **send** button.

```
change the dataview to AdobeOne - Unified Customer Data View
```

![Agent Orchestrator](./images/copilot13.png)

You should then see this. The context is now set correctly so you can start sending specific prompts next.

![Agent Orchestrator](./images/copilot13a.png)

## 1.2.4.4 Start with overall purchase trends to anchor context and zoom into fiber 

**Intent**

Get a toplevel pulse on category demand—Mobile, Landline, Internet, TV, Fiber—specifically for the most recent 60 days. This sets baselines for seasonality, promo effects, and regional variance after the New York rollout. 

Enter the following **Prompt** and click the **send** button.

```
Show me purchases by mainCategory over the last 2 months.
```

![Agent Orchestrator](./images/copilot18.png)

You should then see this:

![Agent Orchestrator](./images/copilot19.png)

Enter the following **Prompt** and click the **send** button.

```
Show me purchases by mainCategory = Fiber over the last 2 months broken down by week
```

![Agent Orchestrator](./images/copilot20.png)

You should then see this, which drills down into Fiber-specific trends. 

![Agent Orchestrator](./images/copilot21.png)

## 1.2.4.5 Correlate Orders with Content Preferences 

**Intent**

Test the hypothesis that a preference for a specific genre (e.g., SciFi, Sports, Drama) predicts broadband upgrade behavior—especially for high bandwidth needs. 

First, you need to find out which field is used to store the genre preference.

Enter the following **Prompt** and click the **send** button.

```
Which field is used to store the preferred genre
```

![Agent Orchestrator](./images/copilot22.png)

You should then see this, which shows that the field used for genre is **`--aepTenantId--.individualCharacteristics.telco.mediaPreferences.favouriteGenre`**.

![Agent Orchestrator](./images/copilot23.png)

With that information, you can start drilling down in the purchase data.

Enter the following **Prompt** and click the **send** button.

```
Show me purchases by preferred genre for the last 2 months until today
```

![Agent Orchestrator](./images/copilot24.png)

You should then see this.

![Agent Orchestrator](./images/copilot25.png)

## 1.2.4.6 Create a new audience

**Intent**

Based on the above findings and research, there's a correlation between customers that consume a lot of data and that have a preferred genre of sci-fi or fantasy. You will now combine these attributes in an audience.

Enter the following **Prompt** and click the **send** button.

```javascript
Create an audience with the name --aepUserLdap-- - Heavy Downloaders - Sci-Fi or Fantasy (Copilot M365) that combines people with an average download usage per month of over 2000 GB and a preferred genre of sci-fi or fantasy.
```

![Coworker](./images/aocptechlab32.png)

If similar, already existing audiences are already available, you should see a similar message. Enter the following **Prompt** and click the **send** button.

```javascript
create a new one
```

![Coworker](./images/aocptechlab32a.png)

Your audience has now been created.

![Coworker](./images/aocptechlab38.png)

## 1.2.4.7 Activate audience to destination

Enter the following **Prompt** and click the **send** button.

```javascript
Which destinations exist?
```

![Coworker](./images/cpcwdest1.png)

You should then see this.

![Coworker](./images/cpcwdest2.png)

Enter the following **Prompt** and click the **send** button.

```javascript
Activate the audience I just created to the Meta destination and set the field customer_file_source to USER_PROVIDED_ONLY.
```

![Coworker](./images/cpcwdest3.png)

You should then see this.

![Coworker](./images/cpcwdest5.png)

## 1.2.4.8 Identify Existing Fiber Journeys

**Intent** 

Discover which active or recently concluded journeys include “Fiber” in the title—e.g., “Fiber Upgrade NYC – Sept”, “Fiber Trial – Streaming Bundle”. 

Enter the following **Prompt** and click the **send** button.

```
What journeys exist?
```

![Agent Orchestrator](./images/copilot28.png)

You should then see a list of journeys.

![Agent Orchestrator](./images/copilot29.png)

Enter the following **Prompt** and click the **send** button.

```
Show me the details of the journey 'CitiSignal - Fiber Max Launch Promotion'
```

![Agent Orchestrator](./images/copilot35.png)

You should then see this.

![Agent Orchestrator](./images/copilot36.png)

## 1.2.4.9 Validate journey performance via fallout analysis 

**Intent**

You want to understand journey performance fallout to know if there are any nodes or conditions within the journey that are experiencing a large percentage of profiles being dropped. This is helpful in understanding if additional adjustments are needed in the journey.

Enter the following **Prompt** and click the **send** button.

```
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey
```

![Agent Orchestrator](./images/copilot37.png)

You should then see this.

![Agent Orchestrator](./images/copilot38.png)

You've now completed this lab.

## Next Steps

Go to [CX Enterprise Coworker with ChatGPT Enterprise](./ex5.md){target="_blank"}

Go Back to [CX Enterprise Coworker](./coworker.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}