# Exercise 2 - Configure Schemas and Set Identifiers

In this exercise, you'll configure the required XDM schemas to classify profile information and customer behavior. In every XDM schema, you'll also have to configure a primary identifier to link all the information to.

The URL to login to Adobe Experience Platform is: [https://platform.adobe.com](https://platform.adobe.com)

## Story

Before you start configuring XDM Schema's and setting Primary Identifiers, we need to think about the business context of what we're trying to do:

* We Want Data
* We Want to Link Data to a Customer
* We Want to Build a Progressive, Unified Profile

There are 2 types of data that we want to capture:

* Who is this customer?
* What does this customer do?

However, the question ```Who is this customer?``` is a very open question that has many answers. When your company wants to see this question answered, you're looking for demographic information like First Name, Last Name and Address. But also for contact information like an Email Address or a Mobile Phone Number. And also for information linked to Language, OptIn/OptOut and maybe even Profile Pictures. And finally, what you really need to know, is how we'll be identifying this customer in the various systems that your company uses.

The same thing goes for the question ```What does this customer do?```. It's a very open question with many answers. When your company wants to see this question answered, you're looking for any interaction a customer has has had with any of your online and offline properties. Which pages or products have been visited? Has this customer added a product to his cart or even purchased an item? What device and browser has been used to browse the website? What kind of information is this customer looking for and how can we use that to configure and deliver a delightful experience to this customer? And finally, what we really need to know, is how we'll be identifying this customer in the various systems that your company will use.

## Exercise 1.1 - Who is this customer?

Capturing the answer to ```Who is this customer?``` for your company is done through the Login/Registration-page.

![Data Ingestion](./images/lb_register_dtl.png)

From a Schema perspective, we look at this as a ``Class``. The question: ```Who is this customer?```is something that we define in the Class ``XDM Individual Profile``.

So when you create an XDM Schema to capture the answer to ```Who is this customer?```, first of all, you'll need to create and define 1 schema that references the class ``XDM Individual Profile``.

To specify what kind of answers can be given to that question, you'll need to define Mixins. Mixins are extensions of the Profile-class, and have very specific configurations. For instance, demographic information like First Name, Last Name, Gender and Birthday are part of the Mixin: ```Profile Person Details```.

Secondly, your company needs to decide how to identify this customer. In the case of your company, the main identifier for a known customer might be a specific customer ID, like for instance an email address. But technically, there are other ways of identifying a customer at your company, like using a mobile phone number.
In this lab, we'll define the email address as the primary identifier and the phone number as a secondary identifier.

Lastly, it's important to distinguish the channel on which data was captured. In this case, we'll be talking about Website Registrations and the schema that needs to be defined needs to reflect ```Where``` the registration data was captured. The channel will also have an important role in influencing what data is captured. As such, it's a best practice to define schema's for every combination of channel, primary identifier and type of data collected.

Based on the above, you'll need to configure a Schema in Adobe Experience Platform.

Log in to Adobe Experience Platform by going to this URL: [https://platform.adobe.com](https://platform.adobe.com).

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./images/home.png)

Before you continue, you need to select your own ``Sandbox``. You can do this by clicking the text ``Production Prod (VA7)`` in the blue line on top of your screen.

![Data Ingestion](./images/sb1.png)

From the list of available sandboxes, select the sandbox that matches the number you've been assigned.

After selecting the appropriate sandbox, you'll see the screen change and now you're in your dedicated sandbox.

![Data Ingestion](./images/sb2.png)

In Adobe Experience Platform, click on ```Schemas```in the menu on the left side of your screen.

![Data Ingestion](./images/menuschemas.png)

Your list of Schemas is currently empty.

![Data Ingestion](./images/schemas.png)

You should create a new schema. To create a new schema, click on the button ```+ Create Schema```.

![Data Ingestion](./images/createschema.png)

After clicking the ```+ Create Schema```button, you'll see an empty, new schema.

![Data Ingestion](./images/emptyschema.png)

Let's first name your schema.

As the name for our schema, we'll use this:
**AEP Demo - Website Registrations Schema**

That should give you something like this:

![Data Ingestion](./images/schemaname.png)

Next, you need to select the class of your schema. As indicated before, the class of your schema should be ``XDM Individual Profile``.

Click on the button ```+ Assign```

![Data Ingestion](./images/assign.png)

In the ```Assign Class```-window, select ```XDM Individual Profile```.

![Data Ingestion](./images/XDMProfile.png)

Click the ```Assign Class```-button to assign the class.

![Data Ingestion](./images/assignclass.png)

You'll now see an overview of the minimal structure of your schema.

![Data Ingestion](./images/classoverview.png)

It's important to note that when eventually ingesting data against this schema, that some fields are required.
For instance, the field ```_id``` is a required field.

* _id needs to contain a unique id for a specific data ingestion

Now you need to define what an answer to the question ```Who is this customer?``` should look like.
In the introduction of this lab, we noted the need for following attributes to define a customer:

* Demographic information like First Name, Last Name and Address
* Contact information like a Home Address, Email Address or a Mobile Phone Number
* Other Information linked to Language, OptIn/OptOut and maybe even Profile Pictures.
* Primary Identifier for a customer

To make that information part of your schema, you need to add the following Mixins to your schema:

* Profile Person Details (Demographic Information)
* Profile Personal Details (Contact Information)
* Profile Preferences Details (Other Information)
* your company's custom Profile Identification Mixin (Primary and Secondary Identifiers)

You can add these Mixins by clicking the ```+ Add```-button below the Class that you just defined.

![Data Ingestion](./images/addmixin.png)

Let's start with **Profile Person Details**.

Click the ```+ Add```-button to start adding a Mixin.

In the ``Add Mixin``-screen, select the Mixin ```Profile Person Details```.

![Data Ingestion](./images/ppd.png)

Click the ``Add Mixin``-button to add the Mixin to your schema.

![Data Ingestion](./images/addmixin1.png)

Next, add the Mixin **Profile Personal Details**.

Click the ```+ Add```-button to start adding a Mixin.

In the ``Add Mixin``-screen, select the Mixin ```Profile Personal Details```.

![Data Ingestion](./images/ppsd.png)

Click the ```Add Mixin```-button to add the Mixin to your schema.

![Data Ingestion](./images/addmixin1.png)

Next, add the Mixin **Profile Preferences Details**.

Click the ```+ Add```-button to start adding a Mixin.

In the ``Add Mixin``-screen, select the Mixin ```Profile Preferences Details```.

![Data Ingestion](./images/ppfd.png)

Click the ```Add Mixin```-button to add the Mixin to your schema.

![Data Ingestion](./images/addmixin1.png)

Lastly, you need a new Mixin to capture the ``Identifier`` used for data collection. As you've seen in the previous exercise, there's a concept of Primary and Secondary Identifiers. A Primary Identifier is the most important one, as all collected data will be linked to this Identifier.

You will now create your own custom Mixin and as such, you'll be extending the XDM Schema to meet your own company's requirements.

Click the ```+ Add```-button to start adding a Mixin.

![Data Ingestion](./images/addmixin.png)

Instead of reusing an existing Mixin, you'll now create your own Mixin. You can do that by selecting ``Create New Mixin``.

![Data Ingestion](./images/createmixin.png)

You now need to provide a ``Display Name`` and ``Description`` for your new Mixin.

As the name for our schema, we'll use this:
**AEP Demo - Profile Identification Mixin**

That should give you something like this:

![Data Ingestion](./images/mixinname.png)

Click the ```Add Mixin```-button to add the newly created Mixin to your schema.

![Data Ingestion](./images/addmixin1.png)

You should now have this Schema structure in place.

![Data Ingestion](./images/schemastructurem.png)

Your new Mixin is still empty, so now you'll have to add fields to that Mixin.
In the Mixins-list, click your custom Mixin.

![Data Ingestion](./images/mixinselected.png)

You now see a number of new buttons appear. These buttons are named ``+ Add Field``.

On the top-level of your Schema, next to your Schema - name, click the ``+ Add Field``-button.

![Data Ingestion](./images/clickaddfield.png)

After clicking the ``+ Add Field``-button, you now see a new ``object`` in your schema. This object represents a custom ``object`` in your Schema and is named after your Adobe Experience Platform Tenant ID. You can view the Tenant ID for your Adobe Experience Platform instance [here](../../environment.md).

![Data Ingestion](./images/tenant.png)

We'll now add a new object under that tenant. To do that, click the field ``New Field`` under the tenant-object.

![Data Ingestion](./images/tenantfield.png)

Use these object-definitions:

* Field name: ``identification``
* Display name:  ``identification``
* Type: ``Object``

![Data Ingestion](./images/tenantfielddef.png)

Click ``Apply`` to save your changes.

![Data Ingestion](./images/apply.png)

After clicking ``Apply``, you now see your ``identification``-object in the Schema.

![Data Ingestion](./images/schemaid.png)

You'll now add 3 new fields under the  ``identification``-object:

* ecid:
  * Field name: ``ecid``
  * Display name:  ``ecid``
  * Type: ``String``

* emailId

  * Field name: ``emailId``
  * Display name:  ``emailId``
  * Type: ``String``
  
* mobilenr

  * Field name: ``mobilenr``
  * Display name:  ``mobilenr``
  * Type: ``String``

Each field will be defined as type ``String`` and we'll configure these fields as ``Identities``. For the Schema ``Website Registration Schema``, we assume that a customer will always be identified by their email-address, which means that you have to configure the field ``emailId`` as a **primary** identifier, and the other fields as **secondary** identifiers.

To add the fields, click the ``Add Field``-button next to the ``identification``-object.

![Data Ingestion](./images/schemaid2.png)

You now have an empty field. You need to configure the above 3 fields as indicated.

![Data Ingestion](./images/emptyfield.png)

This is how each field should look after your initial field configuration:

* ecid

![Data Ingestion](./images/ecidfield.png)

To save your field, scroll down in the ``Field Properties`` until you see the button ``Apply``. Click the ``Apply``-button.

![Data Ingestion](./images/apply.png)

* emailId

![Data Ingestion](./images/emailidfield.png)

To save your field, scroll down in the ``Field Properties`` until you see the button ``Apply``. Click the ``Apply``-button.

![Data Ingestion](./images/apply.png)

* mobilenr

![Data Ingestion](./images/mobilenrfield.png)

To save your field, scroll down in the ``Field Properties`` until you see the button ``Apply``. Click the ``Apply``-button.

![Data Ingestion](./images/apply.png)

You now have 3 fields, but these fields haven't been defined as ``Identity``-fields yet.

![Data Ingestion](./images/3fields.png)

To start defining these fields as ``Identity``-fields, follow these steps:

* Select the field ``emailId``.
* On the right side, in the field properties, scroll down until you see ``Identity``. Check the checkbox for ``Identity``.

  ![Data Ingestion](./images/emailidid.png)

* Now check the checkbox for ``Primary Identity``.

  ![Data Ingestion](./images/emailidprimid.png)
  
* Lastly, select the namespace ``Email`` from the list of ``Namespaces``. A Namespace is used by the Identity Graph in Adobe Experience Platform to classify identifiers in namespaces and define the relationship between those namespaces.

  ![Data Ingestion](./images/emailidprimidns.png)

* Finally, click ``Apply`` to save your changes.

  ![Data Ingestion](./images/apply.png)
  
Next, you have to define the other fields for ``ecid`` and ``mobilenr`` as secondary identifiers.

* Select the field ``ecid``.
* On the right side, in the field properties, scroll down until you see ``Identity``. Check the checkbox for ``Identity``.

  ![Data Ingestion](./images/ecidid.png)

* Next, select the namespace ``ECID`` from the list of ``Namespaces``. A Namespace is used by the Identity Graph in Adobe Experience Platform to classify identifiers in namespaces and define the relationship between those namespaces.

  ![Data Ingestion](./images/ecidprimidns.png)

* Click ``Apply`` to save your changes.

  ![Data Ingestion](./images/apply.png)

* Select the field ``mobilenr``.
* On the right side, in the field properties, scroll down until you see ``Identity``. Check the checkbox for ``Identity``.

  ![Data Ingestion](./images/mobid.png)

* Next, select the namespace ``Phone`` from the list of ``Namespaces``. A Namespace is used by the Identity Graph in Adobe Experience Platform to classify identifiers in namespaces and define the relationship between those namespaces.

  ![Data Ingestion](./images/mobprimidns.png)

* Click ``Apply`` to save your changes.

  ![Data Ingestion](./images/apply.png)

The ``identification``-object should now look like this, with the 3 id-fields now also showing a ``fingerprint``-icon to show that they have been defined as identifiers.

![Data Ingestion](./images/applyiden.png)

You have now defined a Schema, linked existing and newly created mixins and have defined identifiers.

Click ```Save``` to save your changes.

![Data Ingestion](./images/save.png)

The last thing to do here, is to activate the Schema to be linked to the **Profile**.
By enabling your schema for Profile, you're making sure that all data sent to Adobe Experience Platform against this schema will be part of the Real-time Customer Profile environment, which makes sure that all that data can be used in real-time for querying, segmentation and activation.

To do this, let's select the name of your schema.

![Data Ingestion](./images/schemastructure.png)

In the right tab of your schema, you'll see a ``Profile Switcher``, which is currently deactivated.

![Data Ingestion](./images/upswitcher.png)

Activate the Profile - switch by clicking it.

You'll see this message:

![Data Ingestion](./images/sure.png)

Click ```Enable``` to enable this schema for Unified Profile.

Your Schema is now configured to be part of the Real-time Customer Profile.

![Data Ingestion](./images/surey.png)

Finally, click ```Save``` to save your schema.

![Data Ingestion](./images/save.png)

## Exercise 1.2 - What does this customer do?

Capturing the answer to ```What does this customer do?``` for your company is done through f.i. a Product View on a Product Page.

![Data Ingestion](./images/lb_babars.png)

From a Schema perspective, we look at this as a ``Class``. The question: ```What does this customer do?```is something that we've defined in the Class ``ExperienceEvent``.

So when you create an XDM Schema to capture the answer to ```Who is this customer?```, first of all, you'll need to create and define 1 schema that references the class ``ExperienceEvent``.

To specify what kind of answers can be given to that question, you'll need to define Mixins. Mixins are extensions of the Experience Event-class, and have very specific configurations. For instance, information about what kind of products a customer viewed or added to their cart is part of the Mixin ```ExperienceEvent Commerce Details```.

Secondly, your company needs to decide how you'll identify the behavior of this customer. Since we're talking about interactions on a website, it's possible that your company knows the customer but it's equally possible that an unknown, anonymous visitor is active on the website. So we can't use an identifier like email-address. In this case, your company will probably decide to use the Experience Cloud ID (ECID) as the primary identifier.

Lastly, it's important to distinguish the channel on which data was captured. In this case, we'll be talking about Website Interactions and the schema that needs to be defined needs to reflect ```Where``` the interaction data was captured. The channel will also have an important role in influencing what data is captured. As such, it's a best practice to define schema's for every combination of channel, primary identifier and type of data collected.

Based on the above, you'll need to configure a Schema in Adobe Experience Platform.

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./images/home.png)

