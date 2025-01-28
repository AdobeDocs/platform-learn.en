---
title: Getting started with Workfront Fusion
description: Learn how to use Workfront Fusion and Adobe I/O to query Adobe Firefly Services APIs
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 42e260e0-8af0-4d71-b634-48c1966bd912
---
# Getting started with Workfront Fusion

Learn how to use Workfront Fusion and Adobe I/O to query Adobe Firefly Services APIs.

## Create new scenario

1. Go to [https://experience.adobe.com/](https://experience.adobe.com/). Open **Workfront Fusion**.

    ![WF Fusion](./images/wffusion1.png)

1. Go to **Scenarios**.

    ![WF Fusion](./images/wffusion2.png)

1. Select **Create new scenario**.

    ![WF Fusion](./images/wffusion2a.png)

1. Name the folder `--aepUserLdap--` and select **Save**.

    ![WF Fusion](./images/wffusion2b.png)

1. Select your folder, and then select **Create new scenario**.

    ![WF Fusion](./images/wffusion3.png)

1. An empty scenario appears, select **tools** and select **Set multiple variables**.

    ![WF Fusion](./images/wffusion4.png)

1. Move the **clock** icon onto the newly added **Set multiple variables**. 

    ![WF Fusion](./images/wffusion5.png)

    Your screen should look like this.

    ![WF Fusion](./images/wffusion6.png)

1. Right-click on the question mark and select **Delete module**.

    ![WF Fusion](./images/wffusion7.png)

1. Next, right-click on **Set multiple variables** and select **Settings**.

    ![WF Fusion](./images/wffusion8.png)

## Configure Adobe I/O authentication

You now need to configure the variables that are needed to authenticate against Adobe I/O. In the previous exercise, you created an Adobe I/O project. The variables of that Adobe I/O project now need to be defined in Workfront Fusion.

The following variables need to be defined:

| Key     | Value     | 
|:-------------:| :---------------:| 
| `CONST_client_id`         | your Adobe I/O project Client ID |
| `CONST_client_secret`         | your Adobe I/O project Client Secret|
| `CONST_scope`        | your Adobe I/O project Scope |

1. Find these variables by going to [https://developer.adobe.com/console/projects](https://developer.adobe.com/console/projects) and opening your Adobe I/O project, which is named `--aepUserLdap-- Firefly`.

    ![WF Fusion](./images/wffusion9.png)

1. In your project, select **OAuth Serverto-Server** to see the values for the above keys.

    ![WF Fusion](./images/wffusion10.png)

1. Using the above keys and values, you can configure the **Set multiple variables** object. Select **Add item**.   

    ![WF Fusion](./images/wffusion11.png)

1. Enter the **Variable name**: **CONST_client_id** and its **Variable value**, select **Add**.

    ![WF Fusion](./images/wffusion12.png)

1. Select **Add item**.

    ![WF Fusion](./images/wffusion13.png)

1. Enter **Variable name**: **CONST_client_secret** and its **Variable value**, select **Add**.

    ![WF Fusion](./images/wffusion14.png)

1. Select **Add item**.

    ![WF Fusion](./images/wffusion15.png)

1. Enter **Variable name**: **CONST_scope** and its **Variable value**, select **Add**.

    ![WF Fusion](./images/wffusion16.png)

1. Select **OK**.

    ![WF Fusion](./images/wffusion17.png)

1. Hover over **Set multiple variables** and select the big **+** icon to add another module.

    ![WF Fusion](./images/wffusion18.png)

    Your screen should look like this.

    ![WF Fusion](./images/wffusion19.png)

1. In the search bar, enter **http**. Select **HTTP** to open it.

    ![WF Fusion](./images/wffusion21.png)

1. Select **Make a request**.

    ![WF Fusion](./images/wffusion20.png)

    | Key     | Value     | 
    |:-------------:| :---------------:| 
    | `URL`         | `https://ims-na1.adobelogin.com/ims/token/v3` |
    | `Method`         | `POST` |
    | `Body Type`         | `x-www-form-urlencoded` |

1. Select **Add item**. 

    ![WF Fusion](./images/wffusion22.png)

1. Add items for each of the below values:

    | Key     | Value     | 
    |:-------------:| :---------------:| 
    | `client_id`         | your predefined variable for `CONST_client_id` |
    | `client_secret`         | your predefined variable for `CONST_client_secret` |
    | `scope`         | your predefined variable for `CONST_scope` |
    | `grant_type`         | `client_credentials` |

1. Configuration for `client_id`:

    ![WF Fusion](./images/wffusion23.png)

1. Configuration for `client_secret`.

    ![WF Fusion](./images/wffusion25.png)

1. Configuration for `scope`.

    ![WF Fusion](./images/wffusion26.png)

1. Configuration for `grant_type`.

    ![WF Fusion](./images/wffusion28.png)

1. Scroll down and check the box for **Parse response**. Select **OK**.

    ![WF Fusion](./images/wffusion27.png)

1. Your screen should look like this. Select **Run once**.

    ![WF Fusion](./images/wffusion29.png)

    Once the scenario has run, your screen should look like this:

    ![WF Fusion](./images/wffusion30.png)

1. Select the **question mark** icon on the **Set multiple variables** object to see what happened when that object ran.

    ![WF Fusion](./images/wffusion31.png)

1. Select the **question mark** icon on the **HTTP - Make a request** object to see what happened when that object ran. In the **OUTPUT**, see the **access_token** being returned by Adobe I/O.

    ![WF Fusion](./images/wffusion32.png)

1. Hover over **HTTP - Make a request** and select the **+** icon to add another module.

    ![WF Fusion](./images/wffusion33.png)

1. In the search bar, search for `tools`. Select **Tools**.

    ![WF Fusion](./images/wffusion34.png)

1. Select **Set multiple variables**.   

    ![WF Fusion](./images/wffusion35.png)

1. Select **Add item**.

    ![WF Fusion](./images/wffusion36.png)

1. Set **Variable name** to `bearer_token`. Select `access_token` as the dynamic **Variable value**. Select **Add**.

    ![WF Fusion](./images/wffusion37.png)

1. Your screen should look like this. Select **OK**.

    ![WF Fusion](./images/wffusion38.png)

1. Select **Run once** again.

    ![WF Fusion](./images/wffusion39.png)

1. Once the scenario runs, select the **question mark** icon on the last **Set multiple variables** object. You should see that the access_token is being stored in the variable `bearer_token`.

    ![WF Fusion](./images/wffusion40.png)

1. Next, right-click on the first object **Set multiple values** and select **Rename**.

    ![WF Fusion](./images/wffusion41.png)

1. Set the name to **Initialize Constants**. Select **OK**.

    ![WF Fusion](./images/wffusion42.png)

1. Rename the second object to **Authenticate to Adobe I/O**. Select **OK**.

    ![WF Fusion](./images/wffusion43.png)

1. Rename the third object to **Set Bearer Token**. Select **OK**.

    ![WF Fusion](./images/wffusion44.png)

    Your screen should look like this:

    ![WF Fusion](./images/wffusion45.png)

1. Next, change the name of your scenario to `--aepUSerLdap-- - Adobe I/O Authentication`.

    ![WF Fusion](./images/wffusion46.png)

1. Select **Save**.

    ![WF Fusion](./images/wffusion47.png)

## Next Steps

Go to [Use Adobe APIs within Workfront Fusion](./ex2.md){target="_blank"}

Go back to [Automating Adobe Firefly Services](./automation.md){target="_blank"}

Go back to [All Modules](./../../../overview.md){target="_blank"}
