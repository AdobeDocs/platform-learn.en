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

![Firefly Custom Models](./images/ffcm1.png){zoomable="yes"} 

You may see this message. If you do, click **Agree** to continue.

![Firefly Custom Models](./images/ffcm2.png){zoomable="yes"} 

You should then see this. Click **Train a model**.

![Firefly Custom Models](./images/ffcm3.png){zoomable="yes"} 

Configure the following fields:

- **Name**: use `--aepUserLdap-- - Citi Signal Router Model`
- **Training Mode**: select **Subject (tech preview)**
- **Concept**: enter `router`
- **Save to**: open the dropdown list and click **+ Create New Project**

![Firefly Custom Models](./images/ffcm4.png){zoomable="yes"} 

Give the new project a name: `--aepUserLdap-- - Custom Models`. Click **Create**.

![Firefly Custom Models](./images/ffcm5.png){zoomable="yes"} 

You should then see this. Click **Create**.

![Firefly Custom Models](./images/ffcm6.png){zoomable="yes"} 

You now need to provide the reference images for the Custom Model to be trained. Click **Select images from your computer**.

![Firefly Custom Models](./images/ffcm7.png){zoomable="yes"} 

Download the reference images [here](https://tech-insiders.s3.us-west-2.amazonaws.com/CitiSignal_router.zip). Unzip the download file, which whould give you this.

![Firefly Custom Models](./images/ffcm8.png){zoomable="yes"} 

Navigate to the folder that contains the download image files. Select them all and click **Open**.

![Firefly Custom Models](./images/ffcm9.png){zoomable="yes"} 

You'll then see that your images are being loaded.

![Firefly Custom Models](./images/ffcm10.png){zoomable="yes"}

After a couple of minutes, your images are loaded correctly. You may see that some images have an error, this is due to the caption for the image not having been generated, or not being long enough. Review each image with an error and enter a caption that meets the requirements and describes the image.

![Firefly Custom Models](./images/ffcm11.png){zoomable="yes"} 

Once all images have captions that meet the requirements, you still need to provide a sample prompt. Enter any prompt that uses the word 'router'. Once you've done that, you can start training your model. Click **Train**.

![Firefly Custom Models](./images/ffcm12.png){zoomable="yes"} 

You'll then see this. Training your model may take 20-30mins or longer.

![Firefly Custom Models](./images/ffcm13.png){zoomable="yes"} 

After 20-30mins, your model is now trained and can be published. Click **Publish**.

![Firefly Custom Models](./images/ffcm14.png){zoomable="yes"} 

Click **Publish** again.

![Firefly Custom Models](./images/ffcm15.png){zoomable="yes"} 

Close the **Share custom model** popup.

![Firefly Custom Models](./images/ffcm16.png){zoomable="yes"} 

## 1.1.4.2 Use your Custom Model in the UI

Go to [https://firefly.adobe.com/cme/train](https://firefly.adobe.com/cme/train). Click your Custom Model to open it. 

![Firefly Custom Models](./images/ffcm19.png){zoomable="yes"}

Click **Preview and test**.

![Firefly Custom Models](./images/ffcm17.png){zoomable="yes"}

You'll then see the sample prompt that you entered before being executed.

![Firefly Custom Models](./images/ffcm18.png){zoomable="yes"} 

## 1.1.4.3 Enable your Custom Model for Firefly Services Custom Models API

Once your Custom Model is trained, it can also be used through the API. In exercise 1.1.1 you already configured your Adobe I/O project for interaction with Firefly Services through the API. 

Go to [https://firefly.adobe.com/cme/train](https://firefly.adobe.com/cme/train). Click your Custom Model to open it. 

![Firefly Custom Models](./images/ffcm19.png){zoomable="yes"}

Click the 3 dots **...** and then click **Share**.

![Firefly Custom Models](./images/ffcm20.png){zoomable="yes"} 

In order to access a Firefly Custom Model, the Custom Model needs to be shared to the **Technical Account ID** of our Adobe I/O Project.

To retrieve your **Technical Account ID**, go to [https://developer.adobe.com/console/projects](https://developer.adobe.com/console/projects). Click to open your Project, which is named `--aepUserLdap-- Firefly`.

![Firefly Custom Models](./images/ffcm24.png){zoomable="yes"} 

Click **OAuth Server-to-Server**.

![Firefly Custom Models](./images/ffcm25.png){zoomable="yes"} 

Click to copy your **Technical Account ID**.

![Firefly Custom Models](./images/ffcm23.png){zoomable="yes"} 

Paste your **Technical Account ID** and click **Invite to edit**.

![Firefly Custom Models](./images/ffcm21.png){zoomable="yes"} 

The **Technical Account ID** should now be able to access the Custom Model.

![Firefly Custom Models](./images/ffcm22.png){zoomable="yes"}

## 1.1.4.4 Interact with Firefly Services Custom Models API

In Exercise 1.1.1 Getting started with Firefly Services, you downloaded this file: [postman-ff.zip](./../../../assets/postman/postman-ff.zip) to your local desktop and you then imported that collection in Postman.

Open Postman and go to the folder **FF - Custom Models API**.

![Firefly Custom Models](./images/ffcm30.png){zoomable="yes"} 

Open the request **1. FF - getCustomModels** and click **Send**.

![Firefly Custom Models](./images/ffcm31.png){zoomable="yes"} 

You should see the Custom Model that you created before, which is named `--aepUserLdap-- - Citi Signal Router Model`, as part of the response. The field **assetId** is the unique identifier of your Custom Model, which will be referenced in the next request.

![Firefly Custom Models](./images/ffcm32.png){zoomable="yes"} 

Open the request **2. Generate Images Async**. In this example, you'll request 2 variations to be generated based on your Custom Model. Feel free to update the prompt which in this case is `a white router on a volcano in Africa`.

Click **Send**.

![Firefly Custom Models](./images/ffcm33.png){zoomable="yes"} 

The response contains a field **jobId**. The job to generate these 2 images is now running and you can check the status by using the next request.

![Firefly Custom Models](./images/ffcm34.png){zoomable="yes"} 

Open the request **3. Get CM Status** and click **Send**. You should then see that the status is set to running.

![Firefly Custom Models](./images/ffcm35.png){zoomable="yes"} 

After a couple of minutes, click **Send** again for the request **3. Get CM Status**. You should then see that the status changed to **succeeded** and you should see two image URLs as part of the output. Click to open both files.

![Firefly Custom Models](./images/ffcm36.png){zoomable="yes"}

This is the first image that was generated in this example.

![Firefly Custom Models](./images/ffcm37.png){zoomable="yes"}

This is the second image that was generated in this example.

![Firefly Custom Models](./images/ffcm38.png){zoomable="yes"}

You've now completed this exercise.

## Next Steps

Go to [Summary & benefits](./summary.md){target="_blank"}

Go back to [Working with Photoshop APIs](./ex3.md){target="_blank"}

Go back to [Overview of Adobe Firefly Services](./firefly-services.md){target="_blank"}
