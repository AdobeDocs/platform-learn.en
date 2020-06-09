---
title: Module 6, Exercise
description: 
kt: 5342
audience: 
doc-type: tutorial
activity: 
---

# 6.3: Configure Launch to trigger your Event

In this exercise, you'll configure Launch so that the Event you created in Exercise 6.1 is now triggered, and activates the Journey that you built in Exercise 6.2.

Go to [https://launch.adobe.com/](https://launch.adobe.com/) and login with your personal login details.

Select your Launch property.

## 6.3.1 - Edit Rule: Create Account

In the Launch UI, go to Rules.

![Upgrade Launch](./images/rules.png)

Click to open the rule `Create Account`.

![Upgrade Launch](./images/newrulecracc.png)

Open the action `Adobe Experience Platform - Send Beacon`. You'll then see this:

![Launch Setup](./images/beaconconfig.png)

In Schema Mapping, you need to add the following Keys and Values to the Send Beacon action:

| Source Value                 | Target Schema Field               |
|:-------------------------------------------| :------------------ |
|**YourEventID**|_experience.campaign.orchestration.eventID|

The reference to **YourEventID** refers specifically to the EventID of the Event that you configured in 1. Retrieve the Event ID as indicated in 1 and paste it by replacing **YourEventID** with your Event ID.

Go to Journey Orchestration, to Events. Select your event and view the payload, scroll down to your eventID:

![ACOP](./images/payloadeventID.png)

Scroll down in the Schema Mapping and click **Add Another**.

![ACOP](./images/payloadeventID1.png)

Configure your mapping with your eventID, as indicated below:

![ACOP](./images/payloadeventID2.png)

After the above configuration, your rule looks like this:

![Upgrade Launch](./images/cracc_ok.png)

Click **Keep Changes** to save your Action.

Click **Save** to save your changes.

You can now publish these changes into your development environment.

In the Launch UI, navigate to the menu option **Publishing**.

![Launch Setup](./images/publ.png)

Under Development, you'll see your current Development environment.

Click on little arrow to open a dropdown list and click Edit to make changes to your Development library.

![Launch Setup](./images/editv1.png)

Scroll down to the bottom of the window, where you'll see a button called **+ Add All Changed Resources**.

![Launch Setup](./images/addch.png)

Click the **+ Add All Changed Resources** button.

![Launch Setup](./images/addallchanged.png)

Click the **Save & Build for Development** button.

![Launch Setup](./images/savebuild.png)

After clicking the **Save & Build for Development** button, your Development library will be updated and your changes will be available for testing on your Platform Demo website. It can take a couple of minutes for your Launch library to update, wait until you see a green dot next to your Development library.

(FYI: sometimes the Launch library is cached in your browser so you might have to clear your cache)

Once your Launch configuration is published, go to your Platform Demo website, select and load any brand of choice and navigate to the page Login/Register.
Enter your credentials.

![Launch Setup](./images/lb_register_dtl.png)

Click the **Create Account** button. If all goes well, you should receive an email a couple of seconds later.

You've now finished this and this module!

[Go Back to Module 6](./journey-orchestration-create-account.md)

[Go Back to All Modules](../../overview.md)
