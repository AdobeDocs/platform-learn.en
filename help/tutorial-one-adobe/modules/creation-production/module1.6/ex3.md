---
title: Create your external DAM app
description: Create your external DAM app
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 6823e8a0-dde7-460a-a48a-6787e65e4104
---
# 1.6.3 Create your external DAM app

## 1.6.3.1 Download sample app files

Go to [https://github.com/adobe/genstudio-extensibility-examples](https://github.com/adobe/genstudio-extensibility-examples). Click **Code** and then select **Download ZIP**.

![Ext DAM](./images/extdam1.png)

Unpack the zip-file onto your desktop.

![Ext DAM](./images/extdam2.png)

Open the folder **genstudio-extensibility-examples-main**. You'll see multiple sample apps. The one that is of interest for this exercise is the **genstudio-external-dam-app**.

Copy that directory and paste it onto your desktop.

![Ext DAM](./images/extdam4.png)

You should now have this on your desktop:

![Ext DAM](./images/extdam3.png)

For the next exercises, you will only use the **genstudio-external-dam-app** folder.

## 1.6.3.2 Configure the Adobe Developer command-line interface

Right-click the **genstudio-external-dam-app** folder and select **New Terminal at Folder**.

![Ext DAM](./images/extdam5.png)

You should then see this. Enter the command `aio login`. This command will redirect to your browser and will expect you to login.

![Ext DAM](./images/extdam6.png)

After successful login, you should see this in the browser.

![Ext DAM](./images/extdam7.png)

The browser will then redirect back to the terminal window. You should see a message that says **Login successful** and a long token that is returned by the browser.

![Ext DAM](./images/extdam8.png)

The next step is to configure the instance and Adobe IO project that you will use for the external DAM app.

To do this, you need to download a file from the Adobe IO project that you configured before.

Go to [https://developer.adobe.com/console/home](https://developer.adobe.com/console/home){target="_blank"} and open the project you created before, which is named `--aepUserLdap-- GSPeM EXT`. Open the **Production** workspace.

![Ext DAM](./images/extdam9.png)

Click **Download all**. This will download a JSON file.

![Ext DAM](./images/extdam10.png)

Copy the JSON file from your **Downloads** directory into the root directory of the external DAM app.

![Ext DAM](./images/extdam11.png)

Go back to your terminal window. Enter the command `aio app use XXX-YYY-Production.json`.

>[!NOTE]
>
>You need to change the name of the file to match the name of your file.

Once the command has run, your external DAM app will now be connected to the Adobe IO project with App Builder that you created before.

![Ext DAM](./images/extdam12.png)

## 1.6.3.3 Install the GenStudio Extensibility SDK

Next, you need to install the **GenStudio Extensibility SDK**. You can find more detail about the SDK here: [https://github.com/adobe/genstudio-extensibility-sdk](https://github.com/adobe/genstudio-extensibility-sdk).

To install the SDK, run this command in your terminal window:

`npm install @adobe/genstudio-extensibility-sdk`

![Ext DAM](./images/extdam13.png)

After a couple of minutes, the SDK will be installed.

![Ext DAM](./images/extdam14.png)

## 1.6.3.4 Review the external DAM app in Visual Studio Code

Open Visual Studio Code. Click **Open...** to open a folder.

![Ext DAM](./images/extdam15.png)

Select the folder **genstudio-external-dam-app** which contains the app you downloaded before.

![Ext DAM](./images/extdam16.png)

Click to open the file **.env**.

![Ext DAM](./images/extdam17.png)

The **.env** file was created by the command `aio app use` that you ran in the previous step and contains the information needed to connect to your Adobe IO project with App Builder.

![Ext DAM](./images/extdam18.png)

You now need to create 2 new files at the root of your folder: 

- `.env.dev`. Click the **New File** button and then enter the filename `.env.dev`.

![Ext DAM](./images/extdam19.png)

- `.env.prod`.  Click the **New File** button and then enter the filename `.env.prod`.

![Ext DAM](./images/extdam20.png)

These files will contain the credentials needed to connect to the AWS S3 bucket that you created before.

```
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_REGION=
AWS_BUCKET_NAME=
```

The field **AWS_ACCESS_KEY_ID** and **AWS_SECRET_ACCESS_KEY** were available after creating the IAM user in the previous exercise. You were asked to write them down, you can now copy the values.

![ETL](./images/cred1.png)

The field **AWS_REGION** can be taken from the AWS S3 Home view, next to your bucket name. In this example, the region is **us-west-2**.

![ETL](./images/bucket2.png)

The field **AWS_BUCKET_NAME** should be `--aepUserLdap---gspem-dam`.

This information allows you to update the values of each of these variables.

```
AWS_ACCESS_KEY_ID=XXX
AWS_SECRET_ACCESS_KEY=YYY
AWS_REGION=us-west-2
AWS_BUCKET_NAME=--aepUserLdap---gspem-dam
```

You should now paste this text in both files, `.env.dev` and `.env.prod`. Don't forget to save your changes.

![Ext DAM](./images/extdam21.png)


![Ext DAM](./images/extdam22.png)

Next, go back to your terminal window. Run this command:

`export $(grep -v '^#' .env.dev | xargs)`

![Ext DAM](./images/extdam23.png)

## 1.6.3.5 Run your external DAM app

In your terminal window, run the command `aio app run`. You should then see this after 1-2 minutes.

![Ext DAM](./images/extdam24.png)

## Next Steps

Go to [Deploy your code and publish your app privately](./ex4.md){target="_blank"}

Go back to [GenStudio for Performance Marketing - Extensibility](./genstudioext.md){target="_blank"}

Go back to [All Modules](./../../../overview.md){target="_blank"}
