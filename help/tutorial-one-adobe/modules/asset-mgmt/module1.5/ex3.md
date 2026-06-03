---
title: Connect ACCS to AEM Assets CS
description: Connect ACCS to AEM Assets CS
kt: 5342
doc-type: tutorial
exl-id: 2b944efe-3997-46a0-9eb0-61dfda67f5b9
TQID: https://experienceleague.adobe.com/7nbnobK82CId--bLR4u-R60lO7eAsuwWWFFeVeuuxbY
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
---
# 1.5.3 Connect ACCS to AEM Assets CS

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
- **AEM Program**: **Tech Insiders - AEM + ACCS XXX** which you can access through [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)
- **GitHub repository**: [https://github.com/woutervangeluwe/techinsidersXXX-citisignal-aem-accs](https://github.com/woutervangeluwe/techinsidersXXX-citisignal-aem-accs)
- Access your website here:
  - **`https://main--techinsidersX-citisignal-aem-accs--woutervangeluwe.aem.page/`** (replace X by your number)
  - **`https://main--techinsidersX-citisignal-aem-accs--woutervangeluwe.aem.live/`** (replace X by your number)
  - **`https://techinsidersX.adobedemosystem.com/`**  (replace X by your number)

## Introduction

After completing the previous exercise, you could see a product being returned by ACCS to your website but it didn't have an image yet. At the end of this exercise, you should see an image being returned as well.

![ACCS+AEM Sites](./images/accsaemsites11.png)

## 1.5.3.1 Update Pipeline Config

Go to [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. The org you should select is `--aepImsOrgName--`. 

Click to open your Cloud Manager Program, which should be named like one of the below:

-  `--aepUserLdap-- - CitiSignal AEM+ACCS`
-  For in-person tech lab sessions: **Tech Insiders - AEM + ACCS XXX** XXX
-  For guided on-demand sessions: **Tech Insiders On Demand - AEM + ACCS XXX**

![ACCS+AEM Assets](./images/accsaemassets1.png)

Scoll down a little bit and then click **Access Repo Info** on the **Pipelines** tab. 

![ACCS+AEM Assets](./images/accsaemassets2.png)

You should then see this. Click **Generate Password**.

![ACCS+AEM Assets](./images/accsaemassets3.png)

Click **Generate Password** again.

![ACCS+AEM Assets](./images/accsaemassets4.png)

You should then have a password available. Next, click the **copy** icon next to the **URL** field.

![ACCS+AEM Assets](./images/accsaemassets5.png)

Open **GitHub Desktop**. Go to **File** and select **Clone Repository...**.

![ACCS+AEM Assets](./images/ghdskt1.png)

Paste the URL that you copied before in the field **Repository URL** and then click **Clone**.

![ACCS+AEM Assets](./images/ghdskt2.png)

First, copy the **Username** value and then second, copy the **Password** value.

![ACCS+AEM Assets](./images/ghdskt4.png)

Paste the **Username** and **Password** here. Click **Ok**.

![ACCS+AEM Assets](./images/ghdskt3.png)

You should then see this. Click **Show in Finder**.

![ACCS+AEM Assets](./images/ghdskt5.png)

You should then see a folder like this one. Open it.

![ACCS+AEM Assets](./images/ghdskt6.png)

Select all the files and then delete them.

![ACCS+AEM Assets](./images/ghdskt7.png)

You should then have an empty folder.

![ACCS+AEM Assets](./images/ghdskt8.png)

Go to [https://github.com/ankumalh/assets-commerce](https://github.com/ankumalh/assets-commerce). Click **<> Code** and then select **Download ZIP**. Download the file and then drop it on your desktop.

![ACCS+AEM Assets](./images/accsaemassets15a.png)

Next, copy the file **assets-commerce-main.zip** to your desktop and unzip it. Open the folder **assets-commerce-main**.

![ACCS+AEM Assets](./images/accsaemassets16.png)

Copy all the files from the directory **assets-commerce-main** to the empty directory of your GitHub Desktop's Repository directory.

![ACCS+AEM Assets](./images/accsaemassets17.png)

You should then see this.

![ACCS+AEM Assets](./images/accsaemassets17a.png)

Next, open **Microsoft Visual Studio Code** and click **Open...**.

![ACCS+AEM Assets](./images/accsaemassets17b.png)

Open the folder that contains your Program's Pipeline Repository in **Microsoft Visual Studio Code**.

![ACCS+AEM Assets](./images/accsaemassets18.png)

Go to **Search** in the left menu and search for `<my-app>`. You need to replace all occurences of `<my-app>` by `techinsiderscitisignalaemaccs`.

Click the **replace all** icon.

![ACCS+AEM Assets](./images/accsaemassets19.png)

Click **Replace**.

![ACCS+AEM Assets](./images/accsaemassets20.png)

The new files are now ready to be uploaded back to the Git Repo that is linked to your Program's Pipeline Repository. To do that, go back to **GitHub Desktop**. You should see something similar, with changed files waiting to be committed.

![ACCS+AEM Assets](./images/accsaemassets21.png)

Enter `add assets integration` and then click **Commit 13 files to main**.

![ACCS+AEM Assets](./images/accsaemassets22.png)

You should then see this. Click **Push origin**.

![ACCS+AEM Assets](./images/accsaemassets23.png)

You should then see this. Your changes have now been deployed to your Program's Pipeline Git Repo.

![ACCS+AEM Assets](./images/accsaemassets24.png)

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

From the dropdown list for **AEM Environment**, select your environment.

Then, set **Visualization Owner** to `AEM Assets`  (disable the **use system value** checkbox if needed).

Then, set **Synchronization enabled** to `Yes` (disable the **use system value** checkbox if needed).

Ensure that these settings are set as follows:

- **Asset matching rule**: `Match by product SKU`
- **Match by product SKU attribute name**: `commerce:skus`

Click **Save Config**.

![ACCS+AEM Assets](./images/accsaemassets51.png)

You should then see this.

![ACCS+AEM Assets](./images/accsaemassets52.png)

## 1.5.3.3 Update config.json

Go to the GitHub repository that was created when setting up your AEM Sites CS/EDS environment. 

In the root directory, scroll down and click to open the file **config.json**. 

You should see the below line in your **config.json** file (line 17 in this image), make sure it is set to **true**.

```json
 "commerce-assets-enabled": "true",
```

![ACCS+AEM Assets](./images/accsaemassets101.png)

If the value of **commerce-assets-enabled** is set to **false**, update your file and set the value to **true**. Then, commit your changes.

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

You should now repeat these steps for the remaining products, using the table below. Don't forget to approve each image, and then configure the. below SKU settings in the **Commerce** tab.

| Product Name | Key     | Value     | Usage     |
|:-------------:|:-------------:| :---------------:| :---------------:|
|Apple Watch Ultra 3-Black| `Apple-Watch-Ultra-3-Black`| `1` |`thumbnail, image, swatch_image, small_image`|
|Apple Watch Ultra 3-Natural| `Apple-Watch-Ultra-3-Natural`| `1` |`thumbnail, image, swatch_image, small_image`|
|CitiSignal Fiber Max| `CitiSignal-Fiber-Max`| `1` |`thumbnail, image, swatch_image, small_image`|
|Apple One| `Apple-One`| `1` |`thumbnail, image, swatch_image, small_image`|
|YouTube Premium| `YouTube-Premium`| `1` |`thumbnail, image, swatch_image, small_image`|
|Disney Plus| `Disney`| `1` |`thumbnail, image, swatch_image, small_image`|
|Netflix + HBO Max| `Netflix-HBO-Max`| `1` |`thumbnail, image, swatch_image, small_image`|

All your images should then be approved.

![ACCS+AEM Assets](./images/accsaemassets251.png)

## 1.5.3.5 Verify Product Images on AEM Sites CS/EDS Storefront

>[!NOTE]
>
>It may take up to 15 minutes before the changes you made above are successfully deployed. If you don't see your image being shown yet, wait 15 minutes and then try again.
 
To verify that the integration is working, you need to open your CitiSignal website.

You should then see this. Go to **Phones**.

![ACCS+AEM Assets](./images/accsaemassets150.png)

You should then see a product image being shown for the **iPhone Air**. Click **iPhone Air**.

![ACCS+AEM Assets](./images/accsaemassets151.png)

You should then see this. Make a change to the color and storage options, and you'll see the images dynamically change based on the choices you made.

![ACCS+AEM Assets](./images/accsaemassets152.png)

Here's an example of changing the color to **Light-Gold** and the storage size to **256GB**.

![ACCS+AEM Assets](./images/accsaemassets153.png)

Go Back to [Adobe Commerce as a Cloud Service](./accs.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
