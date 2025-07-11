---
title: Working with Photoshop APIs
description: Learn how to work with the Photoshop APIs and Firefly Services
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 60eecc24-1713-4fec-9ffa-a3186db1a8ca
---
# 1.1.3 Working with Photoshop APIs

Learn how to work with the Photoshop APIs and Firefly Services.

## 1.1.3.1 Prerequisites

Before continuing with this exercise, you need to have completed the setup of [your Adobe I/O project](./../../../modules/getting-started/gettingstarted/ex6.md), and you also need to have configured an application to interact with APIs, such as [Postman](./../../../modules/getting-started/gettingstarted/ex7.md) or [PostBuster](./../../../modules/getting-started/gettingstarted/ex8.md).

## 1.1.3.2 Adobe I/O - access_token

In the **Adobe IO - OAuth** collection, select the request named **POST - Get Access Token** and select **Send**. The response should contain a new **accestoken**.

![Postman](./images/ioauthresp.png)

## 1.1.3.3 Programmatically interact with a PSD file

Download [citisignal-fiber.psd](./../../../assets/ff/citisignal-fiber.psd){target="_blank"} to your desktop.

Open **citisignal-fiber.psd** in Photoshop. 

![Azure Storage](./images/ps7.png)

In the **Layers** pane, the designer of the file has given a unique name to each layer. You can see the layer information by opening the PSD file in Photoshop, but you can also do this programmatically.

Let's send your first API request to Photoshop APIs.

### Photoshop API - Hello World

Next, let's say hello to Photoshop APIs to test if all permissions and access is set correctly. 

In the collection **Photoshop**, open the request  **Photoshop Hello (Test Auth.)**. Select **Send**.

![Azure Storage](./images/ps10.png)

You should receive the response **Welcome to the Photoshop API!**.

![Azure Storage](./images/ps11.png)

Next, in order to programmatically interact with the PSD file **citisignal-fiber.psd**, you need to upload it to your storage account. You can do that manually-- by dragging and dropping it into your container using Azure Storage explorer--but this time you should do it through the API.

### Upload PSD to Azure

In Postman, open the request **Upload PSD to Azure Storage Account**. In the previous exercise, you configured these environment variables in Postman, which you'll use now:

- `AZURE_STORAGE_URL`
- `AZURE_STORAGE_CONTAINER`
- `AZURE_STORAGE_SAS_READ`
- `AZURE_STORAGE_SAS_WRITE`

As you can see in the request **Upload PSD to Azure Storage Account**, the URL is configured to use these variables.

![Azure Storage](./images/ps12.png)

In **Body**, select the file **citisignal-fiber.psd**. 

![Azure Storage](./images/ps13.png)

Your screen should look like this. Select **Send**.

![Azure Storage](./images/ps14.png)

You should get this empty response back from Azure, which means that your file is stored in your container in your Azure Storage account.

![Azure Storage](./images/ps15.png)

If you use Azure Storage Explorer to look at your file, be sure to refresh your folder.

![Azure Storage](./images/ps16.png)

### Photoshop API - Get manifest

Next, you need to get the manifest file of your PSD file. 

In Postman, open the request **Photoshop - Get PSD Manifest**. Go to **Body**.

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

Select **Send**.

In the response, you now see a link. As operations in Photoshop can sometimes take some time to complete, Photoshop provides a status file as a response to most incoming requests. To understand what is happening with your request, you need to read the status file.

![Azure Storage](./images/ps17.png)

To read the status file, open the request **Photoshop -  Get PS Status**. You can see that this request is using a variable as a URL, which is a variable that is set by the previous request that you sent, **Photoshop - Get PSD Manifest**. Variables are set in the **Scripts** of each request. Select **Send**.

![Azure Storage](./images/ps18.png)

Your screen should look like this. Currently, the status is set to **pending**, which means that the process hasn't completed yet. 

![Azure Storage](./images/ps19.png)

