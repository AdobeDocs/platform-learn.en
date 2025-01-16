---
title: Working with Photoshop APIs
description: Working with Photoshop APIs
kt: 5342
doc-type: tutorial
---
# 1.1.3 Working with Photoshop APIs

## 1.1.3.1 Update your Adobe I/O integration

Go to [https://developer.adobe.com/console/home](https://developer.adobe.com/console/home).

![Adobe I/O New Integration](./images/iohome.png)

Go to **Projects** and click to open the project you created in the previous exercise, which is called `--aepUserLdap-- Firefly`.

![Azure Storage](./images/ps1.png)

Click **+ Add to Project** and then click **API**.

![Azure Storage](./images/ps2.png)

Select **Creative Cloud** and click **Photoshop - Firefly Services**. Click **Next**.

![Azure Storage](./images/ps3.png)

Click **Next**.

![Azure Storage](./images/ps4.png)

Next, you need to select a product profile that will define what permissions are available to this integration.

Select the profile **Default Firefly Services Configuration** and **Default Creative Cloud Automation Services configuration**.

Click **Save Configured API**.

![Azure Storage](./images/ps5.png)

Your Adobe I/O project is now updated to work with Photoshop & Firefly Services APIs.

![Azure Storage](./images/ps6.png)

## 1.1.3.2 Programmatically interact with a PSD file

Download the file Go to [citisignal-fiber.psd](./../../../assets/ff/citisignal-fiber.psd) to your desktop.

Open the file **citisignal-fiber.psd** in Photoshop. You should then have this.

![Azure Storage](./images/ps7.png)

In the **Layers** pane, you'll see that the designer of the file has given a unique name to each layer. You can see the layer information by opening the PSD file in Photoshop, but you can also do that programmatically.

Let's send your first API request to Photoshop APIs.

Go to Postman. Before sending API requests to Photoshop, you need to authenticate to Adobe I/O. OPen the request that you used before with the name **POST - Get Access Token**.

Go to **Params** and verify that the parameter **Scope** is properly set. The **Value** for **Scope** should look like this: 

`openid,session,AdobeID,read_organizations,additional_info.projectedProductContext, ff_apis, firefly_api`

Then, click **Send**.

![Azure Storage](./images/ps8.png)

You then have a valid access token to interact with Photoshop APIs.

![Azure Storage](./images/ps9.png)

### 1.1.3.2.1 Photoshop API - Hello World

Next, let's say hello to Photoshop APIs to test if all permissions and access is set correctly. In the collection **Photoshop**, open the request with the name **Photoshop Hello (Test Auth.)**. Click **Send**.

![Azure Storage](./images/ps10.png)

You should then receive this response: **Welcome to the Photoshop API!**.

![Azure Storage](./images/ps11.png)

Next, in order to programmatically interact with the PSD file **citisignal-fiber.psd**, you need to upload it to your storage account. You could do that manually, by dragging and dropping it into your container using Azure Storage explorer, but this time, you should do it through the API.

### 1.1.3.2.2 Upload PSD to Azure

In Postman, open the request **Upload PSD to Azure Storage Account**. In the previous exercise, you configured these environment variables in Postman, which you'll now use:

- `AZURE_STORAGE_URL`
- `AZURE_STORAGE_CONTAINER`
- `AZURE_STORAGE_SAS_READ`
- `AZURE_STORAGE_SAS_WRITE`

As you can see in the request **Upload PSD to Azure Storage Account**, the URL is configured to use these variables.

![Azure Storage](./images/ps12.png)

In **Body**, you should now add select the file **citisignal-fiber.psd**. 

![Azure Storage](./images/ps13.png)

You should then have this. Click **Send**.

![Azure Storage](./images/ps14.png)

You should then get this empty response back from Azure, which means that your file is stored in your container in your Azure Storage account.

![Azure Storage](./images/ps15.png)

If you use Azure Storage Explorer to have a look, you'll see your file after refreshing your folder.

![Azure Storage](./images/ps16.png)

### 1.1.3.2.3 Photoshop API - Get Manifest

Next, you need to get the manifest file of your PSD file. In Postman, open the request **Photoshop - Get PSD Manifest**. Go to **Body**.

The body should look like this:

```json
{
  "inputs": [
    {
      "storage": "external",
      "href": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/citisignal-fiber.psd{{AZURE_STORAGE_SAS_READ}}"
    }
  ],
  "options": {
    "thumbnails": {
      "type": "image/jpeg"
    }
  }
}
```

Click **Send**.

In the response, you now see a link. As operations in Photoshop can sometimes take some time to complete, Photoshop will provide a status file as a response to most incoming requests. To understand what is happening with your request, you need to read the status file.

![Azure Storage](./images/ps17.png)

To read the status file, open the request **Photoshop -  Get PS Status**. You then see that this request is using a variable as a URL, which is a variable that is set by the previous request that you sent, **Photoshop - Get PSD Manifest**. Variables are set in the **Scripts** of each request.

Click **Send**.

![Azure Storage](./images/ps18.png)

You should then see this. Currently, the status is set to **pending**, which means that the process hasn't completed yet. 

![Azure Storage](./images/ps19.png)

You can click send a couple more times on the **Photoshop -  Get PS Status** request, until the status changes to **succeeded**. This may take a couple of minutes.

When the response is available, you'll the a json file that contains information on all the layers of the PSD file. This is useful information, as things like the layer name or layer ID can be seen in here.

![Azure Storage](./images/ps20.png)

As an example, search for the text `2048x2048-cta`. You should then see this.

![Azure Storage](./images/ps21.png)

### 1.1.3.2.4 Photoshop API - Change Text 

Next, you now need to change the text for the call to action using the APIs. In Postman, open the request **Photoshop - Change Text** and go to **Body**.

You should then see this. You can see that:

- first, an input file is specified: `citisignal-fiber.psd`
- second, the layer to change is specified, with the text to change to
- third, an output file is specified: `citisignal-fiber-changed-text.psd`

```json
{
  "inputs": [
    {
      "storage": "external",
      "href": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/citisignal-fiber.psd{{AZURE_STORAGE_SAS_READ}}"
    }
  ],
  "options": {
    "layers": [
      {
        "name": "2048x2048-cta",
        "text": {
          "content": "Get Fiber now!"
        }
      }
    ]
  },
  "outputs": [
    {
      "storage": "azure",
      "href": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/citisignal-fiber-changed-text.psd{{AZURE_STORAGE_SAS_WRITE}}",
      "type": "vnd.adobe.photoshop",
      "overwrite": true
    }
  ]
}
```

The output file has a different name, as you don't want to override the original input file.

Click **Send**.

![Azure Storage](./images/ps23.png)

Just like before, the response contains a link that points to the status file that keeps track of the progress.

![Azure Storage](./images/ps22.png)

To read the status file, open the request **Photoshop -  Get PS Status** again and click **Send**. If the status isn't set to **succeeded** immediately, wait a couple of seconds and then click **Send** again.

Once the status is set to **succeeded**, you should then see this. In the path `outputs[0]._links.renditions[0].href`, you should see the URL of output file that was created by Photoshop and which contains the changed text.

Click the URL to download the output file.

![Azure Storage](./images/ps24.png)

The file **citisignal-fiber-changed-text.psd** will then be downloaded to your computer, after which you can open it. You should then see that the placeholder for the call to action has been replaced by the text **Get Fiber now!**.

![Azure Storage](./images/ps25.png)

Lastly, you then also see that file in your container using Azure Storage explorer.

![Azure Storage](./images/ps26.png)

You've now completed this exercise. 

Next Step: [Summary & Benefits](./summary.md)

[Go Back to Module 1.1](./firefly-services.md)

[Go Back to All Modules](./../../../overview.md)
