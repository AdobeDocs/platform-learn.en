---
title: Getting started with Workfront Fusion
description: Getting started with Workfront Fusion
kt: 5342
doc-type: tutorial
---
# 1.2.1 Getting started with Workfront Fusion

In this exercise, you'll use Workfront Fusion and Adobe I/O to query Adobe Firefly Services APIs.

## 1.2.1.1 Create new scenario

Go to [https://experience.adobe.com/](https://experience.adobe.com/). Click to open **Workfront Fusion**.

![WF Fusion](./images/wffusion1.png)

You should then see this. Go to **Scenarios**.

![WF Fusion](./images/wffusion2.png)

Click **Create new scenario**.

![WF Fusion](./images/wffusion3.png)

You'll then see an empty scenario. Click the **tools** icon and select **Set multiple variables**.

![WF Fusion](./images/wffusion4.png)

You now need to move the **clock** icon onto the newly added **Set multiple variables**. 

![WF Fusion](./images/wffusion5.png)

You'll then see this.

![WF Fusion](./images/wffusion6.png)

Then, right-click onto the question mark and select **Delete module**.

![WF Fusion](./images/wffusion7.png)

Next, right-click on the **Set multiple variables** object and select **Settings**.

![WF Fusion](./images/wffusion8.png)

## 1.2.1.2 Configure Adobe I/O authentication

You now need to configure the variables that are needed to authenticate against Adobe I/O. In the previous exercise, you created an Adobe I/O project. The variables of that Adobe I/O project now need to be defined in Workfront Fusion.

The following variables need to be defined:

| Key     | Value     | 
|:-------------:| :---------------:| 
| `CONST_client_id`         | your Adobe I/O project Client ID |
| `CONST_client_secret`         | your Adobe I/O project Client Secret|
| `CONST_scope`        | your Adobe I/O project Scope |

You can find these variables by going to [https://developer.adobe.com/console/projects](https://developer.adobe.com/console/projects) and opening your Adobe I/O project, which is named `--aepUserLdap-- Firefly`.

![WF Fusion](./images/wffusion9.png)

In your project, click **OAuth Serverto-Server** to see the values for the above keys.

![WF Fusion](./images/wffusion10.png)

With the above keys and values, you can configure the **Set multiple variables** object. Click **Add item**.

![WF Fusion](./images/wffusion11.png)

Enter the **Variable name**: **CONST_client_id** and its **Variable value**, click **Add**.

![WF Fusion](./images/wffusion12.png)

Click **Add item**.

![WF Fusion](./images/wffusion13.png)

Enter the **Variable name**: **CONST_client_secret** and its **Variable value**, click **Add**.

![WF Fusion](./images/wffusion14.png)

Click **Add item**.

![WF Fusion](./images/wffusion15.png)

Enter the **Variable name**: **CONST_scope** and its **Variable value**, click **Add**.

![WF Fusion](./images/wffusion16.png)

Click **OK**.

![WF Fusion](./images/wffusion17.png)

Hover over your **Set multiple variables** object and click the big **+** icon to add another module.

![WF Fusion](./images/wffusion18.png)

You should then see this.

![WF Fusion](./images/wffusion19.png)

In the search bar, enter **http**. Select **HTTP** to open it.

![WF Fusion](./images/wffusion21.png)

 and then select **Make a request**.

![WF Fusion](./images/wffusion20.png)

| Key     | Value     | 
|:-------------:| :---------------:| 
| `URL`         | `https://ims-na1.adobelogin.com/ims/token/v3` |
| `Method`         | `POST` |
| `Body Type`         | `x-www-form-urlencoded` |

Click **Add item**.

![WF Fusion](./images/wffusion22.png)

Add items for each of the below values:

| Key     | Value     | 
|:-------------:| :---------------:| 
| `client_id`         | your predefined variable for `CONST_client_id` |
| `client_secret`         | your predefined variable for `CONST_client_secret` |
| `scope`         | your predefined variable for `CONST_scope` |
| `grant_type`         | `client_credentials` |

Configuration for `client_id`.

![WF Fusion](./images/wffusion23.png)

Configuration for `client_secret`.

![WF Fusion](./images/wffusion25.png)

Configuration for `scope`.

![WF Fusion](./images/wffusion26.png)

Configuration for `grant_type`.

![WF Fusion](./images/wffusion28.png)

Configuration overview. Scroll down and check the checkbox for **Parse response**. Click **OK**.

![WF Fusion](./images/wffusion27.png)

You should then see this. Click **Run once**.

![WF Fusion](./images/wffusion29.png)

Once the scenario has run, you should see this.

![WF Fusion](./images/wffusion30.png)

Click the **question mark** icon on the **Set multiple variables** object to see what happened when that object was run.

![WF Fusion](./images/wffusion31.png)

Click the **question mark** icon on the **HTTP - Make a request** object to see what happened when that object was run. In the **OUTPUT**, you'll see the **access_token** being returned by Adobe I/O.

![WF Fusion](./images/wffusion32.png)

Hover over the **HTTP - Make a request** object and click the **+** icon to add another module.

![WF Fusion](./images/wffusion33.png)

In the search bar, search for `tools`. Select **Tools**.

![WF Fusion](./images/wffusion34.png)

Select **Set multiple variables**.

![WF Fusion](./images/wffusion35.png)

Select **Add item**.

![WF Fusion](./images/wffusion36.png)

Set the **Variable name** to `bearer_token`. Select `access_token` as the dynamic **Variable value**. CLick **Add**.

![WF Fusion](./images/wffusion37.png)

You should then have this. Click **OK**.

![WF Fusion](./images/wffusion38.png)

Click **Run once** again.

![WF Fusion](./images/wffusion39.png)

Once the scenario has run, click the **question mark** icon on the last **Set multiple variables** object. You shoudl then see that the access_token is being stored into the variable `bearer_token`.

![WF Fusion](./images/wffusion40.png)

Next, right-click on the first object **Set multiple values** and select **Rename**.

![WF Fusion](./images/wffusion41.png)

Set the name to **Initialize Constants**. Click **OK**.

![WF Fusion](./images/wffusion42.png)

Rename the second object and set the name to **Authenticate to Adobe I/O**. Click **OK**.

![WF Fusion](./images/wffusion43.png)

Rename the third object and set the name to **Set Bearer Token**. Click **OK**.

![WF Fusion](./images/wffusion44.png)

You should then have this.

![WF Fusion](./images/wffusion45.png)

Next, change the name of your scenario to `--aepUSerLdap-- - Adobe I/O Authentication`.

![WF Fusion](./images/wffusion46.png)

Click **Save**.

![WF Fusion](./images/wffusion47.png)

Next Step: [1.2.2 Use Adobe APIs within Workfront Fusion](./ex2.md)

[Go Back to Module 1.2](./automation.md)

[Go Back to All Modules](./../../../overview.md)
