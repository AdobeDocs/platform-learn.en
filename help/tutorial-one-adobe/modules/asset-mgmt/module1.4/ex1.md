---
title: Create your assets and dynamic media template
description: Create your assets and dynamic media template
kt: 5342
doc-type: tutorial
---
# 1.4.1 Create your assets and dynamic media template

>[!IMPORTANT]
>
>In order to complete this exercise, you need to have access to a working AEM Assets CS Author environment with AEM Assets Dynamic Media enabled.
>
>If you don't have such an environment, go to [Adobe Experience Manager Cloud Service & Edge Delivery Services](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"}. Follow the instructions there, and you'll have access to such an environment.

>[!IMPORTANT]
>
>If you have previously configured an AEM CS Program with an AEM Assets CS environment, it may be that your AEM CS sandbox was hibernated. Given that dehibernating such a sandbox takes 10-15 minutes, it would be a good idea to start the dehibernation process now so that you don't have to wait for it at a later time.

## 1.4.1.1 Create your Dynamic Media company

Go to [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. The org you should select is `--aepImsOrgName--`. 

![AEM Assets Dynamic Media](./images/aaemassdmcomp1.png)

Scroll down to **Dynamic Media Companies**. Click the **+** icon to create a new Dynamic Media Company.

![AEM Assets Dynamic Media](./images/aaemassdmcomp2.png)

Enter the following information:

- **Company name**: `--aepUserLdap---CitiSignal`.
- **Company region**: select the region that's closest to you.
- **Company admin emails**: enter your admin email.

Click **Create**.

![AEM Assets Dynamic Media](./images/aaemassdmcomp3.png)

You should then see this.

![AEM Assets Dynamic Media](./images/aaemassdmcomp4.png)

You should now receive an email like the one below, which contains your temporary password. To change your password, or to retrieve it in case you didn't receive an email, you should install the **Adobe Dynamic Media Classic desktop app**. You can find installation instructions here: [https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app](https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app). 

Follow the instructions there, and come back here once the app is installed on your system.

Open the **Adobe Dynamic Media Classic desktop app**. If you know your password, then please enter it here and follow the instructions to change it upon first login.

If you don't know your password, click the **Forgot your password** link and follow the instruction to reset your password, to then come back here and log in.

![AEM Assets Dynamic Media](./images/aaemassdmcomp5.png)

After successful login, you should see a screen similar to this.

![AEM Assets Dynamic Media](./images/aaemassdmcomp6.png)

## 1.4.1.2 Configure Dynamic Media in AEM

Go to [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. The org you should select is `--aepImsOrgName--`. 

Click to open your Cloud Manager Program, which should be called `--aepUserLdap-- - CitiSignal AEM+ACCS`.

![AEM Assets Dynamic Media](./images/accsaemassets1.png)

Click your environment.

![AEM Assets Dynamic Media](./images/accsaemassets3.png)

Click the URL of your environment.

![AEM Assets Dynamic Media](./images/accsaemassets2.png)

Go to **Tools**, to **Cloud Services** and then to **Dynamic Media Configuration**.

![AEM Assets Dynamic Media](./images/accsaemassets4.png)

Select **Global** (don't check the checkbox), and then click **Create**.

![AEM Assets Dynamic Media](./images/accsaemassets5.png)

Enter the following information:

- **Title**: use this title: `--aepUserLdap-- - CitiSignal`.
- **Email**: enter your email address.
- **Password**: enter your Dynamic Media account password 
- **Region**: select the region that you chose when creating your Dynamic Media company, in this example, **Europe**.

Click **Connect to Dynamic Media**.

![AEM Assets Dynamic Media](./images/accsaemassets6.png)

You should then see this. Configure the following:

- Select the **Company**: `--aepUserLdap-- - CitiSignal`.
- Set **Publish Assets** to **Immediate**.
- Check the checkbox to **Sync all content**.

Click **Save**.

![AEM Assets Dynamic Media](./images/accsaemassets7.png)

Your DYnamic Media configuration is now done. Click **OK**.

![AEM Assets Dynamic Media](./images/accsaemassets8.png)

## 1.4.1.3 Export your assets

Download this file [citisignal-fiber-max-is-coming.psd](./assets/citisignal-fiber-max-is-coming.psd){target="_blank"} and open it with Adobe Photoshop.

You should then see this. CitiSignal is planning a rollout of Fiber Max across 3 cities: New York, Paris and Dubai. 

By showing or hiding specific layers, you can view the image that was created by the designers.

Below are the instructions to export the image files from the Photoshop PSD template. If you prefer, you can also download the finished images here [citisignal-dm-email-assets.zip](./assets/citisignal-dm-email-assets.zip){target="_blank"} and unzip the file onto your desktop.

This is the version for New York.

![AEM Assets Dynamic Media](./images/aemdm1.png)

This is the version for Dubai.

![AEM Assets Dynamic Media](./images/aemdm2.png)

This is the version for Paris.

![AEM Assets Dynamic Media](./images/aemdm3.png)

There will potentially be many other cities that CitiSignal will be rolling Fiber Max out to so in the future, new layers may be created in this file. For now, the focus is on the 3 cities already mentioned.

In order to use these variations in combination with AEM Assets Dynamic Media, the layers for each city should be exported as images. To do that, go to **File** > **Export** > **Layers to Files...**.

![AEM Assets Dynamic Media](./images/aemdm4.png)

You should then see something like this. Select a location to export the files to, select the file type **PNG-8** and click **Run**.

![AEM Assets Dynamic Media](./images/aemdm5.png)

After a couple of seconds, you should see this. Click **OK**.

![AEM Assets Dynamic Media](./images/aemdm6.png)

You should then have these files available in the export location that you selected.

![AEM Assets Dynamic Media](./images/aemdm7.png)

## 1.4.1.4 Upload your assets to AEM Assets CS

Go to [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Go to **Experience Manager Assets**.

![AEM Assets Dynamic Media](./images/aemdm8.png)

Select your repository, which should be named `--aepUserLdap-- - CitiSignal AEM + ACCS`.

![AEM Assets Dynamic Media](./images/aemdm9.png)

Go to **Assets** and then click **Create Folder**.

![AEM Assets Dynamic Media](./images/aemdm10.png)

For the folder, use the name: `--aepUserLdap-- - CitiSignal Dynamic Media`. Click **Create**.

![AEM Assets Dynamic Media](./images/aemdm11.png)

Double-click to open the folder you just created.

![AEM Assets Dynamic Media](./images/aemdm12.png)

Click **Add Assets**.

![AEM Assets Dynamic Media](./images/aemdm13.png)

Click **Browse** and then select **Browse Files**.

![AEM Assets Dynamic Media](./images/aemdm15.png)

Select the 4 PNG files that you exported in the previous step.

![AEM Assets Dynamic Media](./images/aemdm16.png)

Click **Upload**.

![AEM Assets Dynamic Media](./images/aemdm17.png)

Your images are now available in AEM Assets CS.

![AEM Assets Dynamic Media](./images/aemdm18.png)

Wait a couple of minutes and then open the **Adobe Dynamic Media Classic desktop app**, you should now also see the uploaded images become available within Dynamic Media.

![AEM Assets Dynamic Media](./images/aemdm19.png)

## 1.4.1.5 Configure Dynamic Media Template

In the left menu, go to **Dynamic Media Assets**. Click to open your folder `--aepUserLdap-- - CitiSignal Dynamic Media`. Then, click **Create Template**.

![AEM Assets Dynamic Media](./images/aemdm20.png)

Enter the following information:

- **Template Name**: `--aepUserLdap-- - CitiSignal Fiber Max Launch Email Assets`
- **Canvas Width**: `600px`
- **Canvas Height**: `600px`

Click **Create**.

![AEM Assets Dynamic Media](./images/aemdm21.png)

You should then see this. Click the **Add Image** icon.

![AEM Assets Dynamic Media](./images/aemdm22.png)

Drag the file **citisignal-fiber-max-is-coming_citisignal-background.png** onto the canvas and make it fit the canvas.

![AEM Assets Dynamic Media](./images/aemdm23.png)

Next, drag the file **citisignal-fiber-max-is-coming_citisignal-newyork.png** onto the canvas and make it fit the canvas.

![AEM Assets Dynamic Media](./images/aemdm24.png)

Next, drag the file **citisignal-fiber-max-is-coming_citisignal-dubai.png** onto the canvas and make it fit the canvas.

![AEM Assets Dynamic Media](./images/aemdm25.png)

Next, drag the file **citisignal-fiber-max-is-coming_citisignal-paris.png** onto the canvas and make it fit the canvas.

![AEM Assets Dynamic Media](./images/aemdm26.png)

You now have all 3 variations in the template as distinct layers at the same time. You can show/hide specific layers by clicking the **layers** icon, where you see that all layers are currently visible. 

![AEM Assets Dynamic Media](./images/aemdm27.png)

By hiding a couple of layers, you can control what the image looks like. In this example, only the layer for **Paris** and the background layer is visible.

![AEM Assets Dynamic Media](./images/aemdm28.png)

Next, you need to add a text layer. Click the **text layer** icon.

![AEM Assets Dynamic Media](./images/aemdm29.png)

You should then see this.

![AEM Assets Dynamic Media](./images/aemdm30.png)

Feel free to adapt the text field in whichever way you see fit, here's an example. Don't forget to enable the option **Smart Text Resize** so that the real text that is inserted at a later stage will look fine.

![AEM Assets Dynamic Media](./images/aemdm31.png)

Add a second text layer and make it look like this. Don't forget to enable the option **Smart Text Resize** so that the real text that is inserted at a later stage will look fine.

![AEM Assets Dynamic Media](./images/aemdm32.png)


## Next Steps

Next Step: [Use your dynamic media template with Adobe Journey Optimizer](./ex2.md){target="_blank"}

Go Back to [Adobe Experience Manager Assets & Dynamic Media](./aemassetsdm.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
