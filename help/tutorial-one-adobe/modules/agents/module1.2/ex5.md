---
title: CX Enterprise Coworker with ChatGPT Enterprise
description: CX Enterprise Coworker with ChatGPT Enterprise
kt: 5342
doc-type: tutorial
---
# 1.2.5 CX Enterprise Coworker with ChatGPT Enterprise

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

## 1.2.5.1 Install the custom MCP server for CX Enterprise Coworker

>[!NOTE]
>
>Using CX Enterprise Coworker in ChatGPT requires the following:
>- a paid version of OpenAI's ChatGPT Enterprise
>- using the ChatGPT Enterprise web client

Go to [https://chatgpt.com/](https://chatgpt.com/) and log in using your account details. Once you're logged in, you should see this. Go to **Plugins**.

![ChatGPT](./images/chatgpt1.png)

Click the **+** icon and then select **Create app**.

![ChatGPT](./images/chatgpt2.png)

Enter the following information:

- **Name**: `--aepUserLdap-- CX Enterprise Coworker`
- **Connection**: enter the URL provided to you by your Adobe contact
- **Authentication**: select `OAuth`
- check the box in front of **I understand and want to continue**

Click **Create**.

![ChatGPT](./images/chatgpt3.png)

Click **Sign in with CX Enterprise Coworker**.

![ChatGPT](./images/chatgpt4.png)

After logging in, you should then see this. CLick **Refresh**.

![ChatGPT](./images/chatgpt5.png)

You should then see this. Close this window and open a new chat.

![ChatGPT](./images/chatgpt6.png)

## 1.2.5.2 Set context in CX Enterprise Coworker

Before interacting further with CX Enterprise Coworker through ChatGPT, the context needs to be set.

For this exercise, the context needs to be set to use:

- **IMS Org**: `--aepImsOrgName--`.

- **Sandbox**: **Prod - One Adobe**

The Sandbox setting helps to identify which sandbox ChatGPT should look at when asking questions.

- **Dataview**: **AdobeOne - Unified Customer Data View**

The Dataview setting helps to identify which dataview ChatGPT should look at when asking questions.

Open a new chat. Enter the following **Prompt** and click the **send** button.

```
using --aepUserLdap-- CX Enterprise Coworker, list sandboxes
```

![Coworker ChatGPT](./images/chatgpt11.png)

You should then see this. Enter the following **Prompt** and click the **send** button.

```
change sandbox to one-adobe
```

![Coworker ChatGPT](./images/chatgpt12.png)

You should then see this. Enter the following **Prompt** and click the **send** button.

```
list dataviews
```

![Coworker ChatGPT](./images/chatgpt13.png)

You should then see this. Enter the following **Prompt** and click the **send** button.

```
switch to AdobeOne - Unified Customer Data View
```

![Coworker ChatGPT](./images/chatgpt14.png)

You should then see this. The context is now set correctly so you can start sending specific prompts next.

![Coworker ChatGPT](./images/chatgpt15.png)

You've now completed this lab.

## Next Steps

Go to [CX Enterprise Coworker and AEM](./ex6.md){target="_blank"}

Go Back to [CX Enterprise Coworker](./coworker.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}