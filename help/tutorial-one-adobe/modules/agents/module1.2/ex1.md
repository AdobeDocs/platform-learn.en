---
title: Getting started with CX Enterprise Coworker
description: Getting started with CX Enterprise Coworker
kt: 5342
doc-type: tutorial
exl-id: 12ceb547-4f1d-4c54-b51b-cb6a5654e922
TQID: https://experienceleague.adobe.com/gabsVds8rjRjfjkv0TGhZ5b-m8MBgjssN4hZAVtP5n0
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
---
# 1.2.1 Getting started with CX Enterprise Coworker

## Prerequisites

In order to follow the steps in this lab as documented below, the following access is required:

- Access to Real-Time CDP, Journey Optimizer and Customer Journey Analytics
- Access to CX Enterprise Coworker

## Instructions for live workshops

For this exercise, you need to use:

- **Instance**: **Adobe Tech Insiders**
- **Sandbox**: **One Adobe**
- **Dataview**: **AdobeOne - Unified Customer Data View**
- **Username**: **adobetechinsiders-XXX@adobeeventlab.com** and replace XXX by the number that was assigned to you
- **Password**: use the password that was shared with you

## Video

In this video, you'll get an explanation and demonstration of all the steps involved in this exercise.

>[!VIDEO](https://video.tv.adobe.com/v/3495927?quality=12&learn=on)

## 1.2.1.1 Access CX Enterprise Coworker

Go to [https://experience.adobe.com/#/coworker/chat](https://experience.adobe.com/#/coworker/chat). Sign in using your Adobe account. After logging in, click your user initials in the bottom left part of the screen and make sure you've selected the correct instance and sandbox by changing selecting them as indicated below.

![AO](./images/aov2lab1.png)

Before continuing, the selected instance and sandbox should look like this.

![AO](./images/aov2lab1a.png)

## 1.2.1.2 Enable CJA plugin

To install the CJA plugin, go to **Configurations**.

![AO](./images/cwcjaplugin1.png)

Search for `cja` and then click **Install**.

![AO](./images/cwcjaplugin2.png)

You should then see this.

![AO](./images/cwcjaplugin3.png)

## 1.2.1.3 Set your context

Click the **+** icon to start a new chat. Enter the following command and click **Send**.

```
list dataviews
```

![AO](./images/aov2lab18.png)

You should then see this. Enter the following command and click **Send**.

```
switch to dataview AdobeOne - Unified Customer Data View
```

![AO](./images/aov2lab20.png)

You should then see this.

![AO](./images/aov2lab21.png)

## 1.2.1.4 Start with overall purchase trends to anchor context and zoom into fiber 

**Intent**

Get a toplevel pulse on category demand—Mobile, Landline, Internet, TV, Fiber—specifically for the most recent 60 days. This sets baselines for seasonality, promo effects, and regional variance after the New York rollout. 

Enter the following **Prompt** and click the **send** button.

```javascript
Show me purchases by mainCategory over the last 2 months.
```

![Coworker](./images/aotechlab4.png)

You should then see this:

![Coworker](./images/aotechlab5.png)

Enter the following **Prompt** and click the **send** button.

```javascript
Show me purchases by mainCategory = Fiber over the last 2 months per week
```

![Coworker](./images/aotechlab6.png)

You should then see this, which drills down into Fiber-specific trends. 

![Coworker](./images/aotechlab7.png)

## 1.2.1.5 Correlate Orders with Content Preferences 

**Intent**

Test the hypothesis that a preference for a specific genre (e.g., SciFi, Sports, Drama) predicts broadband upgrade behavior—especially for high bandwidth needs. 

First, you need to find out which field is used to store the genre preference.

Enter the following **Prompt** and click the **send** button.

```javascript
Which field is used to store the favourite genre?
```

![Coworker](./images/aotechlab7a.png)

You should then see this, which shows that the field used for genre is **`--aepTenantId--.individualCharacteristics.telco.mediaPreferences.favouriteGenre`**.

![Coworker](./images/aotechlab7b.png)

With that information, you can start drilling down in the purchase data.

Enter the following **Prompt** and click the **send** button.

```javascript
Show me purchases by favourite genre for the last 2 months
```

![Coworker](./images/aotechlab8.png)

You should then see this.

![Coworker](./images/aotechlab9.png)

## 1.2.1.6 Identify Existing Fiber Journeys

**Intent** 

Discover which active or recently concluded journeys include “Fiber” in the title—e.g., “Fiber Upgrade NYC – Sept”, “Fiber Trial – Streaming Bundle”. 

Enter the following **Prompt** and click the **send** button.

```javascript
What journeys exist in the sandbox one-adobe?
```

![Coworker](./images/aotechlab12.png)

You should then see something like this. 

![Coworker](./images/aotechlab13.png)

Enter the following **Prompt** and click the **send** button.

```javascript
Give me an overview of the journeys that have 'Fiber' in their name.
```

![Coworker](./images/aotechlab14.png)

You should then see this. 

![Coworker](./images/aotechlab14a.png)

Enter the following **Prompt** and click the **send** button.

```javascript
Give me more details of the journey CitiSignal - Fiber Max Launch Promotion
```

![Coworker](./images/aotechlab15.png)

You should then see this.

![Coworker](./images/aotechlab15b.png)

## 1.2.1.7 Validate journey performance via fallout analysis 

**Intent**

You want to understand journey performance fallout to know if there are any nodes or conditions within the journey that are experiencing a large percentage of profiles being dropped. This is helpful in understanding if additional adjustments are needed in the journey.

Enter the following **Prompt** and click the **send** button.

```javascript
Create a fall-out report on the "CitiSignal - Fiber Max Launch Promotion" journey
```

![Coworker](./images/aotechlab19.png)

You should then see this.

![Coworker](./images/aotechlab20.png)

## 1.2.1.8 Create a new audience

**Intent**

Based on the above findings and research, there's a correlation between customers that consume a lot of data and that have a preferred genre of sci-fi or fantasy. You will now combine these attributes in an audience.

Enter the following **Prompt** and click the **send** button.

```javascript
Create an audience with the name --aepUserLdap-- - Heavy Downloaders - Sci-Fi or Fantasy that combines people with an average download usage per month of over 2000 GB and a preferred genre of sci-fi or fantasy.
```

![Coworker](./images/aotechlab32.png)

If similar, already existing audiences are already available, you should see a similar message. Enter the following **Prompt** and click the **send** button.

```javascript
create a new one
```

![Coworker](./images/aotechlab32a.png)

You should then see this. Enter the following **Prompt** and click the **send** button.

```javascript
use these fields
```

![Coworker](./images/aotechlab33a.png)

You should then see this. Enter the following **Prompt** and click the **send** button.

```javascript
yes
```

![Coworker](./images/aotechlab33b.png)

You should then see this. Enter the following **Prompt** and click the **send** button.

```javascript
proceed
```

![Coworker](./images/aotechlab33c.png)

Approve the request for permissions.

![Coworker](./images/aotechlab33ca.png)

You should then see this. Enter the following **Prompt** and click the **send** button.

```javascript
publish the audience
```

![Coworker](./images/aotechlab33d.png)

If prompted, provide the permissions to perform this task.

![Coworker](./images/aotechlab33e.png)

Your audience has now been created.

![Coworker](./images/aotechlab38.png)

## 1.2.1.9 Activate audience to destination

Enter the following **Prompt** and click the **send** button.

```javascript
Which destinations exist?
```

![Coworker](./images/cwdest1.png)

You should then see this.

![Coworker](./images/cwdest2.png)

Enter the following **Prompt** and click the **send** button.

```javascript
Activate the audience I just created to the Meta destination and set the field customer_file_source to USER_PROVIDED_ONLY.
```

![Coworker](./images/cwdest3.png)

If prompted, provide the permissions to perform this task.

![Coworker](./images/cwdest4.png)

You should then see this.

![Coworker](./images/cwdest5.png)

## 1.2.1.10 Find existing audiences aligned to high usage and check if they are in use

**Intent**: 

Locate any audience named with "heavy downloaders", defined by monthly data usage thresholds.

>[!NOTE]
>
>In the previous step you created a new audience, please remember that it will take 24 hours before the audience is available to AI Assistant for further usage. You should now use another, already existing audience instead.

Enter the following **Prompt** and click the **send** button.

```javascript
Is there an audience that has "heavy downloaders" in the title?
```

![Coworker](./images/ao30.png)

You should then see this. You now want to see all your audiences and how much they have changed over the last few days.

Enter the following **Prompt** and click the **send** button.

```javascript
List how much these audiences changed over the last few days.
```

![Coworker](./images/ao31.png)

You should then see this.

![Coworker](./images/ao31a.png)

There are some existing audiences already for "heavy downloaders". Let's see if they are in use already.

Enter the following **Prompt** and click the **send** button.

```javascript
Which of the above audiences are used in a journey?
```

![Coworker](./images/ao50.png)

You should then see something similar to this.

![Coworker](./images/ao51.png)

For the upcoming launch of Fiber Max, you should now create a new journey.

## 1.2.1.11 Create New Journey for Fiber Max Launch 

**Intent**: 

Build a new journey targeting the compound audience: 

Heavy Downloaders ∩ SciFi Preference. 

Enter the following **Prompt** and click the **send** button.

```javascript
Create a journey with the name --aepUserLdap-- CitiSignal Fiber Journey using the audience I created before. The journey is for the rollout of fiber broadband. There will 2 versions of an email  based on  a split of the audience based on who is in the "Eligble for Fiber upgrade" audience.  After 3 days, profiles from both email treatments who have not purchased fibre max will be sent a follow up email. 
```

![Coworker](./images/aocj1.png)

You should then see this. Review the proposal, and then select **Sabe to AJO**.

![Coworker](./images/aocj2.png)

If prompted, provide the permissions to perform this task.

![Coworker](./images/aocj4.png)

Your journey has now been created in draft mode.

![Coworker](./images/aocj9.png)

## 1.2.1.12 Journey Conflict Management

Enter the following **Prompt** and click the **send** button.

```javascript
How can I manage journey conflicts?
```

![Coworker](./images/aocj80.png)

Review the information. Scroll down and review the **Sources** to find that the information is sourced from Experience League.

![Coworker](./images/aocj81.png)

Enter the following **Prompt** and click the **send** button.

```javascript
List any conflicts for the journey "CitiSignal - Fiber Max Launch Promotion".
```

![Coworker](./images/aocj70.png)

You should then see this. Review the journey conflict information.

![Coworker](./images/aocj70a.png)

## 1.2.1.13 Experiments

Enter the following **Prompt** and click the **send** button.

```javascript
How are the experiments performing for the journey named 'CitiSignal - Fiber Max Launch Promotion'?
```

![Coworker](./images/aoea0.png)

You should then see this:

![Coworker](./images/aoea1.png)

You've now completed this lab.

## Next Steps

Go to [Using CX Enterprise Coworker for insights](./ex2.md){target="_blank"}

Go Back to [CX Enterprise Coworker](./coworker.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
