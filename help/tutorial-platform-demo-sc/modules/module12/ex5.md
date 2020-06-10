---
title: Journey Orchestration - External Weather API, SMS Action & more - Trigger your Orchestrated Customer Journey
description: Journey Orchestration - External Weather API, SMS Action & more - Trigger your Orchestrated Customer Journey
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: 
---

# 12.5 Trigger your Orchestrated Customer Journey

In this exercise, you'll test and trigger the Orchestrated Journey you configured in this module.

* Go to your Platform Demo website.

* You'll be redirected to the **Admin** page. Go to **Select LDAP**.

   ![Demo](./images/1.png)

* Select your LDAP and click **Save**.

   ![Demo](./images/1a.png)

* Back on the **Admin** page, click **Select Brand**.

   ![Demo](./images/2.png)

* Select a brand from the list of available brands. Click **Save**.

   ![Demo](./images/3.png)

* Wait 10 seconds for the brand to load.

* From the Admin homepage, click the logo of your brand.

   ![Demo](./images/3a.png)

* You're now on the homepage of your brand.

   ![Demo](./images/lb_home.png)

* Go to the Register/Login page
  
   >[!IMPORTANT]
   >
   > Please use the following naming convention for your Mobile Phone Number:
   > If your number is 0473622044, you have to enter **+32473622044+DDMMYYYY-XX** as a number, otherwise the sending of SMSs doesn't work. For instance, **+32473622044+26052020-1**
  
  ![Demo](./images/lb_register.png)

* Fill out your registration details and click **CREATE ACCOUNT**.

* After login, go to the Homepage of the website and open the X-ray panel, go to Real-time Customer Profile. On the X-ray panel, you should see all of your personal data displayed.

   ![Demo](./images/lb_x_loggedin.png)

* In the website's menu, click on the **3 dots** and select **Admin**.

   ![Demo](./images/gf10.png)

* You'll then see the **Admin** page. Click **Send Geofence Event**.

   ![Demo](./images/gf13.png)

* You'll then see this:

   ![Demo](./images/gf14.png)

* On the **Send Geofence Event** page, click **Allow** on the prompt to **Know your location**.

   ![Demo](./images/gf15.png)

* After 1-2 seconds (sometimes this can take up to 1-2 minutes), you'll see the coordinates, city and country of your approximate location. Once the coordinates are shown, you have to enter your Orchestration eventID from 1. In this example, the **eventID** is **d9b5069cebd47bb3394e192da031d933a9e10d67046dadde999ec7401eb7bd51**.

   ![Demo](./images/gf16.png)

* Click **Send Geofence Event**. You'll get a visual confirmation when the Geofence Event has been sent.

  ![Demo](./images/gf17.png)

* You should then receive a SMS Message on the Mobile Phone that was attached to your Real-time Customer Profile. The SMS Message will depend on the current weather and the temperature, just like you configured in your Journey.

   >[!NOTE] Twilio doesn't support Indian Mobile Numbers, so if you have an mobile phone number starting with +91, you won't receive any SMS. 

  ![Demo](./images/gf19.png)

* The same message will also be sent to the Adobe Hands-On Lab Slack channel. Your trainer is able to show you the received messages in the Slack channel.
  
  ![Demo](./images/gf18.png)

If you've received your SMS Message, you've successfully completed this module! 

[Go Back to Module 12](journey-orchestration-external-weather-api-sms.md)

[Go Back to All Modules](../../overview.md)
