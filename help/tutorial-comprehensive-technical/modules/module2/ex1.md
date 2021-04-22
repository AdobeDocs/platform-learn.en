---
title: Foundation - Data Ingestion - From unknown to known on the website
description: Foundation - Data Ingestion - From unknown to known on the website
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 05e7557a-256a-48e5-9ba3-2092d2b68001
---
# 2.1 - From unknown to known on the website

## Context

The journey from unknown to known is one of the most important topics amongst brands these days, as is the customer journey from acquisition to retention. 

Adobe Experience Platform plays a huge role in this journey. Platform is the brains for communication, the experience system of record.

Platform is an environment in which the word **customer** is broader than just the **known**-customers. This is a very important thing to mention when speaking to brands: an unknown visitor on the website is also a customer from Platform's perspective and as such, all of the behavior as an unknown visitor is also sent to Platform. Thanks to that approach, when this customer eventually becomes a known customer, a brand can visualize what happened before that moment as well. This helps from an attribution and experience optimization perspective.

## What are you going to do

You will now ingest data into Adobe Experience Platform and that data will be linked to identifiers like ECIDs and email-addresses. The goal of this is to understand the business context of what you're about to do from a configuration perspective. In the next exercise, you'll start configuring everything you need to make all that data ingestion possible in your own sandbox environment.

### Customer Journey flow

* Go to your Platform Demo website.

* You'll be redirected to the **Admin** page

![Demo](../module2/images/1.png)
  
* On the **Admin** page, click **Select LDAP**.
  
![Demo](../module2/images/1a.png)
  
* Select your LDAP from the list of available LDAPs. Click **Save**.
  
![Demo](../module2/images/1b.png)
  
* Back on the **Admin** page, click **Select Brand**.
  
![Demo](../module2/images/2.png)
  
* Select the brand **Luma** from the list of available brands. Click **Save**.
  
![Demo](../module2/images/3.png)
  
* Wait 10 seconds for the brand to load. You'll then be redirected to the Admin homepage.
  
![Demo](../module2/images/4.png)
  
* Click the **Luma**-logo to go to the demo website. You'll then see this:
  
![Demo](../module2/images/lb_home.png)
  
* Have a look at the X-ray panel and the Real-time Customer Profile:
  * **ECID** as the internal Adobe identifier
      
![Demo](../module2/images/lb_home_xup.png)

* You'll also see Experience Events

![Demo](../module2/images/lb_home_xee.png)
  
* Scroll down on the page until you see the products, click on the product **Nadia Elements Shell**.
  
![Demo](../module2/images/lb_homep.png)
  
* Have a look at the product. An Experience Event of type **Product View** has been sent by to Adobe Experience Platform. 
  
![Demo](../module2/images/lb_els_dtl.png)
  
* Next, go to the Homepage. Open the X-ray panel and have a look at your **Experience Events**.
  
![Demo](../module2/images/lb_home1.png)
  
* On the **Home** page, click another product. Another Experience Event has been sent to Adobe Experience Platform. 
  
![Demo](../module2/images/lb_babars.png)
  
* Go back to the Homepage and open the X-ray panel. You'll now see 2 Experience Events of type **Product View**. While the behavior is anonymous, we're able to track every click and store it in in Adobe Experience Platform. Once the anonymous customer becomes known, we'll be able to merge all anonymous behavior automatically to the know profile.
  
![Demo](../module2/images/lb_home2.png)

* Go to the Register/Login page. Fill out your registration details and click **CREATE ACCOUNT**.
  
![Demo](../module2/images/lb_register_dtl.png) 
  
* After clicking **Create Account**, you'll be redirected to the homepage. Open the X-ray panel and go to Real-time Customer Profile. On the X-ray panel, you should see all of your personal data displayed.
  
![Demo](../module2/images/lb_x_loggedin.png)

* On the X-ray panel, go to Experience Events. You should see the 2 products that you viewed before on the X-ray panel.

![Demo](../module2/images/lb_home_xee_dtl.png)
  
You've now ingested data into Adobe Experience Platform and you've linked that data to identifiers like ECIDs and email-addresses. The goal of this is to understand the business context of what you're about to do. In the next exercise, you'll start configuring everything you need to make all that data ingestion possible.

Next Step: [2.2 Configure Schemas and Set Identifiers](./ex2.md)

[Go Back to Module 2](./data-ingestion.md)

[Go Back to All Modules](../../overview.md)
