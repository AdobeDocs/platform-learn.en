---
title: Implement Brand Concierge on your website
description: Implement Brand Concierge on your website
kt: 5342
doc-type: tutorial
---
# 1.4.2 Implement Brand Concierge on your website

>[!IMPORTANT]
>
>In order to complete this exercise, you need to have access to a working AEM Assets CS Author environment and  an AEM CS/EDS website. 
>
>If you don't have such an environment, go to [Adobe Experience Manager Cloud Service & Edge Delivery Services](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"}. Follow the instructions there, and you'll have access to such an environment.

>[!IMPORTANT]
>
>If you have previously configured an AEM CS Program with an AEM Assets CS environment, it may be that your AEM CS sandbox was hibernated. Given that dehibernating such a sandbox takes 10-15 minutes, it would be a good idea to start the dehibernation process now so that you don't have to wait for it at a later time.

## 1.4.2.1 Configure your website to show Brand Concierge - AEM Author

In order for Brand Concierge to appear on your website, you need to create a new custom block that needs to be added to a new page, and you'll need to ensure that your new page is added to the navigation of your website.

You now need to configure the following things in this order:

- Create a new custom block that will be used to load Brand Concierge on your website.
- Create a new page on your website for Brand Concierge.
- Link the newly created custom block on the newly created Brand Concierge page.
- Add a reference to navigate to the newly created Brand Concierge page in your website's navigation header file.

### Create new custom block

To create the new custom block, navigate to the GitHub repository that is linked to your website.

![Block](./images/block1.png)

#### component-definition.json

Scroll down until you see the file **component-definition.json** and open it

![Block](./images/block8.png)

Click the **pencl** icon to start editing the file.

![Block](./images/block8a.png)

Scroll down until you see the **Blocks**. Set your cursor under the closing bracket of the component **Cards**

![Block](./images/block9.png)

Paste this code and enter a comma **,** after the block of code:

```json
{
  "title": "BrandConcierge",
  "id": "brandconcierge",
  "plugins": {
    "xwalk": {
      "page": {
        "resourceType": "core/franklin/components/block/v1/block",
        "template": {
          "name": "BrandConcierge",
          "model": "brandconcierge"
        }
      }
    }
  }
},
```

Click **Commit changes...**.

![Block](./images/block10.png)

Click **Commit changes**.

![Block](./images/block10a.png)

#### component-models.json

Scroll down until you see the file **component-models.json** and click the **pencil** icon to start editing the file.

![Block](./images/block11.png)

Scroll down until you see the last item. Set your cursor next to the closing bracket of the last component.

![Block](./images/block12.png)

Enter a comma **,**, then push enter and on the next line, paste this code:

```json
{
  "id": "brandconcierge",
  "fields": []
}
```

Click **Commit changes...**.

![Block](./images/block13.png)

Click **Commit changes**.

![Block](./images/block13a.png)

#### component-filters.json

Scroll down until you see the file **component-filters.json** and click the **pencil** icon to start editing the file.

![Block](./images/block14.png)

You should then see this.

![Block](./images/block14a.png)

Under **section**, enter a comma `,` and paste the id of your component `"brandconcierge"` after the current last line.

Click **Commit changes...**.

![Block](./images/block15.png)

Click **Commit changes**.

![Block](./images/block15a.png)

#### brandconcierge.css

When creating a block, it's best practice to create a file for the styling of your block, and it should have the same name as your block. you should now create that file, which we will leave empty for now.

Go to the **blocks** folder. Then, click **Add file** and select **Create new file**.

![Block](./images/css1.png)

In the text box, enter `brandconcierge/brandconcierge.css`. The file can remain empty for now. Click **Commit changes...**.

![Block](./images/css2.png)

Click **Commit changes**.

![Block](./images/css3.png)

#### brandconcierge.js

When creating a block, it's best practice to create a file for the javascript related to your block, and it should have the same name as your block.

Click **Add file** and select **Create new file**.

![Block](./images/js1.png)

In the text box, enter `brandconcierge.js`. The file can remain empty for now. Click **Commit changes...**.

```javascript
export default function decorate(block) {
  block.setAttribute('id', 'brand-concierge-mount');
}
```

![Block](./images/js2.png)

Click **Commit changes**.

![Block](./images/js3.png)

### Create new page & link new custom block

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

- Title: **Brand Concierge**
- Name: **brandconcierge**
- Page Title: **Brand Concierge**

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

You should then see an empy block being added to this page. This block will be loaded dynamically using the javacript libraries you'll be adding in the next step.

Click **Publish**.

![AEMCS](./images/block29.png)

Click **Publish** again.

![AEMCS](./images/block30.png)

Your new page is now published, and can now be added to the navigation header in the next step.

### Update navigation header file

In your AEM Sites overview, go to **CitiSignal** and check the checkbox for the file **Header/nav**. Click **Edit**.

![AEMCS](./images/nav0.png)

Select the **Text** field in the preview screen and then click the **Text** field on the right side of the screen to edit it.

![AEMCS](./images/nav0a.png)

Create a new menu option in the nav menu with the text `Brand Concierge`. Then, select the text **Brand Concierge** and click the **link** icon.

