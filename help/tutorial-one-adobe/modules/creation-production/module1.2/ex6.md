---
title: Frame I/O and Workfront Fusion
description: Frame I/O and Workfront Fusion
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: f02ecbe4-f1d7-4907-9bbc-04e037546091
---
# 1.2.6 Frame I/O to Workfront Fusion to AEM Assets

>[!IMPORTANT]
>
>In order to complete this exercise, you need to have access to a working AEM Assets CS Author environment. If you follow exercise [Adobe Experience Manager Cloud Service & Edge Delivery Services](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"} you wil have access to such an environment.

>[!IMPORTANT]
>
>If you have previously configured an AEM Assets CS Program with an Author environment, it may be that your AEM CS sandbox was hibernated. Given that dehibernating such a sandbox takes 10-15 minutes, it would be a good idea to start the dehibernation process now so that you don't get stuck at a later time.

In the previous exercise you configured a scenario that automatically generates variations of an Adobe Photoshop PSD file using Adobe Firefly, Photoshop APIs and Workfront Fusion. The output of that scenario was a new Photoshop PSD file. 

The business teams however don't need a PSD file, they need a PNG file or a JPG file. In this exercise, you'll configure a new automation that will result in a PNG file being generated once the asset in Frame I/O is approved, and that PNG file will be stored in AEM Assets automatically.

## 1.2.6.1 Create a new scenario

Go to [https://experience.adobe.com/](https://experience.adobe.com/). Open **Workfront Fusion**.

![WF Fusion](./images/wffusion1.png)

In the left menu, go to **Scenarios** and select your folder `--aepUserLdap--`. Click **Create a new scenario**.

![Frame IO](./images/aemf1.png)

Use the name `--aepUserLdap-- - Asset Approved PNG AEM Assets`. Next, click the **?** module, enter the search term `webhook` and then click **Webhooks**.

![Frame IO](./images/aemf2.png)

Click **Custom webhook**.

![Frame IO](./images/aemf3.png)

Click **Add** to create a new webhook.

![Frame IO](./images/aemf4.png)

Use the name `--aepUserLdap-- - Frame.io Webhook`. Click **Save**.

![Frame IO](./images/aemf5.png)

You should then see this. Click **Copy address to clipboard**.

![Frame IO](./images/aemf6.png)

## 1.2.6.2 Configure Webhook in Frame.io

Go to [https://developer.frame.io/](https://developer.frame.io/). Click **DEVELOPER TOOLS** and then choose **Custom Actions**.

![Frame IO](./images/aemf7.png)

Click **Create a Webhook**.

![Frame IO](./images/aemf8.png)

Enter the following values:

- **NAME**: use `--aepUserLdap-- - Asset Labels Updated`
- **URL**: enter the URL of the webhook that you just created in Workfront Fusion
- **TEAM**: select the appropriate Frame.io team, in this case, **One Adobe Tutorial**.

![Frame IO](./images/aemf9.png)

Scroll down and enable the checkbox next to **Asset Labels - updated**. Click **Submit**.

![Frame IO](./images/aemf10.png)

You should then see this.

![Frame IO](./images/aemf11.png)

Go to [https://app.frame.io/projects](https://app.frame.io/projects) and go to the folder that you created before, which should be named `--aepUserLdap--`. Double-click to open the asset that was created in the previous exercise.

![Frame IO](./images/aemf11a.png)

You should then see something like this. Click the field **No Status** and change the status to **In Progress**.

![Frame IO](./images/aemf12.png)

Switch back to Workfront Fusion. You should now see that the connection was **Successfully determined**.

![Frame IO](./images/aemf13.png)

Click **Save** to save your changes, and then click **Run once** to do a quick test.

![Frame IO](./images/aemf14.png)

Switch back to Frame.io and click the field **In Progress** and change the status to **Needs review**.

![Frame IO](./images/aemf15.png)

Switch back to Workfront Fusion and click the bubble on the **Custom webhook** module. 

The detailed view of the bubble shows you the data that was received from Frame.io. You should see various ID's. As an example, the field **resource.id** shows the unique ID in Frame.io of the asset **citisignal-fiber.psd**.

![Frame IO](./images/aemf16.png)

## 1.2.6.3 Get Asset Details from Frame.io

Now that the communication between Frame.io and Workfront Fusion has been established over a custom webhook, you should get more details about the asset for which the status label was updated. To do this, you'll once again use the Frame.io connector in Workfront Fusion, similar to the previous exercise.

Click the **?** module and enter the search term `frame`. Click **Frame.io**.

![Frame IO](./images/aemf18.png)

Click **Frame.io (Legacy)**.

![Frame IO](./images/aemf19.png)

Click **Get an asset**.

![Frame IO](./images/aemf20.png)

Verify that the connection is set to the same connection that you created in the previous exercise, which should be named `--aepUserLdap-- - Frame.io Token`.

![Frame IO](./images/aemf21.png)

Next, you need to provide the **Asset ID**. The **Asset ID** is shared by Frame.io to Workfront Fusion as part of the initial **Custom webhook** communication and can be found under the field **resource.id**. Select **resource.id** and click **OK**.

![Frame IO](./images/aemf22.png)

Click **Save** to save your changes and then click **Run once** to test your configuration.

![Frame IO](./images/aemf23.png)

Switch back to Frame.io and click the field **Needs review** and change the status to **In Progress**.

![Frame IO](./images/aemf24.png)

Go back to Workfront Fusion and click the bubble on the **Frame.io - Get an asset** module. You should then see a similar overview.

![Frame IO](./images/aemf25.png)

In the asset details that were provided by Frame.io, you can find a field called **Label** that is set to **in_progress**. You'll have to use that field at a later stage to configure a filter.

![Frame IO](./images/aemf26.png)

## 1.2.6.4 Convert to PNG

Hover over the module **Frame.io - Get an asset** and click the **+** icon.

![Frame IO](./images/aemf27.png)

Enter the search term `photoshop` and then click **Adobe Photoshop**.

![Frame IO](./images/aemf28.png)

Click **Convert Image Format**.

![Frame IO](./images/aemf29.png)

Verify that the field **Connection** is using your previously created connection, which is named `--aepUserLdap-- - Adobe IO`.

Under **Input**, set the field **Storage** to **External** and set the **File Location** to use the variable **Original** that is returned by the module **Frame.io - Get an asset**.

Next, click **Add item** under **Outputs**.

![Frame IO](./images/aemf30.png)

For the **Outputs** configuration, set the field **Storage** to **Fusion internal storage** and the **Type** to **image/png**. Click **Save**.

![Frame IO](./images/aemf31.png)

Click **OK**.

![Frame IO](./images/aemf33.png)

Click **Save** to save your changes.

![Frame IO](./images/aemf32.png)

Next, you should set up a filter to ensure that only for assets that have a status that is **Approved**, a PNG file is rendered. To do that, click the **Wrench** icon between the modules **Frame.io - Get an asset** and **Adobe Photoshop - Convert image format** and then select **Set up a filter**.

![Frame IO](./images/aemf34.png)

Configure the following fields:

- **Label**: use `Is Asset Approved`.
- **Condition**: select the field **Label** from the response of the **Frame.io - Get an asset** module.
- **Basic Operators**: select **Equal to**.
- **Value**: `approved`.

Click **OK**.

![Frame IO](./images/aemf35.png)

Click **Save** to save your changes and then click **Run once** to test your configuration.

![Frame IO](./images/aemf36.png)

Switch back to Frame.io and click the field **In Progress** and change the status to **Approved**.

![Frame IO](./images/aemf37.png)

Go back to Workfront Fusion. You should now see that all modules in your scenario have been executed successfully. Click the bubble on the **Adobe Photoshop - Convert image format** module.

![Frame IO](./images/aemf38.png)

In the details of the execution of the **Adobe Photoshop - Convert image format** module, you can see that a PNG file was now generated. The next step is to then store that file in AEM Assets CS.

![Frame IO](./images/aemf39.png)

## 1.2.6.5 Store PNG in AEM Assets CS

Hover over the **Adobe Photoshop - Convert image format** module and click the **+** icon.

![Frame IO](./images/aemf40.png)

Enter the search term `aem` and select **AEM Assets**.

![Frame IO](./images/aemf41.png)

Click **Upload an asset**.

![Frame IO](./images/aemf42.png)

You now need to configure your connection to AEM Assets CS. Click **Add**.

![Frame IO](./images/aemf43.png)

Use the following settings:

- **Connection Type**: **AEM Assets as a Cloud Service**.
- **Connection Name**: `--aepUserLdap-- AEM Assets CS`.
- **Instance URL**: copy the instance URL of your AEM Assets CS Author environment, which should look like this: `https://author-pXXXXX-eXXXXXXX.adobeaemcloud.com`.
- **Access details fill options**: select **Provide JSON**.

You now need to provide the **Technical account credentials in JSON format**. To do this, there are a number of steps to follow using AEM Cloud Manager. While you do that, keep this screen open.

![Frame IO](./images/aemf44.png)

Go to [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. The org you should select is `--aepImsOrgName--`. You'll then see something like this. Click to open your program, which should be named `--aepUserLdap-- - Citi Signal`.

![Frame IO](./images/aemf45.png)

Click the 3 dots **...** and select **Developer Console**.

![Frame IO](./images/aemf46.png)

Click **Sign in with Adobe**.

![Frame IO](./images/aemf47.png)

You're then taken to the **Developer Console**. Click **Create new technical account**.

![Frame IO](./images/aemf48.png)

You should then see something like this. Copy the full JSON payload to your clipboard.

![Frame IO](./images/aemf50.png)

Go back to Workfront Fusion and paste the full JSON payload in the **Technical account credentials in JSON format** field. Click **Continue**.

![Frame IO](./images/aemf49.png)

Your connection will then be validated and when successful, your connection will be automatically selected in the AEM Assets module. The next thing to do is to configure a folder. As part of the exercise, you should create a new dedicated folder.

![Frame IO](./images/aemf51.png)

To create a new dedicated folder, go to [https://experience.adobe.com](https://experience.adobe.com/). Ensure that the right Experience Cloud instance is selected, which should be `--aepImsOrgName--`. Then, click **Experience Manager Assets**.

![Frame IO](./images/aemf52.png)

Click **Select** on your AEM Assets CS environment, which should be named `--aepUserLdap-- - Citi Signal dev`.

![Frame IO](./images/aemf53.png)

Go to **Assetss** and click **Create Folder**.

![Frame IO](./images/aemf54.png)

Enter the name `--aepUserLdap-- - Frame.io PNG` and click **Create**.

![Frame IO](./images/aemf55.png)

Your folder is then created.

![Frame IO](./images/aemf56.png)

Go back to Workfront Fusion, click **Click here to choose folder** and then choose the folder `--aepUserLdap-- - Frame.io PNG`.

![Frame IO](./images/aemf57.png)

Verify that the destination is set to `--aepUserLdap-- - Frame.io PNG`. Then, under **Source File**, select **Map**.

Under **File name**, choose the variable `{{3.filenames[]}}`.

Under **Data**, choose the variable `{{3.files[]}}`.

>[!NOTE]
>
>Variables in Workfront Fusion can be manually specified using this syntax: `{{3.filenames[]}}`. The number in the variable references the module in the scenario. In this example, you can see that the third module in the scenario is called **Adobe Photoshop - Convert image format** and has a sequence number of **3**. This means that the variable `{{3.filenames[]}}` will access the field **filenames[]** from the module with sequence number 3. Sequence numbers can sometimes be different so pay attention when copying/pasting such variables and always verify that the sequence number used is the correct one.

Click **OK**.

![Frame IO](./images/aemf58.png)

Click **Save** to save your changes.

![Frame IO](./images/aemf59.png)

Next, you need to set specific permissions for the Technical Account that you just created. When the account was created in **Developer Console** in **Cloud Manager**, it was given **Read** access rights but for this use case, **Write** access rights are required. You can do that by going to your AEM CS Author environment.

Go to [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com){target="_blank"}. The org you should select is `--aepImsOrgName--`. Click to open your program, which should be named `--aepUserLdap-- - Citi Signal`. You'll then see something like this. Click the Author URL.

![Frame IO](./images/aemf60.png)

Click **Sign in with Adobe**.

![Frame IO](./images/aemf61.png)

Go to **Settings** > **Security** > **Users**.

![Frame IO](./images/aemf62.png)

Click to open the Technical Account user account.

![Frame IO](./images/aemf63.png)

Go to **Groups** and add this Technical Account user to the group **DAM-Users**.

![Frame IO](./images/aemf64.png)

Click **Save & Close**.

![Frame IO](./images/aemf65.png)

Go back to Workfront Fusion. Click **Run once** to test your scenario.

![Frame IO](./images/aemf66.png)

Switch back to Frame.io and make sure the status of your asset is changed to **Approved** again.

>[!NOTE]
>
>You may have to change it first back to **In Progress** or **Needs Review**, to then change it back to **Approved**.

![Frame IO](./images/aemf15.png)

Your Workfront Fusio scenario will then be activated and should complete successfully. By viewing the information in the bubble on the **AEM Assets** module, you can already see that the PNG file was successfully stored in AEM Assets CS.

![Frame IO](./images/aemf67.png)

Go back to AEM Assets CS and open the folder `--aepUserLdap-- - Frame.io PNG`. You should now see the PNG file that was generated as part of the Workfront Fusion scenario. Double-click the file to open it.

![Frame IO](./images/aemf68.png)

You can now see more details about the metadata of the PNG file that was generated.

![Frame IO](./images/aemf69.png)

You've now successfully completed this exercise.

## Next steps

Go to [Summary and Benefits of Creative Workflow Automation with Workfront Fusion](./summary.md){target="_blank"}

Go back to [Creative Workflow Automation with Workfront Fusion](./automation.md){target="_blank"}

Go back to [All Modules](./../../../overview.md){target="_blank"}
