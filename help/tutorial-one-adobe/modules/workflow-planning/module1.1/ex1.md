---
title: Getting started with Workfront Planning
description: Getting started with Workfront Planning
kt: 5342
doc-type: tutorial
exl-id: 26fa872b-c872-46b6-8f56-fa41696100da
---
# 1.1.1 Getting started with Workfront Planning

## 1.1.1.1 CitiSignal Campaign Brief

To understand the context of CitiSignal and what they're trying to achieve, download and read CitiSignal's Campaign Brief here: [CitiSignal-Fiber-Launch-Winter-2026.pdf](./../../../assets/brief/CitiSignal-Fiber-Launch-Winter-2026.pdf).

## 1.1.1.2 Workfront Planning Terminology

The following are the main Workfront Planning objects and concepts:

| Term                      | Explanation                                                                                                                                                                                                                                              |
| --- | ---|
| **Workspace** | A collection of record types that define the operational lifecycle of a certain organization. A workspace is the work frame of an organizational unit.                                                                               |
| **Record Type** | The name of object types in Workfront Planning. Record types populate workspaces. Unlike Workfront Workflow, where the object types are predefined, in Workfront Planning, you can create your own object types.                                                                              |
| **Record** | An instance of a record type. |
| **Workspace template** | You can create a workspace using predefined templates. You can use the predefined record types and fields that come in a template, or you can add your own. |
| **Fields** | Fields are attributes that you can add to record types. Fields contain information about the record type. |

>[!NOTE]
>
>There are limitations for how many Workfront Planning objects you can create. For more information, see Adobe Workfront Planning object limitations overview.

You will now go hands-on and start creating some of these objects yourself.

## 1.1.1.3 Workspace, Record Type, Fields

