---
title: Use Adobe APIs within Workfront Fusion
description: Learn how to use Adobe APIs in Workfront Fusion
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 23ebf8b4-3f16-474c-afe1-520d88331417
---
# Use Adobe APIs in Workfront Fusion

Learn how to use Adobe APIs in Workfront Fusion.

## Use Firefly Text To Image API with Workfront Fusion

1. Hover over the second **Set multiple variables** node and select **+** to add another module.

  ![WF Fusion](./images/wffusion48.png)

1. Search for **http** and select **HTTP**.

  ![WF Fusion](./images/wffusion49.png)

1. Select **Make a request**.

  ![WF Fusion](./images/wffusion50.png)

1. Select these variables:

  - **URL**: `https://firefly-api.adobe.io/v3/images/generate`
  - **Method**: `POST`

1. Select **Add a header**.

  ![WF Fusion](./images/wffusion51.png)

1. Enter the following headers:

  | Key     | Value     | 
  |:-------------:| :---------------:| 
  | `x-api-key`         | your stored variable for `CONST_client_id` |
  | `Authorization`         | `Bearer ` + your stored variable for `bearer_token` |
  | `Content-Type`         | `application/json` |
  | `Accept`         | `*/*` |

1. Enter the details for `x-api-key`. Select **Add**.

  ![WF Fusion](./images/wffusion52.png)

1. Select **Add a header**.

  ![WF Fusion](./images/wffusion53.png)

1. Enter the details for `Authorization`. Select **Add**.

  ![WF Fusion](./images/wffusion54.png)

1. Select **Add a header**. Enter the details for `Content-Type`. Select **Add**.

  ![WF Fusion](./images/wffusion541.png)

1. Select **Add a header**. Enter the details for `Accept`. Select **Add**.

  ![WF Fusion](./images/wffusion542.png)

1. Set the **Body type** to **Raw**. For **Content type**, select **JSON (application/json)**.

  ![WF Fusion](./images/wffusion55.png)

1. Paste this payload into the **Request content** field.

  ```json
  {
    "numVariations": 1,
    "size": {
      "width": 2048,
      "height": 2048
    },
    "prompt": "Horses in a field",
    "promptBiasingLocaleCode": "en-US"
  }
  ```

1. Check the box for **Parse response**. Select **OK**.

  ![WF Fusion](./images/wffusion56.png)

1. Select **Run once**.

  ![WF Fusion](./images/wffusion57.png)

  Your screen should look like this.

  ![WF Fusion](./images/wffusion58.png)

1. Select the **?** icon on the fourth node, HTTP, to see the response. You should see an image file in the response.

  ![WF Fusion](./images/wffusion59.png)

1. Copy the image URL and open it in a browser window. Your screen should look like this:

  ![WF Fusion](./images/wffusion60.png)

1. Right-click **HTTP** and rename to **Firefly T2I**.

  ![WF Fusion](./images/wffusion62.png)

1. Select **Save** to save your changes.

  ![WF Fusion](./images/wffusion61.png)

## Use Photoshop API with Workfront Fusion

Click the **wrench** icon between the nodes **Set Bearer Token** and **Firefly T2I**. Select **Add a router**.

![WF Fusion](./images/wffusion63.png)

Right-click the **Firefly T2I** object and select **Clone**.

![WF Fusion](./images/wffusion64.png)

Drag and drop the cloned object close to the **Router** object, and it will auto-connect to the **Router**. You should then have this.

![WF Fusion](./images/wffusion65.png)

You now have an identical copy based on the **Firefly T2I** HTTP request. Some of the settings of the **Firefly T2I** HTTP request are similar to what you need to interact with the **Photoshop API**, which is a time saver. You now only need to change the variables that aren't the same, like the request URL and the payload.

Change the **URL** to `https://image.adobe.io/pie/psdService/text`.

![WF Fusion](./images/wffusion66.png)

