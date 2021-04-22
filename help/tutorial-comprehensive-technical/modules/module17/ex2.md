---
title: Connect Dynamics to Adobe Experience Platform via RTCDP and Journey Orchestration
description: Connect Dynamics to Adobe Experience Platform via RTCDP and Journey Orchestration
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 9172aa5b-dc60-44dd-ac33-bcf1557ccffb
---
# 17.2 Connect Dynamics to Adobe Experience Platform via RTCDP and Journey Orchestration

## 17.2.1 Update the Contact Entity in Microsoft Dynamics 365

Login to your Microsoft Dynamics 365 account. The URL of your Microsoft Dynamics 365 account looks like this: https://**NAME**.**REGION**.dynamics.com, for instance, [https://aepdemovangeluw1.crm4.dynamics.com/](https://aepdemovangeluw1.crm4.dynamics.com/).

You'll then see this. Click on **Dynamics 365 - custom**.

![iFrame](./images/azure21.png)

You'll then see this. Click the **gear** icon.

![iFrame](./images/azure22.png)

In the menu, click **Advanced Settings**.

![iFrame](./images/iframe-01.png)

A new browser tab will open. You'll see this.

![iFrame](./images/iframe-01a.png)

In the top menu, click **Settings**, then click **Customizations**.

![iFrame](./images/iframe-02.png)

Next, click **Customize the System**.

![iFrame](./images/iframe-03.png)

A new browser tab will open. In the left menu, click to expand **Entities**.

![iFrame](./images/iframe-04.png)

Scroll down to **Contact**. Click to expand **Contact**.

![iFrame](./images/iframe-04a.png)

Click **Forms**.

![iFrame](./images/iframe-05.png)

Click **Contact**.

![iFrame](./images/iframe-06.png)

A new browser tab will open to display the Contact Entity form fields.

![iFrame](./images/iframe-07.png)

In the panel **Contact Information** you'll add another field called **Sentiment**, right under the **Address** field.

Click **New Field**.

![iFrame](./images/newfield-01.png)

A new browser tab will appear.

![iFrame](./images/newfield-02.png)

Enter the following details:

- Display Name: **Sentiment**
- Data type: **Option Set**

You'll then have this:

![iFrame](./images/newfield-02a.png)

In the Options list, enter the below values. Click the green **+** icon.

| Label | Value |
|--- |--- |
| Neutral | 1 |
| Positive | 2 |
| Negative | 0 |

- Option: Neutral

  ![iFrame](./images/neutral.png)

  **NOTE** When entering a single digit into the Value field the following popup will appear. You can click OK to continue:

  ![iFrame](./images/newfield-031.png)

- Option: Positive

  ![iFrame](./images/positive.png)

  **NOTE** When entering a single digit into the Value field the following popup will appear. You can click OK to continue:

  ![iFrame](./images/newfield-031.png)

- Option: Negative

  ![iFrame](./images/negative.png)

  **NOTE** When entering a single digit into the Value field the following popup will appear. You can click OK to continue:

  ![iFrame](./images/newfield-031.png)

After adding the three option values, click **Save and Close**.

![iFrame](./images/newfield-04.png)

Go back to the Contact Entity Form. Click **Save**.

![iFrame](./images/newfield-04a.png)

Refresh the browser window.

After refreshing the browser window, go to the Field Explorer on the right and select **Custom Fields**.

You now see the new field called **Sentiment** in the list of Custom Fields.

![D365](./images/newfield-06.png)

Now drag your new field **Sentiment** from the Field Explorer window to below the **Address** field.

![D365](./images/newfield-addsentiment.gif)

Click **Save**.

![iFrame](./images/newfield-05.png)

This will take a few seconds and there will be no warning when completed.

Once your changes have been saved, click **Publish**.

![D365](./images/newfield-07.png)

This will take a few seconds. You will see the following message but there will be no warning when completed.

![D365](./images/newfield-08.png)

Once your changes have been published, you can now close this window.

You'll then be back here, close this window as well.

![D365](./images/newfield-09.png)

Return to your Microsoft Dynamics 365 dashboard.

In the left menu, click **Contact**. 

![D365](./images/cthome1.png)

You now see your list of Contacts. Click any contact to view the Contact record.

![D365](./images/cthome2.png)

You should see the new Sentiment field:

![D365](./images/newfield-incontact.png)

## 17.2.2 Connect Adobe Experience Platform to Microsoft Dynamics 365