Go to [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Click to open **Workfront**.

![Workfront Planning](./images/wfpl1.png)

In Workfront, click to open the menu and then select **Planning**.

![Workfront Planning](./images/wfpl2.png)

You should then see this. Click **Create Workspace**.

![Workfront Planning](./images/wfpl3.png)

Click **Use tempmate** for the template **Basic Marketing Management**.

![Workfront Planning](./images/wfpl4.png)

A new workspace is now created. Before you continue, you need to change the name of the workspace. Click the 3 dots **...** and then select **Edit**.

![Workfront Planning](./images/wfpl5.png)

Change the name to `--aepUserLdap-- - Basic: Marketing Management`. Click **Save**.

![Workfront Planning](./images/wfpl6.png)

You should then have this. 

![Workfront Planning](./images/wfpl7a.png)

## 1.1.1.4 Taxonomies: Record Type & Fields

Under **Taxonomies**, click **+ Add Record Type** and then select **Add manually**.

![Workfront Planning](./images/wfpl7.png)

You should then see the **Add record type** popup.

![Workfront Planning](./images/wfpl8.png)

Update the following information on the **Appearance** tab:

- Replace **Untitled record type** by `Business Unit`.
- Description: `Defines which BU is leading campaign planning.`.
- Select a color and shape for the icon of your choice

Click **Save**.

![Workfront Planning](./images/wfpl9.png)

Click to open the newly created **Business Unit** record type.

![Workfront Planning](./images/wfpl10.png)

You'll now see an empty table view, because your newly created record type doesn't yet have any Business Unit records defined.

![Workfront Planning](./images/wfpl11.png)

Click the dropdown button on the field **Start Date** and then select **Delete**.

![Workfront Planning](./images/wfpl12.png)

Select **Delete**.

![Workfront Planning](./images/wfpl13.png)

Click the dropdown button on the field **End Date** and then select **Delete**.

![Workfront Planning](./images/wfpl14.png)

Select **Delete**.

![Workfront Planning](./images/wfpl15.png)

Next, click the **+** icon to add a new field. Scroll down in the list of available field types and select **People**.

![Workfront Planning](./images/wfpl16.png)

Set the **Name** of the field to `Business Unit Lead` and set the description of the field to `Business Unit Lead responsible for budget and resources (VP, Head).`

Click **Save**.

![Workfront Planning](./images/wfpl17.png)

Click the 3 dots **...** on the first record and select **View**.

![Workfront Planning](./images/wfpla1.png)

Set the **Name** to `Consumer Services`.

Set the **Description** to `Handles residential offerings like mobile plans, internet packages, and customer support.`.

Set the **Business Unit Lead** to yourself.

Once done, click the arrow to go back to the previous screen.

![Workfront Planning](./images/wfpla2.png)

Click the 3 dots **...** on the second record and select **View**.

![Workfront Planning](./images/wfpla3.png)

Set the **Name** to `Enterprise & Business Solutions`

Set the **Description** to `Provides connectivity, cloud, and managed services to corporate clients and government entities.`

Set the **Business Unit Lead** to yourself.

Once done, click the arrow to go back to the previous screen.

![Workfront Planning](./images/wfpla4.png)

Click the 3 dots **...** on the third record and select **View**.

![Workfront Planning](./images/wfpla5.png)

Set the **Name** to `Sales & Marketing`

Set the **Description** to `Drives customer acquisition, brand strategy, advertising, and market segmentation.`

Set the **Business Unit Lead** to yourself.

Once done, click the arrow to go back to the previous screen.

![Workfront Planning](./images/wfpla6.png)

You've now created a new record type, you both deleted and created fields and you creatd 3 Business Units. Go back to the Workspace overview screen by clicking the arrow in the top left corner.

![Workfront Planning](./images/wfpl18.png)

You should then see this.

![Workfront Planning](./images/wfpl19.png)

## 1.1.1.5 Operational Record Types: Fields

Click to open **Campaigns**.

![Workfront Planning](./images/wfpl20.png)

Click the **+** icon to create a new field. Select **New connection** and then select **Business Unit**.

![Workfront Planning](./images/wfpl21.png)

Leave the default settings in place. Click **Create**.

![Workfront Planning](./images/wfpl22.png)

Select **Skip**.

![Workfront Planning](./images/wfpl23.png)

Your new field is then shown in the table view.

![Workfront Planning](./images/wfpl24.png)

## 1.1.1.6 Create a Request Form

On the Campaigns overview screen, click the 3 dots **...** and then select **Create request form**.

![Workfront Planning](./images/wfpl25.png)

Change the name to `Campaign Request Form`. Click **Create**.

![Workfront Planning](./images/wfpl26.png)

At this moment, it's not required to make any changes to the form. You will use it without changes. First, click **Save** and then click **Publish**.

![Workfront Planning](./images/wfpl27.png)

Click the arrow in the top left corner to go back to the Request Forms overview screen.

![Workfront Planning](./images/wfpl28.png)

Click the arrow in the top left corner to go back to the Campaigns overview screen.

![Workfront Planning](./images/wfpl29.png)

## 1.1.1.7 Submit a new record using the Request Form

On the Campaigns overview screen, click **+ New Record**.

![Workfront Planning](./images/wfpl31.png)

Select **Submit a request** and click **Continue**.

![Workfront Planning](./images/wfpl32.png)

Set the **Subject** to `--aepUserLdap-- - New Campaign Creation Request`.

Set the **Campaign name** to `--aepUserLdap-- - CitiSignal Fiber Launch`.

Set the **Campaign summary** to:

```
The CitiSignal Fiber Launch campaign introduces CitiSignal’s flagship fiber internet service—CitiSignal Fiber Max—to key residential markets. This campaign is designed to build awareness, drive sign-ups, and establish CitiSignal as the go-to provider for ultra-fast, reliable, and future-ready internet. The campaign will highlight the product’s benefits for remote professionals, online gamers, and smart home families, using persona-driven messaging across digital and physical channels.
```

Fill in the other fields as you like.

Click **Submit request**.

![Workfront Planning](./images/wfpl33.png)

Click **X** to close the popup.

![Workfront Planning](./images/wfpl34.png)

You should then see the newly created campaign in the overview.

![Workfront Planning](./images/wfpl35.png)

## 1.1.1.8 Create Portfolio & Custom Form

In the next step, you'll create an automation that will take information from the campaign that you created in Workfront Planning and that will use that information in Workfront to create a program. Before you can create the automation, there are 2 things to configure in Workfront first: a portfolio and a custom form.

To create the portfolio, open the menu and click **Portfolios**.

![Workfront Planning](./images/wfplss1.png)

Click **+ New Portfolio**.

![Workfront Planning](./images/wfplss2.png)

Set the name of the portfolio to `--aepUserLdap-- - Marketing`.

![Workfront Planning](./images/wfplss3.png)

Next, open the menu and click **Setup** to create the custom form.

![Workfront Planning](./images/wfplss4.png)

In the left menu, go to **Custom Forms**, to **Forms** and then click **+ New custom form**.

![Workfront Planning](./images/wfplss5.png)

Select **Program** and click **Continue**.

![Workfront Planning](./images/wfplss6.png)

Change the name of the form to `--aepUserLdap-- - Program Information`.

![Workfront Planning](./images/wfplss7.png)

Next, go to **Field Library** and search for `budget`. Drag and drop the existing field **Budget** onto the form. 

Click **Apply**.

![Workfront Planning](./images/wfplss8.png)

Your custom form configuration has now been saved.

![Workfront Planning](./images/wfplss9.png)

## 1.1.1.8 Create an Automation

With the portfolio and the custom form created, you can now create the automation.

Click to open the menu and then select **Planning**.

![Workfront Planning](./images/wfpl36.png)

Click to open the workspace you created before, which is named `--aepUserLdap-- - Basic: Marketing Management`.

![Workfront Planning](./images/wfpl37.png)

Click to open **Campaigns**.

![Workfront Planning](./images/wfpl38.png)

On the Campaigns overview screen, click the 3 dots **...** and then select **Manage Automations**. 

![Workfront Planning](./images/wfpl40.png)

Click **New automation**.

![Workfront Planning](./images/wfpl41.png)

Set the name of the Automation to `Campaign to Program`.

Set the description to `This automation will convert a Planning Campaign record to a Workfront Program.`

Click **Save**.

![Workfront Planning](./images/wfpl42.png)

Set the **Action** to **Create program**. Click **+ Add connected field**.

![Workfront Planning](./images/wfpl43.png)

Select the **Program portfolio**: `--aepUserLdap-- - Marketing`.

Select this **Custom form**: `--aepUserLdap-- Program information`.

Click **Save**.

![Workfront Planning](./images/wfpl44.png)

You should then see this. Click the arrow to go back to the Campaigns overview screen.

![Workfront Planning](./images/wfpl45.png)

Check the checkbox in front of the campaign that you created earlier. Then, click the **Campaign to Program** automation.

![Workfront Planning](./images/wfpl46.png)

After a couple of seconds, you should see a confirmation that the automation finished successfully. This means that based on the Campaign object in Workfront Planning, a Program was created in Workfront.

![Workfront Planning](./images/wfpl47.png)

To check the Program in Workfront, scroll to the right and click the program in the **Connected Program** column.

![Workfront Planning](./images/wfpl48.png)

You should then see the program that was just created by the automation you configured.

![Workfront Planning](./images/wfpl50.png)

Next Step: [Summary & Benefits](./summary.md){target="_blank"}

Go Back to [Introduction to Workfront Planning](./wfplanning.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
