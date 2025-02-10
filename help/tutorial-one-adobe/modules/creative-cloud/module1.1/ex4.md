---
title: Firefly Custom Models API
description: Working with Firefly Custom Models API
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 330f4492-d0df-4298-9edc-4174b0065c9a
---
# 1.1.4 Firefly Custom Models API

## 1.1.4.1 Configure your Custom Model

Go to [https://firefly.adobe.com/](https://firefly.adobe.com/). Click **Custom Models**.

![Summary & benefits](./images/ffcm1.png) 

You may see this message. If you do, click **Agree** to continue.

![Summary & benefits](./images/ffcm2.png) 

You should then see this. Click **Train a model**.

![Summary & benefits](./images/ffcm3.png) 

Configure the following fields:

- **Name**: use `--aepUserLdap-- - Citi Signal Router Model`
- **Training Mode**: select **Subject (tech preview)**
- **Concept**: enter `router`
- **Save to**: open the dropdown list and click **+ Create New Project**

![Summary & benefits](./images/ffcm4.png) 

Give the new project a name: `--aepUserLdap-- - Custom Models`. Click **Create**.

![Summary & benefits](./images/ffcm5.png) 

You should then see this. Click **Create**.

![Summary & benefits](./images/ffcm6.png) 

You now need to provide the reference images for the Custom Model to be trained. Click **Select images from your computer**.

![Summary & benefits](./images/ffcm7.png) 

Download the reference images [here](https://tech-insiders.s3.us-west-2.amazonaws.com/CitiSignal_router.zip). Unzip the download file, which whould give you this.

![Summary & benefits](./images/ffcm8.png) 

Navigate to the folder that contains the download image files. Select them all and click **Open**.

![Summary & benefits](./images/ffcm9.png) 

You'll then see that your images are being loaded.

![Summary & benefits](./images/ffcm10.png)

After a couple of minutes, your images are loaded correctly. You may see that some images have an error, this is due to the caption for the image not having been generated, or not being long enough. Review each image with an error and enter a caption that meets the requirements and describes the image.

![Summary & benefits](./images/ffcm11.png) 

Once all images have captions that meet the requirements, you still need to provide a sample prompt. Enter any prompt that uses the word 'router'. Once you've done that, you can start training your model. Click **Train**.

![Summary & benefits](./images/ffcm12.png) 

You'll then see this. Training your model may take 20-30mins or longer.

![Summary & benefits](./images/ffcm13.png) 

After 20-30mins, your model is now trained and can be published. Click **Publish**.

![Summary & benefits](./images/ffcm14.png) 

Click **Publish** again.

![Summary & benefits](./images/ffcm15.png) 

Close the **Share custom model** popup.

![Summary & benefits](./images/ffcm16.png) 

## 1.1.4.2 Use your Custom Model in the UI

Go to [https://firefly.adobe.com/cme/train](https://firefly.adobe.com/cme/train). Click your Custom Model to open it. 

![Summary & benefits](./images/ffcm19.png)

Click **Preview and test**.

![Summary & benefits](./images/ffcm17.png)

You'll then see the sample prompt that you entered before being executed.

![Summary & benefits](./images/ffcm18.png) 

## 1.1.4.3 Use your Custom Model with the API

Once your Custom Model is trained, it can also be used through the API. In exercise 1.1.1 you already configured your Adobe I/O project for interaction with Firefly Services through the API. 

## Next Steps

Go to [Summary & benefits](./summary.md){target="_blank"}

Go back to [Working with Photoshop APIs](./ex3.md){target="_blank"}

Go back to [Overview of Adobe Firefly Services](./firefly-services.md){target="_blank"}
