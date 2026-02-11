---
title: Use Cursor.ai to develop your project
description: Use Cursor.ai to develop your project
kt: 5342
doc-type: tutorial
---
# 1.7.2 Use Cursor.ai to develop your project

## 1.7.2.1 Set up your directory & tools

On your desktop, create a new directory with the name `--aepUserLdap---commerce`

![Commerce & Agentic](./images/cursorai1.png)

Right-click your folder and select **New Terminal at Folder**.

![Commerce & Agentic](./images/cursorai2.png)

You should then see this.

![Commerce & Agentic](./images/cursorai3.png)

You now need to clone an existing Github repository, which you can view [https://github.com/adobe/commerce-integration-starter-kit](https://github.com/adobe/commerce-integration-starter-kit).

This repository is Adobe's integration starter kit that uses Adobe Developer App Builder to improve real-time connection reliability and reduce the time-to-market for integrations between Adobe Commerce and other back-office systems, such as ERPs, CRMs, and PIMs.

![Commerce & Agentic](./images/cursorai4.png)

There are several ways to clone this repository, in this example Terminal is used.

Enter the following command in your Terminal window and execute it.

`git clone https://github.com/adobe/commerce-integration-starter-kit`

![Commerce & Agentic](./images/cursorai5.png)

After a couple of seconds, you should see this result.

![Commerce & Agentic](./images/cursorai6.png)

Next, you should navigate to the folder that was just created. Enter the following command and then execute it.

`cd commerce-integration-starter-kit`

![Commerce & Agentic](./images/cursorai7.png)

You should then see this.

![Commerce & Agentic](./images/cursorai8.png)

Next, you need to set up the Commerce extensibility tools for Cursor.ai. Enter the following command and then execute it.

`aio commerce extensibility tools-setup`

![Commerce & Agentic](./images/cursorai9.png)

Select **Current directory**.

![Commerce & Agentic](./images/cursorai10.png)

Select **Cursor**.

![Commerce & Agentic](./images/cursorai11.png)

Select **npm**.

![Commerce & Agentic](./images/cursorai12.png)

After a couple of minutes, you should see this.

![Commerce & Agentic](./images/cursorai13.png)

By installing Commerce extensibility tools for Cursor.ai, there is now an MCP server available as part of your Cursor.ai environment. In the next exercises, you'll use that MCP server to help you develop and deploy the app builder project.

## 1.7.2.2 Set up your webhook

For this exercise, you'll need a webhook that needs to be configued so that when an order is created, the order event can be streamed to that webhook. In this exercise, you'll use a sample endpoint using [https://pipedream.com/requestbin](https://pipedream.com/requestbin). 

Go to [https://pipedream.com/requestbin](https://pipedream.com/requestbin), create an account and then create a workspace. Once the workspace is created, you'll see something similar to this. 

Click **copy** to copy the url. You'll need to specify this url in the next exercise. The URL in this example is `https://eodts05snjmjz67.m.pipedream.net`.

![Data Ingestion](./images/webhook1.png)

## 1.7.2.3 Cursor.ai

`I would like to build an app that subscribes to order created events and sends them to a configurable URL with basic authentication`

## Next Steps

Go back to [Intelligent Developer Tools for Adobe Commerce](./aiassisteddev.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}