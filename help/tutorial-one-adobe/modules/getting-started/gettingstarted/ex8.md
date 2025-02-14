---
title: Getting Started - Postman setup
description: Getting Started - Postman setup
kt: 5342
doc-type: tutorial
---
# Option 2: PostBuster setup

>[!IMPORTANT]
>
>If you're not an Adobe employee, follow the instructions to [install Postman](./ex7.md)!

## Install PostBuster

Go to [https://adobe.service-now.com/esc?id=adb_esc_kb_article&sysparm_article=KB0020542](https://adobe.service-now.com/esc?id=adb_esc_kb_article&sysparm_article=KB0020542). 

Click to download the latest release of **PostBuster**.

![PostBuster](./images/pb1.png)

Download the correct version for your OS.

![PostBuster](./images/pb2.png)

Once the download has completed and has been installed, open PostBuster. You should then see this. Click **Import**.

![PostBuster](./images/pb3.png)

Download [postbuster.json.zip](./assets/postman/postbuster.json.zip) and extract it on your desktop.

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



Your PostBuster environment is now setup and working. You've now completed the Getting Started module.

## Next Steps

Go to [Applications to install](./ex9.md){target="_blank"}

Go back to [Getting Started](./getting-started.md){target="_blank"}

Go back to [All modules](./../../../overview.md){target="_blank"}