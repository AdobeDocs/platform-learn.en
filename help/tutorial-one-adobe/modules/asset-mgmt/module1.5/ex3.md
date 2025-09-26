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

After completing the previous exercise, you could see a product being returned by ACCS to your website but it didn't have an image yet. At the end of this exercise, you should see an image being returned as well.

![ACCS+AEM Sites](./images/accsaemsites11.png)

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

Go to [https://github.com/ankumalh/assets-commerce](https://github.com/ankumalh/assets-commerce). Click **<> Code** and then select **Download ZIP**. Download the file and then drop it on your desktop.

![ACCS+AEM Assets](./images/accsaemassets15a.png)

Next, copy the file **assets-commerce-main.zip** to your desktop and unzip it. Open the folder **assets-commerce-main**.

![ACCS+AEM Assets](./images/accsaemassets16.png)

Copy all the files from the directory **assets-commerce-main** to the empty directory of your Program's Pipeline Repository directory.

![ACCS+AEM Assets](./images/accsaemassets17.png)

Next, open **Microsoft Visual Studio Code** and open the folder that contains your Program's Pipeline Repository in **Microsoft Visual Studio Code**.

![ACCS+AEM Assets](./images/accsaemassets18.png)

Go to **Search** in the left menu and search for `<my-app>`. You need to replace all occurences of `<my-app>` by `--aepUserLdap--citisignalaemaccs`.

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

## 1.5.3.2 Enable AEM Assets integration in ACCS

Go back to your ACCS instance. In the left menu, go to **Stores** and then select **Configuration**.

![ACCS+AEM Assets](./images/accsaemassets49.png)

Scroll down in the menu to **ADOBE SERVICES** and then open **AEM Assets Integration**. You should then see this.

![ACCS+AEM Assets](./images/accsaemassets50.png)

Fill out the following variables:

- **AEM Assets Program ID**: You can take the Program ID from the AEM CS Author URL. In this example, the Program ID is `166717`.

![ACCS+AEM Assets](./images/accsaemassets50a.png)

- **AEM Assets Environment ID**: You can take the Environment ID from the AEM CS Author URL. In this example, the Environment ID is `1786231`.

![ACCS+AEM Assets](./images/accsaemassets50b.png)

- **Asset Selector IMS Client ID**: set to `1`
- **Synchronization enabled**: set to `Yes`
- **Visualization Owner**: set to `AEM Assets`
- **Asset matching rule**: `Match by product SKU`
- **Match by product SKU attribute name**: `commerce:skus`

Click **Save Config**.

![ACCS+AEM Assets](./images/accsaemassets51.png)

You should then see this.

![ACCS+AEM Assets](./images/accsaemassets52.png)

## 1.5.3.3 Update config.json

Go to the GitHub repository that was created when setting up your AEM Sites CS/EDS environment. That repository was created in the exercise [1.1.2 Setup your AEM CS environment](./../../../modules/asset-mgmt/module2.1/ex3.md){target="_blank"} and should be named **citisignal-aem-accs**.

In the root directory, scroll down and click to open the file **config.json**. Click the **edit** icon to make changes to the file.

![ACCS+AEM Assets](./images/accsaemassets101.png)

Add the below code snippet under line 5 `"commerce-endpoint": "https://na1-sandbox.api.commerce.adobe.com/XXX/graphql",`:

```json
 "commerce-assets-enabled": "true",
```

Click **Commit Changes...**.

![ACCS+AEM Assets](./images/accsaemassets102.png)

Click **Commit Changes**.

![ACCS+AEM Assets](./images/accsaemassets103.png)

Your change is now saved and will be published soon. It may take a couple of minutes before the change is visible on the storefront.

![ACCS+AEM Assets](./images/accsaemassets104.png)

## 1.5.3.4 Verify Commerce Fields in AEM Assets CS

Log in to your AEM CS Author environment and go to **Assets**.

![ACCS+AEM Assets](./images/accsaemassets30.png)

Go to **Files**.

![ACCS+AEM Assets](./images/accsaemassets31.png)

Open the **CitiSignal** folder.

![ACCS+AEM Assets](./images/accsaemassets32.png)

Hover over any asset and click the **info** icon.

![ACCS+AEM Assets](./images/accsaemassets33.png)

You should now see a **Commerce** tab that contains 2 new metadata attributes.

![ACCS+AEM Assets](./images/accsaemassets34.png)

Your AEM Assets CS environment now support the Commerce integration. You can now start uploading product images.

## 1.5.3.4 Upload Product Assets & Link to Products

[Download the product images here](./images/Product_Images.zip). Once downloaded, export the files onto your desktop.

![ACCS+AEM Assets](./images/accsaemassets35.png)

Click **Create** and then select **Folder**.

![ACCS+AEM Assets](./images/accsaemassets36.png)

Enter the value **Product_Images** for the fields **Title** and **Name**. Click **Create**.

![ACCS+AEM Assets](./images/accsaemassets37.png)

Click to open the folder you just created.

![ACCS+AEM Assets](./images/accsaemassets38.png)

Click **Create** and then select **Files**.

![ACCS+AEM Assets](./images/accsaemassets39.png)

Navigate to the **Product_Images** folder on your desktop, select all the files and then click **Open**.

![ACCS+AEM Assets](./images/accsaemassets40.png)

Click **Upload**.

![ACCS+AEM Assets](./images/accsaemassets41.png)

Your images will then be available in your folder. Hover over the product **iPhone-Air-Light-Gold.png** and click the **Properties** icon.

![ACCS+AEM Assets](./images/accsaemassets42.png)

Scroll down and set the field **Review Status** to **Approved**. The AEM Assets CS - ACCS integration only works for approved images.

![ACCS+AEM Assets](./images/accsaemassets44.png)

Scroll up, go to the **Commerce** tab and then click **Add** under **Product skus**.

![ACCS+AEM Assets](./images/accsaemassets45.png)

Add the following SKU's for this product:

| Key     | Value     | Usage     | 
|:-------------:| :---------------:| :---------------:| 
| `iPhone-Air-Light-Gold`| `1` |`thumbnail, image, swatch_image, small_image`|
| `iPhone-Air-Light-Gold-256GB`| `1` |`thumbnail, image, swatch_image, small_image`|
| `iPhone-Air-Light-Gold-512GB`| `1` |`thumbnail, image, swatch_image, small_image`|
| `iPhone-Air-Light-Gold-1TB`| `1` |`thumbnail, image, swatch_image, small_image`|

You should then have this. Click **Save & Close**.

![ACCS+AEM Assets](./images/accsaemassets46.png)

Hover over the product **iPhone-Air-Space-Black.png** and click the **Properties** icon.

![ACCS+AEM Assets](./images/accsaemassets47.png)

Scroll down and set the field **Review Status** to **Approved**. The AEM Assets CS - ACCS integration only works for approved images.

![ACCS+AEM Assets](./images/accsaemassets48.png)

Scroll up, go to the **Commerce** tab and then click **Add** under **Product skus**.

![ACCS+AEM Assets](./images/accsaemassets201.png)

Add the following SKU's for this product:

| Key     | Value     | Usage     | 
|:-------------:| :---------------:| :---------------:| 
| `iPhone-Air-Space-Black`| `1` |`thumbnail, image, swatch_image, small_image`|
| `iPhone-Air-Space-Black-256GB`| `1` |`thumbnail, image, swatch_image, small_image`|
| `iPhone-Air-Space-Black-512GB`| `1` |`thumbnail, image, swatch_image, small_image`|
| `iPhone-Air-Space-Black-1TB`| `1` |`thumbnail, image, swatch_image, small_image`|
| `iPhone-Air`| `1` |`thumbnail, image, swatch_image, small_image`|

You should then have this. Click **Save & Close**.

![ACCS+AEM Assets](./images/accsaemassets202.png)

Hover over the product **iPhone-Air-Sky-Blue.png** and click the **Properties** icon.

![ACCS+AEM Assets](./images/accsaemassets203.png)

Scroll down and set the field **Review Status** to **Approved**. The AEM Assets CS - ACCS integration only works for approved images.

![ACCS+AEM Assets](./images/accsaemassets204.png)

Scroll up, go to the **Commerce** tab and then click **Add** under **Product skus**.

![ACCS+AEM Assets](./images/accsaemassets205.png)

Add the following SKU's for this product:

| Key     | Value     | Usage     | 
|:-------------:| :---------------:| :---------------:| 
| `iPhone-Air-Sky-Blue`| `1` |`thumbnail, image, swatch_image, small_image`|
| `iPhone-Air-Sky-Blue-256GB`| `1` |`thumbnail, image, swatch_image, small_image`|
| `iPhone-Air-Sky-Blue-512GB`| `1` |`thumbnail, image, swatch_image, small_image`|
| `iPhone-Air-Sky-Blue-1TB`| `1` |`thumbnail, image, swatch_image, small_image`|

You should then have this. Click **Save & Close**.

![ACCS+AEM Assets](./images/accsaemassets206.png)

Hover over the product **iPhone-Air-Cloud-White.png** and click the **Properties** icon.

![ACCS+AEM Assets](./images/accsaemassets207.png)

Scroll down and set the field **Review Status** to **Approved**. The AEM Assets CS - ACCS integration only works for approved images.

![ACCS+AEM Assets](./images/accsaemassets208.png)

Scroll up, go to the **Commerce** tab and then click **Add** under **Product skus**.

![ACCS+AEM Assets](./images/accsaemassets209.png)

Add the following SKU's for this product:

| Key     | Value     | Usage     | 
|:-------------:| :---------------:| :---------------:| 
| `iPhone-Air-Cloud-White`| `1` |`thumbnail, image, swatch_image, small_image`|
| `iPhone-Air-Cloud-White-256GB`| `1` |`thumbnail, image, swatch_image, small_image`|
| `iPhone-Air-Cloud-White-512GB`| `1` |`thumbnail, image, swatch_image, small_image`|
| `iPhone-Air-Cloud-White-1TB`| `1` |`thumbnail, image, swatch_image, small_image`|

You should then have this. Click **Save & Close**.

![ACCS+AEM Assets](./images/accsaemassets210.png)

Every **iPhone Air** image should now have a **green thumbs up**, indicating that the asset has been approved.

![ACCS+AEM Assets](./images/accsaemassets250.png)

## 1.5.3.5 Verify Product Images on AEM Sites CS/EDS Storefront

>[!NOTE]
>
>It may take up to 15 minutes before the changes you made above are successfully deployed. If you don't see your image being shown yet, wait 15 minutes and then try again.
 
To verify that the integration is working, you need to open your CitiSignal website.

To acces your website, go to `main--citisignal-aem-accs--XXX.aem.page` and/or `main--citisignal-aem-accs--XXX.aem.live`, after replacing XXX by your GitHub user account, which in this example is `woutervangeluwe`.

So in this example, the full URL becomes this:
`https://main--citisignal-aem-accs--woutervangeluwe.aem.page` and/or `https://main--citisignal-aem-accs--woutervangeluwe.aem.live`.

You should then see this. Go to **Phones**.

![ACCS+AEM Assets](./images/accsaemassets150.png)

You should then see a product image being shown for the **iPhone Air**. Click **iPhone Air**.

![ACCS+AEM Assets](./images/accsaemassets151.png)

You should then see this. Make a change to the color and storage options, and you'll see the images dynamically change based on the choices you made.

![ACCS+AEM Assets](./images/accsaemassets152.png)

Here's an example of changing the color to **Light-Gold** and the storage size to **256GB**.

![ACCS+AEM Assets](./images/accsaemassets153.png)

Next Step: [Summary & Benefits](./summary.md){target="_blank"}

Go Back to [Adobe Commerce as a Cloud Service](./accs.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