Before you continue, you need to select your own ``Sandbox``. You can do this by clicking the text ``Production Prod (VA7)`` in the blue line on top of your screen.

![Data Ingestion](./images/sb1.png)

From the list of available sandboxes, select the sandbox that matches the number you've been assigned.

After selecting the appropriate sandbox, you'll see the screen change and now you're in your dedicated sandbox.

![Data Ingestion](./images/sb2.png)

In Adobe Experience Platform, click on ```Schemas```in the menu on the left side of your screen.

![Data Ingestion](./images/menuschemas.png)

In Schemas, you'll see your previously defined schema.

![Data Ingestion](./images/schemasee.png)

You should create a new schema. To create a new schema, click on the button ```+ Create Schema```.

![Data Ingestion](./images/createschema.png)

After clicking the ```+ Create Schema```button, you'll see an empty, new schema.

![Data Ingestion](./images/emptyschema.png)

Let's first name your schema. Please use the following naming for your schema:

As the name for our schema, we'll use this:
**AEP Demo - Website Interactions Schema**

That should give you something like this:

![Data Ingestion](./images/schemanameee.png)

Next, you need to select the class of your schema. As indicated before, the class of your schema should be ``XDM ExperienceEvent``.

Click on the button ```+ Assign```

![Data Ingestion](./images/assignee.png)

