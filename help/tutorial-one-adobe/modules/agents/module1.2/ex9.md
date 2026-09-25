---
title: CX Enterprise Coworker with Claude
description: CX Enterprise Coworker with Claude Enterprise
kt: 5342
doc-type: tutorial
---
# 1.2.9 CX Enterprise Coworker with Claude

>[!IMPORTANT]
>
>Before you begin, read the below instructions!

## Instructions for in-person workshops

For this exercise, you need to use:

- **Instance**: **Adobe Tech Insiders**
- **Sandbox**: **One Adobe**
- **Dataview**: **AdobeOne - Unified Customer Data View**
- **Username**: **adobetechinsiders-XXX@adobeeventlab.com** and replace XXX by the number that was assigned to you
- **Password**: use the password that was shared with you

## 1.2.9.1 Install the custom MCP server for CX Enterprise Coworker

Go to [https://claude.ai/](https://claude.ai/) and log in using your account details. Once you're logged in, you should see this. Go to **Customize**.

![Claude](./images/claude1.png)

Go to **Connectors**, click **+ Add** and then select **Add custom connector**.

![Claude](./images/claude2.png)

Enter the following information:

- **Name**: `CX Enterprise Coworker`
- **URL**: enter the URL provided to you by your Adobe contact

Click **Continue**.

![Claude](./images/claude3.png)

Leave the default settings in place, and click **Add**.

![Claude](./images/claude4.png)

Click **Connect**. You'll then have to log in using your Adobe credentials.

![Claude](./images/claude5.png)

After logging in, you should then see this.

![Claude](./images/claude6.png)

## 1.2.9.2 Set context in CX Enterprise Coworker

Before interacting further with CX Enterprise Coworker through Claude, the context needs to be set.

For this exercise, the context needs to be set to use:

- **IMS Org**: `--aepImsOrgName--`.

- **Sandbox**: **Prod - One Adobe**

The sandbox setting helps to identify which sandbox ChatGPT should look at when asking questions.

- **Dataview**: **AdobeOne - Unified Customer Data View**

The dataview setting helps to identify which dataview ChatGPT should look at when asking questions.

Open a new chat. Enter the following **Prompt** and click the **send** button.

```
using CX Enterprise Coworker, list sandboxes
```

![Coworker Claude](./images/claude11.png)

Choose **Always allow** or **Allow once**.

![Coworker Claude](./images/claude11a.png)

You should then see this. Enter the following **Prompt** and click the **send** button.

```
change sandbox to one-adobe
```

![Coworker Claude](./images/claude12.png)

You should then see this. Enter the following **Prompt** and click the **send** button.

```
list dataviews
```

![Coworker Claude](./images/claude13.png)

Choose **Always allow** or **Allow once**.

![Coworker Claude](./images/claude13a.png)

You should then see this. Enter the following **Prompt** and click the **send** button.

```
switch to AdobeOne - Unified Customer Data View
```

![Coworker Claude](./images/claude14.png)

You should then see this. The context is now set correctly so you can start sending specific prompts next.

![Coworker Claude](./images/claude15.png)

## 1.2.9.3 Start with overall purchase trends to anchor context and zoom into fiber 

**Intent**

Get a toplevel pulse on category demand—Mobile, Landline, Internet, TV, Fiber—specifically for the most recent 60 days. This sets baselines for seasonality, promo effects, and regional variance after the New York rollout. 

Enter the following **Prompt** and click the **send** button.

```
Show me purchases by mainCategory over the last 2 months.
```

![Coworker](./images/claudecopilot18.png)

Choose **Always allow** or **Allow once**.

![Coworker Claude](./images/claude18a.png)

You should then see this:

![Coworker](./images/claudecopilot19.png)

Enter the following **Prompt** and click the **send** button.

```
Show me purchases by mainCategory = Fiber over the last 2 months broken down by week
```

![Coworker](./images/claudecopilot20.png)

You should then see this, which drills down into Fiber-specific trends. 

![Coworker](./images/claudecopilot21.png)

## 1.2.9.4 Correlate Orders with Content Preferences 

**Intent**

Test the hypothesis that a preference for a specific genre (e.g., SciFi, Sports, Drama) predicts broadband upgrade behavior—especially for high bandwidth needs. 

First, you need to find out which field is used to store the genre preference.

Enter the following **Prompt** and click the **send** button.

```
Which field is used to store the preferred genre
```

![Coworker](./images/claudecopilot22.png)

You should then see this, which shows that the field used for genre is **`--aepTenantId--.individualCharacteristics.telco.mediaPreferences.favouriteGenre`**.

![Coworker](./images/claudecopilot23.png)

With that information, you can start drilling down in the purchase data.

Enter the following **Prompt** and click the **send** button.

```
Show me purchases by preferred genre for the last 2 months until today
```

![Coworker](./images/claudecopilot24.png)

You should then see this.

![Coworker](./images/claudecopilot25.png)

## 1.2.9.5 Create a new audience

**Intent**

Based on the above findings and research, there's a correlation between customers that consume a lot of data and that have a preferred genre of sci-fi or fantasy. You will now combine these attributes in an audience.

Enter the following **Prompt** and click the **send** button.

```javascript
Create an audience with the name --aepUserLdap-- - Heavy Downloaders - Sci-Fi or Fantasy (Claude) that combines people with an average download usage per month of over 2000 GB and a preferred genre of sci-fi or fantasy.
```

![Coworker](./images/claudeaocptechlab32.png)

If similar, already existing audiences are already available, you should see a similar message. Enter the following **Prompt** and click the **send** button.

```javascript
create a new one
```

![Coworker](./images/claudeaocptechlab32a.png)

Enter the following **Prompt** and click the **send** button.

```javascript
proceed
```

![Coworker](./images/claudeaocptechlab33.png)

Enter the following **Prompt** and click the **send** button.

```javascript
it looks correct, continue
```

![Coworker](./images/claudeaocptechlab34.png)

Enter the following **Prompt** and click the **send** button.

```javascript
create the audience and publish it
```

![Coworker](./images/claudeaocptechlab35.png)

Approve the creation of the audience.

![Coworker](./images/claudeaocptechlab36.png)

Enter the following **Prompt** and click the **send** button.

```javascript
Approve.
```

Approve the publication of the audience.

![Coworker](./images/claudeaocptechlab36a.png)

Enter the following **Prompt** and click the **send** button.

```javascript
Approve.
```

![Coworker](./images/claudeaocptechlab36b.png)

Your audience has now been created.

![Coworker](./images/claudeaocptechlab38.png)

## 1.2.9.6 Activate audience to destination

Enter the following **Prompt** and click the **send** button.

```javascript
Which destinations exist?
```

![Coworker](./images/claudecpcwdest1.png)

You should then see this.

![Coworker](./images/claudecpcwdest2.png)

Enter the following **Prompt** and click the **send** button.

```javascript
Activate the audience I just created to the Meta destination and set the field customer_file_source to USER_PROVIDED_ONLY.
```

![Coworker](./images/claudecpcwdest3.png)

Approve the activation of the audience.

![Coworker](./images/claudecpcwdest3a.png)

Enter the following **Prompt** and click the **send** button.

```javascript
Approve.
```

![Coworker](./images/claudecpcwdest3b.png)

You should then see this.

![Coworker](./images/claudecpcwdest5.png)

## 1.2.9.7 Identify Existing Fiber Journeys

**Intent** 

Discover which active or recently concluded journeys include “Fiber” in the title—e.g., “Fiber Upgrade NYC – Sept”, “Fiber Trial – Streaming Bundle”. 

Enter the following **Prompt** and click the **send** button.

```
What journeys exist?
```

![Coworker](./images/claudecopilot28.png)

You should then see a list of journeys.

![Coworker](./images/claudecopilot29.png)

Enter the following **Prompt** and click the **send** button.

```
Show me the details of the journey 'CitiSignal - Fiber Max Launch Promotion'
```

![Coworker](./images/claudecopilot35.png)

You should then see this.

![Coworker](./images/claudecopilot36.png)

You've now completed this lab.

## Next Steps

Go Back to [CX Enterprise Coworker](./coworker.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}