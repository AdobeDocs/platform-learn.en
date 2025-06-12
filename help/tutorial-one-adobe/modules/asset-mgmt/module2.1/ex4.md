---
title: AEM CS - Basic Custom Block
description: AEM CS - Basic Custom Block
kt: 5342
doc-type: tutorial
exl-id: 57c08a88-d885-471b-ad78-1dba5992da9d
---
# 1.1.4 Develop a basic custom block

## 1.1.4.1 Setup your local development environment

Go to [https://desktop.github.com/download/](https://desktop.github.com/download/){target="_blank"}, download and install **Github Desktop**.

![Block](./images/block1.png){zoomable="yes"}

Once Github Desktop is installed, go to the GitHub repo you created in the previous exercise. Click **<> Code** and then click **Open with GitHub Desktop**.

![Block](./images/block2.png){zoomable="yes"}

Your GitHub repo will then be opened in GitHub Desktop. Feel free to change the **Local Path**. Click **Clone**.

![Block](./images/block3.png){zoomable="yes"}

A local folder will now be created.

![Block](./images/block4.png){zoomable="yes"}

Open Visual Studio Code. Go to **File** > **Open Folder**.

![Block](./images/block5.png){zoomable="yes"}

Select the folder that is used by your GitHub setup for **citisignal**.

![Block](./images/block6.png){zoomable="yes"}

You'll now see that folder open in Visual Studio Code, you're now ready to create a new block.

![Block](./images/block7.png){zoomable="yes"}

## 1.1.4.2 Create a basic custom block

Adobe recommends that you develop blocks in a three-phased approach:

- Create the definition and model for the block, review it, and bring it to production.
- Create content with the new block.
- Implement the decoration and styles for the new block.

### component-definition.json

In Visual Studio Code, open the file **component-definition.json**.

![Block](./images/block8.png){zoomable="yes"}

Scroll down until you see the component **Quote**. Set your cursor next to the closing bracket of the last component.

![Block](./images/block9.png){zoomable="yes"}

Paste this code and enter a comma **,** after the block of code:

```json
{
  "title": "FiberOffer",
  "id": "fiberoffer",
  "plugins": {
    "xwalk": {
      "page": {
        "resourceType": "core/franklin/components/block/v1/block",
        "template": {
          "name": "FiberOffer",
          "model": "fiberoffer",
          "offerText": "<p>Fiber will soon be available in your region!</p>",
          "offerCallToAction": "Get your offer now!",
          "offerImage": ""
        }
      }
    }
  }
}
```

Save your changes.

![Block](./images/block10.png){zoomable="yes"}

### component-models.json

In Visual Studio Code, open the file **component-models.json**.

![Block](./images/block11.png){zoomable="yes"}

Scroll down until you see the last item. Set your cursor next to the closing bracket of the last component.

![Block](./images/block12.png){zoomable="yes"}

Enter a comma **,**, then push enter and on the next line, paste this code:

```json
{
  "id": "fiberoffer",
  "fields": [
     {
       "component": "richtext",
       "name": "offerText",
       "value": "",
       "label": "Offer Text",
       "valueType": "string"
     },
     {
       "component": "richtext",
       "valueType": "string",
       "name": "offerCallToAction",
       "label": "Offer CTA",
       "value": ""
     },
     {
       "component": "reference",
       "valueType": "string",
       "name": "offerImage",
       "label": "Offer Image",
        "multi": false
     }
   ]
}
```

Save your changes.

![Block](./images/block13.png){zoomable="yes"}

### component-filters.json

In Visual Studio Code, open the file **component-filters.json**.

![Block](./images/block14.png){zoomable="yes"}

Under **section**, enter a comma **,** and the id of your component **fiberoffer** after the current last line.

Save your changes.

![Block](./images/block15.png){zoomable="yes"}

## 1.1.4.3 Commit your changes

You've now made several changes in your project that need to be committed back to your GitHub repository. To do that, open **GitHub Desktop**.

You should then see the 3 files that you just edited under **Changes**. Review your changes.

![Block](./images/block16.png){zoomable="yes"}

Enter a name for your PR, `Fiber Offer custom block`. Click **Commit to main**.

![Block](./images/block17.png){zoomable="yes"}

You should then see this. Click **Push origin**.

![Block](./images/block18.png){zoomable="yes"}

After a couple of seconds, your changes have been pushed to your GitHub repository.

![Block](./images/block19.png){zoomable="yes"}

In your browser, go to your GitHub account and to the repository your created for CitiSignal. You should then see something like this, showing that your changes have been received.

![Block](./images/block20.png){zoomable="yes"}

## 1.1.4.4 Add your block to a page

Now that your basic quote block is defined and committed to the CitiSignal project, you can add a **fiberoffer** block to an existing page.

Go to [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Click your **Program** to open it.

![AEMCS](./images/aemcs6.png){zoomable="yes"}

Next, click the 3 dots **...** on the **Environments** tab and click **View Details**.

![AEMCS](./images/aemcs9.png){zoomable="yes"}

You'll then see your environment details. Click the URL of your **Author** environment.

>[!NOTE]
>
>It is possible that your environment is hibernated. If that is the case, you'll need to de-hibernate your environment first.

![AEMCS](./images/aemcs10.png){zoomable="yes"}

You should then see your AEM Author environment. Go to **Sites**.

![AEMCS](./images/block21.png){zoomable="yes"}

Go to **CitiSignal** > **us** > **en**.

![AEMCS](./images/block22.png){zoomable="yes"}

Click **Create** and select **Page**.

![AEMCS](./images/block23.png){zoomable="yes"}

Select **Page** and click **Next**.

![AEMCS](./images/block24.png){zoomable="yes"}

Enter the following values:

- Title: **CitiSignal Fiber**
- Name: **citisignal-fiber**
- Page Title: **CitiSignal Fiber**

Click **Create**.

![AEMCS](./images/block25.png){zoomable="yes"}

You should then see this.

![AEMCS](./images/block26.png){zoomable="yes"}

Click in the blank area to select the **section** component. Then, click the plus **+** icon in the right menu.

![AEMCS](./images/block27.png){zoomable="yes"}

You should then see your custom block shown in the list of available blocks. Click to select it.

![AEMCS](./images/block28.png){zoomable="yes"}

You'll then see fields like **Offer Text**, **Offer CTA** and **Offer Image** being added to the editor. Click **+ Add** on the **Offer Image** field to select an image.

![AEMCS](./images/block29.png){zoomable="yes"}

You should then see this. Click to open the folder **citisignal**.

![AEMCS](./images/blockpub1.png){zoomable="yes"}

Select the image **product-enrichment-1.png**. Click **Select**.

![AEMCS](./images/blockpub2.png){zoomable="yes"}

You should then have this. Click **Publish**.

![AEMCS](./images/blockpub3.png){zoomable="yes"}

Click **Publish** again.

![AEMCS](./images/blockpub4.png){zoomable="yes"}

Your new page has now been published.

## 1.1.4.5 Add your new page to the navigation menu

In your AEM Sites overview, go to **CitiSignal** > **Fragments** and check the checkbox for **Header**. Click **Edit**.

![AEMCS](./images/nav0.png){zoomable="yes"}

Add a menu option to the nav menu with the text `Fiber`. Select the text **Fiber** and click the **link** icon.

![AEMCS](./images/nav1.png){zoomable="yes"}

Enter this for the **URL** `/us/en//citisignal-fiber` and click the **V** icon to confirm.

![AEMCS](./images/nav3.png){zoomable="yes"}

You should then have this. Click **Publish**.

![AEMCS](./images/nav4.png){zoomable="yes"}

Click **Publish** again.

![AEMCS](./images/nav5.png){zoomable="yes"}

You will now be able to view the changes to your website by going to `main--citisignal--XXX.aem.page/us/en/` and/or `main--citisignal--XXX.aem.live/us/en/`, after replacing XXX by your GitHub user account, which in this example is `woutervangeluwe`.

In this example, the full URL becomes this:
`https://main--citisignal--woutervangeluwe.aem.page/us/en/` and/or `https://main--citisignal--woutervangeluwe.aem.live/us/en/`.

You should then see this. Click **Fiber**.

![AEMCS](./images/nav6.png){zoomable="yes"}

Here is your basic custom block, but now rendered on the website.

![AEMCS](./images/nav7.png){zoomable="yes"}

Next Step: [1.1.5 Advanced Custom Block](./ex5.md){target="_blank"}

Go Back to [Adobe Experience Manager Cloud Service & Edge Delivery Services](./aemcs.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