![AEMCS](./images/nav1.png)

Enter this for the field **Path or URL** `/content/CitiSignal/brandconcierge.html` and enter `Brand Concierge` for the field **Title**. Click **Save**.

![AEMCS](./images/nav3.png)

You should then have this. Click **Done**.

![AEMCS](./images/nav4.png)

You should then have this. Click **Publish**.

![AEMCS](./images/nav4a.png)

Click **Publish** again.

![AEMCS](./images/nav5.png)

Your new page is now added to the menu.

## 1.4.2.2 Configure your website to show Brand Concierge - GitHub

After updating the content using your AEM Author environment, you now need to update some of the code in the GitHub repository that is used for your website.

### Javascript Libraries

The following libraries are required to implement Brand Concierge on your website running on AEM CS/EDS:

- [styleconfigurations.js](./assets/styleconfigurations.js)
- [alloy.js](./assets/alloy.js)
- [brandconciergemain.js](./assets/brandconciergemain.js)

Download all 3 files to your desktop.

![Brand Concierge](./images/aem0.png)

Go to the GitHub project of your AEM CS/EDS website. Go to **scripts**.

![Brand Concierge](./images/aem1.png)

Click **Add file** and then select **Upload files**.

![Brand Concierge](./images/aem3.png)

Click **Choose your files**.

![Brand Concierge](./images/aem3a.png)

Select all 3 files **styleConfigurations.js, alloy.js and brandconciergemain.js** from your desktop and click **Open**.

![Brand Concierge](./images/aem4.png)

Click **Commit changes**.

![Brand Concierge](./images/aem5.png)

### Update head.html

In the previous step you uploaded 3 new libraries. These libraries now need to be loaded when your website is loaded and the way to do that is to add references to these files in the file **head.html**. 

Additionally, you also need to provide instructions in the **head.html** file to ensure that the libraries are loaded in the right order and in a correct way.

To do that, go to the GitHub project of your AEM CS/EDS website by clicking **Code**.

![Brand Concierge](./images/aem6.png)

Scroll down a little bit. Open the file **head.html**.

![Brand Concierge](./images/aem7.png)

Click the **pencil** icon to edit this file.

![Brand Concierge](./images/aem8.png)

You should then see this. 

![Brand Concierge](./images/aem9.png)

Scroll down to line 43 and paste the following:

There are 2 fields in the below code that you need to update:

>[!IMPORTANT]
>
>- **datastreamId** is currently set to "XXXXX" and need to be replaced by the ID of the datastream that you created in the previous step.
>- **orgId** needs to be replaced by the IMS Org ID of your Adobe Experience Cloud instance.

```javascript
<script src="/scripts/styleconfigurations.js"></script>

<script>
		!function (n, o) {
      o.forEach(function (o) {
        n[o] || ((n.__alloyNS = n.__alloyNS ||
          []).push(o), n[o] = function () {
            var u = arguments; return new Promise(
              function (i, l) { n[o].q.push([i, l, u]) })
          }, n[o].q = [])
      })
    }
      (window, ["alloy"]);
	</script>


<script src="/scripts/alloy.js"></script>

<script>
	alloy("configure", {
		defaultConsent: "in",
        edgeDomain: "edge.adobedc.net",
        edgeBasePath: "ee",
        datastreamId: "XXXXX", // replace datastreamId
        orgId: "--aepImsOrgId--", // replace ims org Id
        debugEnabled: true,
        idMigrationEnabled: false,
        thirdPartyCookiesEnabled: false,
        prehidingStyle: ".personalization-container { opacity: 0 !important }",
    });

window["alloy"]("sendEvent", {
    conversation: {
        fetchConversationalExperience: true
    }
}).then(result => {
    console.log("Conversation experience fetched", result);
    window["alloy"]("bootstrapConversationalExperience", {
        selector: "#brand-concierge-mount",
        src: "/scripts/brandconciergemain.js",
        stylingConfigurations: window.styleConfiguration,
        stickySession: true // create a sticky session cookie with expiration
    })
});
</script>
```

Click **Commit change...**.

![Brand Concierge](./images/aem10.png)

Click **Commit change**.

![Brand Concierge](./images/aem11.png)

You've now updated the required code to load the libraries on your website.

![Brand Concierge](./images/aem12.png)

## 1.4.2.3 Test your configuration

You will now be able to test your changes on your website by going to `main--citisignal-aem-accs--XXX.aem.page` or `main--citisignal-aem-accs--XXX.aem.live`, after replacing XXX by your GitHub user account, which in this example is `woutervangeluwe`.

In this example, the full URL becomes this:
`https://main--citisignal-aem-accs--woutervangeluwe.aem.page` and/or `https://main--citisignal-aem-accs--woutervangeluwe.aem.live`.

It may take some time before all the assets are shown correctly, as they need to be published first.

You should then see this. Click **Brand Concierge**.

![Brand Concierge](./images/aem13.png)

You should then see this Brand Concierge where you can enter your prompt.

![Brand Concierge](./images/aem14.png)

Go Back to [Brand Concierge](./brandconcierge.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}