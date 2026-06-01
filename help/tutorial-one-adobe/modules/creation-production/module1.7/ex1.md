---
title: Getting started with Firefly Creative Production for Enterprise
description: Getting started with Firefly Creative Production for Enterprise
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 7d9ad7ec-7744-4ba6-9c11-c434e6cdef09
TQID: https://experienceleague.adobe.com/2PvTnUAorzI5JGBBWYFe--WFJm1wevkKq7rPOoRmEdM
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
---
# 1.7.1 Getting started with Firefly Creative Production for Enterprise

>[!IMPORTANT]
>
>Your AEM CS sandbox may be hibernated. Given that dehibernating a sandbox takes 10-15 minutes, it would be a good idea to start the dehibernation process now so that you don't have to wait for it at a later time.

>[!IMPORTANT]
>
>Before you begin, read the below instructions!

## Instructions: Partner Lab New Orleans

For this exercise, you need to use:

- **Instance**: **Adobe Tech Insiders**
- **Username**: **adobetechinsiders-XXX@adobeeventlab.com**
- **Password**: use the password that was shared with you

## 1.7.1.1 Remove background

Go to [https://firefly.adobe.com](https://firefly.adobe.com). Click the profile icon in the top right corner and verify you've select the correct instance, which should be `--aepImsOrgName--`.

Go to **Production**.

![Firefly Creative Production for Enterprise](./images/ffcw1.png)

You should then see this. Click **Create workflow (beta)**.

![Firefly Creative Production for Enterprise](./images/ffcw2.png)

To get to know Firefly Creative Production for Enterprise, you'll now implement a basic use case which is focused on removing the background of a specific image.

Change the name of your workflow to `vangeluw - remove background`.

![Firefly Creative Production for Enterprise](./images/ffcw3.png)

Open the **Image**

![Firefly Creative Production for Enterprise](./images/ffcw4.png)

Select **Remove Background**, then drag and drop this node onto the canvas.

You now need to connect an input image node and an output image node to the **Remove Background**.

![Firefly Creative Production for Enterprise](./images/ffcw5.png)

Scroll up and go to **Input and Output**. Click the **Input Images** node and drag it onto the canvas.

![Firefly Creative Production for Enterprise](./images/ffcw6.png)

You should then have this. Connect the **Input Images** node to the **Remove Background** node by hovering over the blue dot next to **Image** on the **Input Images** node, and drawing a line to the blue dot next to **Input Image** on the **Remove Background** node.

![Firefly Creative Production for Enterprise](./images/ffcw7.png)

You should then have this. Next, click the **Output Images** node and drag it onto the canvas.

![Firefly Creative Production for Enterprise](./images/ffcw8.png)

You should then have this. Connect the **Remove Background** node to the **Output Images** node by hovering over the blue dot next to **Output Image** on the **Remove Background** node, and drawing a line to the blue dot next to **Image** on the **Output Images** node.

![Firefly Creative Production for Enterprise](./images/ffcw9.png)

You should then have this.

![Firefly Creative Production for Enterprise](./images/ffcw10.png)

Your basic workflow is now ready to test. Download the image [phone.png](./assets/phone.png) to your desktop.

![Firefly Creative Production for Enterprise](./images/ffcw11.png)

Go back to your workflow. Click the **Drag and drop** area of the **Input Images** node.

![Firefly Creative Production for Enterprise](./images/ffcw11a.png)

Select the file **phone.png**. Click **Open**.

![Firefly Creative Production for Enterprise](./images/ffcw12.png)

You should then see this. Click **Run**.

![Firefly Creative Production for Enterprise](./images/ffcw13.png)

After 1-2 minuntes, you should see this result.

![Firefly Creative Production for Enterprise](./images/ffcw14.png)

## 1.7.1.2 Remove background + Crop

You should now add a **Crop** node to the canvas. In the menu, go to **Image** and scroll down to find **Crop**. Drag it onto the canvas.

![Firefly Creative Production for Enterprise](./images/ffcw15.png)

Position the **Crop** node between the **Remove Background** node and the **Output Image** node. 

You now need to remove the connection between the **Remove Background** node and the **Output Image** node. You can do that by double-clicking the line between both nodes.

![Firefly Creative Production for Enterprise](./images/ffcw16.png)

You should then have this. Connect the **Remove Background** node to the **Crop** node, and then connect the **Crop** node to the **Output Image** node.

![Firefly Creative Production for Enterprise](./images/ffcw17.png)

Check the checkbox to **Auto Crop**, and then you can test your workflow by clicking **Run**.

![Firefly Creative Production for Enterprise](./images/ffcw18.png)

After 1-2 minutes, you should see this, which shows an image with a different resolution now.

![Firefly Creative Production for Enterprise](./images/ffcw19.png)

## 1.7.1.3 Remove background + Crop + Composite Image

In the menu, under **Image** select a **Composite Images (2D)** node and drag it onto the canvas.

![Firefly Creative Production for Enterprise](./images/ffcw20.png)

Add a second connection to the **Crop** node, by connecting the blue dot next to **Cropped image** to the blue dot next to **Input image** on the **Composite Images (2D)** node.

![Firefly Creative Production for Enterprise](./images/ffcw21.png)

In the menu, under **Input and Output**, select an **Input Text** node and drag it onto the canvas. 

Connect the green dot next to **Text** on the **Input Text** node to the green dot next to **Prompt** on the **Composite Images (2D)** node.

![Firefly Creative Production for Enterprise](./images/ffcw22.png)

You should then have this. Enter the below prompt in the **Input Text** node.

`magazine quality photo of a phone on a red pedestal with a pink background surrounded by origami style pink paper hearts`

In the menu, under **Input and Output**, select an **Output Images** node and drag it onto the canvas. 

Connect the blue dot next to **Composite image** on the **Composite Images (2D)** node to the blue dot next to **Input image** on the **Output Image** node.

Click **Run**.

![Firefly Creative Production for Enterprise](./images/ffcw23.png)

After a couple of minutes, you should see something like this, which shows your original image in a composition based on the prompt that was provided, in a specific resolution.

![Firefly Creative Production for Enterprise](./images/ffcw24.png)

## 1.7.1.4 Remove background + Crop + Composite Image + Generate Video

In the menu, go to **Video**. Select the **Generate Video** node and drag it onto the canvas.

Connect the blue dot next to **Composite image** of the **Composite Images (2D)** node to the blue dot next to **Input image** of the **Generate Video** node.

![Firefly Creative Production for Enterprise](./images/ffcw25.png)

In the menu, go to **Input and Output**. Select the **Input Text** node and drag it onto the canvas.

Connect the green dot next to **Text** on the **Input Text** node to the green dot next to **Prompt** of the **Generate Video** node.

Enter the prompt `background hearts fluttering` in the **Input text** node.

In the menu, go to **Input and Output**. Select the **Output Video** node and drag it onto the canvas.

Connect the purple dot next to **Video Output** of the **Generate Video** node to the purple dot next to **Video** on the **Output Video** node.

Click **Run**.

![Firefly Creative Production for Enterprise](./images/ffcw26.png)

After a couple of videos, you should see this which shows a video based on the combination of the provided image and prompt.

![Firefly Creative Production for Enterprise](./images/ffcw27.png)

## 1.7.1.5 Scale

You've now done this for 1 image. Let's now use this workflow, but for multiple images.

Download these images to your desktop:

- [watch.jpg](./assets/watch.jpg) 
- [airpods.jpg](./assets/airpods.jpg) 

![Firefly Creative Production for Enterprise](./images/ffcw28.png)

In your workflow, go back to the first node, **Input Images**. Remove the currently selected image.

![Firefly Creative Production for Enterprise](./images/ffcw29.png)

Click the **Drag and drop** area.

![Firefly Creative Production for Enterprise](./images/ffcw30.png)

Select the 3 images that you've downloaded. Click **Open**.

![Firefly Creative Production for Enterprise](./images/ffcw31.png)

You should then see this. click **Run**.

![Firefly Creative Production for Enterprise](./images/ffcw32.png)

After several minutes, you should see a similar output, with 3 images being generated, and 3 videos.

![Firefly Creative Production for Enterprise](./images/ffcw33.png)

## 1.7.1.5 Store in AEM Assets CS

In this exercise, you'll store the assets that are created as part of your custom workflow in AEM Assets CS.

You should first create a new folder in your AEM Assets CS environment.

To do that, go to [https://experience.adobe.com](https://experience.adobe.com). Click to open **Experience Manager Assets**.

![Firefly Creative Production for Enterprise](./images/ffcw50.png)

Select your AEM Assets CS environment, which should be named `--aepUserLdap-- - CitiSignal AEM + ACCS`.

![Firefly Creative Production for Enterprise](./images/ffcw51.png)

Go to **Assets** and click **Create Folder**.

![Firefly Creative Production for Enterprise](./images/ffcw52.png)

Enter the name: `--aepUserLdap-- - Firefly Creative Production for Enterprise`. Click **Create**.

![Firefly Creative Production for Enterprise](./images/ffcw53.png)

Go back to your custom workflow and go to the **Output Images** node. Click **Default** and then select **AEM Assets**.

![Firefly Creative Production for Enterprise](./images/ffcw57.png)

You should then see this popup. Select your AEM Assets CS repository, and then select the folder that you just created, which should be named: `--aepUserLdap-- - Firefly Creative Production for Enterprise`. Click **Select**.

![Firefly Creative Production for Enterprise](./images/ffcw54.png)

Go to the **Output Video** node. Click **Default** and then select **AEM Assets**.

![Firefly Creative Production for Enterprise](./images/ffcw55.png)

You should then see this popup. Select your AEM Assets CS repository, and then select the folder that you just created, which should be named: `--aepUserLdap-- - Firefly Creative Production for Enterprise`. Click **Select**.

![Firefly Creative Production for Enterprise](./images/ffcw56.png)

You should then have this. Click **Run**.

![Firefly Creative Production for Enterprise](./images/ffcw56a.png)

After a couple of minutes, you should see the assets that are created become available in the folder in AEM Assets CS.

![Firefly Creative Production for Enterprise](./images/ffcw58.png)

Go back to your workflow. Click **Publish**.

![Firefly Creative Production for Enterprise](./images/ffcw59.png)

You should then see this.

![Firefly Creative Production for Enterprise](./images/ffcw60.png)

Your workflow is now published, and can now be executed programmatically as part of the next exercise.

## Next Steps

Go to [1.7.2 Execute your custom workflow programmatically](./ex2.md){target="_blank"}

Go back to [Firefly Creative Production for Enterprise](./workflowbuilder.md){target="_blank"}

Go back to [All Modules](./../../../overview.md){target="_blank"}
