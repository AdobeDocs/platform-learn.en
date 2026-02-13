---
title: Getting started with Firefly Custom Workflows
description: Getting started with Firefly Custom Workflows
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
---
# 1.7.1 Getting started with Firefly Custom Workflows

[!BADGE Beta]

+++Beta Details
By using the Adobe Marketing Agent with Microsoft 365 Copilot Beta, You hereby acknowledge that the Beta is provided “as is” without warranty of any kind. Adobe shall have no obligation to maintain, correct, update, change, modify or otherwise support the Beta. You are advised to use caution and not to rely in any way on the correct functioning or performance of such Beta and/or accompanying materials. The Beta is considered Confidential Information of Adobe.  Any “Feedback” (information regarding the Beta including but not limited to problems or defects you encounter while using the Beta, suggestions, improvements, and recommendations) provided by You to Adobe is hereby assigned to Adobe including all rights, title, and interest in and to such Feedback.

+++

Go to [https://firefly.adobe.com](https://firefly.adobe.com). Click the profile icon in the top right corner and verify you've select the correct instance, which should be `--aepImsOrgName--`.

Go to **Production**.

![Firefly Custom Workflows](./images/ffcw1.png)

You should then see this. Click **Create workflow (beta)**.

![Firefly Custom Workflows](./images/ffcw2.png)

## 1.7.1.1 Remove background

To get to know Firefly Custom Workflows, you'll now implement a basic use case which is focused on removing the background of a specific image.

Change the name of your workflow to `vangeluw - remove background`.

![Firefly Custom Workflows](./images/ffcw3.png)

Open the **Image**

![Firefly Custom Workflows](./images/ffcw4.png)

Select **Remove Background**, then drag and drop this node onto the canvas.

You now need to connect an input image node and an output image node to the **Remove Background**.

![Firefly Custom Workflows](./images/ffcw5.png)

Scroll up and go to **Input and Output**. Click the **Input Images** node and drag it onto the canvas.

![Firefly Custom Workflows](./images/ffcw6.png)

You should then have this. Connect the **Input Images** node to the **Remove Background** node by hovering over the blue dot next to **Image** on the **Input Images** node, and drawing a line to the blue dot next to **Input Image** on the **Remove Background** node.

![Firefly Custom Workflows](./images/ffcw7.png)

You should then have this. Next, click the **Output Images** node and drag it onto the canvas.

![Firefly Custom Workflows](./images/ffcw8.png)

You should then have this. Connect the **Remove Background** node to the **Output Images** node by hovering over the blue dot next to **Output Image** on the **Remove Background** node, and drawing a line to the blue dot next to **Image** on the **Output Images** node.

![Firefly Custom Workflows](./images/ffcw9.png)

You should then have this.

![Firefly Custom Workflows](./images/ffcw10.png)

Your basic workflow is now ready to test. Download the image [phone.png](./assets/phone.png) to your desktop.

![Firefly Custom Workflows](./images/ffcw11.png)

Go back to your workflow. Click the **Drag and drop** area of the **Input Images** node.

![Firefly Custom Workflows](./images/ffcw11a.png)

Select the file **phone.png**. Click **Open**.

![Firefly Custom Workflows](./images/ffcw12.png)

You should then see this. Click **Run**.

![Firefly Custom Workflows](./images/ffcw13.png)

After 1-2 minuntes, you should see this result.

![Firefly Custom Workflows](./images/ffcw14.png)

## 1.7.1.2 Remove background + Crop

You should now add a **Crop** node to the canvas. In the menu, go to **Image** and scroll down to find **Crop**. Drag it onto the canvas.

![Firefly Custom Workflows](./images/ffcw15.png)

Position the **Crop** node between the **Remove Background** node and the **Output Image** node. 

You now need to remove the connection between the **Remove Background** node and the **Output Image** node. You can do that by double-clicking the line between both nodes.

![Firefly Custom Workflows](./images/ffcw16.png)

You should then have this. Connect the **Remove Background** node to the **Crop** node, and then connect the **Crop** node to the **Output Image** node.

![Firefly Custom Workflows](./images/ffcw17.png)

Check the checkbox to **Auto Crop**, and then you can test your workflow by clicking **Run**.

![Firefly Custom Workflows](./images/ffcw18.png)

After 1-2 minutes, you should see this, which shows an image with a different resolution now.

![Firefly Custom Workflows](./images/ffcw19.png)

## 1.7.1.3 Remove background + Crop + Composite Image

In the menu, under **Image** select a **Composite Images (2D)** node and drag it onto the canvas.

![Firefly Custom Workflows](./images/ffcw20.png)

Add a second connection to the **Crop** node, by connecting the blue dot next to **Cropped image** to the blue dot next to **Input image** on the **Composite Images (2D)** node.

![Firefly Custom Workflows](./images/ffcw21.png)

In the menu, under **Input and Output**, select an **Input Text** node and drag it onto the canvas. 

Connect the green dot next to **Text** on the **Input Text** node to the green dot next to **Prompt** on the **Composite Images (2D)** node.

![Firefly Custom Workflows](./images/ffcw22.png)

You should then have this. Enter the below prompt in the **Input Text** node.

`magazine quality photo of a phone on a red pedestal with a pink background surrounded by origami style pink paper hearts`

In the menu, under **Input and Output**, select an **Output Images** node and drag it onto the canvas. 

Connect the blue dot next to **Composite image** on the **Composite Images (2D)** node to the blue dot next to **Input image** on the **Output Image** node.

Click **Run**.

![Firefly Custom Workflows](./images/ffcw23.png)

After a couple of minutes, you should see something like this, which shows your original image in a composition based on the prompt that was provided, in a specific resolution.

![Firefly Custom Workflows](./images/ffcw24.png)

## 1.7.1.4 Remove background + Crop + Composite Image + Generate Video

In the menu, go to **Video**. Select the **Generate Video** node and drag it onto the canvas.

Connect the blue dot next to **Composite image** of the **Composite Images (2D)** node to the blue dot next to **Input image** of the **Generate Video** node.

![Firefly Custom Workflows](./images/ffcw25.png)

In the menu, go to **Input and Output**. Select the **Input Text** node and drag it onto the canvas.

Connect the green dot next to **Text** on the **Input Text** node to the green dot next to **Prompt** of the **Generate Video** node.

Enter the prompt `background hearts fluttering` in the **Input text** node.

In the menu, go to **Input and Output**. Select the **Output Video** node and drag it onto the canvas.

Connect the purple dot next to **Video Output** of the **Generate Video** node to the purple dot next to **Video** on the **Output Video** node.

Click **Run**.

![Firefly Custom Workflows](./images/ffcw26.png)

After a couple of videos, you should see this which shows a video based on the combination of the provided image and prompt.

![Firefly Custom Workflows](./images/ffcw27.png)

## 1.7.1.4 Scale

You've now done this for 1 image. Let's now use this workflow, but for multiple images.

Download these images to your desktop:

- [watch.png](./assets/watch.png) 
- [airpods.png](./assets/airpods.png) 

![Firefly Custom Workflows](./images/ffcw28.png)

In your workflow, go back to the first node, **Input Images**. Remove the currently selected image.

![Firefly Custom Workflows](./images/ffcw29.png)

Click the **Drag and drop** area.

![Firefly Custom Workflows](./images/ffcw30.png)

Select the 3 images that you've downloaded. Click **Open**.

![Firefly Custom Workflows](./images/ffcw31.png)

You should then see this. click **Run**.

![Firefly Custom Workflows](./images/ffcw32.png)

After several minutes, you should see a similar output, with 3 images being generated, and 3 videos.

![Firefly Custom Workflows](./images/ffcw33.png)

## Next Steps

Go to [...](./ex1.md){target="_blank"}

Go back to [Workflow Builder](./workflowbuilder.md){target="_blank"}

Go back to [All Modules](./../../../overview.md){target="_blank"}
