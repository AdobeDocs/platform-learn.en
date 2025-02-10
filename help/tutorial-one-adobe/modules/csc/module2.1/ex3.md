---
title: Setup your AEM CS environment
description: Setup your AEM CS environment
kt: 5342
doc-type: tutorial
exl-id: 62715072-0257-4d07-af1a-8becbb793459
---
# 2.1.3 Setup your AEM CS environment

## 2.1.3.1 Setup your GitHub repo

Go to [https://github.com](https://github.com){target="_blank"}. Click **Sign In**.

![AEMCS](./images/aemcssetup1.png){zoomable="yes"}

Enter your credentials. Click **Sign In**. 

![AEMCS](./images/aemcssetup2.png){zoomable="yes"}

Once signed in, you'll see your GitHub Dashboard.

![AEMCS](./images/aemcssetup3.png){zoomable="yes"}

Go to [https://github.com/AdobeDevXSC/citisignal-one](https://github.com/AdobeDevXSC/citisignal-one){target="_blank"}. You'll then see this. Click **Use this template** and then click **Create a new repository**.

![AEMCS](./images/aemcssetup4.png){zoomable="yes"}

For the **Repository name**, use `citisignal`. Set the visibility to **Private**. Click **Create repository**.

![AEMCS](./images/aemcssetup5.png){zoomable="yes"}

After a couple of seconds, you'll then have your repository created.

![AEMCS](./images/aemcssetup6.png){zoomable="yes"}

Next, go to [https://github.com/apps/aem-code-sync](https://github.com/apps/aem-code-sync){target="_blank"}. Click **Configure**.

![AEMCS](./images/aemcssetup7.png){zoomable="yes"}

Click your GitHub account.

![AEMCS](./images/aemcssetup8.png){zoomable="yes"}

Click **Only select repositories** and then add the repository that you just created. Next, click **Install**.

![AEMCS](./images/aemcssetup9.png){zoomable="yes"}

You'll then get this confirmation.

![AEMCS](./images/aemcssetup10.png){zoomable="yes"}

## 2.1.3.2 Update file fstab.yaml

In your GitHub repo, click to open the file `fstab.yaml`.

![AEMCS](./images/aemcssetup11.png){zoomable="yes"}

Click the **edit** icon.

![AEMCS](./images/aemcssetup12.png){zoomable="yes"}

You now need to update the value for the field **url** on line 4. 

![AEMCS](./images/aemcssetup13.png){zoomable="yes"}

You need to replace the current value by the URL of your specific AEM CS environment in combination with the settings of your GitHub repo. 

This is the current value of the URL: `https://author-p131639-e1282833.adobeaemcloud.com/bin/franklin.delivery/adobedevxsc/citisignal-one/main`.

There are 3 parts of the URL that need to be updated

`https://XXX/bin/franklin.delivery/YYY/ZZZ/main`

XXX should be replaced by the URL of your AEM CS Author environment.

YYY should be replaced by your GitHub user account.

ZZZ should be replaced by the name of the GitHub repository that you used in the previous exercise.

You can find the URL of your AEM CS Author environment by going to [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Click your **Program** to open it.

![AEMCS](./images/aemcs6.png){zoomable="yes"}

Next, click the 3 dots **...** on the **Environments** tab and click **View Details**.

![AEMCS](./images/aemcs9.png){zoomable="yes"}

You'll then see your environment details, including the URL of your **Author** environment. Copy the URL.

![AEMCS](./images/aemcs10.png){zoomable="yes"}

XXX = `author-p148073-e1511503.adobeaemcloud.com`

For the GitHub user account name, you can easily find that in the URL of your browser. In this example, the user account name is `woutervangeluwe`.

YYY = `woutervangeluwe`

![AEMCS](./images/aemcs11.png){zoomable="yes"}

For the GitHub repository name, you can also find it in the browser window that you have open in GitHub. In this case, the repository name is `citisignal`.

ZZZ = `citisignal`

![AEMCS](./images/aemcs12.png){zoomable="yes"}

These 3 values combined, lead to this new URL that needs to be configured in the file `fstab.yaml`.

`https://author-p148073-e1511503.adobeaemcloud.com/bin/franklin.delivery/woutervangeluwe/citisignal/main`

Click **Commit changes...**.

![AEMCS](./images/aemcs13.png){zoomable="yes"}

Click **Commit changes**.

![AEMCS](./images/aemcs14.png){zoomable="yes"}

The file `fstab.yaml` has now been updated.

## 2.1.3.3 Upload CitiSignal assets

Go to [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Click your **Program** to open it.

![AEMCS](./images/aemcs6.png){zoomable="yes"}

Next, click the URL of your Author environment.

![AEMCS](./images/aemcssetup18.png){zoomable="yes"}

Click **Sign in with Adobe**.

![AEMCS](./images/aemcssetup19.png){zoomable="yes"}

You'll then see your Author environment.

![AEMCS](./images/aemcssetup20.png){zoomable="yes"}

Your URL will look like this: `https://author-p148073-e1511503.adobeaemcloud.com/ui#/aem/aem/start.html?appId=aemshell`

You now need to access the **CRX Package Manager** environment of AEM. To do that, remove `ui#/aem/aem/start.html?appId=aemshell` from the URL and replace it by `crx/packmgr`, which means your URL should look like this now:
`https://author-p148073-e1511503.adobeaemcloud.com/crx/packmgr`. 
Hit **Enter** to load the package manager environment

![AEMCS](./images/aemcssetup22.png){zoomable="yes"}

Next, click **Upload package**.

![AEMCS](./images/aemcssetup21.png){zoomable="yes"}

Click **Browse** to locate the package to upload.

The package to upload is called **citisignal-assets.zip** and can be downloaded here: [https://tech-insiders.s3.us-west-2.amazonaws.com/one-adobe/citisignal-assets.zip](https://tech-insiders.s3.us-west-2.amazonaws.com/one-adobe/citisignal-assets.zip){target="_blank"}.

![AEMCS](./images/aemcssetup23.png){zoomable="yes"}

Select the package and click **Open**.

![AEMCS](./images/aemcssetup24.png){zoomable="yes"}

Next, click **OK**.

![AEMCS](./images/aemcssetup25.png){zoomable="yes"}

The package will then be uploaded.

![AEMCS](./images/aemcssetup26.png){zoomable="yes"}

Next, click **Install** on the package you just uploaded.

![AEMCS](./images/aemcssetup27.png){zoomable="yes"}

Click **Install**.

![AEMCS](./images/aemcssetup28.png){zoomable="yes"}

After a couple of minutes, your package will then be installed.

![AEMCS](./images/aemcssetup29.png){zoomable="yes"}

You can now close this window.


## 2.1.3.4 Publish CitiSignal assets

Go to [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Click your **Program** to open it.

![AEMCS](./images/aemcs6.png){zoomable="yes"}

Next, click the URL of your Author environment.

![AEMCS](./images/aemcssetup18.png){zoomable="yes"}

Click **Sign in with Adobe**.

![AEMCS](./images/aemcssetup19.png){zoomable="yes"}

You'll then see your Author environment. Click **Sites**.

![AEMCS](./images/aemcsassets1.png){zoomable="yes"}

Click **Files**.

![AEMCS](./images/aemcsassets2.png){zoomable="yes"}

Click to select the folder **CitiSignal** and then click **Manage Publication**.

![AEMCS](./images/aemcsassets3.png){zoomable="yes"}

Click **Next**.

![AEMCS](./images/aemcsassets4.png){zoomable="yes"}

Click **Publish**.

![AEMCS](./images/aemcsassets5.png){zoomable="yes"}

Your assets have now been published.

## 2.1.3.5 Create CitiSignal website

Go to [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Click your **Program** to open it.

![AEMCS](./images/aemcs6.png){zoomable="yes"}

Next, click the URL of your Author environment.

![AEMCS](./images/aemcssetup18.png){zoomable="yes"}

Click **Sign in with Adobe**.

![AEMCS](./images/aemcssetup19.png){zoomable="yes"}

You'll then see your Author environment. Click **Sites**.

![AEMCS](./images/aemcssetup30.png){zoomable="yes"}

Click **Create** and then click **Site from template**.

![AEMCS](./images/aemcssetup31.png){zoomable="yes"}

Click **Import**.

![AEMCS](./images/aemcssetup32.png){zoomable="yes"}

You now need to import a preconfigured template for your site. You can download the template [here](./../../../assets/aem/citisignal-edge-delivery-services-template-0.0.4.zip){target="_blank"}. Save the file to your desktop.

Next, select the file `citisignal-edge-delivery-services-template-0.0.4.zip` and click **Open**.

![AEMCS](./images/aemcssetup33.png){zoomable="yes"}

You'll then see this. Click to select the template you just uploaded and then, click **Next**.

![AEMCS](./images/aemcssetup34.png){zoomable="yes"}

You now need to fill out some details.

- Site title: use **CitiSignal**
- Site name: use **citisignal-one**
- GitHub URL: copy the URL of the GitHub repo you were using before

![AEMCS](./images/aemcssetup35.png){zoomable="yes"}

You'll then have this. Click **Create**.

![AEMCS](./images/aemcssetup36.png){zoomable="yes"}

Your site is now being created. This may take a couple of minutes. Click **Okay**.

![AEMCS](./images/aemcssetup37.png){zoomable="yes"}

Refresh your screen after a couple of minutes, you'll then see your newly created CitiSignal website.

![AEMCS](./images/aemcssetup38.png){zoomable="yes"}

## 2.1.3.6 Publish CitiSignal website

Next, click the checkbox in front of **CitiSignal**. Then, click **Manage Publication**.

![AEMCS](./images/aemcssetup39.png){zoomable="yes"}

Click **Next**.

![AEMCS](./images/aemcssetup40.png){zoomable="yes"}

Click **Include Children Settings**.

![AEMCS](./images/aemcssetup41.png){zoomable="yes"}

Click to select the checkbox **Include children** and then click to unselect the other checkboxes. Click **OK**.

![AEMCS](./images/aemcssetup42.png){zoomable="yes"}

Click **Publish**.

![AEMCS](./images/aemcssetup43.png){zoomable="yes"}

You'll then be sent back here. Navigate to **CitiSignal** > **us** > **en**. Click the checkbox in front of **index** and then click **Edit**.

![AEMCS](./images/aemcssetup44.png){zoomable="yes"}

Your website will then open in the **Universal Editor**.

![AEMCS](./images/aemcssetup45.png){zoomable="yes"}

You will now be able to acces your website by going to `main--citisignal--XXX.aem.page/us/en` and/or `main--citisignal--XXX.aem.live/us/en`, after replacing XXX by your GitHub user account, which in this example is `woutervangeluwe`.

In this example, the full URL becomes this:
`https://main--citisignal--woutervangeluwe.aem.page/us/en` and/or `https://main--citisignal--woutervangeluwe.aem.live/us/en`.

It may take some time before all the assets are shown correctly, as they need to be published first.

You'll then see this:

![AEMCS](./images/aemcssetup46.png){zoomable="yes"}

After a couple of minutes, the assets will all be loading properly.

![AEMCS](./images/aemcssetup47.png){zoomable="yes"}

## 2.1.3.7 Test Page Performance

Go to [https://pagespeed.web.dev/](https://pagespeed.web.dev/){target="_blank"}. Enter your URL and click **Analyze**.

![AEMCS](./images/aemcssetup48.png){zoomable="yes"}

You'll then see that your website, in both a mobile and desktop visualization, gets a high score:

**Mobile**:

![AEMCS](./images/aemcssetup49.png){zoomable="yes"}

**Desktop**:

![AEMCS](./images/aemcssetup50.png){zoomable="yes"}

Next Step: [2.1.4 Configure a custom block](./ex4.md){target="_blank"}

[Go Back to Module 2.1](./aemcs.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
