---
title: Getting started with Adobe Commerce as a Cloud Service
description: Getting started with Adobe Commerce as a Cloud Service
kt: 5342
doc-type: tutorial
---
# 1.5.1 Getting started with Adobe Commerce as a Cloud Service

Go to [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Ensure you're in the correct environment, which should be named `--aepImsOrgName--`. Click **Commerce**.

![AEM Assets](./images/accs1.png)

## 1.5.1.1 Create your ACCS instance

You should then see this. Click **+ Add Instance**.

![AEM Assets](./images/accs2.png)

Fill out the fields like this:

- **Instance name**: `--aepUserLdap-- - ACCS`
- **Environment**: `Sandbox`
- **Region**: `North America`

Click **Add instance**.

![AEM Assets](./images/accs3.png)

You're instance is now being created. This may take 5-10 minutes.

![AEM Assets](./images/accs4.png)

Once the instance is ready, click your instance to open it.

![AEM Assets](./images/accs5.png)

## 1.5.1.2 Setup your CitiSignal store

You should then see this. Click **Sign in with Adobe ID** and then log in.

![AEM Assets](./images/accs6.png)

Once you're logged in, you should see this homepage. The first step is to set up your CitiSignal store in Commerce. Click **Stores**.

![AEM Assets](./images/accs7.png)

Click **All Stores**.

![AEM Assets](./images/accs8.png)

Click **Create Website**.

![AEM Assets](./images/accs9.png)

Fill out the fields like this:

- **Name**: `CitiSignal`
- **Code**: `citisignal`

Click **Save Web Site**.

![AEM Assets](./images/accs10.png)

You should then be back here. Click **Create Store**.

![AEM Assets](./images/accs11.png)

Fill out the fields like this:

- **Website**: `CitiSignal`
- **Name**: `CitiSignal`
- **Code**: `citisignal`
- **Root Category**: `Default Category`

Click **Save Store**.

![AEM Assets](./images/accs12.png)

You should then be back here. Click **Create Store View**.

![AEM Assets](./images/accs13.png)

Fill out the fields like this:

- **Store**: `CitiSignal`
- **Name**: `CitiSignal`
- **Code**: `citisignal`
- **Status**: `Enabled`

Click **Save Store View**.

![AEM Assets](./images/accs14.png)

You should then see this message. Click **OK**.

![AEM Assets](./images/accs15.png)

You should then be back here. Click the **CitiSignal** website to open it.

![AEM Assets](./images/accs16.png)

Check the checkbox to set this website as the default website.

Click **Save Web Site**.

![AEM Assets](./images/accs16a.png)

You should then be back here. 

![AEM Assets](./images/accs16.png)

## 1.5.1.3 Configure Categories and Products

Go to **Catalog** and then select **Categories**.

![AEM Assets](./images/accs17.png)

Select **Default Category** and then click **Add Subcategory**.

![AEM Assets](./images/accs18.png)

Enter the name `Phones` and then click **Save**.

![AEM Assets](./images/accs19.png)

Select **Default Category** and then click **Add Subcategory** again.

![AEM Assets](./images/accs20.png)

Enter the name `Watches` and then click **Save**.

![AEM Assets](./images/accs21.png)

You should then have 2 categories created.

![AEM Assets](./images/accs22.png)

Next, go to **Catalog** and then select **Products**.

![AEM Assets](./images/accs23.png)

You should then see this. Click **Add Product**.

![AEM Assets](./images/accs24.png)

Configure your product like this:

- **Product Name**: `iPhone Air`
- **SKU**: `iPhone-Air`
- **Price**: `999`
- **Quantity**: `10000`
- **Categories**: select `Phones`

Click **Save**.

![AEM Assets](./images/accs25.png)

Scroll down to **Configurations** and click **Create Configurations**.

![AEM Assets](./images/accs26.png)

You should then see this. Click **Create New Attribute**.

![AEM Assets](./images/accs27.png)

Set the **Default Label** to `Storage` and then click **Add Option** under **Manage Options**.

![AEM Assets](./images/accs28.png)

Configure the first option using the name `256GB` in all 3 columns, and then click **Add Option** again.

![AEM Assets](./images/accs29.png)

Configure the second option using the name `512GB` in all 3 columns, and then click **Add Option** again.

![AEM Assets](./images/accs30.png)

Configure the third option using the name `1TB` in all 3 columns, and then click **Add Option** again.

![AEM Assets](./images/accs31.png)

Scroll down to **Storefront Properties**. Set the following options to **Yes**:

- **Use in Search**
- **Allow HTML Tags on Storefront**
- **Visible on Catalog Pages on Storefront**
- **Use in Product Listing**

![AEM Assets](./images/accs32.png)

Scroll up and click **Save Attribute**.

![AEM Assets](./images/accs33.png)

You should then see this. Seledct both attributes for **color** and **storage** and click **Next**.

![AEM Assets](./images/accs34.png)

You should then see this. You now need to add the available color options. To do that, click **Create New Value**.

![AEM Assets](./images/accs35.png)

Enter the value `Sky-Blue` and click **Create New Value**.

![AEM Assets](./images/accs36.png)

Enter the value `Light-Gold` and click **Create New Value**.

![AEM Assets](./images/accs37.png)

Enter the value `Cloud-White` and click **Create New Value**.

![AEM Assets](./images/accs38.png)

Enter the value `Space-Black`. Click **Select all**

![AEM Assets](./images/accs39.png)

Select all 3 options under **Storage** and click **Next**.

![AEM Assets](./images/accs40.png)

Leave the default settings and click **Next**.

![AEM Assets](./images/accs41.png)

You should then see this. Click **Generate Products**.

![AEM Assets](./images/accs42.png)

Click **Save**.

![AEM Assets](./images/accs43.png)

Scroll down to **Product in Websites** and check the checkbox for **CitiSignal**.

Click **Save**.

![AEM Assets](./images/accs44.png)

Click **Confirm**.

![AEM Assets](./images/accs45.png)

You should then see this. Click **Back**.

![AEM Assets](./images/accs46.png)

You now see the product **iPhone Air** and its variations in the Product Catalog.

![AEM Assets](./images/accs47.png)


Next Step: [Connect ACCS to AEM Sites CS/EDS Storefront](./ex2.md){target="_blank"}

Go Back to [Adobe Commerce as a Cloud Service](./accs.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
