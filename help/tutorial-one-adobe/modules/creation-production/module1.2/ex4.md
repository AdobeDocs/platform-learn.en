---
title: Automation using Connectors
description: Automation using Connectors
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 0b20ba91-28d4-4f4d-8abe-074f802c389e
---
# 1.2.4 Automation using Connectors

You will now start using the out-of-the-box connectors in Workfront Fusion for Photoshop and you'll connect the Firefly Text-2-Image request and the Photoshop requests into one scenario.

## 1.2.4.1 Duplicate and prepare your scenario

In the left menu, go to **Scenarios** and select your folder `--aepUserLdap--`. You should then see the scenario you created before, which is named `--aepUSerLdap-- - Adobe I/O Authentication`.

![WF Fusion](./images/wffc1.png)

Click the arrow to open the dropdown menu and select **Clone**.

![WF Fusion](./images/wffc2.png)

Set the **Name** of the cloned scenario to `--aepUserLdap-- - Firefly + Photoshop` and select the appropriate **Target team**. Click **Add** to add a new webhook.

![WF Fusion](./images/wffc3.png)

Set the **Webhook name** to `--aepUserLdap-- - Firefly + Photoshop Webhook`. Click **Save**.

![WF Fusion](./images/wffc4.png)

You should then see this. Click **Save**.

![WF Fusion](./images/wffc5.png)

You should then see this. Click the **Webhook** node.

![WF Fusion](./images/wffc6.png)

Click **Copy address to clipboard** and then click **Re-determine data structure**.

![WF Fusion](./images/wffc7.png)

Open Postman. Add a new request in the same folder you were using before.

![WF Fusion](./images/wffc9.png)

Make sure the following settings are applied:

- Request name: `POST - Send Request to Workfront Fusion Webhook Firefly + Photoshop`
- Request type: `POST`
- Request URL: paste the URL you copied from your Workfront Fusion Scenario's webhook.

Go to **Body** and set the **Body Type** to **raw** - **JSON**. Paste the following payload in the **Body**.

```json
{
    "psdTemplate": "citisignal-fiber.psd",
    "xlsFile": "placeholder",
    "prompt":"misty meadows",
    "cta": "Buy this now!",
    "button": "Click here to buy!"
}
```

This new payload will ensure that all variable information is provided from outside the scenario instead of it being hardcoded in the scenario. In an enterprise scenario, an organization needs a scenario to be defined in a reusable way, which means that a number of variables need to be provided as input variables instead of having them hardcoded in the scenario.

You should then have this. Click **Send**.

![WF Fusion](./images/wffc10.png)

The Workfront Fusion webhook is still waiting for input. 

![WF Fusion](./images/wffc11.png)

Once you've clicked **Send**, the message should change tp **Successfully determined**. Click **OK**.

![WF Fusion](./images/wffc12.png)

## 1.2.4.2 Update Firefly T2I node

Click the node **Firefly T2I**. You should then see this. The prompt in this request was previously hardcoded to **horses in a field**. You will now remove that hardcoded text and replace it by a field coming from the webhook.

![WF Fusion](./images/wffcfft2i1.png)

Remove the text **horses in a field** and replace it by the variable **prompt** which can be found under the **Webhook** variables. Click **OK** to save your changes.

![WF Fusion](./images/wffcfft2i2.png)

## 1.2.4.2 Change background of PSD file

You will now update your scenario to make it smarter by using out-of-the-box connectors. You'll also connect the output from Firefly to Photoshop, so that the background image of the PSD-file changes dynamically by using the output from the Firefly Generate Image action.

In the previous exercise, you had disabled the **Firefly T2I** route. You should now undo that. Click the **stop**-icon to enable the route again. 

![WF Fusion](./images/wffc13.png)

You'll then see that the **stop** icon disappears. Next, click the **wrench** icon on the other route towards the configuration of the previous exercise and select **Disable route**.

![WF Fusion](./images/wffc14.png)

You should then see this. Next, hover over the **Firefly T2I** node and click the **+** icon.

![WF Fusion](./images/wffc15.png)

In the search menu, enter `Photoshop`and then click the **Adobe Photoshop** action.

![WF Fusion](./images/wffc16.png)

Select **Apply PSD edits**.

![WF Fusion](./images/wffc17.png)

You should then see this. Click **Add** to add a new connection to Adobe Photoshop. 

![WF Fusion](./images/wffc18.png)

Configure your connection as follows:

- Connection type: select **Adobe Photoshop (Server-to-Server)**
- Connection name: enter `--aepUserLdap-- - Adobe IO`
- Client ID: paste your Client ID
- Client Secret: paste your Client Secret

Click **Continue**.

