---
title: Getting started with Brand Concierge
description: Getting started with Brand Concierge
kt: 5342
doc-type: tutorial
exl-id: e05b60b1-62d7-4b70-834d-ef91782ac388
TQID: https://experienceleague.adobe.com/ZL7Bq5aArrt9g75boyHdOPqG9DDE5WSjTrLYLrJscBc
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
subfeature_v2:
  - id: e5ae22e3-a3b0-46ed-804f-9abf1bbe3e74
    internal-label: Guardrails
---
# 1.4.1 Getting started with Brand Concierge

>[!IMPORTANT]
>
>Before you begin, read the below instructions!

## Instructor-Led Training (ILT) Instructions

IF YOUR NUMBER IS BETWEEN **1** and **95**, you need to use the following environment details for setting up Brand Concierge:

- **Instance**: **Adobe Tech Insiders**
- **Sandbox**: **techinsidersXXX** and replace XXX by the number that was assigned to you
- **Username**: **adobetechinsiders-XXX@adobeeventlab.com** and replace XXX by the number that was assigned to you
- **Password**: use the password that was shared with you

IF YOUR NUMBER IS BETWEEN **95** and **180**, you need to use:

- **Instance**: **Adobe Tech Insiders 2**
- **Sandbox**: **techinsidersXXX** and replace XXX by the number that was assigned to you
- **Username**: **adobetechinsiders-XXX@adobeeventlab.com** and replace XXX by the number that was assigned to you
- **Password**: use the password that was shared with you


## 1.4.1.1 Brand Concierge instance configuration

To start creating your own Brand Concierge instance, follow the below steps.

