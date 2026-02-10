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

In order to use these variations in combination with AEM Assets Dynamic Media, the layers for each city should be exported as images separately without the background file, and another export should be done for the background layer without including any cities. 

You should now hide and show only one of the layers. The first layer to show is the **Paris** layer, and all other layers should be hidden.

To export that layer, go to **File** > **Export** > **Export As...**.

![AEM Assets Dynamic Media](./images/aemdm4.png)

You should then see this. Select the file type **PNG**, make sure **Transparency** is enabled and then click **Export**.

![AEM Assets Dynamic Media](./images/aemdm5.png)

Change the filename to `citisignal-fiber-max-is-coming-paris.png`and click **Export**.

![AEM Assets Dynamic Media](./images/aemdm6.png)

The next layer to show is the **Dubai** layer, and all other layers should be hidden.

To export that layer, go to **File** > **Export** > **Export As...**.

![AEM Assets Dynamic Media](./images/aemdm4a.png)

You should then see this. Select the file type **PNG**, make sure **Transparency** is enabled and then click **Export**.

![AEM Assets Dynamic Media](./images/aemdm5a.png)

Change the filename to `citisignal-fiber-max-is-coming-dubai.png`and click **Export**.

![AEM Assets Dynamic Media](./images/aemdm6a.png)

The next layer to show is the **New York** layer, and all other layers should be hidden.

To export that layer, go to **File** > **Export** > **Export As...**.

![AEM Assets Dynamic Media](./images/aemdm4b.png)

You should then see this. Select the file type **PNG**, make sure **Transparency** is enabled and then click **Export**.

![AEM Assets Dynamic Media](./images/aemdm5b.png)

Change the filename to `citisignal-fiber-max-is-coming-newyork.png`and click **Export**.

![AEM Assets Dynamic Media](./images/aemdm6b.png)

The next layer to show is the **background** layer, and all other layers should be hidden.

To export that layer, go to **File** > **Export** > **Export As...**.

![AEM Assets Dynamic Media](./images/aemdm4c.png)

You should then see this. Select the file type **PNG**, make sure **Transparency** is enabled and then click **Export**.

![AEM Assets Dynamic Media](./images/aemdm5c.png)

Change the filename to `citisignal-fiber-max-is-coming-background`and click **Export**.

![AEM Assets Dynamic Media](./images/aemdm6c.png)

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

Select the first text layer. Click the 3 dots **...** and then select **Edit**.

![AEM Assets Dynamic Media](./images/aemdm33.png)

You should then see this. Scroll down.

![AEM Assets Dynamic Media](./images/aemdm34.png)

Click the **switcher** icon so that the field **Text** is enabled. Change the **Parameter Name** to `title`.

![AEM Assets Dynamic Media](./images/aemdm35.png)

Select the second text layer. Click the 3 dots **...** and then select **Edit**.

![AEM Assets Dynamic Media](./images/aemdm36.png)

You should then see this. Scroll down.

![AEM Assets Dynamic Media](./images/aemdm37.png)

Click the **switcher** icon so that the field **Text** is enabled. Change the **Parameter Name** to `body`.

![AEM Assets Dynamic Media](./images/aemdm38.png)

Select the layer for **Paris**. Click the 3 dots **...** and click **Edit**.

![AEM Assets Dynamic Media](./images/aemdm39.png)

Go to **Paramaters**. Enable the field **Hide** and enter the **Parameter Name**: `city_paris`. Click **Save**.

![AEM Assets Dynamic Media](./images/aemdm40.png)

Select the layer for **Dubai**. Click the 3 dots **...** and click **Edit**.

![AEM Assets Dynamic Media](./images/aemdm41.png)

Go to **Paramaters**. Enable the field **Hide** and enter the **Parameter Name**: `city_dubai`. Click **Save**.

![AEM Assets Dynamic Media](./images/aemdm42.png)

Select the layer for **New York**. Click the 3 dots **...** and click **Edit**.

![AEM Assets Dynamic Media](./images/aemdm43.png)