Replace the **Request content** by the below payload:

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
        "name": "2048x2048-button-text",
        "text": {
          "content": "Click here"
        }
      },
      {
        "name": "2048x2048-cta",
        "text": {
          "content": "Buy this stuff"
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

![WF Fusion](./images/wffusion67.png)

In order for this **Request content** to function properly, there are some variables that are missing:

- `AZURE_STORAGE_URL`
- `AZURE_STORAGE_CONTAINER`
- `AZURE_STORAGE_SAS_READ`
- `AZURE_STORAGE_SAS_WRITE`

Go back to your first node, click **Initialize Constants** and then select **Add item** for each of these variables.

![WF Fusion](./images/wffusion69.png)

| Key     | Example Value     | 
|:-------------:| :---------------:| 
| `AZURE_STORAGE_URL`| `https://vangeluw.blob.core.windows.net` |
| `AZURE_STORAGE_CONTAINER`| `vangeluw` |
| `AZURE_STORAGE_SAS_READ`| `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D` |
| `AZURE_STORAGE_SAS_WRITE`| `?sv=2023-01-03&st=2025-01-13T17%3A21%3A09Z&se=2025-01-14T17%3A21%3A09Z&sr=c&sp=racwl&sig=FD4m0YyyqUj%2B5T8YyTFJDi55RiTDC9xKtLTgW0CShps%3D` |

You can find your variables by going back to Postman, and opening your **Environment Variables**.

![Azure Storage](./../module1.1/images/az105.png)

Copy these values across to Workfront Fusion, and add a new item for each of these 4 variables.

You should then have this. Click **OK**.

![WF Fusion](./images/wffusion68.png)

Next, go back to the cloned HTTP request to update the **Request content**. You'll notice these black variables in the **Request content**, which are the variables you copied across from Postman. You now need to change these to the variables you just defined in Workfront Fusion. Replace each variable one by one by deleting the black text and replacing it by the correct variable.

![WF Fusion](./images/wffusion70.png)

There are 3 changes to make in the **inputs** section.

![WF Fusion](./images/wffusion71.png)

There are also 3 change to make in the **outputs** section. Click **OK**.

![WF Fusion](./images/wffusion72.png)

Right-click the cloned node, and select **Rename**. Change the name to **Photoshop Change Text**.

![WF Fusion](./images/wffusion73.png)

You should then have this.

![WF Fusion](./images/wffusion74.png)

Click **Run once**.

![WF Fusion](./images/wffusion75.png)

Click the **search** icon on the the **Photoshop Change Text** node to see the response. You should have a response that looks like this, with a link to a status file.

![WF Fusion](./images/wffusion76.png)

Before continuing with the Photoshop API interactions, let's disable the route to the **Firefly T2I** node to not send unneeded API calls to that API endpoint. Click the **wrench** icon, and then select **Disable route**.

![WF Fusion](./images/wffusion77.png)

You should then have this.

![WF Fusion](./images/wffusion78.png)

Next, add another **Set multiple variables** node.

![WF Fusion](./images/wffusion79.png)

Place it after the **Photoshop Change Text** node.

![WF Fusion](./images/wffusion80.png)

Click the **Set multiple variables** node, select **Add item**. Select the variable value from the response of the previous request.

| Variable name     | Variable value     | 
|:-------------:| :---------------:| 
| `psdStatusUrl`| `data > _links > self > href` |

Click **Add**. 

![WF Fusion](./images/wffusion81.png)

Click **OK**.

![WF Fusion](./images/wffusion82.png)

Right-click on the **Photoshop Change Text** node and select **Clone**.

![WF Fusion](./images/wffusion83.png)

Drag the cloned HTTP request after the **Set multiple variables** node that you just created.

![WF Fusion](./images/wffusion83.png)

Right-click the cloned HTTP request, select **Rename** and change the name to **Photoshop Check Status**.

![WF Fusion](./images/wffusion84.png)

Click to open the HTTP request. Change the URL so that it references the variable that you created in the previous step, and set the **Method** to **GET**.

![WF Fusion](./images/wffusion85.png)

Remove the **Body** by selecting the empty option.

![WF Fusion](./images/wffusion86.png)

Click **OK**.

![WF Fusion](./images/wffusion87.png)

Click **Run once**.

![WF Fusion](./images/wffusion88.png)

You should then get a response which contains the field **status**, with status set to **running**. It takes a couple of seconds for Photoshop to complete the proces.

![WF Fusion](./images/wffusion89.png)

Now that you know the response needs a bit more time to be finished, it may be a good idea to add a timer in front of this HTTP request so that it doesn't run immediately.

Click the **Tools** node and then select **Sleep**.

![WF Fusion](./images/wffusion90.png)

Position the **Sleep** node in between **Set multiple variables** and **Photoshop Check Status**. Set the **Delay** to **5** seconds. Click **OK**.

![WF Fusion](./images/wffusion91.png)

You'll then have this. The challenge with the below configuration is that 5 seconds of waiting may be enough, but maybe it isn't enough. In reality, it would be better to have a more intelligent solution like a do...while loop that checks the status every 5 seconds until the status equals **succeeded**. You will now implement such a tactic in the next steps.

![WF Fusion](./images/wffusion92.png)

Click the **wrench** icon in between **Set multiple variables** and **Sleep**. Select **Add module**.

![WF Fusion](./images/wffusion93.png)

Search for `flow` and then select **Flow Control**.

![WF Fusion](./images/wffusion94.png)

Select **Repeater**.

![WF Fusion](./images/wffusion95.png)

Set the **Repeats** to **20**. Click **OK**.

![WF Fusion](./images/wffusion96.png)

Next, click **+** on the **Photoshop Check Status** to add another module.

![WF Fusion](./images/wffusion97.png)

Search for **flow** and select **Flow Control**.

![WF Fusion](./images/wffusion98.png)

Select **Array Aggregator**.

![WF Fusion](./images/wffusion99.png)

Set **Source Module** to **Repeater**. CLick **OK**.

![WF Fusion](./images/wffusion100.png)

You should then have this:

![WF Fusion](./images/wffusion101.png)

Click the **wrench** icon and select **Add a module**.

![WF Fusion](./images/wffusion102.png)

Search for **tools** and select **Tools**.

![WF Fusion](./images/wffusion103.png)

Select **Get multiple variables**.

![WF Fusion](./images/wffusion104.png)

Click **+ Add item** and set the **Variable name** to `done`.

![WF Fusion](./images/wffusion105.png)

Click **OK**.

![WF Fusion](./images/wffusion106.png)

Click the **Set multiple variables** node that you configured before. In order to initialize the variable **done**, you need to set it to `false` here. Clik **+ Add item**.

![WF Fusion](./images/wffusion107.png)

For the **Variable name**, use `done`. To set the status, a boolean value is needed. To find the boolean value, click the **gear** icon and then select `false`. Click **Add**.

![WF Fusion](./images/wffusion108.png)

Click **OK**.

![WF Fusion](./images/wffusion109.png)

Next, click the **wrench** icon after the **Get multiple variables** node that you configured.

![WF Fusion](./images/wffusion110.png)

Select **Set up a filter**. You now need to check the value of the variable **done**. If that value is set to **false**, then the next part of the loop has to be executed. If the value is set to **true**, it means that the process has already successfully completed so there's no need to continue with the next part of the loop.

![WF Fusion](./images/wffusion111.png)

For the label, use **Are we done?**. Set the **Condition** using the already existing variable **done**, the operator should be set to **Equal to** and the value should be the boolean variable `false`. Click **OK**.

![WF Fusion](./images/wffusion112.png)

Next, make some room between the nodes **Photoshop Check Status** and **Array aggregator**. Then, click the **wrench** icon and select **Add a router**. You're doing this because after checking the status of the Photoshop file, there should be 2 paths. If the status is `succeeded`, then the variable of **done** should be set to `true`. If the status is not equal to `succeeded`, then the loop should continue. The router will make it possible to check and set this.

![WF Fusion](./images/wffusion113.png)

After adding the router, click the **wrench** icon and select **Set up a filter**.

![WF Fusion](./images/wffusion114.png)

For the label, use **We are done**. Set the **Condition** using the response from the **Photoshop Check Status** node by choosing the resposne field **data.outputs[].status**, the operator should be set to **Equal to** and the value should be `succeeded`. Click **OK**.

![WF Fusion](./images/wffusion115.png)

Next, click the empty node with the question mark and search for **tools**. Then, select **Tools**.

![WF Fusion](./images/wffusion116.png)

Select **Set multiple variables**.

![WF Fusion](./images/wffusion117.png)

When this branch of the router is used, it means the status of the Photoshop file creation has successfully completed. This means that the do...while loop no longer need to continue checking the status in Photoshop, so you should set the variable `done` to `true`.

For the **Variable name**, use `done`. For the **Variable value**, you shoudl use the boolean value `true`. Click the **gear** icon and then select `true`. Click **Add**.

![WF Fusion](./images/wffusion118.png)

Click **OK**.

![WF Fusion](./images/wffusion119.png)

Next, right-click the **Set multiple variables** node you just created and select **Clone**.

![WF Fusion](./images/wffusion120.png)

Drag the cloned node so that it connects with the **Array aggregator**. Then, right-click the node and select **Rename**, and change the name to `Placeholder End`.

![WF Fusion](./images/wffusion122.png)

Remove the existing variable and click **+ Add Item**. For the **Variable name**, use `placeholder`, for the **Variable value**, use `end`. Click **Add** and then click **OK**.

![WF Fusion](./images/wffusion123.png)

Click **Save** to save your scenario. Next, click **Run once**.

![WF Fusion](./images/wffusion124.png)

Your scneario will then be executed and should finish successfully. You'll notice that the do...while loop that you configured worked fine. In the below run, you can see that the **Repeater** ran 20 times based on the bubble on the **Tools > Get multiple variables** node. After that node, you configured a filter that checked the status and only if the status was not equal to **succeeded**, the next nodes were executed. In this run, the part after the filter only ran once, because the status was already **succeeded** in the first run.

![WF Fusion](./images/wffusion125.png)

You can verify the status of the creation of your new Photoshop file by clicking the bubble on the **Photoshop Check Status** HTTP request and drilling down to the **status** field.

![WF Fusion](./images/wffusion126.png)

You've now configured the basic version of a repeatable scenario that automates a number of steps. In the next exercise, you'll iterate on that by adding complexity.

Next Step: [1.2.3 Process automation with Workfront Fusion](./ex3.md)

[Go Back to Module 1.2](./automation.md)

[Go Back to All Modules](./../../../overview.md)
