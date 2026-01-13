---
title: Foundation - Data Ingestion - Configure Schemas and Set Identifiers
description: Foundation - Data Ingestion - Configure Schemas and Set Identifiers
kt: 5342
doc-type: tutorial
exl-id: 3cc1fbe3-1f40-45a3-a123-ee6f1463e7b5
---
# 1.2.2 Configure Schemas and Set Identifiers

In this exercise, you'll review the configuration of the required XDM schemas to classify profile information and customer behavior. In every XDM schema, you'll also see that a primary identifier is defined to link all the customer-related information to.
 
## Story

Before you start configuring XDM Schema's and defining Identifiers, you need to think about the business context of what we're trying to do: 

- You want data
- You want to link data to a customer
- You want to build a progressive, Real-time Customer Profile

There are 2 types of data that we want to capture:

- Who is this customer?
- What does this customer do?

However, the question **Who is this customer?** is a very open question that has many answers. When your organisation wants to see this question answered, you're looking for demographic information like First Name, Last Name and Address. But also for contact information like an Email Address or a Mobile Phone Number. And also for information linked to Language, OptIn/OptOut and maybe even Profile Pictures. And finally, what you really need to know, is how we'll be identifying this customer in the various systems that your organisation uses.

The same thing goes for the question **What does this customer do?**. It's a very open question with many answers. When your organisation wants to see this question answered, you're looking for any interaction a customer has had with any of your online and offline properties. Which pages or products have been visited? Has this customer added a product to his cart or even purchased an item? What device and browser has been used to browse the website? What kind of information is this customer looking for and how can we use that to configure and deliver a delightful experience to this customer? And finally, what we really need to know, is how we'll be identifying this customer in the various systems that your organisation will use.

## Who is this customer

Capturing the answer to **Who is this customer?** for your organisation is done through the Login/Registration-page.

![Data Ingestion](./images/pv10.png)

From a Schema perspective, we look at this as a **Class**. The question: **Who is this customer?** is something that we define in the Class **[!UICONTROL XDM Individual Profile]**.

So when you create an XDM Schema to capture the answer to **Who is this customer?**, first of all, you'll need to create and define 1 schema that references the class **[!UICONTROL XDM Individual Profile]**.

To specify what kind of answers can be given to that question, you'll need to define [!UICONTROL Field Groups]. [!UICONTROL Field Groups] are extensions of the Profile-class, and have very specific configurations. For instance, demographic information like First Name, Last Name, Gender and Birthday are part of the [!UICONTROL Field Group]: **[!UICONTROL Demographic Details]**.

Secondly, your organisation needs to decide how to identify this customer. In the case of your organisation, the main identifier for a known customer might be a specific customer ID, like for instance an email address. But technically, there are other ways of identifying a customer at your organisation, like using a mobile phone number.
In this lab, we'll define the email address as the primary identifier and the phone number as a secondary identifier.

Lastly, it's important to distinguish the channel on which data was captured. In this case, we'll be talking about Website Registrations and the schema that needs to be defined needs to reflect **where** the registration data was captured. The channel will also have an important role in influencing what data is captured. As such, it's a best practice to define schema's for every combination of channel, primary identifier and type of data collected.

Based on the above, schema's were created in Adobe Experience Platform.

Log in to Adobe Experience Platform by going to this URL: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxName--``. After selecting the appropriate sandbox, you'll see the screen change and now you're in your dedicated sandbox.

![Data Ingestion](./images/sb1.png)

In Adobe Experience Platform, click on **[!UICONTROL Schemas]** in the menu on the left side of your screen. You'll see the list of available [!UICONTROL Schemas]. You should create a new schema. To create a new schema, click **[!UICONTROL + Create Schema]**.

![Data Ingestion](./images/menuschemas.png)

Select **Manual** and click **Select**.

![Data Ingestion](./images/createschemaa.png)

Next, select **Individual Profile** and click **Next**.

![Data Ingestion](./images/createschemab.png)

Enter the name of your schema like this: `--aepUserLdap-- - Demo System - Profile Schema for Website`. Click **Finish**.

![Data Ingestion](./images/createschemac.png)

A new schema is now created. 

![Data Ingestion](./images/emptyschema.png)

Now you need to define what an answer to the question **Who is this customer?** should look like.
In the introduction of this lab, we noted the need for following attributes to define a customer:

- Demographic information like First Name, Last Name and Address
- Contact information like a Home Address, Email Address or a Mobile Phone Number
- Other Information linked to Language, OptIn/OptOut and maybe even Profile Pictures. 
- Primary Identifier for a customer