![WF Fusion](./images/wffc19.png)

To find your **Client ID** and **Client Secret**, go to [https://developer.adobe.com/console/home](https://developer.adobe.com/console/home){target="_blank"} and open your Adobe I/O project, which is named `--aepUserLdap-- One Adobe tutorial`. Go to **OAuth Server-to-Server** to find your Client ID and Client Secret. Copy those values and paste them in the connection setup in Workfront Fusion.

![WF Fusion](./images/wffc20.png)

After clicking **Continue**, a popup window will be shown briefly while your credentials are being verified. Once done, you should see this.

![WF Fusion](./images/wffc21.png)

You now need to enter the file location of the PSD file that you want Fusion to work with. For **Storage**, select **Azure** and for **File location**, enter `{{1.AZURE_STORAGE_URL}}/{{1.AZURE_STORAGE_CONTAINER}}/{{1.AZURE_STORAGE_SAS_READ}}`. Put the cursor next to the second `/`. Then, have a look a the available variables and scroll down to find the variable **psdTemplate**. Click the variable **psdTemplate** to select it.

![WF Fusion](./images/wffc22.png)

You should then see this.

![WF Fusion](./images/wffc23.png)

Scroll all the way down until you see **Layers**. Click **Add item**.

![WF Fusion](./images/wffc24.png)

You should then see this. You now need to enter the name of the layer in your Photoshop PSD template that is used for the background of the file. 

![WF Fusion](./images/wffc25.png)

In the file **citisignal-fiber.psd**, you'll find the layer that used for the background. In this example, that layer is named **2048x2048-background**.

![WF Fusion](./images/wffc26.png)

Paste the name **2048x2048-background** in the Workfront Fusion dialog.

![WF Fusion](./images/wffc27.png)

Scroll down until you see **Input**. You now need to define what needs to be inserted in the background layer. In this case, you need to select the output of the Firefly T2I object, which contains the dynamically generated image.

For **Storage**, select **External**. For **File location**, search and find the variable `data.outputs[].image.url` from the output of the **Firefly T2I** request.

![WF Fusion](./images/wffc28.png)

Next, scroll down until you see **Edit**. Set **Edit** to **Yes** and set **Type** to **Layer**. Click **Add**.

![WF Fusion](./images/wffc29.png)

You should then see this. Next, you need to define the output of the action. Click **Add item** under **outputs**.

![WF Fusion](./images/wffc30.png)

Select **Azure** for **Storage**, paste this `{{1.AZURE_STORAGE_URL}}/{{1.AZURE_STORAGE_CONTAINER}}/citisignal-fiber-replacedbg.psd{{1.AZURE_STORAGE_SAS_WRITE}}` under  **File Location** and select **vnd.adobe.photoshop** under **Type**. Click to enable **Show advanced settings**.

![WF Fusion](./images/wffc31.png)

Under **Advanced Settings**, select **Yes** to overwrite files with the same name.
Click **Add**.

![WF Fusion](./images/wffc32.png)

You should then have this. Click **OK**.

![WF Fusion](./images/wffc33.png)

## 1.2.4.3 Change text layers of PSD file

### Call To Action Text

Next, hover over the **Adobe Photoshop - Apply PSD edits** node and click the **+** icon.

![WF Fusion](./images/wffc34.png)

Select **Adobe Photoshop**.

![WF Fusion](./images/wffc35.png)

Select **Edit text layers**.

![WF Fusion](./images/wffc36.png)

You should then see this. First, select your previously already configured Adobe Photoshop connection, which should be named `--aepUserLdap-- Adobe IO`. 

You now need to define the location of the **Input file**, which is the output of the previous step and under **Layers**, you need to enter the **Name** of the text layer you want to change. 

![WF Fusion](./images/wffc37.png)

For the **Input file**, select **Azure** for **Input file storage** and make sure to select the output from the previous request, **Adobe Photoshop - Apply PSD edits**, which you can take from here: `data[]._links.renditions[].href`

![WF Fusion](./images/wffc37a.png)

Open the file **citisignal-fiber.psd**. In the file, you'll notice that the layer containing the call to action is named **2048x2048-cta**.

![WF Fusion](./images/wffc38.png)

Enter the name **2048x2048-cta** under **Name** in the dialog.

![WF Fusion](./images/wffc39.png)

Scroll down until you see **Text** > **Content**. Select the variable **cta** from the Webhook payload.

![WF Fusion](./images/wffc40.png)

Scroll down until you see **Output**. For **Storage**, select **Azure**. For **File location**, enter the below location. Please note the addition of the variable `{{timestamp}}` to the filename which is used to ensure that every file that is generated has a unique name. Also, set the **Type** to **vnd.adobe.photoshop**. Click **OK**.

`{{1.AZURE_STORAGE_URL}}/{{1.AZURE_STORAGE_CONTAINER}}/citisignal-fiber-changed-text-{{timestamp}}.psd{{1.AZURE_STORAGE_SAS_WRITE}}`

![WF Fusion](./images/wffc41.png)

### Button Text

Right-click the node you just created and select **Clone**. This will create a second similar object.

![WF Fusion](./images/wffc42.png)

You should then see this. First, select your previously already configured Adobe Photoshop connection, which should be named `--aepUserLdap-- Adobe IO`. 

You now need to define the location of the **Input file**, which is the output of the previous step and under **Layers**, you need to enter the **Name** of the text layer you want to change. 

![WF Fusion](./images/wffc43.png)

For the **Input file**, select **Azure** for **Input file storage** and make sure to select the output from the previous request, **Adobe Photoshop - Edit text layers**, which you can take from here: `data[]._links.renditions[].href`

Open the file **citisignal-fiber.psd**. In the file, you'll notice that the layer containing the call to action is named **2048x2048-button-text**.

![WF Fusion](./images/wffc44.png)

Enter the name **2048x2048-cta** under **Name** in the dialog.

![WF Fusion](./images/wffc43.png)

Scroll down until you see **Text** > **Content**. Select the variable **cta** from the Webhook payload.

![WF Fusion](./images/wffc45.png)

Scroll down until you see **Output**. For **Storage**, select **Azure**. For **File location**, enter the below location. Please note the addition of the variable `{{timestamp}}` to the filename which is used to ensure that every file that is generated has a unique name. Also, set the **Type** to **vnd.adobe.photoshop**. Click **OK**.

`{{1.AZURE_STORAGE_URL}}/{{1.AZURE_STORAGE_CONTAINER}}/citisignal-fiber-changed-text-{{timestamp}}.psd{{1.AZURE_STORAGE_SAS_WRITE}}`

![WF Fusion](./images/wffc46.png)

Click **Save** to save your changes.

![WF Fusion](./images/wffc47.png)

## 1.2.4.4 Webhook response

After applying these changes to your Photoshop file, you now need to configure a **Webhook response** which will be sent back to whichever application has activated this scenario.

Hover over the node **Adobe Photoshop - Edit text layers** and click the **+** icon.

![WF Fusion](./images/wffc48.png)

Search for **webhook** and select **Webhook**.

![WF Fusion](./images/wffc49.png)

Select **Webhook response**.

![WF Fusion](./images/wffc50.png)

You should then see this. Paste the below payload in **Body**.

```json
{
    "newPsdTemplate": ""
}
```

![WF Fusion](./images/wffc51.png)

Select the path `data[]._links.renditions[].href` from the output of the previous request. Enable the checkbox for **Show advanced settings** and then click **Add item**.

![WF Fusion](./images/wffc52.png)

In the field **Key**, enter `Content-Type`. In the field **Value**, enter `application/json`. Click **Save**.

![WF Fusion](./images/wffc52a.png)

You should then have this. Click **OK**.

![WF Fusion](./images/wffc53.png)

Click **Auto-align**.

![WF Fusion](./images/wffc54.png)

You should then see this. Click **Run once**.

![WF Fusion](./images/wffc55.png)

Go back to Postman and click **Send**. The prompt being used here is **misty meadows**.

![WF Fusion](./images/wffc56.png)

The scenario will then be activated and after some time, a response will be shown in Postman that contains the URL of the newly created PSD file.

![WF Fusion](./images/wffc58.png)

As a reminder: once the scenario has run in Workfront Fusion, you'll be able to see information about each node by clicking the bubble above each node.

![WF Fusion](./images/wffc59.png)

Using Azure Storage Explorer, you can then find and open the newly created PSD file by double-clicking it in Azure Storage Explorer.

![WF Fusion](./images/wffc60.png)

Your file should then look like this, with the background that is replaced by a background with **misty meadows**.

![WF Fusion](./images/wffc61.png)

If you run your scenario once again, and then send a new request from Postman using a different prompt, you'll then see how easy and reusable your scenario has become. In this example, the new prompt being used is **sunny desert**.

![WF Fusion](./images/wffc62.png)

And a couple of minutes later, a new PSD file has been generated with a new background.

![WF Fusion](./images/wffc63.png)

## Next steps

Go to [1.2.5 Frame.io and Workfront Fusion](./ex5.md){target="_blank"}

Go back to [Creative Workflow Automation with Workfront Fusion](./automation.md){target="_blank"}

Go back to [All Modules](./../../../overview.md){target="_blank"}
