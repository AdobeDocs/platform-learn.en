---
title: Getting Started - Postman setup
description: Getting Started - Postman setup
kt: 5342
doc-type: tutorial
---
# Option 2: PostBuster setup

>[!IMPORTANT]
>
>If you're not an Adobe employee, follow the instructions to [install Postman](./ex7.md). The below instructions are only intended for Adobe employees.

## Install PostBuster

Go to [https://adobe.service-now.com/esc?id=adb_esc_kb_article&sysparm_article=KB0020542](https://adobe.service-now.com/esc?id=adb_esc_kb_article&sysparm_article=KB0020542). 

Click to download the latest release of **PostBuster**.

![PostBuster](./images/pb1.png)

Download the correct version for your OS.

![PostBuster](./images/pb2.png)

Once the download has completed and has been installed, open PostBuster. You should then see this. Click **Import**.

![PostBuster](./images/pb3.png)

Download [postbuster.json.zip](./../../../assets/postman/postbuster.json.zip) and extract it on your desktop.

![PostBuster](./images/pbpb.png)

Click **Choose a File**.

![PostBuster](./images/pb4.png)

Select the file **postbuster.json**. Click **Open**.

![PostBuster](./images/pb5.png)

You should then see this. Click **Scan**.

![PostBuster](./images/pb6.png)

Click **Import**.

![PostBuster](./images/pb7.png)

You should then see this. Click to open the imported collection.

![PostBuster](./images/pb8.png)

Now you see your collection. You still need to configure an environment to hold some environment variables.

![PostBuster](./images/pb9.png)

Click **Base Environment** and then click the **edit** icon.

![PostBuster](./images/pb10.png)

You should then see this.

![PostBuster](./images/pb11.png)

Copy the below environment placeholder and paste it in the **Base Environment**.

```json
{
	"CLIENT_SECRET": "",
	"API_KEY": "",
	"ACCESS_TOKEN": "",
	"SCOPES": [
		"openid",
		"AdobeID",
		"read_organizations", 
		"additional_info.projectedProductContext", 
		"session",
		"ff_apis",
		"firefly_api"
	],
	"TECHNICAL_ACCOUNT_ID": "",
	"IMS": "ims-na1.adobelogin.com",
	"IMS_ORG": "",
	"access_token": "",
	"IMS_TOKEN": "",
	"AZURE_STORAGE_URL": "",
	"AZURE_STORAGE_CONTAINER": "",
	"AZURE_STORAGE_SAS_READ": "",
	"AZURE_STORAGE_SAS_WRITE": ""
}
```

You should then have this.

![PostBuster](./images/pb12.png)

## Enter your Adobe I/O variables

Go to [https://developer.adobe.com/console/home](https://developer.adobe.com/console/home){target="_blank"} and open your project.

![Adobe I/O New Integration](./images/iopr.png){zoomable="yes"}

Go to **OAuth Server-to-Server**. 

![Adobe I/O New Integration](./images/iopbvar1.png){zoomable="yes"}

You now need to copy the following values from your Adobe I/O project and paste them in your PostBuster Base Environment.

- Client ID
- Client Secret (Click **Retrieve Client Secret**)
- Technical Account ID
- Organization ID (Scroll down to find your Organization ID)

![Adobe I/O New Integration](./images/iopbvar2.png){zoomable="yes"}

Copy the above variables one by one, and paste them in your **Base Environment** in PostBuster.

| Variable Name in Adobe I/O     | Variable Name in PostBuster Base Environment      | 
|:-------------:| :---------------:| 
| Client ID          | `API_KEY` |
| Client Secret          | `CLIENT_SECRET` |
| Technical Account ID    | `TECHNICAL_ACCOUNT_ID`|
| Organization ID          | `IMS_ORG` |

After having copied these variables on by one, your PostBuster Base Environment should look like this:

![Adobe I/O New Integration](./images/iopbvar3.png){zoomable="yes"}

In the **Adobe IO - OAuth** collection, select the request named **POST - Get Access Token** and select **Send**. 

You should see a similar response containing the following information:

| Key     | Value     | 
|:-------------:| :---------------:| 
| token_type          | **bearer** |
| access_token    | **eyJhbGciOiJS...** | 
| expires_in          | **86399** |

The Adobe I/O **bearer-token** has a specific value (the very long access_token) and an expiration window and is now valid for 24 hours. This means that after 24 hours, if you want to use Postman to interact with Adobe APIs, you will have to generate a new token by running this request again.

![Adobe I/O New Integration](./images/iopbvar4.png){zoomable="yes"}

Your PostBuster environment is now setup and working. You've now completed the Getting Started module.

## Next Steps

Go to [Applications to install](./ex9.md){target="_blank"}

Go back to [Getting Started](./getting-started.md){target="_blank"}

Go back to [All modules](./../../../overview.md){target="_blank"}