To make that information part of your schema, you need to add the following [!UICONTROL Field Groups] to your schema:

- Demographic Details (Demographic Information)
- Personal Contact Details (Contact Information)
- Consent and Preference Details (Other Information)
- your organisation's custom Profile Identification Field Group (Primary and Secondary Identifiers)

Click the **+Add** button under **Field groups**.

![Data Ingestion](./images/createschemad.png)

In the **[!UICONTROL Add Field Group]** screen, select the [!UICONTROL Field Group] **[!UICONTROL Demographic Details]**, **[!UICONTROL Personal Contact Details]** and **[!UICONTROL Consent and Preference Details]**.

Click the **[!UICONTROL Add Field Groups]** button to add the [!UICONTROL Field Group] to your schema.

![Data Ingestion](./images/ppfd.png)

You'll now have this:

![Data Ingestion](./images/schemathis.png)

Next, you need a new [!UICONTROL Field Group] to capture the **[!UICONTROL Identifier]** used for data collection. As you've seen in the previous exercise, there's a concept of Identifiers. A Primary Identifier is the most important one, as all collected data will be linked to this Identifier.

You will now create your own custom [!UICONTROL Field Group] and as such, you'll be extending the [!UICONTROL XDM Schema] to meet your own organisation's requirements.

Click **[!UICONTROL + Add]** under **Field groups** to start adding a [!UICONTROL Field Group].

![Data Ingestion](./images/addmixin2.png)

Instead of reusing an existing [!UICONTROL Field Group], you'll now create your own [!UICONTROL Field Group]. You can do that by selecting **[!UICONTROL Create New Field Group]**.

![Data Ingestion](./images/createmixin.png)

You now need to provide a **[!UICONTROL Display Name]** and **[!UICONTROL Description]** for your new [!UICONTROL Field Group]. 

As the name for our schema, we'll use this:
`--aepUserLdap-- - Profile Identification Field Group`

Click the **[!UICONTROL Add Field Groups]** button to add the newly created [!UICONTROL Field Group] to your schema.

![Data Ingestion](./images/mixinname.png)

You now have this schema structure in place.

![Data Ingestion](./images/schemastructurem.png)

Your new [!UICONTROL Field Group] is still empty, so now you'll have to add fields to that [!UICONTROL Field Group].
In the [!UICONTROL Field Group]-list, click your custom [!UICONTROL Field Group].

![Data Ingestion](./images/schemastructurem.png)

You now see a number of new buttons appear.

At the top-level of your schema, click the **[!UICONTROL + Add Field]** button.

![Data Ingestion](./images/clickaddfield.png)

After clicking the **[!UICONTROL + Add Field]** button, you now see a new untitled field in your schema. 

![Data Ingestion](./images/tenantschema1.png)

You should now enter the information of this new field, using these object-definitions:

- Field name: **`--aepUserLdap--_identification`**
- Display name:  **`--aepUserLdap--_identification`**
- Type: **[!UICONTROL Object]**
- Field Group: **`--aepUserLdap-- - Profile Identification Field Group`**

Click **Apply**.

![Data Ingestion](./images/tenantfielddef.png)

You'll now see a new object in your schema, which represents a custom **[!UICONTROL object]** in the schema, and which is named after your Adobe Experience Platform Tenant ID. Your Adobe Experience Platform tenant id is `--aepTenantId--` and it is unique for every AEP instance.

![Data Ingestion](./images/tenant.png)

You'll now add a 3 new fields object under that tenant, in the **identification** object that you've just created. To start adding every single on of these 3 fields, click the **+-icon** under **identification** for every field.

![Data Ingestion](./images/tenantfield.png)

Use the below information to create those 3 new fields under the  **[!UICONTROL identification]** object:

- ecid:
  - Field name: **`--aepUserLdap--_ecid`**
  - Display name:  **`--aepUserLdap--_ecid`**
  - Type: **[!UICONTROL String]**
  - Field Group: **`--aepUserLdap-- - Profile Identification Field Group`**

- emailId
  - Field name: **`--aepUserLdap--_emailId`**
  - Display name:  **`--aepUserLdap--_emailId`**
  - Type: **[!UICONTROL String]**
  - Field Group: **`--aepUserLdap-- - Profile Identification Field Group`**
  
- mobilenr
  - Field name: **`--aepUserLdap--_mobilenr`**
  - Display name:  **`--aepUserLdap--_mobilenr`**
  - Type: **[!UICONTROL String]**
  - Field Group: **`--aepUserLdap-- - Profile Identification Field Group`**

This is how each field should look after your initial field configuration.

- `--aepUserLdap--_mobilenr`

![Data Ingestion](./images/mobilenrfield.png)