Select send a couple more times on **Photoshop -  Get PS Status**, until the status changes to **succeeded**. This may take a couple of minutes.

When the response is available, you can see the json file contains information on all the layers of the PSD file. This is useful information, as things like the layer name or layer ID can be identified.

![Azure Storage](./images/ps20.png)

As an example, search for the text `2048x2048-cta`. Your screen should look like this:

![Azure Storage](./images/ps21.png)


### Photoshop API - SmartObject Replace

Next, you need to change the background of the file citisignal-fiber.psd by using the image that you generated using Firefly in one of the previous exercises. 

In Postman, open the request **Photoshop - SmartObject Replace** and go to **Body**.

Your screen should look like this:

- first, an input file is specified: `citisignal-fiber.psd`
- second, the layer to change is specified, with the new background file to use
- third, an output file is specified: `citisignal-fiber-replacedbg.psd`

```json
  {
    "inputs": [
        {
            "storage": "azure",
            "href": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/citisignal-fiber.psd{{AZURE_STORAGE_SAS_READ}}"
        }
    ],
    "options": {
        "layers": [
            {
                "name": "2048x2048-image",
                "input": {
                    "href": "{{FIREFLY_COMPLETED_ASSET_URL}}",
                    "storage": "external"
                }
            }
        ]
    },
    "outputs": [
        {
            "storage": "azure",
            "href": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/citisignal-fiber-replacedbg.psd{{AZURE_STORAGE_SAS_WRITE}}",
            "type": "vnd.adobe.photoshop",
            "overwrite": true
        }
    ]
}
```

The output file has a different name, because you don't want to override the original input file.

Select **Send**.

![Azure Storage](./images/psbg23.png)

Just like before, the response contains a link that points to the status file that keeps track of the progress.

![Azure Storage](./images/psbg22.png)

To read the status file, open the request **Photoshop -  Get PS Status** and select **Send**. If the status isn't set to **succeeded** immediately, wait a couple of seconds and then select **Send** again.

Select the URL to download the output file.

![Azure Storage](./images/psbg24.png)

Open **citisignal-fiber-replacedbg.psd** after downloading the file to your computer. You should see that the background image has changed to a similar image like below:

![Azure Storage](./images/psbg25.png)

You can also see this file in your container using Azure Storage explorer.

![Azure Storage](./images/psbg26.png)

### Photoshop API - Change Text 

Next, you need to change the text for the call to action using the APIs. 

In Postman, open the request **Photoshop - Change Text** and go to **Body**.

Your screen should look like this:

- first, an input file is specified: `citisignal-fiber-replacedbg.psd`, which is the file that was generated in the previous step when you changed the background image
- second, the layer to change is specified, with the text to change to
- third, an output file is specified: `citisignal-fiber-changed-text.psd`

```json
  {
  "inputs": [
    {
      "storage": "external",
      "href": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/citisignal-fiber-replacedbg.psd{{AZURE_STORAGE_SAS_READ}}"
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

The output file has a different name, because you don't want to override the original input file.

Select **Send**.

![Azure Storage](./images/ps23.png)

Just like before, the response contains a link that points to the status file that keeps track of the progress.

![Azure Storage](./images/ps22.png)

To read the status file, open the request **Photoshop -  Get PS Status** and select **Send**. If the status isn't set to **succeeded** immediately, wait a couple of seconds and then select **Send** again.

Select the URL to download the output file.

![Azure Storage](./images/ps24.png)

Open **citisignal-fiber-changed-text.psd** after downloading the file to your computer. You should see the placeholder for the call to action has been replaced by the text **Get Fiber now!**.

![Azure Storage](./images/ps25.png)

You can also see this file in your container using Azure Storage explorer.

![Azure Storage](./images/ps26.png)

## Next Steps

Go to [Firefly Custom Models API](./ex4.md){target="_blank"}

Go back to [Overview of Adobe Firefly Services](./firefly-services.md){target="_blank"}

Go back to [All Modules](./../../../overview.md){target="_blank"}