---
title: Optimize your Firefly Process using Microsoft Azure and Presigned URLs
description: Learn how to optimize your Firefly process using Microsoft Azure and presigned URLs
role: Developer
level: Beginner
jira: KT-5342
doc-type: tutorial
exl-id: 5f9803a4-135c-4470-bfbb-a298ab1fee33
---
# 1.1.2 Optimize your Firefly process using Microsoft Azure and presigned URLs

Learn how to optimize your Firefly process using Microsoft Azure and pre-signed URLs.

## 1.1.2.1 What are pre-signed URLs?

A presigned URL is a URL that grants you temporary access to a specific object in a storage location. Using the URL, a user can for instance either READ the object or WRITE an object (or update an existing object). The URL contains specific parameters which are set by your application. 

In the context of creating content supply chain automation, there often are multiple file operations that need to happen for a specific use case. As an example, the background of a file may need to be changed, the text of various layers may have to be changed, etc. It isn't always possible to do all the file operations at the same time which creates the need for a multi-step approach. After every intermediate step, the output then is a temporary file that is needed for the next step to be executed. Once that next step is executed, the temporary file quickly loses value and is often no longer needed so it should be deleted.

Adobe Firefly Services currently supports these domains:

- Amazon AWS: *.amazonaws.com
- Microsoft Azure: *.windows.net
- Dropbox: *.dropboxusercontent.com

The reason why often cloud storage solutions are used, is that the intermediate assets that are being created lose value quickly. The problem that is solved by pre-signed URLs is often best solved with a commodity storage solution, which is typically one of the above cloud services.

Within the Adobe ecosystem there also are storage solutions, such as Frame.io, Workfront Fusion and Adobe Experience Manager assets. These solutions also suppport pre-signed URLs so it often becomes a choice that needs to be made during the implementation. The choice is then often based on a combination of already available applications, and storage cost.

As such, pre-signed URLs are used in combination with Adobe Firefly Services operations because:

- organizations often need to process multiple changes to the same image in intermediate steps, and intermediate storage is needed to make that possible.
- access to reading and writing from cloud storage locations should be secure and in a server-side environment, it's not possible to manually log in so security needs to be baked into the URL directly.

A pre-signed URL uses three parameters to limit the access to the user:

- Storage location: this could be an AWS S3 bucket location, a Microsoft Azure storage account location with container
- Filename: the specific file that needs to be read, updated, deleted.
- Query string parameter: a query string parameter always starts with a question mark and is followed by a complex series of paramaters

Example:

- **Amazon AWS**: `https://bucket.s3.eu-west-2.amazonaws.com/image.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AXXXXXXXXXX%2Feu-west-2%2Fs3%2Faws4_request&X-Amz-Date=20250510T171315Z&X-Amz-Expires=1800&X-Amz-Signature=XXXXXXXXX&X-Amz-SignedHeaders=host`
- **Microsoft Azure**: `https://storageaccount.blob.core.windows.net/container/image.png?sv=2023-01-03&st=2025-01-13T07%3A16%3A52Z&se=2026-01-14T07%3A16%3A00Z&sr=b&sp=r&sig=XXXXXX%3D`

## 1.1.2.2 Create an Azure Subscription

>[!NOTE]
>
>If you already have an existing Azure Subscription, you can skip this step. Please proceed with the next exercise in that case.

>[!NOTE]
>
>If you're following this tutorial as part of an in-person guided workshop or a guided on-demand training, you likely already have access to a Microsoft Azure Storage Account. In that case, you don't need to create your own account - please use the account that has been provided to you as part of the training.

