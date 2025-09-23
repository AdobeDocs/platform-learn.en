---
title: AEM CS - Basic Custom Block
description: AEM CS - Basic Custom Block
kt: 5342
doc-type: tutorial
exl-id: 57c08a88-d885-471b-ad78-1dba5992da9d
---
# 1.1.3 Develop a basic custom block

## 1.1.3.1 Setup your local development environment

Go to [https://desktop.github.com/download/](https://desktop.github.com/download/){target="_blank"}, download and install **Github Desktop**.

![Block](./images/block1.png)

Once Github Desktop is installed, go to the GitHub repo you created in the previous exercise. Click **<> Code** and then click **Open with GitHub Desktop**.

![Block](./images/block2.png)

Your GitHub repo will then be opened in GitHub Desktop. Feel free to change the **Local Path**. Click **Clone**.

![Block](./images/block3.png)

A local folder will now be created.

![Block](./images/block4.png)

Open Visual Studio Code. Go to **File** > **Open Folder**.

![Block](./images/block5.png)

Select the folder that is used by your GitHub setup for **citisignal-aem-accs**.

![Block](./images/block6.png)

You'll now see that folder open in Visual Studio Code, you're now ready to create a new block.

![Block](./images/block7.png)

## 1.1.3.2 Create a basic custom block

Adobe recommends that you develop blocks in a three-phased approach:

- Create the definition and model for the block, review it, and bring it to production.
- Create content with the new block.
- Implement the decoration and styles for the new block.

### component-definition.json

In Visual Studio Code, open the file **component-definition.json**.

![Block](./images/block8.png)

Scroll down until you see the **Blocks**. Set your cursor under the closing bracket of the component **Cards**

![Block](./images/block9.png)

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

![Block](./images/block10.png)

### component-models.json

In Visual Studio Code, open the file **component-models.json**.

![Block](./images/block11.png)

Scroll down until you see the last item. Set your cursor next to the closing bracket of the last component.

![Block](./images/block12.png)

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

![Block](./images/block13.png)

### component-filters.json

In Visual Studio Code, open the file **component-filters.json**.

![Block](./images/block14.png)

Under **section**, enter a comma `,` and paste the id of your component `"fiberoffer"` after the current last line.

Save your changes.

![Block](./images/block15.png)

## 1.1.3.3 Commit your changes

You've now made several changes in your project that need to be committed back to your GitHub repository. To do that, open **GitHub Desktop**.

You should then see the 3 files that you just edited under **Changes**. Review your changes.

![Block](./images/block16.png)

Enter a name for your PR, `Fiber Offer custom block`. Click **Commit to main**.

![Block](./images/block17.png)

You should then see this. Click **Push origin**.

![Block](./images/block18.png)

After a couple of seconds, your changes have been pushed to your GitHub repository.

![Block](./images/block19.png)

In your browser, go to your GitHub account and to the repository your created for CitiSignal. You should then see something like this, showing that your changes have been received.

![Block](./images/block20.png)

## 1.1.3.4 Add your block to a page

Now that your basic quote block is defined and committed to the CitiSignal project, you can add a **fiberoffer** block to an existing page.

Go to [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. Click your **Program** to open it.

![AEMCS](./images/aemcs6.png)

Next, click the 3 dots **...** on the **Environments** tab and click **View Details**.

![AEMCS](./images/aemcs9.png)

You'll then see your environment details. Click the URL of your **Author** environment.

>[!NOTE]
>
>It is possible that your environment is hibernated. If that is the case, you'll need to de-hibernate your environment first.

![AEMCS](./images/aemcs10.png)

You should then see your AEM Author environment. Go to **Sites**.

![AEMCS](./images/block21.png)

Go to **CitiSignal**. Click **Create** and select **Page**.

![AEMCS](./images/block23.png)

Select **Page** and click **Next**.

![AEMCS](./images/block24.png)

Enter the following values:

- Title: **Fiber**
- Name: **fiber**
- Page Title: **Fiber**

Click **Create**.

![AEMCS](./images/block25.png)

Select **Open**.

![AEMCS](./images/block22.png)

You should then see this. 

![AEMCS](./images/block26.png)

Click in the blank area to select the **section** component. Then, click the plus **+** icon in the right menu.

![AEMCS](./images/block27.png)

You should then see your custom block shown in the list of available blocks. Click to select it.

![AEMCS](./images/block28.png)

You'll then see fields like **Offer Text**, **Offer CTA** and **Offer Image** being added to the editor. Click **+ Add** on the **Offer Image** field to select an image.

![AEMCS](./images/block29.png)

You should then see this. Click to open the folder **citisignal**.

![AEMCS](./images/blockpub1.png)

Select the image **product-enrichment-1.png**. Click **Select**.

![AEMCS](./images/blockpub2.png)

You should then have this. Click **Publish**.

![AEMCS](./images/blockpub3.png)

Click **Publish** again.

![AEMCS](./images/blockpub4.png)

Your new page has now been published.

## 1.1.3.5 Add your new page to the navigation menu

In your AEM Sites overview, go to **CitiSignal** and check the checkbox for the file **Header/nav**. Click **Edit**.

![AEMCS](./images/nav0.png)

Select the **Text** field in the preview screen and then click the **Text** field on the right side of the screen to edit it.

![AEMCS](./images/nav0a.png)

Add a menu option to the nav menu with the text `Fiber`. Select the text **Fiber** and click the **link** icon.

![AEMCS](./images/nav1.png)

Enter this for the **URL** `/content/CitiSignal/fiber.html` and click the **V** icon to confirm.

![AEMCS](./images/nav3.png)

You should then have this. Click **Done**.

![AEMCS](./images/nav4.png)

You should then have this. Click **Publish**.

![AEMCS](./images/nav4a.png)

Click **Publish** again.

![AEMCS](./images/nav5.png)

You will now be able to view the changes to your website by going to `main--citisignal--XXX.aem.page/us/en/` and/or `main--citisignal--XXX.aem.live/us/en/`, after replacing XXX by your GitHub user account, which in this example is `woutervangeluwe`.

In this example, the full URL becomes this:
`https://main--citisignal--woutervangeluwe.aem.page/us/en/` and/or `https://main--citisignal--woutervangeluwe.aem.live/us/en/`.

You should then see this. Click **Fiber**.

![AEMCS](./images/nav6.png)

Here is your basic custom block, but now rendered on the website.

![AEMCS](./images/nav7.png)

Next Step: [Advanced Custom Block](./ex4.md){target="_blank"}

Go Back to [Adobe Experience Manager Cloud Service & Edge Delivery Services](./aemcs.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