Go to **Paramaters**. Enable the field **Hide** and enter the **Parameter Name**: `city_ny`. Click **Save**.

![AEM Assets Dynamic Media](./images/aemdm44.png)

Click **Preview**.

![AEM Assets Dynamic Media](./images/aemdm45.png)

Enable the switcher for **Include all parameters** and change some input variables as indicated in the screenshot. You should see your image change dynamically based on the input provided. For the fields **city_paris**, **city_dubai** and **city_ny**, a value of 0 means that this image will NOT be hidden and a value of 1 means this image will be hidden.

![AEM Assets Dynamic Media](./images/aemdm46.png)

By changing some variables, you now see another image being shown.

![AEM Assets Dynamic Media](./images/aemdm47.png)

By changing more variables, you now see another image being shown.

In order to use this template with Adobe Journey Optimizer, and to meet the requirements of this use case, you should add one more layer that will be used to dynamically change the path of the file that needs to be displayed, based on a field that is part of the Real-Time Customer Profile in Adobe Experience Platform.

During dataprep, a field was created in Adobe Experience Platform Schema's to store the **closest rollout city** for a customer. The path of the field is `--aepTenantId--.individualCharacteristics.fiber_rollout.closest_rollout_city`. 

>[!NOTE]
>
>The screenshot below of the Adobe Experience Platform Schema is for information only. There is no need to navigate to AEP to visualize this yourself.

![AEM Assets Dynamic Media](./images/aemdm50.png)

In the next exercise, you will use that field to dynamically select which image should be shown to which customer.

To make that possible, you should add a new image layer.

First, let's hide the other layers that contain images for the rollout cities.

![AEM Assets Dynamic Media](./images/aemdm51.png)

Next, go to **Images** and select a random image of a city and add it to the canvas, and make sure it fits the whole canvas. It doesn't matter which city image you choose, as the path will be change dynamically by AJO in the next exercise.

![AEM Assets Dynamic Media](./images/aemdm52.png)


![AEM Assets Dynamic Media](./images/aemdm53.png)

Go to **Parameters**. 

Click the **switcher** icon so that the field **Hide** is enabled. Change the **Parameter Name** to `dynamic_city_hide`.

Click the **switcher** icon so that the field **Hide** is enabled. Change the **Parameter Name** to `dynamic_city_image`.

Click **Save**.

![AEM Assets Dynamic Media](./images/aemdm54.png)

Click **Preview**.

![AEM Assets Dynamic Media](./images/aemdm55.png)

You should then see this. Enable the switcher icon to **Include all parameters**. Change some input variables as indicated in the screenshot. You should see your image change dynamically based on the input provided. The static fields **city_paris**, **city_dubai** and **city_ny**, should be set to 1 which means that these images will be hidden.

The field **dynamic_city_hide** should be set to 0, which means that it will be shown.

The field **dynamic_city_image** now has the URL to the image of Paris, which looks like this: `vangeluwCitiSignalDM/citisignal-fiber-max-is-coming_citisignal-paris-1`.

![AEM Assets Dynamic Media](./images/aemdm56.png)

Select the word **paris** in the URL.

![AEM Assets Dynamic Media](./images/aemdm57.png)

Change **paris** to `newyork` and then click somewhere else in the UI to see the image change to the New York city image.

![AEM Assets Dynamic Media](./images/aemdm58.png)

Select the word **newyork** and change it to `dubai` and then click somewhere else in the UI to see the image change to the Dubai city image.

Finally, click **Publish**.

![AEM Assets Dynamic Media](./images/aemdm60.png)

You should then see this. Click **Yes**.

![AEM Assets Dynamic Media](./images/aemdm61.png)

Your Dynamic Media template is now configured and published successfully. In the next exercise, you'll use that template in combination with an email campaign in Adobe Journey Optimizer.

## Next Steps

Next Step: [Use your dynamic media template with Adobe Journey Optimizer](./ex2.md){target="_blank"}

Go Back to [Adobe Experience Manager Assets & Dynamic Media](./aemassetsdm.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