To save your field, scroll down in the **[!UICONTROL Field Properties]** until you see the button **[!UICONTROL Apply]**. Click the **[!UICONTROL Apply]** button.

![Data Ingestion](./images/apply.png)

- `--aepUserLdap--_ecid`

![Data Ingestion](./images/ecidfield.png)

Don't forget to scroll down and click **Apply**.

- `--aepUserLdap--_emailId`

![Data Ingestion](./images/emailidfield.png)

Don't forget to scroll down and click **Apply**.

Each field is defined as type **[!UICONTROL String]** and you'll now configure these fields as **[!UICONTROL Identities]**. For this schema, we assume that a customer will always be identified by their email-address, which means that you have to configure the field **[!UICONTROL emailId]** as a **[!UICONTROL primary]** identifier, and the other fields as normal identifiers.

Your 3 fields now have to be defined as **[!UICONTROL Identity]**-fields.

![Data Ingestion](./images/3fields.png)

To start defining these fields as **[!UICONTROL Identity]**-fields, follow these steps:

- Select the field **`--aepUserLdap--_emailId`**.
- On the right side, in the field properties, scroll down until you see **[!UICONTROL Identity]**. Check the checkbox for **[!UICONTROL Identity]**. 

![Data Ingestion](./images/emailidid.png)

- Now check the checkbox for **[!UICONTROL Primary Identity]**.

![Data Ingestion](./images/emailidprimid.png)
  
- Lastly, select the namespace **[!UICONTROL Email]** from the list of **[!UICONTROL Namespaces]**. A Namespace is used by the Identity Graph in Adobe Experience Platform to classify identifiers in namespaces and define the relationship between those namespaces. Click **[!UICONTROL Apply]** to save your changes.

![Data Ingestion](./images/emailidprimidns.png)
  
Next, you have to define the other fields for **`--aepUserLdap--_ecid`** and **`--aepUserLdap--_mobilenr`** as standard identifiers.

Select the field **`--aepUserLdap--_ecid`**. On the right side, in the field properties, scroll down until you see **[!UICONTROL Identity]**. Check the checkbox for **[!UICONTROL Identity]**. 
Next, select the namespace **[!UICONTROL ECID]** from the list of **[!UICONTROL Namespaces]**. 
Click **[!UICONTROL Apply]** to save your changes.

![Data Ingestion](./images/ecidid.png)

Select the field **`--aepUserLdap--_mobilenr`**. On the right side, in the field properties, scroll down until you see **[!UICONTROL Identity]**. Check the checkbox for **[!UICONTROL Identity]**. 
Select the namespace **[!UICONTROL Phone]** from the list of **[!UICONTROL Namespaces]**. 
Click **[!UICONTROL Apply]** to save your changes.

![Data Ingestion](./images/mobid.png)

The **[!UICONTROL identification]** object should now look like this, with the 3 id-fields now also showing a **[!UICONTROL fingerprint]** icon to show that they have been defined as identifiers.

![Data Ingestion](./images/applyiden.png)

Click **[!UICONTROL Save]** to save your changes.

![Data Ingestion](./images/saveschema.png)

The last thing to do here, is to activate the Schema to be linked to the **[!UICONTROL Profile]**.
By enabling your schema for Profile, you're making sure that all data sent to Adobe Experience Platform against this schema will be part of the Real-time Customer Profile environment, which makes sure that all that data can be used in real-time for querying, segmentation and activation.

To do this, select the name of your schema.

![Data Ingestion](./images/schemastructure.png)

In the right tab of your schema, click the **[!UICONTROL Profile toggle]**, which is currently deactivated.

![Data Ingestion](./images/upswitcherps.png)

Activate the [!UICONTROL Profile] - switch by clicking it.

Click **[!UICONTROL Enable]** to enable this schema for Profile.

![Data Ingestion](./images/sureps.png)

Your Schema is now configured to be part of the [!UICONTROL Real-time Customer Profile]. Click **[!UICONTROL Save]** to save your schema.

![Data Ingestion](./images/sureyps.png)

## What does this customer do?

Capturing the answer to the question **What does this customer do?** for your organisation is done through for instance a product view on a product page.

![Data Ingestion](./images/pv7.png)

From a schema perspective, we look at this as a **[!UICONTROL Class]**. The question: **What does this customer do?** is something that we've defined in the class **[!UICONTROL ExperienceEvent]**.

So when you create an [!UICONTROL XDM Schema] to capture the answer to **What does this customer do?**, first of all, you'll need to create and define 1 schema that references the class **[!UICONTROL ExperienceEvent]**.

