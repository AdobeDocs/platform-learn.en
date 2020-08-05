---
title: Model data into schemas | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
description: 
feature: data ingestion
topics: 
kt: 4348
audience: data architect,data engineer
doc-type: tutorial
activity: implement
---

# Model Data in Schemas

Standardization and interoperability are key concepts behind Adobe Experience Platform. Experience Data Model (XDM), driven by Adobe, is an effort to standardize customer experience data and define schemas for customer experience management.

XDM is a publicly documented specification designed to improve the power of digital experiences. It provides common structures and definitions for any application to use to communicate with Platform services. By adhering to XDM standards, all customer experience data can be incorporated into a common representation that can deliver insights in a faster, more integrated way. You can gain valuable insights from customer actions, define customer audiences through segments, and express customer attributes for personalization purposes.

XDM is the foundational framework that allows Adobe Experience Cloud, powered by Experience Platform, to deliver the right message to the right person, on the right channel, at exactly the right moment. The methodology on which Experience Platform is built, **XDM System**, operationalizes Experience Data Model schemas for use by Platform services.

<!--
This seems too lengthy. The video should suffice

Key terms:

* **Schema**: a representation of your data. A schema is comprised of a class and optional mixins and is used to create datasets. A schema includes behavioral attributes, timestamp, identity, attribute definitions, and relationships.
* **XDM Profile Class**: a common schema class used to represent record data
* **XDM ExperienceEvent Class**: a common schema class used to reporesent time-series data
* **Mixin**: allows users to extend reusable fields that contain variables defining one or more attribute intended to be included in a schema or added to a class.
* **Standard Mixin**: an open-source Mixin built to conform to common industry standards, used to accelerate implementation and support repeatable services operating on the data
* **Data type**: a reusable object with properties in a hierarchical representation. These can be standard types or custom-defined defined types to describe your own data in your own way (for example, a collection of fields that you use to describe your products). Unlike Mixins, data types can be used in schemas regardless of the class.
* **Field**: a field is the lowest level element of a schema. Each field has a name for referencing and a type to identify the type of data that it contains. Field types can include, integer, number, string, Boolean and schema.
-->

