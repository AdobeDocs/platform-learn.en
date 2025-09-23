---
title: Setup your AEM CS environment
description: Setup your AEM CS environment
kt: 5342
doc-type: tutorial
exl-id: 62715072-0257-4d07-af1a-8becbb793459
---
# 1.1.2 Setup your AEM CS environment

## 1.1.2.1 Setup your GitHub repo

Go to [https://github.com](https://github.com){target="_blank"}. Click **Sign In**.

![AEMCS](./images/aemcssetup1.png)

Enter your credentials. Click **Sign In**. 

![AEMCS](./images/aemcssetup2.png)

Once signed in, you'll see your GitHub Dashboard.

![AEMCS](./images/aemcssetup3.png)

Go to [https://github.com/adobe-rnd/aem-boilerplate-xcom](https://github.com/adobe-rnd/aem-boilerplate-xcom){target="_blank"}. You'll then see this. Click **Use this template** and then click **Create a new repository**.

![AEMCS](./images/aemcssetup4.png)

For the **Repository name**, use `citisignal-aem-accs`. Set the visibility to **Private**. Click **Create repository**.

![AEMCS](./images/aemcssetup5.png)

After a couple of seconds, you'll then have your repository created.

![AEMCS](./images/aemcssetup6.png)

Next, go to [https://github.com/apps/aem-code-sync](https://github.com/apps/aem-code-sync){target="_blank"}. Click **Install** or **Configure**.

![AEMCS](./images/aemcssetup7.png)

Click the **Continue** button next to your GitHub user account.

![AEMCS](./images/aemcssetup8.png)

Click **Configure** next to your GitHub user account.

![AEMCS](./images/aemcssetup8a.png)

Click **Only select repositories** and then add the repository that you just created. 

![AEMCS](./images/aemcssetup9.png)

Scroll down and cliclk **Save**.

![AEMCS](./images/aemcssetup9a.png)

You'll then get this confirmation.

![AEMCS](./images/aemcssetup10.png)

## 1.1.2.2 Update file fstab.yaml

In your GitHub repo, click to open the file `fstab.yaml`.

![AEMCS](./images/aemcssetup11.png)

Click the **edit** icon.

![AEMCS](./images/aemcssetup12.png)

You now need to update the value for the field **url** on line 3. 

![AEMCS](./images/aemcssetup13.png)

You need to replace the current value by the URL of your specific AEM Sites CS environment in combination with the settings of your GitHub repo. 

This is the current value of the URL: `https://author-p130360-e1272151.adobeaemcloud.com/bin/franklin.delivery/adobe-rnd/aem-boilerplate-xcom/main`.

There are 3 parts of the URL that need to be updated

`https://XXX/bin/franklin.delivery/YYY/ZZZ/main`

XXX should be replaced by the URL of your AEM CS Author environment.

YYY should be replaced by your GitHub user account.

ZZZ should be replaced by the name of the GitHub repository that you used in the previous exercise.

You can find the URL of your AEM CS Author environment by going to [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Click your **Program** to open it.

![AEMCS](./images/aemcs6.png)

Next, click the 3 dots **...** on the **Environments** tab and click **View Details**.

![AEMCS](./images/aemcs9.png)

You'll then see your environment details, including the URL of your **Author** environment. Copy the URL.

![AEMCS](./images/aemcs10.png)

XXX = `author-p166717-e1786231.adobeaemcloud.com`

For the GitHub user account name, you can easily find that in the URL of your browser. In this example, the user account name is `woutervangeluwe`.

YYY = `woutervangeluwe`

![AEMCS](./images/aemcs11.png)

For the GitHub repository name, you can also find it in the browser window that you have open in GitHub. In this case, the repository name is `citisignal`.

ZZZ = `citisignal-aem-accs`

![AEMCS](./images/aemcs12.png)

These 3 values combined, lead to this new URL that needs to be configured in the file `fstab.yaml`.

`https://author-p166717-e1786231.adobeaemcloud.com/bin/franklin.delivery/woutervangeluwe/citisignal-aem-accs/main`

Click **Commit changes...**.

![AEMCS](./images/aemcs13.png)

Click **Commit changes**.

![AEMCS](./images/aemcs14.png)

The file `fstab.yaml` has now been updated.

## 1.1.2.3 Upload CitiSignal assets

Go to [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Click your **Program** to open it.

![AEMCS](./images/aemcs6.png)

Next, click the URL of your Author environment.

![AEMCS](./images/aemcssetup18.png)

Click **Sign in with Adobe**.

![AEMCS](./images/aemcssetup19.png)

You'll then see your Author environment.

![AEMCS](./images/aemcssetup20.png)

Your URL will look like this: `https://author-p166717-e1786231.adobeaemcloud.com/ui#/aem/aem/start.html?appId=aemshell`

You now need to access the **CRX Package Manager** environment of AEM. To do that, remove `ui#/aem/aem/start.html?appId=aemshell` from the URL and replace it by `crx/packmgr`, which means your URL should look like this now:
`https://author-p166717-e1786231.adobeaemcloud.com/crx/packmgr`. 
Hit **Enter** to load the package manager environment

![AEMCS](./images/aemcssetup22.png)

Next, click **Upload package**.

![AEMCS](./images/aemcssetup21.png)

Click **Browse** to locate the package to upload.

The package to upload is called **citisignal-assets.zip** and can be downloaded here: [https://tech-insiders.s3.us-west-2.amazonaws.com/one-adobe/citisignal-assets.zip](https://tech-insiders.s3.us-west-2.amazonaws.com/one-adobe/citisignal-assets.zip){target="_blank"}.

![AEMCS](./images/aemcssetup23.png)

Select the package and click **Open**.

![AEMCS](./images/aemcssetup24.png)

Next, click **OK**.

![AEMCS](./images/aemcssetup25.png)

The package will then be uploaded.

![AEMCS](./images/aemcssetup26.png)

Next, click **Install** on the package you just uploaded.

![AEMCS](./images/aemcssetup27.png)

Click **Install**.

![AEMCS](./images/aemcssetup28.png)

After a couple of minutes, your package will then be installed.

![AEMCS](./images/aemcssetup29.png)

You can now close this window.

## 1.1.2.4 Publish CitiSignal assets

Go to [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Click your **Program** to open it.

![AEMCS](./images/aemcs6.png)

Next, click the URL of your Author environment.

![AEMCS](./images/aemcssetup18.png)

Click **Sign in with Adobe**.

![AEMCS](./images/aemcssetup19.png)

You'll then see your Author environment. Click **Assets**.

![AEMCS](./images/aemcsassets1.png)

Click **Files**.

![AEMCS](./images/aemcsassets2.png)

Click to select the folder **CitiSignal** and then click **Manage Publication**.

![AEMCS](./images/aemcsassets3.png)

Click **Next**.

![AEMCS](./images/aemcsassets4.png)

Click **Publish**.

![AEMCS](./images/aemcsassets5.png)

Your assets have now been published.

## 1.1.2.5 Create CitiSignal website

Go to [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Click your **Program** to open it.

![AEMCS](./images/aemcs6.png)

Next, click the URL of your Author environment.

![AEMCS](./images/aemcssetup18.png)

Click **Sign in with Adobe**.

![AEMCS](./images/aemcssetup19.png)

You'll then see your Author environment. Click **Sites**.

![AEMCS](./images/aemcssetup30.png)

Click **Create** and then click **Site from template**.

![AEMCS](./images/aemcssetup31.png)

Click **Import**.

![AEMCS](./images/aemcssetup32.png)

You now need to import a preconfigured template for your site. You can download the template [here](./../../../assets/aem/citisignal-aem-sites-commerce-with-edge-delivery-services-template-0.4.0.zip){target="_blank"}. Save the file to your desktop.

Next, select the file `citisignal-aem-sites-commerce-with-edge-delivery-services-template-0.4.0.zip` and click **Open**.

![AEMCS](./images/aemcssetup33.png)

You'll then see this. Click to select the template you just uploaded and then, click **Next**.

![AEMCS](./images/aemcssetup34.png)

You now need to fill out some details.

- Site title: use **CitiSignal**
- Site name: use **CitiSignal**
- GitHub URL: copy the URL of the GitHub repo you were using before

![AEMCS](./images/aemcssetup35.png) 

You'll then have this. Click **Create**.

![AEMCS](./images/aemcssetup36.png)

Your site is now being created. This may take a couple of minutes. Click **Okay**.

![AEMCS](./images/aemcssetup37.png)

Refresh your screen after a couple of minutes, you'll then see your newly created CitiSignal website.

![AEMCS](./images/aemcssetup38.png)

## 1.1.2.6 Update file paths.json

In your GitHub repo, click to open the file `paths.json`.

![AEMCS](./images/aemcssetupjson1.png)

Click the **edit** icon.

![AEMCS](./images/aemcssetupjson2.png)

You now need to update the replace the text `aem-boilerplate-commerce` by `CitiSignal` on lines 3, 4, 5, 6, 7 and 10. 

Click **Commit Changes**.

![AEMCS](./images/aemcssetupjson3.png)

Click **Commit Changes**.

![AEMCS](./images/aemcssetupjson4.png)

The file `paths.json` has now been updated.

## 1.1.2.7 Publish CitiSignal website

Next, click the checkbox in front of **CitiSignal**. Then, click **Manage Publication**.

![AEMCS](./images/aemcssetup39.png)

Click **Next**.

![AEMCS](./images/aemcssetup40.png)

Click **Include Children Settings**.

![AEMCS](./images/aemcssetup41.png)

Click to select the checkbox **Include children** and then click to unselect the other checkboxes. Click **OK**.

![AEMCS](./images/aemcssetup42.png)

Click **Publish**.

![AEMCS](./images/aemcssetup43.png)

You'll then be sent back here. Click **CitiSignal**, select the checkbox in front of **index** and then click **Edit**.

![AEMCS](./images/aemcssetup44.png)

Your website will then open in the **Universal Editor**.

![AEMCS](./images/aemcssetup45.png)

You will now be able to acces your website by going to `main--citisignal-aem-accs--XXX.aem.page` and/or `main--citisignal-aem-accs--XXX.aem.live`, after replacing XXX by your GitHub user account, which in this example is `woutervangeluwe`.

In this example, the full URL becomes this:
`https://main--citisignal-aem-accs--woutervangeluwe.aem.page` and/or `https://main--citisignal-aem-accs--woutervangeluwe.aem.live`.

It may take some time before all the assets are shown correctly, as they need to be published first.

You'll then see this:

![AEMCS](./images/aemcssetup46.png)

## 1.1.2.8 Test Page Performance

Go to [https://pagespeed.web.dev/](https://pagespeed.web.dev/){target="_blank"}. Enter your URL and click **Analyze**.

![AEMCS](./images/aemcssetup48.png)

You'll then see that your website, in both a mobile and desktop visualization, gets a high score:

**Mobile**:

![AEMCS](./images/aemcssetup49.png)

**Desktop**:

![AEMCS](./images/aemcssetup50.png)

Next Step: [Develop a custom block](./ex4.md){target="_blank"}

Go Back to [Adobe Experience Manager Cloud Service & Edge Delivery Services](./aemcs.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