To specify what kind of answers can be given to that question, you'll need to define [!UICONTROL Field Group]. [!UICONTROL Field Groups] are extensions of the [!UICONTROL ExperienceEvent] Class, and have very specific configurations. For instance, information about what kind of products a customer viewed or added to their cart is part of the [!UICONTROL Field Group] **Commerce Details**.

Secondly, your organisation needs to decide how you'll identify the behavior of this customer. Since we're talking about interactions on a website, it's possible that your organisation knows the customer but it's equally possible that an unknown, anonymous visitor is active on the website. So we can't use an identifier like email-address. In this case, your organisation will probably decide to use the [!UICONTROL Experience Cloud ID (ECID)] as the primary identifier.

Lastly, it's important to distinguish the channel on which data was captured. In this case, we'll be talking about Website Interactions and the schema that needs to be defined needs to reflect **where** the interaction data was captured. The channel will also have an important role in influencing what data is captured. As such, it's a best practice to define schema's for every combination of channel, primary identifier and type of data collected.

Based on the above, you'll need to configure a schema in Adobe Experience Platform.

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./images/home.png)

Before you continue, you need to select a **[!UICONTROL sandbox]**. The [!UICONTROL sandbox] to select is named ``--aepSandboxName--``. After selecting the appropriate sandbox, you'll see the screen change and now you're in your dedicated sandbox.

![Data Ingestion](./images/sb1.png)

In Adobe Experience Platform, click on **[!UICONTROL Schemas]** in the menu on the left side of your screen and go to **Browse**. You should create a new schema. To create a new schema, click on the button **[!UICONTROL + Create Schema]**.

![Data Ingestion](./images/menuschemas.png)

Select **Manual** and click **Select**.

![Data Ingestion](./images/createschema1.png)

Select **Experience Event** and click **Next**.

![Data Ingestion](./images/createschema1a.png)

Enter a name for the schema, like this: `--aepUserLdap-- - Demo System - Event Schema for Website`. Click **Finish**.

![Data Ingestion](./images/schemaname1ee.png)

A new schema is created and you can configure what data will be collected against it.

![Data Ingestion](./images/emptyschemaee.png)

Now you need to define what an answer to the question **What does this customer do?** should look like.
In the introduction of this lab, we noted the need for following attributes to define what a customer does:

- Which pages or products have been visited? 
- Has this customer added a product to their cart or even purchased an item? 
- What device and browser has been used to browse the website? 
- What kind of information is this customer looking for and how can we use that to configure and deliver a delightful experience to this customer?
- Primary Identifier for a customer


To make that information part of your schema, you need to add the following [!UICONTROL Field Group] to your schema:

- AEP Web SDK ExperienceEvent
- your organisation's custom Profile Identification [!UICONTROL Field Group] 

Click **+ Add** under **Field groups**.

![Data Ingestion](./images/eeedfg.png)

In the **[!UICONTROL Add Field Group]** screen, select the [!UICONTROL Field Group] **[!UICONTROL AEP Web SDK ExperienceEvent]**. Click **[!UICONTROL Add Field Groups]**.

![Data Ingestion](./images/eeed.png)

You'll then have this:

![Data Ingestion](./images/eethis.png)

Next, you need to create a new [!UICONTROL Field Group] to capture the **[!UICONTROL Identifier]** used for data collection. 

You will now create your own custom [!UICONTROL Field Group] and as such, you'll be extending the [!UICONTROL XDM Schema] to meet your own organisation's requirements.

A [!UICONTROL Field Group] is linked to a [!UICONTROL Class], so that means that you can't simply reuse the previously created [!UICONTROL Field Group].

Click the **[!UICONTROL + Add]** button to start adding a [!UICONTROL Field Group].

![Data Ingestion](./images/addmixinee2.png)

Instead of reusing an existing [!UICONTROL Field Group], you'll now create your own [!UICONTROL Field Group]. Select **[!UICONTROL Create New Field Group]** and enter the name for your Field Group, like this: `--aepUserLdap-- - ExperienceEvent Identification Field Group`. 
Click **Add field groups**

![Data Ingestion](./images/createmixineew.png)

You should now have this [!UICONTROL Schema] structure in place.

![Data Ingestion](./images/schemastructuremee.png)

Your new [!UICONTROL Field Group] is still empty, so now you'll have to add fields to that Field Group.
In the [!UICONTROL Field Group]-list, click your custom [!UICONTROL Field Group].

![Data Ingestion](./images/schemastructuremee1.png)

You now see a number of new buttons appear. 

On the top-level of your Schema, next to your Schema - name, click the **[!UICONTROL +]** button.