First, watch this short video to learn more about schemas and the Experience Data Model (XDM):
>[!VIDEO](https://video.tv.adobe.com/v/27105?quality=12&learn=on)


## Permissions required

In the [Configure Permissions](configure-permissions.md) lesson, you setup all the access controls you need to complete this lesson, specifically:

* Permission item **[!UICONTROL Data Modeling]** > **[!UICONTROL View Schemas]**
* Permission item **[!UICONTROL Data Modeling]** > **[!UICONTROL Manage Schemas]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
* Developer-role access to the `Luma Tutorial Platform` product profile (for API)



## Luma's goals

## Create Luma Loyalty Schema via UI

In this exercise we will create a Luma Loyalty Schema to ingest loyalty data of customers.

1. Go to Platform UI and ensure your sandbox is selected.
1. Go to **[!UICONTROL Schemas]** in the left navigation
1. Click the **[!UICONTROL Create Schema]** button on the top right
1. From the dropdown menu, select **[!UICONTROL XDM Individual Profile]**
  ![Schema with OOTB Mixin](assets/schemas-loyaltyCreateSchema.png)

1. In **[!UICONTROL Schema Properties]**, on the right-hand side of the screen, enter **[!UICONTROL Display Name]** `Luma Loyalty Schema`

### Add standard mixins

Fields are added to schemas by adding mixins. You can choose from a large set of industry-standard mixins provided by Adobe or create your own. As you start modeling your own data in Experience Platform, it is good to become familiar with the industry-standard mixins provided by Adobe. Whenever possible, it is a best-practice to use them as they sometimes power downstream services, such as Customer AI, Attribution AI, Adobe Analytics, etc.

To add mixins:

1. On the left side of the schema editor, in the **[!UICONTROL Mixin]** section, click the **[!UICONTROL Add]** button:
   
    ![Add Mixin](assets/schemas-loyalty-addMixin.png)

1. In the **[!UICONTROL Mixins]** section, select following mixins
   1. **[!UICONTROL Profile Personal Details]**
   1. **[!UICONTROL Profile Person Details]**
1. Note that you can preview the fields in the mixin by clicking the icon on the right side of the row. 
1. Click **[!UICONTROL Save]** to save the schema.
    ![Add out-of-the-box mixins to loyalty schema](assets/schemas-loyalty-saveOotbMixins.png)


Now take some time to explore the current state of the schema. Note that these two mixins have added standard fields related to a person and their contact details. You may find these two mixins very useful when you create schemas for your own company's data. See how the visualization happens when you click a specific mixin row or check the box next to the mixin name. 

![Schema with OOTB Mixin](assets/schemas-loyalty-mixins.png)

>[!NOTE]
>
>It is okay if a mixin adds a field for a data point that you are not going to upload during the ingestion process. For example, "faxPhone" might be a field for which Luma doesn't collect data. That's fine. Just because a field is defined in the schema doesn't mean that data for it *needs* to be ingested later on.

### Add custom mixins

Next we need to add fields that are specific to Luma's Loyalty system and which don't exist in any standard mixins. For that you can create your own mixins.

1. In the **Mixins** section of the schema editor, click the **[!UICONTROL Add]** button
1.  Select **[!UICONTROL Create new mixin]** radio button
1.  Enter the Display name as `Luma Loyalty Details` and click the **[!UICONTROL Add mixin]** button
    ![Add Field To Mixin](assets/schemas-loyalty-addCustomMixin.png)
1.  In the **Mixins** section of the schema editor, select the newly created mixin
1.  In **[!UICONTROL Structure]** section, click **[!UICONTROL Add field]** at top level in structure of Schema. It will create an object with your tenant id and a field '_New field_'.

1. In Field Properties section, enter the following
   1. Field Name: `loyalty`
   1. Display Name: `Loyalty`
   1. Type: **[!UICONTROL Object]**
1.  Click **[!UICONTROL Apply]** to add the field

    ![Add Field To Mixin](assets/schemas-loyalty-customMixin.png)

1.  Select the newly created `loyalty` object and click **[!UICONTROL Add Field]** button next to it to add a field within the object
1.  Create a field with following values
       1. Field Name: `memberSince`
       1. Display Name: `Member Since`
       1. Type: **[!UICONTROL Date]**

1.  Repeat Step 8 and 9 to add two more fields within the `loyalty` object:
    1.  Points
           1. Field Name : `points`
           1. Display Name : `Points`
           1. Type : **[!UICONTROL Integer]**
           1. Default : 0
    1. Level
       1. Field Name : `level`
       1. Display Name : `Level`
       1. Type : **[!UICONTROL String]**
       1. Enum: Checked, with the following enum values:
            | Value              |  Label    |  
            |-------------------|-----------|
            | bronze            | Bronze    | 
            |   silver            | Silver    |  
            | gold              | Gold      |  
            | platinum          | Platinum  |  

   
1. Click **[!UICONTROL Save]** to save the current state of your schema, which should look like this:

    ![Loyalty Mixin Complete](assets/schemas-loyaltyMixinComplete.png) 

Now we will create another mixin to contain the loyaltyId field, as well as other identifiers which we will use in the other schemas. Since you are now familiar with how to create mixins in the interface, create one named `Identity Profile Mixin` with an object called `systemIdentifier` containing the following fields *all of type 'string'*:

   1. loyaltyId
   1. crmId
   1. emailId
   1. mobileNumberId

Your new mixin should look like this. Click the **[!UICONTROL Save]** button to save your changes, but leave the schema open 
    ![Loyalty Mixin Complete](assets/schemas-loyalty-identityMixinComplete.png) 


## Create a data type

Custom mixins, such as your new `Luma Loyalty Details Mixin`, can be reused in other schemas, allowing you to enforce standard data definitions for fields used in multiple systems. Mixins however can only be reused _in other schemas that share the same class_, in this case the XDM Profile Class.

The data type is another multi-field construct which can be reused in schemas _across multiple classes_. Let's convert our new `systemIdentifier` object into a new data type:

With the `Luma Loyalty Schema` still open, select the `systemIdentifier` object and click the **[!UICONTROL Convert to new data type]**

![Loyalty Mixin Complete](assets/schemas-loyalty-convertToDataType.png) 

If this doesn't make sense now, it will by the end of the lesson. 


## Create Luma CRM Schema via API

Now we will create a schema using the API. 

First we need to create the schema:

1. Open Postman
1. If you haven't made a call in a while, your authorization tokens have probably expired. Open the call **[!DNL Adobe I/O Access Token Generation > Local Signing (Non-production use-only) > IMS: JWT Generate + Auth via User Token]** and click **Send** to request new JWT and Access Tokens, just like you did in the Postman lesson.
1. Open your environment variables and change the value of **CONTAINER_ID** from global to tenant
1. Open the call **[!DNL Schema Registry API > Schemas > Create a new tenant-defined schema]**
1. Open the Body tab and paste the following code and click **Send** to make the API call. This will create a new schema using the same `XDM Individual Profile` base class that was used in the Loyalty schema:

    ```json
    {
    "type": "object",
    "title": "Luma CRM Schema",
    "description": "Schema for CRM data of Luma Retail ",
    "allOf": [
      {
        "$ref": "https://ns.adobe.com/xdm/context/profile"
      }
      ]
    }
    ```

1. You should get a "201 Created" response
1. Copy `meta:altId` from Response body. We will use it later in exercise.
  ![Create the CRM schema](assets/schemas-crm-createSchemaCall.png) 

1. The new schema should be visible in the UI but without any mixins
  ![Create the CRM schema](assets/schemas-loyalty-emptySchemaInTheUI.png) 

>[!NOTE]
>
> The `meta:altId` value can be obtained from the URL when the schema is open in the interface or by making the API request **[!DNL Schema Registry API > Schemas > List all schemas within the specified container.]** in the tenant container.

>[!TIP]
>
> Common issues making this call:
>
> 1. No auth token: Run the **IMS: JWT Generate + Auth via User Token** call to generate new tokens
> 1. `401: Not Authorized to PUT/POST/PATCH/DELETE for this path : /global/schemas/`: Update the **CONTAINER_ID** environment variable from `global` to `tenant`
> 1. `403: PALM Access Denied. POST access is denied for this resource from access control`: Verify your user permission in the Admin Console

### Add standard mixins

Now it's time to add the mixins to the schema:

1. In Postman, open the call **[!DNL Schema Registry API > Schemas > Modify or update part of a tenant-defined schema]**
1. In the **Params** tab, paste the `meta:altId` value from the previous response as the `$id`
1. Open the Body tab and paste the following code and click **Send** to make the API call. This will add the three standard mixins to your `Luma CRM` schema:

    ```json
    [
      { 
        "op": "add",
        "path": "/allOf/-",
        "value":  
        {
          "$ref": "https://ns.adobe.com/xdm/context/profile-personal-details"
          }
        },
        { 
          "op": "add",
          "path": "/allOf/-",
          "value":  
          {
            "$ref": "https://ns.adobe.com/xdm/context/profile-person-details"
          }
        },
        { "op": "add",
        "path": "/allOf/-",
        "value":  
          {
          "$ref": "https://ns.adobe.com/xdm/context/profile-preferences-details"
          }
        }
    ]
    ```

1. You should get a 200 OK status for the response and the mixins should be visible as part of your schema in the UI

### Add custom mixin

Now let's add our Identity Profile Mixin to the schema. Looking at the Body of the request from our last call, how do we know what `$ref` value to use?

1. Open the call **[!DNL Schema Registry API > Schemas > Return a list of all mixins within the specified container.]**
1. In the **Headers** tab, update the **Accept** header to `application/vnd.adobe.xed-id+json`
1. Click the **Send** button
1. Grab the `$id` value (which will be different from this screenshot)
  ![Retrieve the list of mixins](assets/schemas-crm-getListOfMixins.png) 

Now see if you can modify the request Body from the request used to add the standard mixins to add the Identity Profile Mixin. It should look something like this (with a different `$ref` value)
  ![Retrieve the list of mixins](assets/schemas-crm-addIdentityMixin.png) 

Verify that the mixin has been added to the schema by checking the UI or, for bonus points, see if you can figure out how to list the mixins in the schema using the **[!DNL Lookup a specific schema by its unique ID]** call in the Postman collection.

## Exercise: Add Offline Purchase Event Schema


Now we have required datatype and custom mixin available, we will now create **Luma Offline Purchase Schema** based on **XDM ExperienceEvent** class.

1. Go to Platform UI and ensure your sandbox is selected.
1. Go to **[!UICONTROL Schemas]** in the left navigation
1. Click the **[!UICONTROL Create Schema]** button on the top right
1. From the dropdown menu, select **[!UICONTROL XDM ExperienceEvent]**
1. In **[!UICONTROL Schema Properties]**, on the right-hand side of the screen, enter **[!UICONTROL Display Name]** `Luma Offline Purchase Event Schema`
1. Save it and review the difference in base structure, Notice _id and timestamp are required fields in experience event class.

    ![Experience Event Base Structure](assets/schemas-offlinePurchase-experienceEventbase.png)


### Add Mixins and Fields

#### Adding Luma Identities Mixin

1. Go to Mixins section, and click Add button.
1. Search for **Identity Profile Mixin**. Note that it is not available because our new schema has a different base class. We will add a new mixin for the ExperienceEvent class that contains the same identity fields via our data type
1. Select **[!UICONTROL Create new mixin]** radio button
1. Enter the Display name as `Identity ExperienceEvent Mixin` and click the **[!UICONTROL Add mixin]** button`
1. In the **Mixins** section of the schema editor, select the newly created mixin
1. In **[!UICONTROL Structure]** section, click **[!UICONTROL Add field]** at top level in structure of Schema.
1. Enter `systemIdentifier` as the **[!UICONTROL Field Name]**
1. Enter `System Identifier` as the **[!UICONTROL Display Name]**
1. Select **System Identifier** as the **[!UICONTROL Type]**
1. Click the **[!UICONTROL Apply]** button 
1. Click the **[!UICONTROL Save]** button to save your schema

Note how the data type added all of the fields!

![Add the data type to the mixin](assets/schemas-offlinePurchases-addDatatype.png)

##### Adding Luma Purchase Event Mixin

1. Now we will create another mixin for Purchase Event.
1. Add Mixin > Create New Mixin
1. Provide Label **Luma Product Purchase Event Mixin** and click **Add mixin**
1. Select **Luma Product Purchase Event Mixin** and click **Add Field** icon at top of Schema Structure to add field.
1. Provide following details in field properties

| Field         |  Value          |  
|---------------|-----------------|
| Field Name    | purchase_event  | 
| Display name  | Purchase Event  |  
| Type          | Object          | 


1. Select **purchase_event** object and click **Add Field** icon to add following fields one by one.

**Receipt Number**

| Field         |  Value          |  
|---------------|-----------------|
| Field Name    | receipt_number  | 
| Display name  | Receipt Number  |  
| Type          | String          | 
| Required      | Check           | 


**Receipt Date**

| Field         |  Value          |  
|---------------|-----------------|
| Field Name    | receipt_date    | 
| Display name  | Receipt Date    |  
| Type          | DateTime        | 
| Required      | Check           | 


**Products**

| Field         |  Value             |  
|---------------|--------------------|
| Field Name    | products           | 
| Display name  | Purchased products |  
| Type          | Luma Product Item | 
| Array         | Check              | 


**Receipt Total**

| Field         |  Value          |  
|---------------|-----------------|
| Field Name    | receipt_total    | 
| Display name  | Receipt Total   |  
| Type          | Double          | 


#### Verify Final Schema

Click Apply and Save and your schema should look like following

![Experience Event Final Structure](assets/schemas-offlinePurchase-experienceEventFinalSchema.png)

## Add Web Event Schema

Now we are going to add one more schema for Luma's website data. By this point you should be an expert creating schema. I will keep the 

| Property         |  Value          |  
|---------------|-----------------|
| Schema Name    | Luma Web Events    | 
| Class  | XDM ExperienceEvent   |  
| Mixin          | AEP Web SDK          | 
| Mixin          | AEP Web SDK          | 

Luma Identities Mixin ( Custom Mixin)
Profile Personal Details
Profile Person Details
Profile Preferences Details

Schemas

* Luma Loyalty Members (UI)
  * Profile Person Details
  * Profile Personal Details
  * Custom Luma Loyalty Mixin
    * loyaltyId primary Id from data type
    * level
    * points
    * memberSince
  * Create Identity data type
* Luma CRM (API)
* Luma Web Events (UI)
  * AEP Web SDK Mixin
  * Commerce Mixin
* Luma Offline Purchases (API)
* Create Class
* Luma Products
* Relationship schema


## Create an Event-based Schema

In this tutorial we will be ingesting data from the following sources:

Abhishek

* Schema: Luma Loyalty Members
  * Profile Personal Details
  * Profile Person Details
  * Custom Mixin
    * loyalty object
    * loyaltyId
    * joiningDate
    * points
    * loyaltyLevel
* Data Type - Luma Product Item
  * productSKU
  * productName
  * productPrice
  * quantityPurchased
  * productTotal
  * productSize
* Mixin with API-- Luma Identities
* Schema: Luma Offline Purchase Event
  * Luma Identities
  * Luma Product Purchase Event Mixin
    * purchase_event
    * receipt_number
    * receipt_date
    * products (uses Luma Product Item data type)
    * receipt_total
* Schema with Custom Class: 
  * Schema: Luma Product Catalog
  * Custom Class: Luma Product Class
  * productName
  * productCategory
  * productColor
  * productSku
  * productSize
* Schema with API
  * CRM Schema
    * Luma Identities Mixin
    * Profile Personal Details
    * Profile Person Details
    * Profile Preferences Details


DMA

* CRM Schema
  * Profile work details
  * Profile person details
  * Profile personal details
  * Custom Identity Mixin
    * crmid
    * declaredId
    * emailId
    * phoneNbr
* Loyalty Schema
  * Custom Identity Mixin
    * add loyaltyId
  * Custom Loyalty Mixin
    * lifeTimeValue
    * loyaltyExpDate
    * loyaltyPoints
    * loyaltyStatus
* Offline Purchase Schema
  * SKU
  * Product Name
  * Price
  * Quantity
  * priceTotal
  * currencyCode
  * loyaltyId
  * receipt_nbr
  * Order Date
  * timestamp

* Website
* CRM system
* Loyalty system
* Offline purchases

We'll be starting with the CRM schema because we can build it quickly using a few standard mixins. For Luma, the fields they want to onboard into Platform from their own CRM system are:
Id
crmId
person_first_name
person_last_name
birthdate
gender
work_country
work_countryCode
work_postalCode
work_Street
work_email
home_address_city
home_address_country
home_address_country_code
home_address_country_street
home_address_country_label
home_address_country_state
home_phone
mobile_phone
personalEmail
As you go through these steps, see if you can determine which CRM fields match to which XDM fields.

### Relationship schemas

Firstly we need to establish relationship between **Luma Offline Purchase Event** schema with **Luma Product Catalog** Schema

1. Go to **Luma Offline Purchase Event**
1. Select **Luma Offline Purchase Event** mixin
1. Navigate to **_tenant > purchase_event > products** 
1. Select **productSku**
1. In field properties, mark checkbox for **Relationship**
1. In **Reference Schema** , Select **Luma Product Catalog**
1. **Reference identity namespace** will be automatically selected as **lumaProductSKU**
   ![Product Relationship](assets/segment-productRelationship.png)
1. Apply & Save.
1. Now go back to **Luma Offline Purchase Event** dataset and re-ingest data

## Additional Resources

* [Experience Data Model (XDM) System documentation](https://docs.adobe.com/content/help/en/experience-platform/xdm/home.html)
* [Schema Registry API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/schema-registry.yaml)