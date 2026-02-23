---
title: Create your first form
description: Create your first form
kt: 5342
doc-type: tutorial
---
# 1.3.1 Create your first form

>[!IMPORTANT]
>
>In order to complete this exercise, you need to have access to a working AEM Assets CS Author environment with AEM Assets Dynamic Media enabled.
>
>If you don't have such an environment, go to [Adobe Experience Manager Cloud Service & Edge Delivery Services](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"}. Follow the instructions there, and you'll have access to such an environment.

>[!IMPORTANT]
>
>If you have previously configured an AEM CS Program with an AEM Assets CS environment, it may be that your AEM CS sandbox was hibernated. Given that dehibernating such a sandbox takes 10-15 minutes, it would be a good idea to start the dehibernation process now so that you don't have to wait for it at a later time.

## 1.3.1.1 Environment requirements for using AEM Forms with Edge Delivery Services

Prior to configuring your first form, there are a number of requirements that need to be met before you can follow the below steps.

### Program setup

In the **Solutions & add-ons** of your Cloud Manager Program, **Forms** needs to be enabled.

![AEM Forms](./images/program.png)

### blocks

In your Github repository, you need to have the following blocks available:

- **form**
- **embed-adaptive-form**

![AEM Forms](./images/block.png)

### scripts

In your Github repository, you need to have the following scripts available:

- **form-editor-support.css**
- **form-editor-support.js**

![AEM Forms](./images/scripts1.png)

Additionally, in the file **editor-support.js**, the following changes need to be done to enable editing forms in the Universal Editor.