In the ```Assign Class```-window, select ```XDM ExperienceEvent```.

![Data Ingestion](./images/XDMEE.png)

Click the ```Assign Class```-button to assign the class.

![Data Ingestion](./images/assignclass.png)

You'll now see an overview of the minimal structure of your schema.

![Data Ingestion](./images/classoverviewee.png)

It's important to note that when eventually ingesting data against this schema, that some fields are required.
For instance, the fields ```_id``` and ```timestamp``` are required fields.

* _id needs to contain a unique id for a specific data ingestion
* timestamp needs to be the timestamp of this hit, in the format **"YYYY-MM-DDTHH:MM:SSZ"**, like f.i.: **"2019-04-08T07:20:00Z"**

Now you need to define what an answer to the question ```What does this customer do?``` should look like.
In the introduction of this lab, we noted the need for following attributes to define what a customer does:

* Which pages or products have been visited?
* Has this customer added a product to his cart or even purchased an item?
* What device and browser has been used to browse the website?
* What kind of information is this customer looking for and how can we use that to configure and deliver a delightful experience to this customer?
* Primary Identifier for a customer

To make that information part of your schema, you need to add the following Mixins to your schema:

* ExperienceEvent Web Details
* ExperienceEvent Commerce Details
* ExperienceEvent Environment Details
* your company's custom Profile Identification Mixin (Primary and Secondary Identifiers)