Go to [https://portal.azure.com](https://portal.azure.com){target="_blank"} and login with your Azure account. If you don't have one, please use your personal email address to create your Azure account.

![Azure Storage](./images/02azureportalemail.png){zoomable="yes"}

After successful login you should see the following screen:

![Azure Storage](./images/03azureloggedin.png){zoomable="yes"}

On the left menu select **All Resources**, the Azure subscription screen appears if you are not yet subscribed. 

If you are not subscribed, select **Start with an Azure free Trial**. 

![Azure Storage](./images/04azurestartsubscribe.png){zoomable="yes"}

Fill in the Azure subscription form and provide your mobile phone and credit card for activation (you will have a free tier for 30 days and you will not be charged, unless you upgrade).

When the subscription process is finished you are good to go.

![Azure Storage](./images/06azuresubscriptionok.png){zoomable="yes"}

## 1.1.2.3 Create Azure Storage Account

Search for `storage account` and then select **Storage accounts**.

![Azure Storage](./images/azs1.png){zoomable="yes"}

Select **+ Create**.

![Azure Storage](./images/azs2.png){zoomable="yes"}

Select your **Subscription** and select (or create) a **Resource group**.

Under **Storage account name** use `--aepUserLdap--`.

Select **Review + create**.

![Azure Storage](./images/azs3.png){zoomable="yes"}

Select **Create**.

![Azure Storage](./images/azs4.png){zoomable="yes"}

After confirmation select **Go to resource**.

![Azure Storage](./images/azs5.png){zoomable="yes"}

Your Azure Storage Account is now ready to be used.

![Azure Storage](./images/azs6.png){zoomable="yes"}

Select **Data Storage**, and then go to **Containers**. Select **+ Container**.

![Azure Storage](./images/azs7.png){zoomable="yes"}

Use `--aepUserLdap--` for the name and select **Create**.

![Azure Storage](./images/azs8.png){zoomable="yes"}

Your container is now ready to be used.

![Azure Storage](./images/azs9.png){zoomable="yes"}

## 1.1.2.4 Install Azure Storage Explorer

[Download Microsoft Azure Storage Explorer to manage your files](https://azure.microsoft.com/en-us/products/storage/storage-explorer#Download-4){target="_blank"}. Select the correct version for your specific OS, download and install it.

![Azure Storage](./images/az10.png){zoomable="yes"}

Open the application and select **Sign in with Azure**.

![Azure Storage](./images/az11.png){zoomable="yes"}

Select **Subscription**.

![Azure Storage](./images/az12.png){zoomable="yes"}

Select **Azure** and then **Next**.

![Azure Storage](./images/az13.png){zoomable="yes"}

Select your Microsoft Azure account and complete the authentication process.

![Azure Storage](./images/az14.png){zoomable="yes"}

After authentication, this message appears.

![Azure Storage](./images/az15.png){zoomable="yes"}

Back in the Microsoft Azure Storage Explorer app, select your subscription and choose **Open Explorer**.

>[!NOTE]
>
>If your account isn't shown, click the **gear** icon next to your email address and select **Un-filter**.

![Azure Storage](./images/az16.png){zoomable="yes"}

Your storage account appears under **Storage Accounts**.

![Azure Storage](./images/az17.png){zoomable="yes"}

Open **Blob Containers** and then select the container you created in the previous exercise.

![Azure Storage](./images/az18.png){zoomable="yes"}

## 1.1.2.5 Manual file upload and using an image file as style reference

Upload a image file of your choice or [this file](./images/gradient.jpg){target="_blank"} into the container.

![Azure Storage](./images/gradient.jpg)

Once uploaded, you can see it in your container:

![Azure Storage](./images/az19.png){zoomable="yes"}

Right-click on `gradient.jpg` and then select **Get Shared Access Signature**.

![Azure Storage](./images/az20.png){zoomable="yes"}

Under **Permissions**, only **Read** is required. Select **Create**.

![Azure Storage](./images/az21.png){zoomable="yes"}

Copy your presigned URL for this image file for the next API request to Firefly.

![Azure Storage](./images/az22.png){zoomable="yes"}

Back in Postman open the request **POST - Firefly - T2I (styleref) V3**. 
This appears in **Body**.    

![Azure Storage](./images/az23.png){zoomable="yes"}

Replace the placeholder URL with the presigned URL for your image file and select **Send**.

![Azure Storage](./images/az24.png){zoomable="yes"}

Open the response Firefly Services new image in your browser.

![Azure Storage](./images/az25.png){zoomable="yes"}

Another image appears with `horses in a field`, but this time the style is similar to the image file that you provided as style reference.

![Azure Storage](./images/az26.png){zoomable="yes"}

## 1.1.2.6 Programmatic file upload 

In order to use programmatic file upload with Azure Storage Accounts, you need to create a new **Shared Access Signature (SAS)** token with permissions that allow you to write a file.

In Azure Storage Explorer, right-click your container, and select **Get Shared Access Signature**.

![Azure Storage](./images/az27.png){zoomable="yes"}

Under **Permissions**, select the following required permissions:

- **Read**
- **Add**
- **Create**
- **Write**
- **List**

Select **Create**.

![Azure Storage](./images/az28.png){zoomable="yes"}

After receiving your **Shared Access Signature**, select **Copy** to copy the URL.

![Azure Storage](./images/az29.png){zoomable="yes"}

Use the **SAS-token** to upload a file into your Azure Storage Account. 

Back in Postman, select the folder **FF - Firefly Services Tech Insiders**, then select **...** on the **Firefly** folder, and then select **Add request**.

![Azure Storage](./images/az30.png){zoomable="yes"}

Change the name of the empty request to **Upload file to Azure Storage Account**, change the **Request Type** to **PUT** and paste the SAS-token URL in the URL section, then select **Body**.

![Azure Storage](./images/az31.png){zoomable="yes"}

Next, select a file from your local machine or use another image file located [here](./images/gradient2-p.jpg){target="_blank"}.

![Gradient file](./images/gradient2-p.jpg)

In **Body**, select **binary** then **Select file**, then select **+ New file from local machine**.

![Azure Storage](./images/az32.png){zoomable="yes"}

Select your file of choice and select **Open**.  

![Azure Storage](./images/az33.png){zoomable="yes"}

Next specify the file name to be used in your Azure Storage Account by placing your cursor in front of the question mark **?** in the URL like this:

![Azure Storage](./images/az34.png){zoomable="yes"}

The URL currently looks like this, but needs to be changed. 

`https://vangeluw.blob.core.windows.net/vangeluw?sv=2023-01-03...`

Change the file name to `gradient2-p.jpg`, and change the URL to include the filename like this:

`https://vangeluw.blob.core.windows.net/vangeluw/gradient2-p.jpg?sv=2023-01-03...`

![Azure Storage](./images/az34a.png){zoomable="yes"}

Next, go to **Headers** to add a new header manually like this:

| Key     | Value     | 
|:-------------:| :---------------:| 
| `x-ms-blob-type`          | `BlockBlob` |


![Azure Storage](./images/az35.png){zoomable="yes"}

Go to **Authorization** and set the **Auth Type** to **No Auth**, and select **Send**.

![Azure Storage](./images/az36.png){zoomable="yes"}

Next, this empty response appears in Postman, which means that your file upload is fine.

![Azure Storage](./images/az37.png){zoomable="yes"}

Back in Azure Storage Explorer refresh the content of your folder, and the newly uploaded file appears.

![Azure Storage](./images/az38.png){zoomable="yes"}

## 1.1.2.7 Programmatic file usage

To programmatically read files from Azure Storage Accounts in the long term, you need to create a new **Shared Access Signature (SAS)** token, with permissions that allow you to read a file. Technically you could use the SAS-token created in the previous exercise, but it's best practice to have a separate token with only **Read** permissions and separate token with only **Write** permissions.

### Long-term Read SAS token

Go back to Azure Storage Explorer, right-click your container and then select **Get Shared Access Signature**.

![Azure Storage](./images/az27.png){zoomable="yes"}

Under **Permissions**, select the following required permissions:

- **Read**
- **List**

Set **Expiry Time** to 1 year from now.

Select **Create**.

![Azure Storage](./images/az100.png){zoomable="yes"}

Copy the URL and write it down in a file on your computer to get your long-term SAS-token with Read permissions. 

![Azure Storage](./images/az101.png){zoomable="yes"}

Your URL should look like this:

`https://vangeluw.blob.core.windows.net/vangeluw?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`

You can derive a couple of values out of the above URL:

- `AZURE_STORAGE_URL`: `https://vangeluw.blob.core.windows.net`
- `AZURE_STORAGE_CONTAINER`: `vangeluw`
- `AZURE_STORAGE_SAS_READ`: `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`

### Long-term Write SAS token

Go back to Azure Storage Explorer, right-click your container and select **Get Shared Access Signature**.

![Azure Storage](./images/az27.png){zoomable="yes"}

Under **Permissions**, select the following required permissions:

- **Read**
- **List**
- **Add**
- **Create**
- **Write**

Set the **Expiry Time** to 1 year from now.

Select **Create**.

![Azure Storage](./images/az102.png){zoomable="yes"}

Copy the URL and write it down in a file on your computer to get your long-term SAS-token with Read permissions.

![Azure Storage](./images/az103.png){zoomable="yes"}

Your URL should look like this:

`https://vangeluw.blob.core.windows.net/vangeluw?sv=2023-01-03&st=2025-01-13T07%3A38%3A59Z&se=2026-01-14T07%3A38%3A00Z&sr=c&sp=acw&sig=lR9%2FMUfyYLcBK7W9Kv7YJdYz5HEEEovExAdOCOCUdMk%3D`

You can derive a couple of values out of the above URL:

- `AZURE_STORAGE_URL`: `https://vangeluw.blob.core.windows.net`
- `AZURE_STORAGE_CONTAINER`: `vangeluw`
- `AZURE_STORAGE_SAS_READ`: `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`
- `AZURE_STORAGE_SAS_WRITE`: `?sv=2023-01-03&st=2025-01-13T07%3A38%3A59Z&se=2026-01-14T07%3A38%3A00Z&sr=c&sp=acw&sig=lR9%2FMUfyYLcBK7W9Kv7YJdYz5HEEEovExAdOCOCUdMk%3D`

### Variables in Postman

As you can see in the above section, there are some common variables in both the Read and the Write token.

Next you need to create variables in Postman that store the various elements of the above SAS-tokens. There are some values that are the same in both URLs:

- `AZURE_STORAGE_URL`: `https://vangeluw.blob.core.windows.net`
- `AZURE_STORAGE_CONTAINER`: `vangeluw`
- `AZURE_STORAGE_SAS_READ`: `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`
- `AZURE_STORAGE_SAS_WRITE`: `?sv=2023-01-03&st=2025-01-13T07%3A38%3A59Z&se=2026-01-14T07%3A38%3A00Z&sr=c&sp=acw&sig=lR9%2FMUfyYLcBK7W9Kv7YJdYz5HEEEovExAdOCOCUdMk%3D`

For future API interactions, the main thing that changes is the asset name, while the above variables remain the same. In that case, it makes sense to create variables in Postman so that you don't need to specify them manually every time.

In Postman, select **Environments**, open **All variables** and select **Environment**.

![Azure Storage](./images/az104.png){zoomable="yes"}

Create these 4 variables in the table that is shown and for the columns **Initial value** and **Current value**, enter your specific personal values.

- `AZURE_STORAGE_URL`: your url
- `AZURE_STORAGE_CONTAINER`: your container name
- `AZURE_STORAGE_SAS_READ`: your SAS Read token
- `AZURE_STORAGE_SAS_WRITE`: your SAS Write token

Select **Save**.

![Azure Storage](./images/az105.png){zoomable="yes"}

### Variables in PostBuster

As you can see in the above section, there are some common variables in both the Read and the Write token.

Next you need to create variables in PostBuster that store the various elements of the above SAS-tokens. There are some values that are the same in both URLs:

- `AZURE_STORAGE_URL`: `https://vangeluw.blob.core.windows.net`
- `AZURE_STORAGE_CONTAINER`: `vangeluw`
- `AZURE_STORAGE_SAS_READ`: `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`
- `AZURE_STORAGE_SAS_WRITE`: `?sv=2023-01-03&st=2025-01-13T07%3A38%3A59Z&se=2026-01-14T07%3A38%3A00Z&sr=c&sp=acw&sig=lR9%2FMUfyYLcBK7W9Kv7YJdYz5HEEEovExAdOCOCUdMk%3D`

Open PostBuster. Select **Base Environment** and then click the **edit** icon to open the Base Environment.

![Azure Storage](./images/pbbe1.png)

You'll then see 4 empty variables. Enter your Azure Storage Account details here.

![Azure Storage](./images/pbbe2.png)

Your Base Environment file should now look like this. Click **Close**.

![Azure Storage](./images/pbbe3.png)

### Test your configuration

In one of the previous exercises, the **Body** of your the request **Firefly - T2I (styleref) V3** looked like this:

`"url": "https://vangeluw.blob.core.windows.net/vangeluw/gradient.jpg?sv=2023-01-03&st=2025-01-13T07%3A16%3A52Z&se=2026-01-14T07%3A16%3A00Z&sr=b&sp=r&sig=x4B1XZuAx%2F6yUfhb28hF0wppCOMeH7Ip2iBjNK5A%2BFw%3D"`

![Azure Storage](./images/az24.png){zoomable="yes"}

Change the URL to:

`"url": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/gradient.jpg{{AZURE_STORAGE_SAS_READ}}"`

Select **Send** to test the changes you made.

![Azure Storage](./images/az106.png){zoomable="yes"}

If the variables were configured correctly, an image URL is returned.

![Azure Storage](./images/az107.png){zoomable="yes"}

Open the image URL to verify your image.

![Azure Storage](./images/az108.jpg)

## Next Steps

Go to [Working with Photoshop APIs](./ex3.md){target="_blank"}

Go back to [Overview of Adobe Firefly Services](./firefly-services.md){target="_blank"}

Go back to [All Modules](./../../../overview.md){target="_blank"}