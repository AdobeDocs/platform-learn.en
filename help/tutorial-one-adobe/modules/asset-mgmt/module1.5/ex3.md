---
title: Connect ACCS to AEM Assets CS
description: Connect ACCS to AEM Assets CS
kt: 5342
doc-type: tutorial
---
# 1.5.3 Connect ACCS to AEM Assets CS

>[!IMPORTANT]
>
>In order to complete this exercise, you need to have access to a working AEM Sites and Assets CS with EDS environment. 
>
>If you don't have such an environment yet, go to exercise [Adobe Experience Manager Cloud Service & Edge Delivery Services](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"}. Follow the instructions there, and you'll have access to such an environment.

>[!IMPORTANT]
>
>If you have previously configured an AEM CS Program with an AEM Sites and Assets CS environment, it may be that your AEM CS sandbox was hibernated. Given that dehibernating such a sandbox takes 10-15 minutes, it would be a good idea to start the dehibernation process now so that you don't have to wait for it at a later time.

## 1.5.3.1 Update Pipeline Config

Go to [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. The org you should select is `--aepImsOrgName--`. 

Click to open your Cloud Manager Program, which should be called `--aepUserLdap-- - CitiSignal AEM+ACCS`.

![ACCS+AEM Assets](./images/accsaemassets1.png)

Scoll down a little bit and then click **Access Repo Info** on the **Pipelines** tab. 

![ACCS+AEM Assets](./images/accsaemassets2.png)

You should then see this. Click **Generate Password**.

![ACCS+AEM Assets](./images/accsaemassets3.png)

Click **Generate Password** again.

![ACCS+AEM Assets](./images/accsaemassets4.png)

You should then have a password available. Next, click the **copy** icon next to the **Git command line** field.

![ACCS+AEM Assets](./images/accsaemassets5.png)

Create a new directory in a location of choice on your computer and name it **AEM Pipeline GitHub**.

![ACCS+AEM Assets](./images/accsaemassets6.png)

Right-click your folder and then select **New Terminal at Folder**.

![ACCS+AEM Assets](./images/accsaemassets7.png)

You should then see this.

![ACCS+AEM Assets](./images/accsaemassets8.png)

Paste the **Git command line** command that you copied before in the Terminal window.

![ACCS+AEM Assets](./images/accsaemassets9.png)

You need to enter a user name. Copy the user name from the Cloud Manager's Program Pipeline **Access Repo Info** and hit **enter**.

![ACCS+AEM Assets](./images/accsaemassets10.png)

Next, you need to enter the password. Copy the password from the Cloud Manager's Program Pipeline **Access Repo Info** and hit **enter**.

![ACCS+AEM Assets](./images/accsaemassets11.png)

This maye take a minute. Once completed, you'll have a local opy of the Git Repo that is linked to your Program's Pipeline.

![ACCS+AEM Assets](./images/accsaemassets12.png)

You'll see a new directory in the **AEM Pipeline GitHub** directory. Open that directory.

![ACCS+AEM Assets](./images/accsaemassets13.png)

Select all the files in that directory and delete all of them. 

![ACCS+AEM Assets](./images/accsaemassets14.png)

Make sure the directory is empty.

![ACCS+AEM Assets](./images/accsaemassets15.png)

Next, copy the file **assets-commerce-main.zip** to your desktop and unzip it. Open the folder **assets-commerce-main**.

![ACCS+AEM Assets](./images/accsaemassets16.png)

Copy all the files from the directory **assets-commerce-main** to the empty directory of your Program's Pipeline Repository directory.

![ACCS+AEM Assets](./images/accsaemassets17.png)

Next, open **Microsoft Visual Studio Code** and open the folder that contains your Program's Pipeline Repository in **Microsoft Visual Studio Code**.

![ACCS+AEM Assets](./images/accsaemassets18.png)

Go to **Search** in the left menu and search for `<my-app>`. You need to replace all occurences of `<my-app>` by `--aepUserLdap--aemaccs`.

Click the **replace all** icon.

![ACCS+AEM Assets](./images/accsaemassets19.png)

Click **Replace**.

![ACCS+AEM Assets](./images/accsaemassets20.png)

The new files are now ready to be uploaded back to the Git Repo that is linked to your Program's Pipeline Repository. To do that, open the folder **AEM Pipeline GitHub** and right-click on the folder that contains the new files. Select **New Terminal at Folder**.

![ACCS+AEM Assets](./images/accsaemassets21.png)

You should then see this. Paste the command `git add .` and hit **enter**.

![ACCS+AEM Assets](./images/accsaemassets22.png)

You should then see this. Paste the command `git commit -m "add assets integration"` and hit **enter**.

![ACCS+AEM Assets](./images/accsaemassets23.png)

You should then see this. Paste the command `git push origin main` and hit **enter**.

![ACCS+AEM Assets](./images/accsaemassets24.png)

You should then see this. Your changes have now been deployed to your Program's Pipeline Git Repo.

![ACCS+AEM Assets](./images/accsaemassets25.png)

Go back to Cloud Manager and click **Close**.

![ACCS+AEM Assets](./images/accsaemassets26.png)

After making changes to the Pipeline's Git Repo, you need to run the **Deploy to Dev** pipeline again. Click the 3 dots **...** and select **Run**.

![ACCS+AEM Assets](./images/accsaemassets27.png)

Click **Run**. Running a pipeline deployment may take 10-15 minutes. You need to wait until the pipeline deployment completes successfully before continuing.

![ACCS+AEM Assets](./images/accsaemassets28.png)

## 1.5.3.4 Update config.json

Add the below code snippet under line 6 `"ac-environment-id":XXX`:

```json
 "commerce-assets-enabled": "true",
```
 


Next Step: [Summary & Benefits](./summary.md){target="_blank"}

Go Back to [Adobe Commerce as a Cloud Service](./accs.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
