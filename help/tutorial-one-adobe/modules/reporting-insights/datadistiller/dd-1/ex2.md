---
title: Query Service - Getting Started
description: Query Service - Getting Started
kt: 5342
doc-type: tutorial
exl-id: 07f91736-2fb8-4381-b076-50df33f051b1
---
# 2.1.2 Getting Started

## Getting familiar with the Adobe Experience Platform UI

Go to [Adobe Experience Platform](https://experience.adobe.com/platform). After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./../../../../modules/delivery-activation/datacollection/dc1.2/images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxName--``. After selecting the appropriate [!UICONTROL sandbox], you'll see the screen change and now you're in your dedicated [!UICONTROL sandbox].

![Data Ingestion](./../../../../modules/delivery-activation/datacollection/dc1.2/images/sb1.png)

## Explore data on the platform

Bringing data from different channels is a tough task for any brand. And in this exercise, Citi Signal customers are engaging with Citi Signal on its website, on its mobile app, purchase data is collected by Citi Signal’s Point of Sale system, and they have CRM and Loyalty data. Citi Signal is using Adobe Analytics and Adobe Launch to capture data across its website, mobile app as well as POS system, so this data is already flowing into Adobe Experience Platform. Let's begin with exploring all the data for Citi Signal that already exists in Adobe Experience Platform.

In the left menu, go to **Datasets**.

![emea-website-interaction-dataset.png](./images/emeawebsiteinteractiondataset.png)

Citi Signal is streaming data into Adobe Experience Platform and this data is available in the `Demo System - Event Dataset for Website (Global v1.1)` dataset. Search for `Demo System - Event Dataset for Website`.

![emea-callcenter-interaction-dataset.png](./images/emeawebsiteinteractiondataset1.png)

Citi Signal's Callcenter Interaction data is captured in the `Demo System - Event Dataset for Call Center (Global v1.1)` dataset. Search for `Demo System - Event Dataset for Call Center` data in search box. Click on the dataset's name to open it.

![emea-callcenter-interaction-dataset.png](./images/emeacallcenterinteractiondataset.png)

After clicking the dataset, you will get an overview of the dataset activity such as ingested and failed batches. Click **Preview Dataset** to see a sample of the data stored in `Demo System - Event Dataset for Call Center (Global v1.1)` dataset. 

![preview-interaction-dataset.png](./images/previewinteractiondataset.png)

The left panel shows the schema structure for this dataset and on the right side you'll see a sample of the data that was ingested.

![explore-interaction-dataset.png](./images/exploreinteractiondataset.png)

Click **Close** to close the **Preview Dataset** window.

## Introduction to Query Service

Query Service is accessed by clicking **Queries** in the left menu.

![select-queries.png](./images/selectqueries.png)

By going to **Log** you'll see the Query List page, which provides you a list of all the queries that have run in this organization, with the latest at the top.

![query-list.png](./images/querylist.png)

Click on any SQL query from the list and observe the details provided in the right rail.

![click-sql-query.png](./images/clicksqlquery.png)

You can scroll the window to see the entire query, or you can click on the icon highlighted below to copy the entire query to your notepad. You do not have to copy the query at this time.

![click-copy-query.png](./images/clickcopyquery.png)

You can't just see the queries that have been executed, this User Interface lets you create new datasets from queries. These datasets can be linked to Adobe Experience Platform's Real-time Customer Profile or can be used as input for Adobe Experience Platform Data Science Workspace.

## Connect PSQL Client to Query Service

Query Service supports clients with a driver for PostgreSQL. In this we'll be using PSQL, a command-line interface, and Power BI or Tableau. Let's connect to PSQL.

Click **Credentials**.

![queries-select-configuration.png](./images/queriesselectconfiguration.png)

You will see the screen below. The screen provides server information and credentials for authenticating to Query Service. For now, we will focus on the right side of the screen which contains a connect command for PSQL. Click the copy button to copy the command to your clipboard.

![copy-psql-connection.png](./images/copypsqlconnection.png)

For Windows: Open the command line by hitting the windows key and typing cmd  and then clicking on the Command Prompt result.

![open-command-prompt.png](./images/opencommandprompt.png)

For macOS: Open the terminal.app via spotlight search:

![open-terminal-osx.png](./images/openterminalosx.png)

Paste the connect command that you have copied from the Query Service UI and hit enter in the command prompt window:

Windows:

![command-prompt-connected.png](./images/commandpromptconnected.png)

MacOS:

![command-prompt-paste-osx.png](./images/commandpromptpasteosx.png)

You are now connected to Query Service using PSQL.

In the next exercises, there will be quite some interaction with this window. We will refer to it as your **PSQL command-line interface**.

Now you are ready to start submitting queries.

## Next Steps

Go to [2.1.3 Using the Query Service](./ex3.md){target="_blank"}

Go back to [Query Service](./query-service.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