Go to [Adobe Experience Platform](https://experience.adobe.com/platform/home).

![demo](./images/home.png)

In the left menu, go to Sources.

![demo](./images/sources1.png)

You'll then see the **Sources** homepage. In the **Sources** menu, click on **CRM**.

![demo](./images/sourceshome.png)

Click the **Microsoft Dynamics** card. Next, click on **+ Connect source**.

![Connect](./images/connect03.png)

From the Microsoft Dynamics account connection screen, click **New account**.

![Connect](./images/connect-newaccount.png)

Next, you have to enter your Microsoft Dynamics 365 details.

Enter your details like this:

| Key | Description| Example|
|--- |--- |--- |
| Account name | **ldap** AEP Demo Dynamics 365 Account| vangeluw AEP Demo Dynamics 365 Account| 
| Description | **ldap** AEP Demo Dynamics 365 Account | vangeluw AEP Demo Dynamics 365 Account| 
| serviceUri | https://**NAME**.**REGION**.dynamics.com/ | https://aepdemovangeluw1.crm4.dynamics.com/| 
| Username | The username you use to connect to Microsoft Dynamics 365| admin@aepdemovangeluw1.onmicrosoft.com| 
| Password | The password you use to connect to Microsoft Dynamics 365 | Password_1234| 

After filling out all the fields, click **Connect to source**.

![Connect](./images/connect04.png)

Wait for the connection to be made. When successful you should see:

![Connect](./images/connect05.png)

Click **Next**.

![Connect](./images/connect-next.png)

You now see this. The next step is to select the data from Microsoft Dynamics 365.

![Connect](./images/connect08a.png)

From the list of **Table Names**, you need to select **Contact**. Given that the list of **Table Names** isn't sorted in an alphabetical way, the best way to find **Contact** is to use the search functionality of your browser and search for the word **Contact**.

![Connect](./images/connect07a.png)

Here's the table name you need. Select **Contact**, and after a couple of seconds you should see a preview of the table on the right side of your screen.

![Connect](./images/connect07.png)

Click **Next**.

![Connect](./images/connect-next.png)

You'll now see this. Next, you'll need to setup the mapping between the Microsoft Dynamics 365 fields and Adobe Experience Platform's Experience Data Model (XDM).

![Connect](./images/connect08.png)

For this exercise, a dataset has already been created. Click **Existing dataset**.

Next, click the **database** icon.

![Connect](./images/contact-existingdataset.png)

Search and select the **AEP Demo - MSFT Dynamics Profile** dataset.

![Connect](./images/contact-existingdataset-db.png)

Click **Confirm**.

![Connect](./images/connect-confirm.png)

You now need to map the fields in the Contacts Entity in Microsoft Dynamics 365 to the **AEP Demo - MSFT Dynamics Profile Schema** in Adobe Experience Platform.

First, click **Clear all mappings** as you don't need to map all the fields.

![Connect](./images/connect-clearmappings.png)

Next, you need to add the following seven fields from the **Contact** table and map then with the schema for your selected dataset.

For each of the required mappings, click the **Add new mapping** button.

![Connect](./images/connect-clearmappings1.png)

| Source Field | Target Field|
|--- |--- |
| contactid |--aepTenantId--.identification.crmId|
| emailaddress1 |--aepTenantId--.identification.emailId|
| emailaddress1 |personalEmail.address|
| firstname |person.name.firstName|
| lastname |person.name.lastName|
| birthdate |person.birthDate|
| mobilephone |mobilePhone.number|
| new_sentiment |--aepTenantId--.sentiment.sentiment|

Your final mapping should look like:

![Connect](./images/connect-mapping-list.png)

If your mapping looks like the above screenshot, click **Next**.

![Connect](./images/connect-next.png)

Next, you need to setup the **Scheduling**.

Define the following fields like this:

- Set **Frequency** to every 15 minutes.
- Set **Load incremental data by** to **modifiedon**.

![Connect](./images/connect-modifiedon.png)

Click **Next**.

![Connect](./images/connect-next.png)

Now you will need to name your **Flow**.

Set the **Dataflow name** to: **ldap Dynamics Contact Dataflow**. For instance, in this example, the Dataflow Name should be **vangeluw Dynamics Contact Dataflow**.

![Connect](./images/connect-dataset.png)

Click **Next**.

![Connect](./images/connect-next.png)

Review your configuration

![D365](./images/connect-review.png)

Click **Finish**.

![Connect](./images/connect-finish.png)

After clicking Finish, you'll see this:

![Connect](./images/connect-finish1.png)

Once you click on finish, it may take up to ~15 minutes to ingest the data from Microsoft Dynamics 365 into the **AEP Demo - MSFT Dynamics Profile** dataset in Adobe Experience Platform. 

Next Step: [17.3 Create a Contact in Microsoft Dynamics 365 using Journey Orchestration & Import data from Microsoft Dynamics](./ex3.md)

[Go Back to Module 17](./adobe-experience-platform-microsoft-dynamics-365.md)

[Go Back to All Modules](./../../overview.md)
