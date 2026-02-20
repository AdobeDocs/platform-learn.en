---
title: Content Production Agent
description: Content Production Agent
kt: 5342
doc-type: tutorial
exl-id: cb1bf6f0-f329-4e38-ba64-36ffdc3b8bd4
---
# 1.6.1 Getting started with AEM Agents

>[!IMPORTANT]
>
>In order to complete this exercise, you need to have access to a working AEM Sites and Assets CS with EDS environment and the various AEM Agents need to be enabled for the IMS Org you're using.
>
>If you don't have such an environment yet, go to exercise [Adobe Experience Manager Cloud Service & Edge Delivery Services](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"}. Follow the instructions there, and you'll have access to such an environment.

>[!IMPORTANT]
>
>If you have previously configured an AEM CS Program with an AEM Sites and Assets CS environment, it may be that your AEM CS sandbox was hibernated. Given that dehibernating such a sandbox takes 10-15 minutes, it would be a good idea to start the dehibernation process now so that you don't have to wait for it at a later time.

## 1.6.1.1 Discovery Agent

The Adobe Experience Manager (AEM) Discovery Agent is an AI-powered tool within AEM as a Cloud Service that enables users to find, retrieve, and utilize content—including Assets, Content Fragments, and Adaptive Forms—using natural language prompts. It eliminates the need for manual, click-heavy, or complex filtering by understanding intent and searching across the repository.

In order to use **Discovery Agent**, you will first create some Tags in Adobe Experience Manager, and you will then tag some assets using those tags. Once that's done, you'll be able to use AI Assistant to discover assets in an easy and business-friendly way.

Go to [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. The org you should select is `--aepImsOrgName--`. 

### Create and use Tags with Assets

Click to open your Cloud Manager Program, which should be called `--aepUserLdap-- - CitiSignal AEM+ACCS`.

![AEM Agents](./images/aemagents1.png)

Click the URL of your environment to open it.

![AEM Agents](./images/aemagents2.png)

Click the **hammer** icon.

![AEM Agents](./images/aemagents3.png)

Under **General**, click **Tagging**.

![AEM Agents](./images/aemagents4.png)

You should then see this. Click **Create** and then select **Create Namespace**.

![AEM Agents](./images/aemagents5.png)

In the field **Title**, enter: `CitiSignal`. Click **Create**.

![AEM Agents](./images/aemagents6.png)

Drill down into the namespace **CitiSignal** by clicking it. Click **Create** and then select **Create Tag**.

![AEM Agents](./images/aemagents7.png)

In the field **Title**, enter: `Campaign`. Click **Submit**.

![AEM Agents](./images/aemagents8.png)

Select the tag **Campaign** by clicking it. Click **Create** and then select **Create Tag**.

![AEM Agents](./images/aemagents9.png)

In the field **Title**, enter: `Winter 2026`. Click **Submit**.

![AEM Agents](./images/aemagents10.png)

Select the tag **Campaign** by clicking it. Click **Create** and then select **Create Tag**.

![AEM Agents](./images/aemagents11.png)

In the field **Title**, enter: `Spring 2026`. Click **Submit**.

![AEM Agents](./images/aemagents12.png)

You should now have this.

![AEM Agents](./images/aemagents13.png)

Click **Adobe Experience Manager** and then click **Assets**.

![AEM Agents](./images/aemagents14.png)

Click **Files**.

![AEM Agents](./images/aemagents15.png)

Double-click the folder **CitiSignal** to open it.

![AEM Agents](./images/aemagents16.png)

Click **Create** and then select **Files**.

![AEM Agents](./images/aemagents17.png)

Download the file [citisignal-images-campaign.zip](./assets/citisignal-images-campaign.zip) and unzip it onto your desktop.

![AEM Agents](./images/aemagents17a.png)

Select. the 3 files that you just downloaded and click **open**.

![AEM Agents](./images/aemagents18.png)

Click **Upload**.

![AEM Agents](./images/aemagents19.png)

You should then see this.

![AEM Agents](./images/aemagents20.png)

Select the first image and then click **Properties**.

![AEM Agents](./images/aemagents21.png)

Click the **folder**-icon under Tags.

![AEM Agents](./images/aemagents22.png)

Select the tag **Spring 2026** and click **Select**. Repeat that process for these images:

- citisignal_lion.png
- citisignal_leopard.png
- citisignal_gorilla.png
- citisignal_rabbit.png

![AEM Agents](./images/aemagents23.png)

Once you've selected that tag for all images, go to **Experience Manager Assets**.

![AEM Agents](./images/aemagents24.png)

Select the repo you're using.

![AEM Agents](./images/aemagents25.png)

Go to **Assets** and open the folder **CitiSignal**.

![AEM Agents](./images/aemagents26.png)

Open the first image.

![AEM Agents](./images/aemagents27.png)

Select **Approved** and then click **Save**.

![AEM Agents](./images/aemagents28.png)

Under **Tags**, you can see the tag that you selected previously.

![AEM Agents](./images/aemagents29.png)

Repeat that process so that all 4 images are approved.

![AEM Agents](./images/aemagents30.png)

Next, go to **My workspace** and click to open **AI Assistant**.

![AEM Agents](./images/aemagents31.png)

Enter the following prompt and click **Send**.

```javascript
find all assets tagged with 'Spring 2026'
```

![AEM Agents](./images/aemagents32.png)

In case you have access to multiple AEM Assets CS environments you will see something like this. Click the proposed answer for the environment you wish to use and then click **Send**.

![AEM Agents](./images/aemagents34.png)

You should then see a similar answer. Click the icon to expand the AI Assistant to full screen.

![AEM Agents](./images/aemagents35.png)

Review the answers.

![AEM Agents](./images/aemagents36.png)

From within the AI Assistant window, you can click to view any of these assets.

![AEM Agents](./images/aemagents37.png)

You will then be taken directly into AEM Assets CS, to that specific image.

![AEM Agents](./images/aemagents38.png)

You can then also review any of the other available metadata.

![AEM Agents](./images/aemagents39.png)

## 1.6.1.2 Experience Production Agent

### Content Update

The Content Update skill updates existing content — including content fragments, pages, forms and assets — with ease. The agent can perform actions such as updating, removing, replacing, or adding content elements to keep experiences accurate and current. Inputs can be natural language description, and when used with Jira PDFs and screenshots can provide input too.

Go back to the AI Assistant screen.

![AEM Agents](./images/aemagents40.png)

Enter the following prompt and click **Send**.

`Generate multiple social media formats (Instagram 1080x1920, Facebook 1200x630, Twitter 1200x675) for the third image`

![AEM Agents](./images/aemagents40a.png)

After a couple of minutes, you should see a similar response.

![AEM Agents](./images/aemagents41.png)

Review the images that were generated.

![AEM Agents](./images/aemagents42.png)

### Form Creation

The Form Creation skill enables users to build adaptive forms through natural language prompts without dependency on development or IT teams. This capability accelerates form development while maintaining brand consistency and allowing business users to create forms without deep technical product knowledge.


## Next Steps

Go Back to [AEM & Agents](./aemagents.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
