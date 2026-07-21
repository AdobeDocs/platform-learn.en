---
title: Getting started with AEM Agents
description: Getting started with AEM Agents
kt: 5342
doc-type: tutorial
exl-id: cb1bf6f0-f329-4e38-ba64-36ffdc3b8bd4
---
# 1.6.1 Getting started with AEM Agents

>[!IMPORTANT]
>
>Your AEM CS sandbox may be hibernated. Given that dehibernating a sandbox takes 10-15 minutes, it would be a good idea to start the dehibernation process now so that you don't have to wait for it at a later time.

>[!IMPORTANT]
>
>Before you begin, read the below instructions!

## Instructions for live workshops

For this exercise, you need to use:

- **Instance**: **Adobe Tech Insiders**
- **Username**: adobetechinsiders-XXX@adobeeventlab.com
- **Password**: use the password that was shared with you
- **AEM Program**: Tech Insiders - AEM + ACCS XXX which you can access through [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)
- **GitHub repository**: [https://github.com/woutervangeluwe/techinsidersXXX-citisignal-aem-accs](https://github.com/woutervangeluwe/techinsidersXXX-citisignal-aem-accs)

## 1.6.1.1 Discovery Agent

The Adobe Experience Manager (AEM) Discovery Agent is an AI-powered tool within AEM as a Cloud Service that enables users to find, retrieve, and utilize content—including Assets, Content Fragments, and Adaptive Forms—using natural language prompts. It eliminates the need for manual, click-heavy, or complex filtering by understanding intent and searching across the repository.

In order to use **Discovery Agent**, you will first create some Tags in Adobe Experience Manager, and you will then tag some assets using those tags. Once that's done, you'll be able to use AI Assistant to discover assets in an easy and business-friendly way.

Go to [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com). The org you should select is `--aepImsOrgName--`. 

### Create and use Tags with Assets

Click to open your Cloud Manager Program, which should use of the below naming options:

- **`Tech Insiders - AEM + ACCS X`** whereby X stands for the number that was assigned to you.
- **`Tech Insiders On Demand - AEM + ACCS X`** whereby X stands for the number that was assigned to you.
- **`--aepUserLdap-- - CitiSignal AEM+ACCS`**, in this case you don't have a number as you're using your own AEM program that you created yourself.

In this example, the program **Tech Insiders - AEM + ACCS 100** will be used. You should use your own program.

![AEM Agents](./images/aemagents1.png)

Click the URL of your environment to open it.

![AEM Agents](./images/aemagents2.png)

Click the **tools** icon.

![AEM Agents](./images/aemagents3.png)

Under **General**, click **Tagging**.

![AEM Agents](./images/aemagents4.png)

You should then see this. Click **Create** and then select **Create Namespace**.

![AEM Agents](./images/aemagents5.png)

In the field **Title**, enter: `--aepUserLdap-- - CitiSignal`. Click **Create**.

![AEM Agents](./images/aemagents6.png)

Drill down into the namespace **`--aepUserLdap-- - CitiSignal`** by clicking it. Click **Create** and then select **Create Tag**.

![AEM Agents](./images/aemagents7.png)

In the field **Title**, enter: `--aepUserLdap-- - Campaign`. Click **Submit**.

![AEM Agents](./images/aemagents8.png)

Select the tag **`--aepUserLdap-- - Campaign`** by clicking it. Click **Create** and then select **Create Tag**.

![AEM Agents](./images/aemagents9.png)

In the field **Title**, enter: `--aepUserLdap-- - Winter 2026`. Click **Submit**.

![AEM Agents](./images/aemagents10.png)

Select the tag **Campaign** by clicking it. Click **Create** and then select **Create Tag**.

![AEM Agents](./images/aemagents11.png)

In the field **Title**, enter: `--aepUserLdap-- - Spring 2026`. Click **Submit**.

![AEM Agents](./images/aemagents12.png)

You should now have this.

![AEM Agents](./images/aemagents13.png)

Click **Adobe Experience Manager** and then click **Assets**.

![AEM Agents](./images/aemagents14.png)

Click **Files**.

![AEM Agents](./images/aemagents15.png)

Click the folder **CitiSignal** to open it.

![AEM Agents](./images/aemagents16.png)

Click **Create** and then select **Files**.

![AEM Agents](./images/aemagents17.png)

Download the file [citisignal-images-campaign.zip](./assets/citisignal-images-campaign.zip) and unzip it onto your desktop.

![AEM Agents](./images/aemagents17a.png)

Select the 3 files that you just downloaded and click **open**.

![AEM Agents](./images/aemagents18.png)

Click **Upload**.

![AEM Agents](./images/aemagents19.png)

You should then see this.

![AEM Agents](./images/aemagents20.png)

Select the first image (citisignal_lion.png) and then click **Properties**.

![AEM Agents](./images/aemagents21.png)

Click the **folder**-icon under Tags.

![AEM Agents](./images/aemagents22.png)

Select the tag **`--aepUserLdap-- - Spring 2026`** and click **Select**. 

![AEM Agents](./images/aemagents23.png)

Click **Save & Close**.

![AEM Agents](./images/aemagents23a.png)

Repeat these for these images:

- `citisignal_leopard.png`
- `citisignal_gorilla.png`
- `citisignal_neon_rabbit.png`

Once you've selected that tag for all images, go to **Experience Manager Assets**.

![AEM Agents](./images/aemagents24.png)

Click the **profile** icon at the top right of your screen. Click **Switch view**.

![AEM Agents](./images/aemagents25.png)

You should then see this.

![AEM Agents](./images/aemagents26.png)

Doubmle-click to open the first image.

![AEM Agents](./images/aemagents27.png)

Select **Approved** and then click **Save**.

![AEM Agents](./images/aemagents28.png)

Under **Tags**, you can see the tag that you selected previously.

![AEM Agents](./images/aemagents29.png)

Repeat that process so that all 4 images are approved.

![AEM Agents](./images/aemagents30.png)

Next, go to **My workspace** and click to open **AI Assistant**.

![AEM Agents](./images/aemagents31.png)

Go to [https://experience.adobe.com/#/coworker/chat](https://experience.adobe.com/#/coworker/chat). Sign in using your Adobe account. After logging in, click your user initials in the bottom left part of the screen and make sure you've selected the correct instance and sandbox by changing selecting them as indicated below.

![AEM Agents](./images/aemagentscw1.png)

Enter the following prompt and click **Send**.

```javascript
find all assets tagged with '--aepUserLdap-- - Spring 2026'
```

![AEM Agents](./images/aemagents32.png)

In case you have access to multiple AEM Assets CS environments you will see something like this. Either you can enter the number of your environment, or you can speicfy the full path of your AEM Assets environemtn and then click **Send**.

![AEM Agents](./images/aemagents34.png)

You should then see a similar answer.

![AEM Agents](./images/aemagents35.png)

Click the link on any of the assets.

![AEM Agents](./images/aemagents37.png)

You will then see an enlarged view of the asset you selected, with some metadata.

![AEM Agents](./images/aemagents38.png)

## 1.6.1.2 Experience Production Agent

### Content Update - Assets

The Content Update skill updates existing content — including content fragments, pages, forms and assets — with ease. The agent can perform actions such as updating, removing, replacing, or adding content elements to keep experiences accurate and current. Inputs can be natural language description, and when used with Jira PDFs and screenshots can provide input too.

Go back to the AI Assistant screen. Close the side panel.

![AEM Agents](./images/aemagents40.png)

Select one of the proposed prompts and click **Send**.

`For the first image, generate renditions for Instagram and LinkedIn posts`

![AEM Agents](./images/aemagents40a.png)

After a couple of minutes, you should see a similar response.

![AEM Agents](./images/aemagents41.png)

Review the images that were generated.

![AEM Agents](./images/aemagents42.png)

Feel free to experiment with other prompts. Scroll up and select one of the other proposed prompts, or enter your own, and click **Send**.

`For the first image, generate a mirrored image`

![AEM Agents](./images/aemagents42a.png)

Review the image that was generated.

![AEM Agents](./images/aemagents42b.png)

### Content Update - Pages

Go back to your Adobe Experience Manager Author environment and then go to **Sites**.

![AEM Agents](./images/aemagents43.png)

Go to **CitiSignal**. Click **Create** and select **Page**.

![AEM Agents](./images/aemagents44.png)

Select **Page** and click **Next**.

![AEM Agents](./images/aemagents45.png)

Enter the following values:

- Title: **Fiber Max**
- Name: **fiber-max**
- Page Title: **Fiber Max**

Click **Create**.

![AEM Agents](./images/aemagents46.png)

Select **Open**.

![AEM Agents](./images/aemagents47.png)

You should then see this. 

![AEM Agents](./images/aemagents48.png)

Click in the blank area to select the **section** component. Then, click the plus **+** icon in the right menu and select **Hero**.

![AEM Agents](./images/aemagents49.png)

You should then see this. Click **+ Add** to add an image.

![AEM Agents](./images/aemagents50.png)

Select your assets repository. Then, open the folder **CitiSignal**.

![AEM Agents](./images/aemagents51.png)

Choose the image of the lion that you uploaded earlier. Click **Select**.

![AEM Agents](./images/aemagents52.png)

You should then see this. Click the **text** area to change the text.

![AEM Agents](./images/aemagents53.png)

Paste this text in the are:

```
This winter, be as fast as a lion.
```

Select **Heading 1** and then click **Done**.

![AEM Agents](./images/aemagents54.png)

You should then see this. Go to **Content tree** and select the area **Section**.

![AEM Agents](./images/aemagents55.png)

Click the **+** icon and then select **Cards**.

![AEM Agents](./images/aemagents56.png)

You should then see this. Make sure that in the **Content tree**, **Cards** is selected.

Then, click the button **+** 4 times.

![AEM Agents](./images/aemagents57.png)

You should now see this, where there are 4 **Card** objects in the **Cards** object.

![AEM Agents](./images/aemagents58.png)

Select the first **Card**. Click the **text** area to change the text.

![AEM Agents](./images/aemagents59.png)

Paste the following text. Make sure the first line of text is using **Heading 1**. Click **Done**.

```
99.9% network reliability

Game, video chat and stream on multiple devices with ultra low lag.
```

![AEM Agents](./images/aemagents60.png)

Select the second **Card**. Click the **text** area to change the text.

![AEM Agents](./images/aemagents61.png)

Paste the following text. Make sure the first line of text is using **Heading 1**. Click **Done**.

```
3-year

price lock guarantee

For new and existing Fiber Max customers on all internet plans.

No hidden fees.
```

![AEM Agents](./images/aemagents62.png)

Select the third **Card**. Click the **text** area to change the text.

![AEM Agents](./images/aemagents63.png)

Paste the following text. Make sure the first line of text is using **Heading 1**. Click **Done**.

```
More ways to save

Save over 45% on the best entertainment with CitiSignal
```

![AEM Agents](./images/aemagents64.png)

Select the fourth **Card**. Click the **text** area to change the text.

![AEM Agents](./images/aemagents65.png)

Paste the following text. Make sure the first line of text is using **Heading 1**. Click **Done**.

```
Get Fiber Max now!

Fill out the form here to get started.
```

![AEM Agents](./images/aemagents66.png)

You should now have this. Click **Publish**.

![AEM Agents](./images/aemagents67.png)

Click **Publish** again.

![AEM Agents](./images/aemagents68.png)

Click **Open Page**.

![AEM Agents](./images/aemagents69.png)

Copy the URL of the page as you'll need it next.

The URL should be similar to this: `https://author-pXXXXXX-eXXXXXXX.adobeaemcloud.com/content/CitiSignal/fiber-max.html`.

>[!NOTE]
>
>You will need to use this URL again at a later time so please write it down in a separate word document, or keep it open in a separate tab in your browser.

![AEM Agents](./images/aemagents70.png)

Go back to your CX Enterprise Coworker chat on [https://experience.adobe.com/#/coworker/chat](https://experience.adobe.com/#/coworker/chat).

![AEM Agents](./images/aemagents71.png)

Paste the following prompt and click **send**. Replace XXX in this prompt by the URL that you copied in the previous step.

```
On the page XXX, please make the following changes:

- change the word 'winter' to 'spring'
- change the word 'lion' to 'leopard'
- change the image in the hero block to use the image 'citisignal_leopard.png'
- change the text '99.9% network reliability' to '99.999% network reliability'
```

![AEM Agents](./images/aemagents72.png)

After 1-2 minutes, you should see this. Select the prompt `Proceed` and click **Submit**.

![AEM Agents](./images/aemagents74.png)

A couple of minutes later, you should see a confirmation like this that the changes have been performed. Click the **Preview** link.

![AEM Agents](./images/aemagents75.png)

You now get a visual confirmation of the changes that have been done. This preview page is purely for informational purpose, you can't take action from this page.

![AEM Agents](./images/aemagents76.png)

To take action, click **Edit**. 

![AEM Agents](./images/aemagents75a.png)

In the Universal Editor, you now see all the changes in detail, with the ability the change anything. 

![AEM Agents](./images/aemagents77.png)

Go back to your Coworker chat. Select **Promote** and then click **Submit**.

![AEM Agents](./images/aemagents77a.png)

Refresh your page, you should now see all your changes on the published page.

![AEM Agents](./images/aemagents85.png)

### Content Update - Form Creation

The Form Creation skill now enables users to build adaptive forms through natural language prompts without dependency on development or IT teams. This capability accelerates form development while maintaining brand consistency and allowing business users to create forms without deep technical product knowledge.

Go back to your CX Enterprise Coworker chat on [https://experience.adobe.com/#/coworker/chat](https://experience.adobe.com/#/coworker/chat).

Enter the following prompt and click **send**.

```
Create a new adaptive form using Edge Delivery Services and the existing CitiSignal site, with the following details:
- Form name: "citisignal-fiber-max-interest-2"
- Form fields: 4 text input fields are needed, for "first-name", "last-name", "email" and "city"
```

![AEM Agents](./images/aemagentsforms1.png)

You should then get an answer like this one.

Enter the following prompt and click **send**.

```
can you create the adaptive form for me?
```

![AEM Agents](./images/aemagentsforms2.png)

## Next Steps

Go to [1.6.2 AEM MCP Servers & Cursor](./ex2.md){target="_blank"}

Go Back to [AEM & Agents](./aemagents.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}