Go to [https://experience.adobe.com/](https://experience.adobe.com/). Open **Brand Concierge**.

![Brand Concierge](./images/bc1.png)

You should then see this. Click the **sandbox selection** menu. Choose the sandbox that has been assigned to you. That sandbox should be named `techinsidersX` (replace X by the number you've been assigned).

![Brand Concierge](./images/bc2.png)

Next, enter the URL of your CitiSignal website, which should look like this: (replace X by your number). Click **Create**.

```
techinsidersX.adobedemosystem.com
```

![Brand Concierge](./images/bc2a.png)

You shuold then see this.

![Brand Concierge](./images/bc2b.png)

Update your **Brand Expression**. Click **Continue**.

![Brand Concierge](./images/bc2c.png)

You should then see this. Review your **Brand Profile**. If needed, update the values in the fields using the below details.

**Industry**

```
Telecommunications
```

**Goal**

```
Help customers find their best device, plan or entertainment deal. Help users discover internet plans, entertainment deals,  and help find the best available packages. Answer questions about devices such as phones, watches and FiberMax packages.
```

**Product and services**

```
CitiSignal sells a comprehensive mix of wireless devices, home and business internet services, entertainment bundles, and hardware accessories. CitiSignal's inventory spans consumer tech, home networking, and enterprise services.

Mobile Devices & Plans:
- Smartphones: Current-generation flagship models including the Apple iPhone Air series.
-Tablets & Laptops: Cellular-enabled mobile computing tablets from Apple.
- Smartwatches: Connected wearables such as the Apple Watch Ultra.
- Mobile Broadband
- Wireless Plans: Postpaid and prepaid cellular data subscriptions tailored for individuals, families, and senior citizens.

Broadband & Entertainment Services
- FiberMax Home Internet: High-speed, fiber-optic residential broadband connections.
```

**Target audience**

```
CitiSignal's target audience is divided into two primary categories: individual consumers (B2C) and corporate/government entities (B2B). Because they position themselves as a premium provider focused on network reliability and speed, their marketing strategies target specific demographics, lifestyles, and professional tiers.
```

**Brand value**

```
- Network Reliability Equity: CitiSignal has spent decades positioning its brand around network quality, consistency, and "bulletproof" coverage, allowing it to charge premium tier pricing.
- Infrastructure Investment: Continued multi-billion dollar deployments of 5G Home Internet and high-speed fiber-optic FiberMax networks secure long-term subscriber retention.
- Enterprise & Public Sector Footprint: Serving as the primary communications backbone for federal agencies, municipal first responders, and multinational enterprise organizations ensures immense financial stability and high cash generation.
```

**Key differentiators**

```
CitiSignal differentiates itself from competitors through network reliability, a premium bundling ecosystem, and deep corporate/enterprise integration. While competitors often lean heavily on aggressive pricing strategies, CitiSignal leverages specific structural, technological, and service-based pillars to maintain its high-value customer base.
```

**Common use cases**

```
CitiSignal's common use cases span daily consumer activities, enterprise-grade industrial automation, and highly secure public sector communications. Because CitiSignal provides cellular, fiber, and cloud network computing infrastructures, their technology is applied to multiple distinct real-world scenarios.
```

Click **Continue**.

![Brand Concierge](./images/bc2d.png)

Review your setup and then click **Save Concierge**.

![Brand Concierge](./images/bc2e.png)

After a couple of minutes, you should then see this. 

![Brand Concierge](./images/bc2f.png)

## 1.4.1.2 Knowledge Sources Configuration

Go to **Knowledge Source** and click **Build your knowledge source**.

![Brand Concierge](./images/bc7.png)

Select **Website links** and click **Continue**.

![Brand Concierge](./images/bc7a.png)

You should then see this. Enter `CitiSignal website` as name for your knowledge source. 

You now need to upload a csv file that contains the links of your website. Download [CitiSignal website links CSV file](./assets/citisignal-website-links.csv.zip) to your desktop.

![Brand Concierge](./images/bc8z.png)

Click **Browse Files**.

![Brand Concierge](./images/bc8.png)

Open the file **citisignal-website-links.csv** and update the links to point to your own CitiSignal website.

If you're doing this tech lab as part of the Tech Insiders Tech Lab deliveries, you have been given access to an existing demo website based on an assigned number. These demo websites come with a custom domain that looks like this, whereby XX stand for the number that has been given to you:

**https://techinsidersXX.adobedemosystem.com/** (for in-person training)

or

**https://techinsidersodXX.adobedemosystem.com/** (for on-demand training)

In the below image, you need to replace the base URL by your website's URL.

The links to the products in the file below are related to the products that you configured as part of exercise 1 in the module 
[1.5 Adobe Commerce as a Cloud Service](./../../../modules/asset-mgmt/module1.5/accs.md). 

![Brand Concierge](./images/bc8a.png)

If your number is **1**, your file should look like this:

![Brand Concierge](./images/bc8b.png)

If your number is **90**, your file should look like this:

![Brand Concierge](./images/bc8c.png)

Once you've updated the file as instructed above, select that file **citisignal-website-links.csv** next. Click **Open**.

![Brand Concierge](./images/bc9.png)

Your file is now added to this knowledge source. Click **Add**.

![Brand Concierge](./images/bc10.png)

You should then see this. Click **Build your knowledge source**.

![Brand Concierge](./images/bc11.png)

Select **Product catalog** and click **Continue**.

![Brand Concierge](./images/bc20.png)

You should then see this. Enter `CitiSignal Products` as name for your knowledge source. Click **Browse Files** and then select **Browse from your device**.

![Brand Concierge](./images/bc21.png)

You now need to upload a csv file that contains the links of your website. Download [CitiSignal product catalog](./assets/CitiSignal-catalog.json.zip) to your desktop and unzip it.

![Brand Concierge](./images/bc26.png)

Select the file **CitiSignal-catalog.json** and click **Open**.

![Brand Concierge](./images/bc23.png)

You should then see this. Click **Add**.

![Brand Concierge](./images/bc24.png)

You'll then be back here. Processing will take 10-20 minutes so you'll have to come back here at a later stage to verify if processing was successful.

>[!NOTE]
>
>Don't wait for processing to complete to continue. Continue with the next steps.

![Brand Concierge](./images/bc25.png)

## 1.4.1.3 Data Collection onboarding steps

Brand Concierge uses Adobe Experience Platform to store interaction data from conversations. The connection between Brand Concierge and Experience Platform requires a datastream to be configured and used by Brand Concierge.

### Datastream

Go to [https://experience.adobe.com/](https://experience.adobe.com/). Open **Experience Platform**.

![Brand Concierge](./images/aep1.png)

Ensure that you've selected the right sandbox, which should be named `techinsidersX`. In the left menu, scroll down and select **Datastreams**.

![Brand Concierge](./images/aep2.png)

Click **New Datastream**.

![Brand Concierge](./images/aep3.png)

Enter the **Datastream Name** `--aepUserLdap-- - Brand Concierge` and then select the **Mapping Schema** `cja-brand-concierge-sb-XXX`. 

Click **Save**.

![Brand Concierge](./images/aep4.png)

You shoudl then see this. Click **Add Service**.

![Brand Concierge](./images/aep5.png)

Select the following:

- **Service**: **Adobe Experience Platform**
- **Event Dataset**: **Brand Concierge Conversations Event Dataset**
- check the box in front of **Brand Concierge**

Click **Save**.

![Brand Concierge](./images/aep6.png)

Your datastream is now configured. Copy the datastream name and the datastream id and write them down in a text file on your computer.

![Brand Concierge](./images/aep7.png)

### Datastream Config Management

The next step is to enable the Brand Concierge Configuration Management API to configure the datastream that you just created. This is required to resolve things like IMS Org ID and sandbox details during request processing.

Go to **Home** and then click your Brand Concierge instance..

![Brand Concierge](./images/admincontrols1.png)

Go to **Deployments**.

![Brand Concierge](./images/admincontrols2.png)

You should then see this. Click **+ Add Config**.

![Brand Concierge](./images/admincontrols3.png)

Paste the **Datastream ID** of the datastream that you created earlier. Click **Save**.

![Brand Concierge](./images/admincontrols4.png)

Click **Modify** next to **Surface Config Management**.

![Brand Concierge](./images/admincontrols5.png)

Enter the following:

- **Domain** equals `techinsidersX.adobedemosystem.com`
- **Path** equals `/brandconcierge`

Click **Save**.

![Brand Concierge](./images/admincontrols6.png)

You should then see this.

![Brand Concierge](./images/admincontrols7.png)

## 1.4.1.4 Finish knowledge source setup

Go to **Knowledge Sources**. After 10-20 minutes, the **Status** of both knowledge sources should be **Completed**. 

![Brand Concierge](./images/admincontrols10.png)

Once the status is **Success** for both knowledge sources, click **Home** and then select your Brand Concierge instance.

![Brand Concierge](./images/bc28.png)

Click **Integrations**.

![Brand Concierge](./images/bc29.png)

Click **Browse Integrations**.

![Brand Concierge](./images/bc30.png)

Select the integration **Product Catalog** and click **Configure**.

![Brand Concierge](./images/bc31.png)

Click **Select knowledge source**.

![Brand Concierge](./images/bc32.png)

Select the knowledge source **CitiSignal Products** and click **Save**.

![Brand Concierge](./images/bc33.png)

Click the **Save** icon.

![Brand Concierge](./images/bc34.png)

You should then see this. Click **Knowledge Base Search**.

![Brand Concierge](./images/bc35.png)

Click **Configure**.

![Brand Concierge](./images/bc36.png)

Click the field for the current knowledge source.

![Brand Concierge](./images/bc37.png)

Select **CitiSignal website** and click **Save**.

![Brand Concierge](./images/bc38.png)

You should then see this. Click **Save**.

![Brand Concierge](./images/bc39.png)

You can now start testing your Brand Concierge. Enter the question `what products do you sell?` and click **send**.

![Brand Concierge](./images/bc102.png)

You should then get a similar response back.

![Brand Concierge](./images/bc103.png)

Your Brand Concierge instance is now ready to be implemented on your website.

## Next Steps

Go to [Implement Brand Concierge on your website](./ex2.md){target="_blank"}

Go back to [Brand Concierge](./brandconcierge.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}