You can add these Mixins by clicking the ```+ Add```-button below the Class that you just defined.

![Data Ingestion](./images/addmixinee.png)

Let's start with **ExperienceEvent Web Details**.

Click the ```+ Add```-button to start adding a Mixin.

In the ``Add Mixin``-screen, select the Mixin ```ExperienceEvent Web Details```.

![Data Ingestion](./images/eewd.png)

Click the ```Add Mixin```-button to add the Mixin to your schema.

![Data Ingestion](./images/addmixin1.png)

Next, add the Mixin **ExperienceEvent Commerce Details**.

Click the ```+ Add```-button to start adding a Mixin.

In the ``Add Mixin``-screen, select the Mixin ```ExperienceEvent Commerce Details```.

![Data Ingestion](./images/eecd.png)

Click the ```Add Mixin```-button to add the Mixin to your schema.

![Data Ingestion](./images/addmixin1.png)

Next, add the Mixin **ExperienceEvent Environment Details**.

Click the ```+ Add```-button to start adding a Mixin.

In the ``Add Mixin``-screen, select the Mixin ```ExperienceEvent Environment Details```.

![Data Ingestion](./images/eeed.png)

Click the ```Add Mixin```-button to add the Mixin to your schema.

![Data Ingestion](./images/addmixin1.png)