![Data Ingestion](./images/clickaddfieldee.png)

After clicking the **+** button, you now see a new untitled field in your schema. 

Use this to define your new field:

- Field name: **`--aepUserLdap--_identification`**
- Display name:  **`--aepUserLdap--_identification`**
- Type: **[!UICONTROL Object]**
- Field Group: `--aepUserLdap-- - ExperienceEvent Identification Field Group`

Click **Apply**.

![Data Ingestion](./images/tenantfielddefee.png)

Your new field is now created under your Adobe Experience Platform Tenant ID. Your Adobe Experience Platform tenant id is `--aepTenantId--`.

![Data Ingestion](./images/tenantee.png)

You'll now add 1 new field under the **[!UICONTROL identification]** object.

Click the **[!UICONTROL +]** button next to the **[!UICONTROL identification]** object to create a new field.

![Data Ingestion](./images/tenantfieldeewv.png)

The ECID-field will be defined as type **[!UICONTROL String]** and you'll configure this field as an **[!UICONTROL Identity]**. For the Schema **[!UICONTROL Demo System - Event Schema for Website]**, we assume that a customer will always be identified by their [!UICONTROL ECID], which means that you have to configure the field **[!UICONTROL ECID]** as a **primary** identifier

You now have an empty field. You need to configure the above field as indicated.

- ecid:

  - Field name: **`--aepUserLdap--_ecidweb`**
  - Display name:  **`--aepUserLdap--_ecidweb`**
  - Type: **[!UICONTROL String]**
  - Field Group: `--aepUserLdap-- - ExperienceEvent Identification Field Group`

This is how the `--aepUserLdap--_ecidweb`-field should look after your initial field configuration:

![Data Ingestion](./images/ecidfieldee.png)

Scroll down and click **[!UICONTROL Apply]**.

![Data Ingestion](./images/applywv.png)

You now have a new field, but this field hasn't been defined as an **[!UICONTROL Identity]**-field yet.

![Data Ingestion](./images/3fieldsee.png)

To start defining these fields as **[!UICONTROL Identity]**-fields, select the field **`--aepUserLdap--_ecidweb`**.
On the right side, in the field properties, scroll down until you see **[!UICONTROL Identity]**. Check the checkbox for **[!UICONTROL Identity]** and check the checkbox for **[!UICONTROL Primary Identity]**.
Select the namespace **[!UICONTROL ECID]** from the list of **[!UICONTROL Namespaces]**. 

Click **[!UICONTROL Apply]** to save your changes.

![Data Ingestion](./images/ecididee.png)

The **[!UICONTROL identification]** object should now look like this, with the ecid-field now also showing a **fingerprint** icon to show that they have been defined as identifiers. 
Click **[!UICONTROL Save]** to save your changes.

![Data Ingestion](./images/applyidenee.png)

It's important to note that when eventually ingesting data against this schema, that some fields are required.
For instance, the fields **[!UICONTROL _id]** and **[!UICONTROL timestamp]** are required fields, which is a requirement that is imposed by the ExperienceEvent Class.

- _id needs to contain a unique id for a specific data ingestion
- timestamp needs to be the timestamp of this hit, in the format **`"YYYY-MM-DDTHH:MM:SSSZ"`**, like for instance: **`"2024-11-18T07:20:000Z"`**

You have now defined a schema, linked existing and newly created [!UICONTROL Field Groups] and have defined identifiers.

The last thing to do here, is to activate the Schema to be linked to the **[!UICONTROL Profile]**.
By enabling your schema for [!UICONTROL Profile], you're making sure that all data sent to Adobe Experience Platform against this schema will be part of the Real-time Customer Profile, which makes sure that all that data can be used in real-time for querying, segmentation and activation.

To do this, click the name of your schema.

![Data Ingestion](./images/schemastructureeee.png)

In the right tab of your schema, you'll see a **[!UICONTROL Profile] toggle**, which is currently deactivated. Click the [!UICONTROL Profile] - switchto enable it.

![Data Ingestion](./images/upswitcheree.png)

You'll see this message. Click **[!UICONTROL Enable]** to enable this schema for Profile.

![Data Ingestion](./images/sureeewv.png)

Your schema is now configured to be part of the Real-time Customer Profile.

Click **[!UICONTROL Save]** to save your schema.

![Data Ingestion](./images/saveeewv.png)

You've now finished building schemas that are activated to be used in the Real-time Customer Profile.

Let's have a look at datasets in the next exercise.

Next Step: [1.2.3 Configure Datasets](./ex3.md)

[Go Back to Module 1.2](./data-ingestion.md)

[Go Back to All Modules](../../../overview.md)
