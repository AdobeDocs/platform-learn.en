---
title: AEM CS - Create your document-based website
description: AEM CS - Create your document-based website
kt: 5342
doc-type: tutorial
exl-id: db366111-3873-4504-95f1-b240836c833f
---
# 1.1.2 Create your document-based website

While you wait for your Cloud Manager Program to be created, you have enough time to set up your first document-based authoring website. The below exercise is based on the [aem.live Developer Tutorial](https://www.aem.live/developer/tutorial){target="_blank"}. Follow the steps below to get started.

## 1.1.2.1 Setup your Google Drive

Go to [https://drive.google.com](https://drive.google.com){target="_blank"}. Click **+ New** and then click **New Folder**.

![AEMCS](./images/googledrive1.png){zoomable="yes"}

Name your folder `aemdocb-test`. Click **Create**.

![AEMCS](./images/googledrive2.png){zoomable="yes"}

Download the file [aemboilerplate.zip](./../../../assets/aem/aemboilerplate.zip){target="_blank"} and extract it on your computer.

![AEMCS](./images/googledrive3.png){zoomable="yes"}

You'll see 3 files in that folder. Copy those files into your new Google Drive folder.

![AEMCS](./images/googledrive4.png){zoomable="yes"}

You now need to convert these files into a native Google file. To do that, open each file and then go to **File** > **Save as Google Docs**.

![AEMCS](./images/googledrive5.png){zoomable="yes"}

You should do this for all 3 files, and afterwards you'll see 6 files in your Google Drive folder.

![AEMCS](./images/googledrive6.png){zoomable="yes"}

You then have this in your folder.

![AEMCS](./images/googledrive7.png){zoomable="yes"}

In order for the document-based authoring demo to work, you now need to share your Google Drive folder with the email address **helix@adobe.com**. Click your folder name, click **Share** and then click **Share** again.

![AEMCS](./images/googledrive8.png){zoomable="yes"}

Enter the email address **helix@adobe.com** and click **Send**.

![AEMCS](./images/googledrive9.png){zoomable="yes"}

Next, copy and write down the URL of your Google Drive folder as you'll need that in the next exercise. Click your folder name, click **Share** and then click **Copy link**.

![AEMCS](./images/googledrive10.png){zoomable="yes"}

`https://drive.google.com/drive/folders/1PNIOFeptIfszSebawT-Y_bwB4_anQWk5?usp=drive_link`

You should remove the query string parameter `?usp=drive_link` so the URL should look like this:

`https://drive.google.com/drive/folders/1PNIOFeptIfszSebawT-Y_bwB4_anQWk5`

## 1.1.2.2 Setup your GitHub repo

Go to [https://github.com](https://github.com){target="_blank"}. Click **Sign In**.

![AEMCS](./images/aemcssetup1.png){zoomable="yes"}

Enter your credentials. Click **Sign In**. 

![AEMCS](./images/aemcssetup2.png){zoomable="yes"}

Once signed in, you'll see your GitHub Dashboard.

![AEMCS](./images/aemcssetup3.png){zoomable="yes"}

Go to [https://github.com/adobe/aem-boilerplate](https://github.com/adobe/aem-boilerplate){target="_blank"}. You'll then see this. Click **Use this template** and then click **Create a new repository**.

![AEMCS](./images/aemdocbcssetup4.png){zoomable="yes"}

For the **Repository name**, use `aemdocb-test`. Set the visibility to **Private**. Click **Create repository**.

![AEMCS](./images/aemdocbcssetup5.png){zoomable="yes"}

After a couple of seconds, you'll then have your repository created.

![AEMCS](./images/aemdocbcssetup6.png){zoomable="yes"}

Next, go to [https://github.com/apps/aem-code-sync](https://github.com/apps/aem-code-sync){target="_blank"}. Click **Configure**.

![AEMCS](./images/aemcssetup7.png){zoomable="yes"}

Click your GitHub account.

![AEMCS](./images/aemcssetup8.png){zoomable="yes"}

Click **Only select repositories** and then add the repository that you just created. Next, click **Install**.

![AEMCS](./images/aemdocbcssetup9.png){zoomable="yes"}

You'll then get this confirmation.

![AEMCS](./images/aemcssetup10.png){zoomable="yes"}

## 1.1.2.3 Update file fstab.yaml

In your GitHub repo, click to open the file `fstab.yaml`.

![AEMCS](./images/aemdocbcssetup11.png){zoomable="yes"}

Click the **edit** icon.

![AEMCS](./images/aemdocbcssetup12.png){zoomable="yes"}

You now need to update the value for the field **url** on line 2. 

![AEMCS](./images/aemdocbcssetup13.png){zoomable="yes"}

You need to replace the current value by the URL of your specific AEM CS environment in combination with the settings of your GitHub repo. 

This is the current value of the URL: `https://drive.google.com/drive/u/0/folders/1MGzOt7ubUh3gu7zhZIPb7R7dyRzG371j`.

Replace that value by the URL you copied from your Google Drive folder, `https://drive.google.com/drive/folders/1PNIOFeptIfszSebawT-Y_bwB4_anQWk5`. Click **Commit changes...**.

![AEMCS](./images/aemdocbcssetup14.png){zoomable="yes"}

Click **Commit changes**.

![AEMCS](./images/aemdocbcssetup15.png){zoomable="yes"}

## 1.1.2.4 Install AEM Sidekick extension

Go to [https://chromewebstore.google.com/detail/aem-sidekick/ccfggkjabjahcjoljmgmklhpaccedipo](https://chromewebstore.google.com/detail/aem-sidekick/ccfggkjabjahcjoljmgmklhpaccedipo){target="_blank"}. Click **Add to Chrome**.

![AEMCS](./images/aemdocbcssetup16.png){zoomable="yes"}

Pin the **AEM Sidekick** extension.

![AEMCS](./images/aemdocbcssetup17.png){zoomable="yes"}

## 1.1.2.5 Preview and Publish your document-based website

Go back to your Google Drive folder. In the task bar, click the **AEM Sidekick** extension. You then see a, AEM Sidekick bar popup on your folder.

![AEMCS](./images/aemdocbcssetup18.png){zoomable="yes"}

Select the 3 files in your Google Drive folder. Click **Preview**.

![AEMCS](./images/aemdocbcssetup19.png){zoomable="yes"}

Click **Preview** again.

![AEMCS](./images/aemdocbcssetup20.png){zoomable="yes"}

Click to close the green dialog popup.

![AEMCS](./images/aemdocbcssetup21.png){zoomable="yes"}

Select the 3 files in your Google Drive folder again. Now, click **Publish**.

![AEMCS](./images/aemdocbcssetup22.png){zoomable="yes"}

Click **Publish**.

![AEMCS](./images/aemdocbcssetup23.png){zoomable="yes"}

Click to close the green dialog again. Now, select the file **index**, click **Copy URLs** and then click **Copy Live URLs**.

![AEMCS](./images/aemdocbcssetup24.png){zoomable="yes"}

The URL that was copied will look like this: `https://main--aemdocb-test--woutervangeluwe.aem.live/`. 

In the above URL:

- **main** refers to the branch on your GitHub repo
- **aemdocb-test** refers to the GitHub repository name
- **woutervangeluwe** refers to the GitHub user account name
- **.live** refers to the live environment of your AEM instance
- You can replace **.live** by **.page** to open the preview environment of your AEM instance

Open a new browser window and navigate to the URL.

![AEMCS](./images/aemdocbcssetup25.png){zoomable="yes"}

## 1.1.2.6 Make a change and publish your change

Go back to your Google Drive and open the filer **index** in Google.

![AEMCS](./images/aemdocbcssetup27.png){zoomable="yes"}

Replace the text **Testing** by any other text of choice. Click **Preview**.

![AEMCS](./images/aemdocbcssetup28.png){zoomable="yes"}

The preview version of your website will then open. Review your change and click **Publish**.

![AEMCS](./images/aemdocbcssetup29.png){zoomable="yes"}

You'll then see the live version of your website.

![AEMCS](./images/aemdocbcssetup30.png){zoomable="yes"}

The above exercise was a good way to get started and experience document-based authoring yourself. You can now continue with the next exercise, where you'll set up your own demo website using CitiSignal as a demo brand.

Next Step: [1.1.3 Setup your AEM CS environment](./ex3.md){target="_blank"}

Go Back to [Adobe Experience Manager Cloud Service & Edge Delivery Services](./aemcs.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