Lastly, you need a new Mixin to capture the ``Identifier`` used for data collection. As you've seen in the previous exercise, there's a concept of Primary and Secondary Identifiers. A Primary Identifier is the most important one, as all collected data will be linked to this Identifier.

You will now create your own custom Mixin and as such, you'll be extending the XDM Schema to meet your own company's requirements.

A Mixin is linked to a Class, so that means that we can't simply reuse the previously created Mixin.

Click the ```+ Add```-button to start adding a Mixin.

![Data Ingestion](./images/addmixinee.png)

Instead of reusing an existing Mixin, you'll now create your own Mixin. You can do that by selecting ``Create New Mixin``.

![Data Ingestion](./images/createmixin.png)

You now need to provide a ``Display Name`` and ``Description`` for your new Mixin.

As the name for our schema, we'll use this:
**AEP Demo - EE Identification**

That should give you something like this:

![Data Ingestion](./images/mixinnameee.png)

Click the ```Add Mixin```-button to add the newly created Mixin to your schema.

![Data Ingestion](./images/addmixin1.png)

You should now have this Schema structure in place.

![Data Ingestion](./images/schemastructuremee.png)

Your new Mixin is still empty, so now you'll have to add fields to that Mixin.
In the Mixins-list, click your custom Mixin.

![Data Ingestion](./images/mixinselectedee.png)

You now see a number of new buttons appear. These buttons are named ``+ Add Field``.

