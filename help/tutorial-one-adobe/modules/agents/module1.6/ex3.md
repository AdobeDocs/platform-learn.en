---
title: Scale Content Fragments with ChatGPT & MCP Server
description: Scale Content Fragments with ChatGPT & MCP Server
kt: 5342
doc-type: tutorial
exl-id: b7105351-e9de-4b2c-b3d7-2d4c8627f852
---
# 1.6.3 Scale Content Fragments with ChatGPT & MCP Server

>[!IMPORTANT]
>
>Your AEM CS sandbox may be hibernated. Given that dehibernating a sandbox takes 10-15 minutes, it would be a good idea to start the dehibernation process now so that you don't have to wait for it at a later time.

>[!IMPORTANT]
>
>Before you begin, read the below instructions!

## Instructions: Partner Lab New Orleans

For this exercise, you need to use:

- **Instance**: **Adobe Tech Insiders**
- **Username**: adobetechinsiders-XXX@adobeeventlab.com
- **Password**: use the password that was shared with you
- **AEM Program**: Tech Insiders - AEM + ACCS XXX which you can access through [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)
- **GitHub repository**: [https://github.com/woutervangeluwe/techinsidersXXX-citisignal-aem-accs](https://github.com/woutervangeluwe/techinsidersXXX-citisignal-aem-accs)

## 1.6.3.1 Create Content Fragment Model

Go back to your Adobe Experience Manager Author environment, to **Tools** and then go to **Configuration Browser**.

![AEM Agents](./images/aemagentscfm1.png)

Click **Create**.

![AEM Agents](./images/aemagentscfm2.png)

Use `Content Fragments` for the fields **Title** and **Name**.

Make sure the options **Content Fragment Models** and **GraphQL Persisted Queries** are both enabled.

Click **Create**.

![AEM Agents](./images/aemagentscfm3.png)

Go back to your Adobe Experience Manager Author environment and then go to **Content Fragments**.

![AEM Agents](./images/aemagentscf1.png)

Go to **Content Fragment Models**, select your configuration **Content Fragments** and then click **Create**.

![AEM Agents](./images/aemagentscfm4.png)

Use the name `--aepUserLdap-- - CitiSignal CFM`. Click **Create and open**.

![AEM Agents](./images/aemagentscfm5.png)

You should then see this. Drag and drop a **Single line text** field onto the canvas.

![AEM Agents](./images/aemagentscfm6.png)

Change the field **Field label** to `Header`.

![AEM Agents](./images/aemagentscfm7.png)

Go back to **Data Types**. Drag and drop a **Single line text** field onto the canvas.

![AEM Agents](./images/aemagentscfm8.png)

Change the field **Field label** to `Subheader`.

![AEM Agents](./images/aemagentscfm9.png)

Go back to **Data Types**. Drag and drop a **Multi line text** field onto the canvas.

![AEM Agents](./images/aemagentscfm10.png)

Change the field **Field label** to `Detail Description`.

![AEM Agents](./images/aemagentscfm11.png)

Go back to **Data Types**. Drag and drop a **Single line text** field onto the canvas.

![AEM Agents](./images/aemagentscfm12.png)

Change the field **Field label** to `CTA Text`.

![AEM Agents](./images/aemagentscfm13.png)

Go back to **Data Types**. Drag and drop a **Single line text** field onto the canvas.

![AEM Agents](./images/aemagentscfm14.png)

Change the field **Field label** to `CTA Link`. Click **Save**.

![AEM Agents](./images/aemagentscfm15.png)

You should then see this.

![AEM Agents](./images/aemagentscfm16.png)

Select your content fragment model and click **Publish**.

![AEM Agents](./images/aemagentscfm17.png)

Click **Publish**.

![AEM Agents](./images/aemagentscfm18.png)

## 1.6.3.2 Create Content Fragment

Go back to your Adobe Experience Manager Author environment and then go to **Content Fragments**.

![AEM Agents](./images/aemagentscf1.png)

You should then see this. Click **Create** and then select **Folder**.

![AEM Agents](./images/aemagentscf2.png)

Enter the title: `--aepUserLdap-- - CF`. Click **Create**.

![AEM Agents](./images/aemagentscf3.png)

Go back to your Adobe Experience Manager Author environment and then go to **Assets**.

![AEM Agents](./images/aemagentscfmm1.png)

Go to **Files**.

![AEM Agents](./images/aemagentscfmm2.png)

Select the folder you just created, which should be named `--aepUserLdap-- - CF` and click **Properties**.

![AEM Agents](./images/aemagentscfmm3.png)

Go to **Cloud Services** and then click the **folder** icon.

![AEM Agents](./images/aemagentscfmm4.png)

Select the cloud configuration you created before, which should be named **Content Fragments**. Click **Select**.

![AEM Agents](./images/aemagentscfmm5.png)

You shoudl then see this. Click **Save & Close**.

![AEM Agents](./images/aemagentscfmm6.png)

Go back to your Adobe Experience Manager Author environment and then go to **Content Fragments**.

![AEM Agents](./images/aemagentscf1.png)

You should then see this. Click **Create** and then select **Content Fragment**.

![AEM Agents](./images/aemagentscf4.png)

Select the **Content Fragment Model** you created before, which should be named `--aepUserLdap-- - CitiSignal CFM`. Use the name `--aepUserLdap-- CitiSignal Fiber Max`.

Click **Create and open**.

![AEM Agents](./images/aemagentscf5.png)

You should then see this.

![AEM Agents](./images/aemagentscf5a.png)

Fill out the fields like this:

- **Header**: `CitiSignal Fiber Max`
- **Subheader**: `Experience high speed internet now`
- **Detail Description**:

```
Experience the future of connectivity with CitiSignal Fiber Max, the ultimate solution for high-speed internet. Designed for homes and businesses that demand performance, Fiber Max delivers blazing-fast fiber speeds, ensuring seamless streaming, ultra-responsive gaming, and crystal-clear video calls.

Key Features:

Unmatched Speed: Enjoy lightning-fast downloads and uploads powered by cutting-edge fiber technology.
Reliable Performance: Consistent connectivity for work, entertainment, and everything in between.
Future-Ready: Built to handle the growing demands of smart homes and digital lifestyles.
Unlimited Potential: No data caps, no throttling—just pure speed.
Why Choose CitiSignal Fiber Max? Stay ahead with internet that works as hard as you do. Whether you're powering a remote office or streaming in 4K, Fiber Max ensures you never miss a beat.
```

**CTA Text**: `Upgrade now by signing your new contract!`
**CTA Link**: `https://techinsiders68.adobedemosystem.com/`

Click **Publish** and then select **Now**.

![AEM Agents](./images/aemagentscf6.png)

Click **Publish**.

![AEM Agents](./images/aemagentscf7.png)

## 1.6.3.3 Configure MCP server in ChatGPT

>[!NOTE]
>
>Using Adobe Marketing Agent in ChatGPT requires the following:
>- a paid version of OpenAI's ChatGPT Enterprise
>- using the ChatGPT Enterprise web client

Go to [https://chatgpt.com/](https://chatgpt.com/){target="_blank"} and log in using your account details. Once you're logged in, you should see this. Click your username and then select **Settings**.

![ChatGPT](./images/chatgpt2.png)

Go to **Apps** and then select **Advanced settings**.

![ChatGPT](./images/chatgpt3.png)

Turn on **Developer mode** and then click **Back**.

![ChatGPT](./images/chatgpt4.png)

Click **Create app**.

![ChatGPT](./images/chatgpt5.png)

Fill out the fields like this:

- **Name**: `aem`
- **MCP Server URL**: `https://mcp.adobeaemcloud.com/adobe/mcp/content`
- **Authentication**: `OAuth`

Check the checkbox for **I understand and want to continue**.

Click **Create**.

![ChatGPT](./images/chatgpt6.png)

ChatGPT will now attempt to connect to your Adobe account. Select **Allow Access** and then you'll have to log in with your Adobe account.

Once you've logged in successfully, you should see that your Adobe Marketing Agent is now connected successfully.

![ChatGPT](./images/chatgpt8.png)

## 1.6.3.4 Use AEM MCP server in ChatGPT

Close this window.

![Agent Orchestrator](./images/chatgpt8.png)

You should then see this. Click the **+** icon, go to **More** and then select **aem**.

![Agent Orchestrator](./images/chatgpt10.png)

Enter the following prompt and click **Send**.

```
I just created a new custom mcp server named 'aem'. what can I do with that?
```

![Agent Orchestrator](./images/chatgpt11.png)

You should then see something like this. Enter the following prompt and click **Send**.

```
use the author url https://author-pXXXXXX-eXXXXXXX.adobeaemcloud.com/ from now on
```

![Agent Orchestrator](./images/chatgpt12.png)

You should then see something like this. Enter the following prompt and click **Send**.

```
find the content fragment --aepUserLdap-- - CitiSignal Fiber Max and make a variation called --aepUserLdap-- - CitiSignal Fiber Max (FR), then translate all fields into french
```

![Agent Orchestrator](./images/chatgpt13.png)

Click **CreateFragmentVariation**.

![Agent Orchestrator](./images/chatgpt14.png)

Click **UpdateFragment**.

![Agent Orchestrator](./images/chatgpt15.png)

You should then see this. Your fragment variation has been created successfully.

![Agent Orchestrator](./images/chatgpt16.png)

You can now see your new variation in the AEM UI as well.

![Agent Orchestrator](./images/chatgpt17.png)

Next, use ChatGPT to translate your content fragment into more variations. Enter the following prompt and click **Send**.

```
now do the same thing for the 5 top country's languages that CitiSignal does business with
```

![Agent Orchestrator](./images/chatgpt18.png)

Confirm your language choice.

![Agent Orchestrator](./images/chatgpt23.png)

Click **CreateFragmentVariation**.

![Agent Orchestrator](./images/chatgpt22.png)

Click **UpdateFragment**.

![Agent Orchestrator](./images/chatgpt24.png)

Repeat this process for each of the languages you selected. Once done, you should see something like this.

![Agent Orchestrator](./images/chatgpt26.png)

Go back to your AEM UI and refresh your screen. You can now see your new variations in your content fragment.

![Agent Orchestrator](./images/chatgpt27.png)

## Next Steps

Go Back to [AEM & Agents](./aemagents.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}