- change function declaration from **function attachEventListners(main) {** to **async function attachEventListners(main) {**
- add lines 152 and 153:
  
```
const module = await import('./form-editor-support.js');
module.attachEventListners(main);
```
  
![AEM Forms](./images/scripts2.png)

Also, in the file **editor-support.js**, change lines 90-92 like this:

```
if (block.dataset.aueModel === 'form') {
        return true;
      } else if (newBlock) {
```

![AEM Forms](./images/scripts3.png)

### paths.json

Please verify your Github repo configuration, specifically in the file **paths.json**. These lines need to be present in the file:

- Under mappings: **"/content/forms/af/:/forms/"**
- Under includes: **"/content/forms/af/"**

```json
{
  "mappings": [
    "/content/CitiSignal/:/",
    "/content/CitiSignal/configuration:/.helix/config.json",
    "/content/CitiSignal/headers:/.helix/headers.json",
    "/content/CitiSignal/metadata:/metadata.json",
    "/content/CitiSignal.resource/enrichment/enrichment.json:/enrichment/enrichment.json",
    "/content/forms/af/:/forms/"
  ],
  "includes": [
    "/content/CitiSignal/",
    "/content/forms/af/"
  ]
}
```

![AEM Forms](./images/paths.png)

With these requirements in place, you can create your first form.

## 1.3.1.1 Create form

Go to [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. The org you should select is `--aepImsOrgName--`. Open your environment.

![AEM Forms](./images/aemforms1.png)

Go to **Forms**.

![AEM Forms](./images/aemforms2.png)

Go to **Forms & Documents**.

![AEM Forms](./images/aemforms3.png)

Click **Create** and then select **Adaptive Form**.

![AEM Forms](./images/aemforms4.png)

Select **Edge Delivery Services** and then select **Blank Page**. Click **Create**.

![AEM Forms](./images/aemforms5.png)

You should then see this. Fill out the following fields:

- **Title**: `Fiber Max Interest Form`
- **Name**: should be populated automatically based on the field **Title**.
- **Github URL**: provide the path to the Github repo that is linked to your website

Click **Create**.

![AEM Forms](./images/aemforms6.png)

After clicking **Create**, the **Universal Editor** should open automatically and you should see something like this. Click the icon to open the **Content Tree**.

![AEM Forms](./images/aemforms7.png)

In the **Content Tree**, select the object **Adaptive Form**.

![AEM Forms](./images/aemforms8.png)

Then, click the **+** icon to add a new element, and select **text Input**.

![AEM Forms](./images/aemforms9.png)

In the **Content Tree**, select the field **Text Input**.

![AEM Forms](./images/aemforms10.png)

Go to the **Basic** view. You should see this.

Fill out the following fields:

- **Name**: `first-name`
- **Title**: `First Name`

Then, go to **Validation**.

![AEM Forms](./images/aemforms11.png)

Flip the switch to make this a required field. Fill out the following fields:

- **Error message**: `Enter your first name`
- **Pattern**: `[A-Za-z][A-Za-z ]+`
- **Pattern error message**: `Letters only!`

![AEM Forms](./images/aemforms12.png)

In the **Content Tree**, select the field **Adaptive Form**. Click the **+** icon and then select **text Input**.

![AEM Forms](./images/aemforms13.png)

In the **Content Tree**, select the newly created field **Text Input**. Go to **Properties**.

![AEM Forms](./images/aemforms14.png)

Go to the **Basic** view. You should see this.

Fill out the following fields:

- **Name**: `last-name`
- **Title**: `Last Name`

Then, go to **Validation**.

![AEM Forms](./images/aemforms15.png)

Flip the switch to make this a required field. Fill out the following fields:

- **Error message**: `Enter your last name`
- **Pattern**: `[A-Za-z][A-Za-z ]+`
- **Pattern error message**: `Letters only!`

![AEM Forms](./images/aemforms16.png)

In the **Content Tree**, select the field **Adaptive Form**. Click the **+** icon and then select **text Input**.

![AEM Forms](./images/aemforms17.png)

In the **Content Tree**, select the newly created field **Text Input**. Go to **Properties**.

![AEM Forms](./images/aemforms18.png)

Go to the **Basic** view. You should see this.

Fill out the following fields:

- **Name**: `email`
- **Title**: `Email`

Then, go to **Validation**.

![AEM Forms](./images/aemforms19.png)

Flip the switch to make this a required field. Fill out the following fields:

- **Error message**: `Enter your email address`
- **Pattern**: `^[^@]+@[^@]+\.[^@]+$`
- **Pattern error message**: `Please verify your email address!`

![AEM Forms](./images/aemforms20.png)

In the **Content Tree**, select the field **Adaptive Form**. Click the **+** icon and then select **text Input**.

![AEM Forms](./images/aemforms21.png)

In the **Content Tree**, select the newly created field **Text Input**.

![AEM Forms](./images/aemforms22.png)

Go to the **Basic** view. You should see this.

Fill out the following fields:

- **Name**: `city`
- **Title**: `city`

Then, go to **Validation**.

![AEM Forms](./images/aemforms23.png)

Flip the switch to make this a required field. Fill out the following fields:

- **Error message**: `Enter your city`
- **Pattern**: `[A-Za-z][A-Za-z ]+`
- **Pattern error message**: `Letters only!`

![AEM Forms](./images/aemforms24.png)

Click **Publish**.

![AEM Forms](./images/aemforms25.png)

Click **Publish** again.

![AEM Forms](./images/aemforms26.png)

Click to open your form.

![AEM Forms](./images/aemforms27.png)

You can then fill out the form, but you can't submit it yet.

![AEM Forms](./images/aemforms28.png)

After publishing your form, it's now also available on your Edge Delivery Services domain, which looks like this:

`https://main--techinsidersXX-citisignal-aem-accs--woutervangeluwe.aem.page/forms/fiber-max-interest-form`

![AEM Forms](./images/aemforms29.png)

## 1.3.1.2 Submit form

In order to submit your form, 2 things are required:

- a **Submit** button
- a **Submit** action

Also, in this exercise you should use a Google spreadsheet to record submissions of this form.

### Google spreadsheet

Go to [https://drive.google.com](https://drive.google.com) and create a new blank spreadsheet.

![AEM Forms](./images/sheet1.png)

Name your file `citisignal-fiber-max-interest`.

In line 1, in cells A-B-C-D, enter the following field names:

- first-name
- last-name
- email
- city

Then, click **Share**.

![AEM Forms](./images/sheet2.png)

Share the file with **forms@adobe.com** with **Editor**-level access rights.

Then, click **Copy link**.

Click **Send**.

![AEM Forms](./images/sheet3.png)

You will need to use the copied link in the next step.

### Submit button

To configure the **Submit** button, go to **Content tree**, select **Adaptive Form**, click the **+** icon and then select **Submit**.

![AEM Forms](./images/aemforms30.png)

You should then see this.

![AEM Forms](./images/aemforms31.png)

### Submit action

Submit actions are part of an extension for the Universal Editor. 

>[!NOTE]
>
>If you don't see the **Edit Form Properties** icon, it means that this etxension isn't enabled for your environment yet. To enable this extension, go to [https://experience.adobe.com/#/aem/extension-manager](https://experience.adobe.com/#/aem/extension-manager) and enable the **Edit Form Properties** extension.
>
>![AEM Forms](./images/extmgr.png)

Click the **Edit Form Properties** icon.

![AEM Forms](./images/aemforms32.png)

Select **Submit to Spreadsheet**. Paste the URL of the Google Sheet that you created earlier.

Click **Save & Close**.

![AEM Forms](./images/aemforms33.png)

>[!NOTE]
>
>If you receive an error 401 - Unauthorized, it may be. because your environment hasn't been enabled to work with Google Sheets. Contact your Adobe representative to have your environment enabled.

Click **Publish**.

![AEM Forms](./images/aemforms34.png)

Click **Publish** again.

![AEM Forms](./images/aemforms35.png)

You can then refresh your site, fill out the forms and click **Submit**.

![AEM Forms](./images/aemforms36.png)

Your submission should then be successful.

![AEM Forms](./images/aemforms37.png)

If you then have a look at your Google sheet, you should see the successful submission there as well.

![AEM Forms](./images/aemforms38.png)

You've now successfully finished this exercise.

## Next Steps

Go Back to [Adobe Experience Manager Forms with Edge Delivery Services](./aemforms.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