On the top-level of your Schema, next to your Schema - name, click the ``+ Add Field``-button.

![Data Ingestion](./images/clickaddfieldee.png)

After clicking the ``+ Add Field``-button, you now see a new ``object`` in your schema. This object represents a custom ``object`` in your Schema and is named after your Adobe Experience Platform Tenant ID. You can view the Tenant ID for your Adobe Experience Platform instance [here](../../environment.md).

![Data Ingestion](./images/tenantee.png)

We'll now add a new object under that tenant. To do that, click the field ``New Field`` under the tenant-object.

![Data Ingestion](./images/tenantfieldee.png)

Use these object-definitions:

* Field name: ``identification``
* Display name:  ``identification``
* Type: ``Object``

![Data Ingestion](./images/tenantfielddefee.png)

Click ``Apply`` to save your changes.

![Data Ingestion](./images/apply.png)

After clicking ``Apply``, you now see your ``identification``-object in the Schema.

![Data Ingestion](./images/schemaidee.png)

We'll now add 1 new field under the  ``identification``-object:

* ecid:

  * Field name: ``ecid``
  * Display name:  ``ecid``
  * Type: ``String``

The ECID-field will be defined as type ``String`` and we'll configure this field as an ``Identity``. For the Schema ``AEP Demo - Website Interactions Schema``, we assume that a customer will always be identified by their ECID, which means that you have to configure the field ``ECID`` as a **primary** identifier

To add the fields, click the ``Add Field``-button next to the ``identification``-object.

![Data Ingestion](./images/schemaid2ee.png)

You now have an empty field. You need to configure the above field as indicated.

![Data Ingestion](./images/emptyfieldee.png)

This is how the ecid-field should look after your initial field configuration:

![Data Ingestion](./images/ecidfieldee.png)

You now have a new field, but this field hasn't been defined as an ``Identity``-field yet.

![Data Ingestion](./images/3fieldsee.png)

To start defining these fields as ``Identity``-fields, follow these steps:

* Select the field ``ecid``.
* On the right side, in the field properties, scroll down until you see ``Identity``. Check the checkbox for ``Identity``.

  ![Data Ingestion](./images/ecididee.png)

* Now check the checkbox for ``Primary Identity``.

  ![Data Ingestion](./images/ecidprimidee.png)
  
* Lastly, select the namespace ``ECID`` from the list of ``Namespaces``. A Namespace is used by the Identity Graph in Adobe Experience Platform to classify identifiers in namespaces and define the relationship between those namespaces.

  ![Data Ingestion](./images/ecidprimidnsee.png)

* Finally, click ``Apply`` to save your changes.

  ![Data Ingestion](./images/apply.png)

The ``identification``-object should now look like this, with the ecid-field now also showing a ``fingerprint``-icon to show that they have been defined as identifiers.

![Data Ingestion](./images/applyidenee.png)

You have now defined a Schema, linked existing and newly created mixins and have defined identifiers.

Click ```Save``` to save your changes.

![Data Ingestion](./images/save.png)

The last thing to do here, is to activate the Schema to be linked to the **Profile**.
By enabling your schema for Profile, you're making sure that all data sent to Adobe Experience Platform against this schema will be part of the Real-time Customer Profile environment, which makes sure that all that data can be used in real-time for querying, segmentation and activation.

To do this, let's select the name of your schema.

![Data Ingestion](./images/schemastructureeee.png)

In the right tab of your schema, you'll see a ``Profile Switcher``, which is currently deactivated.

![Data Ingestion](./images/upswitcheree.png)

Activate the Profile - switch by clicking it.

You'll see this message:

![Data Ingestion](./images/sure.png)

Click ```Enable``` to enable this schema for Unified Profile.

Your Schema is now configured to be part of the Real-time Customer Profile.

![Data Ingestion](./images/surey.png)

Finally, click ```Save``` to save your schema.

![Data Ingestion](./images/save.png)

You've now finished building schemas that are activated to be used in the Real-time Customer Profile.

Let's have a look at datasets in the next exercise.

---

Next Step: [Exercise 3 - Configure Datasets](./ex3.md)

[Go Back to Module 1](./README.md)

[Go Back to All Modules](../../README.md)
