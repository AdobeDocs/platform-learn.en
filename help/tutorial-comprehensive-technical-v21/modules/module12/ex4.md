---
title: Journey Orchestration - External Weather API, SMS Action & more - Design a trigger-based Customer Journey
description: Journey Orchestration - External Weather API, SMS Action & more - Design a trigger-based Customer Journey
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 6bec303b-b58a-4b9f-8ded-5e7354cf06b6
---
# 12.4 Design a trigger-based Customer Journey

In this exercise, you'll create an orchestrated journey by making use of Journey Orchestration in combination with Adobe Experience Platform.

Go to [https://experience.adobe.com/](https://experience.adobe.com/)

You'll see the **Adobe Experience Cloud** homepage.

![Demo](./images/aec.png)

Click on **Journey Orchestration**.

![Demo](./images/aecjo.png)

Next, you'll see the **Journey Orchestration** homepage, which shows all existing Journeys.

![Demo](./images/journeyhome.png)

Click **Create** to start creating your Journey.

![Demo](./images/jocreate.png)

You'll then see a new, blank Journey.

![Demo](./images/jonew.png)

You should first name your Journey.

As a Name for the Journey, use `LDAP Geofence Entry Journey` and replace `LDAP` with your LDAP. In this example, the Journey Name is `joconnor Geofence Entry Journey`. No other values must be set at this moment.

![Demo](./images/joname.png)

Click **OK**.

![Demo](./images/jonameok.png)

On the left side of your screen, have a look at **Events**. You should see your previously created Event in that list. Select it, then drag and drop it on the Journey Canvas.

![Demo](./images/joevents.png)

Your Journey then looks like this:

![Demo](./images/jo1.png)

Next, click on **Orchestration**.

![Demo](./images/jo2.png)

You now see **Orchestration** capabilities.

![Demo](./images/jo3.png)

Select **Condition**, then drag and drop it on the Journey Canvas.

![Demo](./images/jo4.png)

You now have to define three conditions:

* It's colder than 10° Celsius
* It's between 10° and 25° Celsius
* It's warmer than 25° Celsius

Let's define the first condition.

## Condition 1: Colder than 10° Celsius

Click on the **Condition**.  Click on **Path1** and edit the name of the path to **Colder than 10 C**

![Demo](./images/jo5.png)

Click on the **Edit** icon for the expression of Path1.

![Demo](./images/jo6.png)

You'll then see an empty **Simple Editor** screen.

![Demo](./images/jo7.png)

Our query will be a bit more advanced, so we'll need the **Advanced Mode**.
Click **Advanced Mode**.

![Demo](./images/jo8.png)

You'll then see the **Advanced Editor** which allows code entry.

![Demo](./images/jo9.png)

Select the below code and paste it in the **Advanced Editor**.

`#{ldapWeatherApi.ldapWeatherByCity.main.temp} <= 10` (replace Ldap by your LDAP)

You'll then see this.

![Demo](./images/jo10.png)

In order to retrieve the temperature as part of this Condition, you need to provide the city in which the customer currently is.
The **City** needs to be linked to the dynamic parameter `q`, just like we saw previously in the Open Weather API Documentation.

Click the field **dynamic val: q** as indicated in the screenshot.

![Demo](./images/jo11.png)

You then need to find the field that contains the current city of the customer in one of the available Data Sources.

![Demo](./images/jo12.png)

You can find the field by navigating to ```ldapGeofenceEntry.placeContext.geo.city``` (replace Ldap by your LDAP).

By clicking that field, it will be added as the dynamic value for the parameter `q`. This field will be populated by for instance the geolocation-service that you've implemented in your Mobile App.  In our case we will simulate this with the admin console of public.aepdemo.net.

![Demo](./images/jo13.png)

Click **OK**.

![Demo](./images/jook.png)

Next, we'll add the 2nd condition.

## Condition 2: Between 10° and 25° Celsius

After having added the first condition, you'll see this screen.

![Demo](./images/joc2.png)

Click **Add Path**.

![Demo](./images/joadd.png)

Double click on **Path1** and edit the path name to **Between 10 and 25 C**. Then click on the **Edit** icon for the expression this path.

![Demo](./images/joc6.png)

You'll then see an empty **Simple Editor** screen.

![Demo](./images/jo7.png)

Our query will be a bit more advanced, so we'll need the **Advanced Mode**.
Click **Advanced Mode**.

![Demo](./images/jo8.png)

You'll then see the **Advanced Editor** which allows code entry.

![Demo](./images/jo9.png)

Select the below code and paste it in the **Advanced Editor**.

`#{ldapWeatherApi.ldapWeatherByCity.main.temp} > 10 and #{ldapWeatherApi.ldapWeatherByCity.main.temp} <= 25` (Replace ldap by your LDAP)

You'll then see this.

![Demo](./images/joc10.png)

In order to retrieve the temperature as part of this Condition, you need to provide the city in which the customer currently is.
The **City** needs to be linked to the dynamic parameter **q**, just like we saw previously in the Open Weather API Documentation.

Click the field **dynamic val: q** as indicated in the screenshot.

![Demo](./images/joc11.png)

You then need to find the field that contains the current city of the customer in one of the available Data Sources.

![Demo](./images/jo12.png)

You can find the field by navigating to ```ldapGeofenceEntry.placeContext.geo.city``` (Replace ldap by your LDAP). By clicking that field, it will be added as the dynamic value for the parameter **q**. This field will be populated by for instance the geolocation-service that you've implemented in your Mobile App.

![Demo](./images/jo13.png)

Click **OK**.

![Demo](./images/jook.png)

Next, we'll add the 3rd condition.

## Condition 3: Warmer than 25° Celsius

After having added the second condition, you'll see this screen.

![Demo](./images/joct2.png)

Click **Add Path**.

![Demo](./images/joadd.png)

Double click on Path1 to change the name to **Warmer than 25 C**. 
Then click on the **Edit** icon for the expression this path.

![Demo](./images/joct6.png)

You'll then see an empty **Simple Editor** screen.

![Demo](./images/jo7.png)

Our query will be a bit more advanced, so we'll need the **Advanced Mode**.
Click **Advanced Mode**.

![Demo](./images/jo8.png)

You'll then see the **Advanced Editor** which allows code entry.

![Demo](./images/jo9.png)

Select the below code and paste it in the **Advanced Editor**.

`#{ldapWeatherApi.ldapWeatherByCity.main.temp} > 25` (Replace ldap by your LDAP)

You'll then see this.

![Demo](./images/joct10.png)

In order to retrieve the temperature as part of this Condition, you need to provide the city in which the customer currently is.
The **City** needs to be linked to the dynamic parameter **q**, just like we saw previously in the Open Weather API Documentation.

Click the field **dynamic val: q** as indicated in the screenshot.

![Demo](./images/joct11.png)

You then need to find the field that contains the current city of the customer in one of the available Data Sources.

![Demo](./images/jo12.png)

You can find the field by navigating to ```ldapGeofenceEntry.placeContext.geo.city```. By clicking that field, it will be added as the dynamic value for the parameter **q**. This field will be populated by for instance the geolocation-service that you've implemented in your Mobile App.

![Demo](./images/jo13.png)

Click **OK**.

![Demo](./images/jook.png)

You now have three configured paths.

![Demo](./images/jo3path.png)

Click **Ok**.

![Demo](./images/joblueok.png)


As this is a journey for learning purpose, we'll now configure a couple of actions to showcase the variety of options marketeers now have to deliver messages.

## Send messages for **Colder than 10° Celsius** Path

For each of the temperature contexts, we'll attempt to send an SMS Message to our customer. We can only send an SMS if we have a Mobile Number available for a customer, so we'll first have to verify that we do.

Let's focus on **Colder than 10 C**.

![Demo](./images/p1steps.png)

Let's take another **Condition** element and drag it as indicated in the screenshot below. We'll verify if for this customer, we have a mobile number available.

![Demo](./images/joa1.png)

As this is just an example, we are only configuring the option where the customer has a mobile number available. So, first add a label of **Has mobile?** and then double click on **Path1** and edit the text to **Yes**.

Click on the **Edit** icon for the Expression for the **Yes** path.

![Demo](./images/joa2.png)

In the Data Sources shown on the left, navigate to **ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number**. You're now reading the mobile phone number directly from Adobe Experience Platform's Real-time Customer Profile.

![Demo](./images/joa3.png)

Select the field **Number**, then drag and drop it to the Condition Canvas.

Select the operator **is not empty**.

![Demo](./images/joa4.png)

Click **Ok**.

![Demo](./images/josmallblueok.png)

You'll then see this:

![Demo](./images/joa6.png)

Click **OK**.

![Demo](./images/joblueok.png)

Your Journey will then look like this. Click on **Actions** as indicated in the screenshot.

![Demo](./images/joa8.png)

Select the `ldapSmsTwilio - action` (verify your LDAP), then drag and drop it after the condition you just added.

![Demo](./images/joa9.png)

You'll see a panel on the right hand side where you can configure the action.

![Demo](./images/joa10.png)

Navigate to the **Action Parameters**.

![Demo](./images/joa11.png)

Click on the **Edit** icon for the Action Parameter **TEXTMESSAGE**.

![Demo](./images/joa12.png)

In the popup you'll see, click on **Advanced Mode**.

![Demo](./images/jo8.png)

Select the below code, copy it and paste it in the **Advanced Mode Editor**.

`"Brrrr..." + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + " It's freezing. 20% discount on Jackets today!"`

![Demo](./images/joa14.png)

Click **OK**.

Click on the **Edit** icon for the Action Parameter **MOBILENR**.

![Demo](./images/joa15.png)

You'll see a popup with the **Simple Mode Editor**.

![Demo](./images/joasm.png)

In the popup you'll see, click on **Advanced Mode**.

![Demo](./images/jo8.png)

Paste this code in the **Advanced Mode Editor**. Click **OK**.

`substr(#{ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number}, 0, 12)`

FYI: This code is intended to work with mobile phone numbers that have 12 digits (including the +), like this one: +32463622044.
Several other countries have 13-digit phone numbers. If your mobile phone number has 13 digits (including the +), you need to update this code to:

`substr(#{ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number}, 0, 13)`

![Demo](./images/joa16.png)

Click **Ok**.

![Demo](./images/joblueok.png)

And you will see your completed action.

![Demo](./images/joa17.png)

Click **Ok** in the top right to save your action.

![Demo](./images/joblueok.png)


In the left menu, go back to **Actions**, select the Action **ldapTextSlack**, then drag and drop it after the **ldapSmsTwilio**-Action (Replace ldap by your LDAP).

![Demo](./images/joa18.png)

Go to **Action Parameters** and click the **Edit** icon for the parameter `TEXTTOSLACK`.

![Demo](./images/joa19.png)

In the popup-window, click **Advanced Mode**.

![Demo](./images/joa20.png)

Select the below code, copy it and paste it in the **Advanced Mode Editor**.

`"Brrrr..." + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + " It's freezing. 20% discount on Jackets today!"`

![Demo](./images/joa21.png)

Click **Ok**.

![Demo](./images/joblueok.png)

You will see your completed action.

![Demo](./images/joa22.png)

Click **Ok** in the top right to save the action.

![Demo](./images/joblueok.png)

In the left menu, go to **Orchestration**, select **End**, then drag and drop **End** after the `joconnorTextSlack` action.

![Demo](./images/joa23.png)

## Send Messages for **Between 10° and 25° Celsius** Path

For each of the temperature contexts, we'll attempt to send an SMS Message to our customer. We can only send an SMS if we have a Mobile Number available for a customer, so we'll first have to verify that we do.

Let's focus on **Between 10 and 25 C** path.

![Demo](./images/p2steps.png)

Let's take another **Condition** element and drag it as indicated in the screenshot above. We'll verify if for this customer, we have a mobile number available.

![Demo](./images/jop1.png)

As this is just an example, we are only configuring the option where the customer has a mobile number available. So, first add a label of **Has mobile?** and then double click on **Path1** and edit the text to **Yes**.

Click on the **Edit** icon for the Expression for the **Yes** path.

![Demo](./images/joa2.png)

In the Data Sources shown on the left, navigate to **ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number**. You're now reading the mobile phone number directly from Adobe Experience Platform's Real-time Customer Profile.

![Demo](./images/joa3.png)

Select the field **Number**, then drag and drop it to the Condition Canvas.

Select the operator **is not empty**.

![Demo](./images/joa4.png)

Click **Ok**.

![Demo](./images/josmallblueok.png)

You'll then see this:

![Demo](./images/joa6.png)

Click **OK**.

![Demo](./images/joblueok.png)

Your Journey will then look like this. Click on **Actions** as indicated in the screenshot.

![Demo](./images/jop8.png)

Select the `ldapSmsTwilio - action` (verify your LDAP), then drag and drop it after the condition you just added.

![Demo](./images/jop9.png)

You'll see a panel on the right hand side where you can configure the action.

![Demo](./images/joa10.png)

Navigate to the **Action Parameters**.

![Demo](./images/joa11.png)

Click on the **Edit** icon for the Action Parameter **TEXTMESSAGE**.

![Demo](./images/joa12.png)

In the popup you'll see, click on **Advanced Mode**.

![Demo](./images/jo8.png)

Select the below code, copy it and paste it in the **Advanced Mode Editor**.

`"What nice weather for the time of year, " + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + " 20% discount on Sweaters today!"`

![Demo](./images/jop14.png)

Click **OK**.

Click on the **Edit** icon for the Action Parameter **MOBILENR**.

![Demo](./images/jop15.png)

You'll see a popup with the **Simple Mode Editor**.

![Demo](./images/joasm.png)

In the popup you'll see, click on **Advanced Mode**.

![Demo](./images/jo8.png)

Paste this code in the **Advanced Mode Editor**. Click **OK**.

`substr(#{ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number}, 0, 12)`

FYI: This code is intended to work with mobile phone numbers that have 12 digits (including the +), like this one: **+32463622044`.
Several other countries have 13-digit phone numbers. If your mobile phone number has 13 digits (including the +), you need to update this code to:

`substr(#{ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number}, 0, 13)`

![Demo](./images/joa16.png)

Click **OK**.

![Demo](./images/jop17.png)

Click **Ok** in the top right to save your action.

![Demo](./images/joblueok.png)


In the left menu, go back to **Actions**, select the Action **ldapTextSlack**, then drag and drop it after the **ldapSmsTwilio**-Action (Replace ldap by your LDAP).

![Demo](./images/jop18.png)

Go to **Action Parameters** and click the **Edit** icon for the parameter `TEXTTOSLACK`.

![Demo](./images/joa19.png)

In the popup-window, click **Advanced Mode**.

![Demo](./images/joa20.png)

Select the below code, copy it and paste it in the **Advanced Mode Editor**.

`"What nice weather for the time of year, " + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + " 20% discount on Sweaters today!"`

![Demo](./images/jop21.png)

Click **Ok**.

![Demo](./images/joblueok.png)

You will see your completed action.

![Demo](./images/jop22.png)

Click **Ok** in the top right to save the action.

![Demo](./images/joblueok.png)

In the left menu, go to **Orchestration**, select **End**, then drag and drop **End** after the `joconnorTextSlack` action.

![Demo](./images/jop23.png)

## Send messages for **Warmer than 25° Celsius** Path

For each of the temperature contexts, we'll attempt to send an SMS Message to our customer. We can only send an SMS if we have a Mobile Number available for a customer, so we'll first have to verify that we do.

Let's focus on **Warmer than 25 C** path.

![Demo](./images/p3steps.png)

Let's take another **Condition** element and drag it as indicated in the screenshot above. We'll verify if for this customer, we have a mobile number available.

![Demo](./images/jod1.png)

As this is just an example, we are only configuring the option where the customer has a mobile number available. So, first add a label of **Has mobile?** and then double click on **Path1** and edit the text to **Yes**.

Click on the **Edit** icon for the Expression for the **Yes** path.

![Demo](./images/joa2.png)

In the Data Sources shown on the left, navigate to **ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number**. You're now reading the mobile phone number directly from Adobe Experience Platform's Real-time Customer Profile.

![Demo](./images/joa3.png)

Select the field **Number**, then drag and drop it to the Condition Canvas.

Select the operator **is not empty**.

![Demo](./images/joa4.png)

Click **Ok**.

![Demo](./images/josmallblueok.png)

You'll then see this:

![Demo](./images/joa6.png)

Click **OK**.

![Demo](./images/joblueok.png)

Your Journey will then look like this. Click on **Actions** as indicated in the screenshot.

![Demo](./images/jod8.png)

Select the `ldapSmsTwilio - action` (verify your LDAP), then drag and drop it after the condition you just added.

![Demo](./images/jod9.png)

You'll see a panel on the right hand side where you can configure the action.

![Demo](./images/joa10.png)

Navigate to the **Action Parameters**.

![Demo](./images/joa11.png)

Click on the **Edit** icon for the Action Parameter **TEXTMESSAGE**.

![Demo](./images/joa12.png)

In the popup you'll see, click on **Advanced Mode**.

![Demo](./images/jo8.png)

Select the below code, copy it and paste it in the **Advanced Mode Editor**.

`"So warm, " + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + "! 20% discount on swimwear today!"`

![Demo](./images/jod14.png)

Click **OK**.

Click on the **Edit** icon for the Action Parameter **MOBILENR**.

![Demo](./images/jod15.png)

You'll see a popup with the **Simple Mode Editor**.

![Demo](./images/joasm.png)

In the popup you'll see, click on **Advanced Mode**.

![Demo](./images/jo8.png)

Paste this code in the **Advanced Mode Editor**. Click **OK**.

`substr(#{ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number}, 0, 12)`

FYI: This code is intended to work with mobile phone numbers that have 12 digits (including the +), like this one: **+32463622044`.
Several other countries have 13-digit phone numbers. If your mobile phone number has 13 digits (including the +), you need to update this code to:

`substr(#{ExperiencePlatform.ProfileFieldGroup.profile.mobilePhone.number}, 0, 13)`

![Demo](./images/joa16.png)

Click **OK**.

![Demo](./images/jod17.png)

Click **Ok** in the top right to save your action.

![Demo](./images/joblueok.png)


In the left menu, go back to **Actions**, select the Action **ldapTextSlack**, then drag and drop it after the **ldapSmsTwilio**-Action (Replace ldap by your LDAP).

![Demo](./images/jod18.png)

Go to **Action Parameters** and click the **Edit** icon for the parameter `TEXTTOSLACK`.

![Demo](./images/joa19.png)

In the popup-window, click **Advanced Mode**.

![Demo](./images/joa20.png)

Select the below code, copy it and paste it in the **Advanced Mode Editor**.

`"So warm, " + #{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName} + "! 20% discount on swimwear today!"`

![Demo](./images/jod21.png)

Click **Ok**.

![Demo](./images/joblueok.png)

You will see your completed action.

![Demo](./images/jod22.png)

Click **Ok** in the top right to save the action.

![Demo](./images/joblueok.png)

In the left menu, go to **Orchestration**, select **End**, then drag and drop **End** after the `joconnorTextSlack` action.

![Demo](./images/jod23.png)

Your Journey is now fully configured.

![Demo](./images/jodone.png)

Click **Publish**.

![Demo](./images/jopublish.png)

Click **Publish**.

![Demo](./images/jopublish1.png)

Your Journey is now published.

![Demo](./images/jopublish2.png)

In the next exercise, you'll be able to test your Journey.

Next Step: [12.5 Trigger your Orchestrated Customer Journey](./ex5.md)

[Go Back to Module 12](journey-orchestration-external-weather-api-sms.md)

[Go Back to All Modules](../../overview.md)
