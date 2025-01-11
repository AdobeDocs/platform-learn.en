---
title: Adobe Journey Optimizer - Configure a trigger-based journey - Order Confirmation
description: In this section you will configure a trigger-based journey - Order Confirmation
kt: 5342
doc-type: tutorial
exl-id: b9d9b357-08d1-4f65-9e0b-46224d035602
---
# 3.4.1 Configure a trigger-based journey - Order Confirmation

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](./../../../modules/ajo-b2c/module3.1/images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxName--`. You'll then be in the **Home** view of your sandbox `--aepSandboxName--`.

![ACOP](./../../../modules/ajo-b2c/module3.1/images/acoptriglp.png)

## 3.4.1.1 Create your event

In the menu, go to **Configurations** and click **Manage** under **Events**.

![Journey Optimizer](./images/oc30.png)

On the **Events** screen, you'll see a view similar to this. Click **Create Event**.

![Journey Optimizer](./images/oc31.png)

You'll then see an empty event configuration.

First of all, give your Event a Name like this: `--aepUserLdap--PurchaseEvent`, and add a description like this: `Purchase Event`.

For **Type**, select **Unitary**.
For **Event ID Type**, select **System Generated**.

![Journey Optimizer](./images/eventidtype.png)

Next is the Schema selection. A schema was prepared for this exercise. Please use the schema `Demo System - Event Schema for Website (Global v1.1) v.1`.

After selecting the Schema, you'll see a number of fields being selected in the **Payload** section. Click the **Edit/Pencil** icon to add additional fields to this event.

![Journey Optimizer](./images/oc36.png)

You'll then see this popup. You now need to check additional checkboxes in order to access additional data when this event gets triggered.

![Journey Optimizer](./images/oc37.png)

First of all, check the checkbox on the line `--aepTenantId--`.

![Journey Optimizer](./images/oc38.png)

Next, scroll down and check the checkbox on the line `commerce`. 

![Journey Optimizer](./images/oc391.png)

Next, scroll down and check the checkbox on the line `productListItems`. Click **Ok**.

![Journey Optimizer](./images/oc39.png)

You'll then see that additional fields have been added to the event. Click **Save**.

![Journey Optimizer](./images/oc40.png)

Your new event is then saved and you'll see your event in the list of available events now.

Click on your event again to open up the **Edit Event** screen again. 
Hover over the **Payload** field again to see the 3 icons again. Click on the **View Payload** icon. 

![Journey Optimizer](./images/oc41.png)

You'll now see an example of the expected payload. Your event has a unique orchestration eventID, which you can find by scrolling down in that payload until you see `_experience.campaign.orchestration.eventID`.

![Journey Optimizer](./images/oc42.png)

The event ID is what needs to be sent to Adobe Journey Optimizer in order to trigger the journey that you'll build in the next step. Write down this eventID, as you'll need it in one of the next steps.
`"eventID": "1c8148a8ab1993537d0ba4e6ac293dd4f2a88d80b2ca7be6293c3b28d4ff5ae6"`

Click **Ok**, followed by **Cancel**.

Your event is now configured and ready to be used.

## 3.4.1.2 Create your journey

In the menu, go to **Journeys** and click **Create Journey**.

![Journey Optimizer](./images/oc43.png)

You'll then see this. Give your journey a name. Use `--aepUserLdap-- - Order Confirmation journey`. Click **Save**.

![Journey Optimizer](./images/oc45.png)

First, you need to add your event as the starting point of your journey. Search for your event `--aepUserLdap--PurchaseEvent` and drag and drop it onto the canvas. Click **Save**.

![Journey Optimizer](./images/oc46.png)

Next, under **Actions**, search for the **Email** action and add it onto the canvas.

![Journey Optimizer](./images/oc47.png)

Set the **Category** to **Marketing** and select an email surface that enables you to send email. In this case, the email surface to select is **Email**. Ensure that the checkboxes for **Clicks on email** and **email opens** are both enabled.

![ACOP](./images/journeyactions1.png)

The next step is to create your message. To do that, click **Edit content**.

![ACOP](./images/journeyactions2.png)

You now see this. Click the **Subject line** text field.

![ACOP](./images/journeyactions3.png)

In the text area start writing **Thanks for your order,** and click the **Personalization** icon.

![Journey Optimizer](./images/oc5.png)

The subject line is not done yet. Next you need to bring in the personalization token for the field **First name** which is stored under `profile.person.name.firstName`. In the left menu, scroll down to find the **Person** > **Full name** >  **First name** field and click on the **+** icon to add the personalization token into the subject line. Click **Save**.

![Journey Optimizer](./images/oc6.png)

You'll then be back here. Click **Edit email body** to create the email's content. 

![Journey Optimizer](./images/oc7.png)

In the next screen, click **Design from scratch**.

![Journey Optimizer](./images/oc8.png)

In the left menu, you'll find the structure components that you can use to define the structure of the email (rows and columns).

Drag and drop 8 times a **1:1 column** on the canvas, which should give you this:

![Journey Optimizer](./images/oc9.png)

In the left menu, go to **Fragments**. Drag the header you created earlier in [exercise 3.1.2.1](./../module3.1/ex2.md) onto the first component in the canvas. Drag the footer you created earlier in [exercise 3.1.2.2](./../module3.1/ex2.md) onto the last component in the canvas.

![Journey Optimizer](./images/fragm1.png)

Click the **+** icon in the left menu. Go to **Contents** to start adding content onto the canvas.

![Journey Optimizer](./images/oc10.png)

Go to **Contents** and drag and drop an **Image** component on the second row. Click **Browse**.

![Journey Optimizer](./images/oc15.png)

Open the folder **citi-signal-images**, click to select the image **citisignal-preparing.png**, and click **Select**.

![Journey Optimizer](./images/oc14.png)

Under **Styles**, change the width to **40%**.

![Journey Optimizer](./images/oc14a.png)

Next, go to **Contents** and drag and drop a **Text** component on the third row. 

![Journey Optimizer](./images/oc17.png)

Select the default text in that component **Please type your text here.** and replace it by the below text:

```javascript

You’re one step closer!

Hi 

We've received your order details!

We will also send you a separate email containing your VAT Invoice.

We'll be back in touch with you as soon as we've finished packing your package. Please read carefully the Order Information detailed below.
```

![Journey Optimizer](./images/oc18.png)

Put the cursor next to the text **Hi** and click **Add Personalization**.

![Journey Optimizer](./images/oc19.png)

Navigate to the **Person** > **Full name** > **First name** field and click on the **+** icon to add the personalization token into the subject line. Click **Save**.

![Journey Optimizer](./images/oc20.png)

You'll then see this:

![Journey Optimizer](./images/oc21.png)

Next, go to **Contents** and drag and drop a **Text** component on the fourth row. 

![Journey Optimizer](./images/oc22.png)

Select the default text in that component **Please type your text here.** and replace it by the below text:

`Order Information`

Change the font size to **26px** and center your text in this cell. You'll then have this:

![Journey Optimizer](./images/oc23.png)

Next, go to **Contents** and drag and drop an **HTML** component on the fifth row. Click the HTML component and then click **Show the source code**.

![Journey Optimizer](./images/oc24.png)

In the **Edit HTML** popup, paste this HTML:

```<table><tbody><tr><td><b>Items purchased</b></td><td></td><td><b>Quantity</b></td><td><b>Subtotal</b></td></tr><tr><td colspan="4" width="500"><hr></td></tr></tbody></table>```

Click **Save**.

![Journey Optimizer](./images/oc25.png)

You'll then have this. Click **Save** to save your progress.

![Journey Optimizer](./images/oc26.png)

Go to **Contents** and drag and drop an **HTML** component on the sixth row. Click the HTML component and then click **Show the source code**.

![Journey Optimizer](./images/oc57.png)

In the **Edit HTML** popup, paste this HTML:

```{{#each xxx as |item|}}<table width="500"><tbody><tr><td><img src="{{item.--aepTenantId--.core.imageURL}}" width="100"></td><td><table><tbody><tr><td><b>{{item.name}}</b><br>{{item.--aepTenantId--.core.subCategory}}<br><b>{{item.priceTotal}}</b><br>&nbsp;<br>Article no: {{item.SKU}}</td></tr></tbody></table></td><td>{{item.quantity}}</td><td><b>{{item.priceTotal}}</b></td></tr></tbody></table>{{/each}}```

You'll then have this:

![Journey Optimizer](./images/oc58.png)

You now have to replace **xxx** by a reference to the productListItems object that is part of the event that triggers the journey.

![Journey Optimizer](./images/oc59.png)

First, delete **xxx** in your HTML code first.

![Journey Optimizer](./images/oc60.png)

In the left menu, click **Contextual attributes**. This context is passed to the message from the journey. 

You'll then see this. Click the arrow next to **Journey Orchestration** to drill deeper.

![Journey Optimizer](./images/oc601.png)

Click the arrow next to **Events** to drill deeper.

![Journey Optimizer](./images/oc62.png)

Click the arrow next to `--aepUserLdap--PurchaseEvent` to drill deeper.

![Journey Optimizer](./images/oc63.png)

Click the arrow next to **productListItems** to drill deeper.

![Journey Optimizer](./images/oc64.png)

Click the **+** icon next to **Name** to add it to the canvas. You'll then have this. You now need to select  **.name** as indicated in the below screenshot, and then you should remove **.name**.

![Journey Optimizer](./images/oc65.png)

You'll then have this. Click **Save**.

![Journey Optimizer](./images/oc66.png)

You'll be back in the Email Designer now. Click **Save** to save your progress.

![Journey Optimizer](./images/oc67.png)

Next, go to **Contents** and drag and drop an **HTML** component on the seventh row. Click the HTML component and then click **Show the source code**.

![Journey Optimizer](./images/oc68.png)

In the **Edit HTML** popup, paste this HTML:

```<table><tbody><tr><td><b>Subtotal</b><br>Delivery charge (included)</td><td align="right"><b>xxx</b><br><b>5</b></td></tr><tr><td colspan="2" width="500"><hr></td></tr><tr><td><b>Total including VAT</b></td><td align="right"><b>xxx</b></td></tr></tbody></table>```

There are 2 references of **xxx** in this HTML code. You now have to replace each **xxx** by a reference to the productListItems object that is part of the event that triggers the journey.

![Journey Optimizer](./images/oc69.png)

First, delete the first **xxx** in your HTML code.

![Journey Optimizer](./images/oc71.png)

In the left menu, click **Contextual Attributes**.
Click the arrow next to **Journey Orchestration** to drill deeper.

![Journey Optimizer](./images/oc72.png)

Click the arrow next to **Events** to drill deeper.

![Journey Optimizer](./images/oc722.png)

Click the arrow next to `--aepUserLdap--PurchaseEvent` to drill deeper.

![Journey Optimizer](./images/oc73.png)

Click the arrow next to **Commerce** to drill deeper.

![Journey Optimizer](./images/oc733.png)

Click the arrow next to **Order** to drill deeper.

![Journey Optimizer](./images/oc74.png)

Click the **+** icon next to **Price Total** to add that to the canvas.

![Journey Optimizer](./images/oc75.png)

You'll then have this. Now delete the second **xxx** in your HTML code. 

![Journey Optimizer](./images/oc76.png)

Click the **+** icon next to **Price Total** again to add that to the canvas. 
You can also add the field **Currency** from within the **Order** object onto the canvas, as you can see here. 
When you're done, click **Save** to save your changes.

![Journey Optimizer](./images/oc77.png)

You'll then be back in the Email Designer. Click **Save** again.

![Journey Optimizer](./images/oc78.png)

Go back to the message dashboard by clicking the **arrow** next to the subject line text in the top-left corner.

![Journey Optimizer](./images/oc79.png)

Click the arrow in the top left corner to go back to your journey.

![Journey Optimizer](./images/oc79a.png)

Click **Save** to close your email action.

![Journey Optimizer](./images/oc79b.png)

Click **Publish** to publish your journey.

![Journey Optimizer](./images/oc511.png)

Click **Publish** again.

![Journey Optimizer](./images/oc512.png)

Your journey is now published.

![Journey Optimizer](./images/oc513.png)

## 3.4.1.5 Update your Adobe Experience Platform Data Collection Client property

Go to [Adobe Experience Platform Data Collection](https://experience.adobe.com/launch/) and select **Tags**.

This is the Adobe Experience Platform Data Collection Properties page you saw before.

![Properties page](./../../../modules/datacollection/module1.1/images/launch1.png) 

In **Getting Started**, Demo System created two Client properties for you: one for the website and one for the mobile app. Find them by searching for `--aepUserLdap--` in the **[!UICONTROL Search]** box. Click to open the **Web** property.

![Search box](./../../../modules/datacollection/module1.1/images/property6.png)

Go to **Data Elements**. Search and open the data element **XDM - Purchase**.

![Journey Optimizer](./images/oc91.png)

You'll then see this. Navigate to the field **_experience.campaign.orchestration.eventID** and fill out your eventID here. The eventID to fill out here, is the eventID you created as part of exercise 3.4.1.1 Click **Save** or **Save to Library**.

![Journey Optimizer](./images/oc92.png)

Save your changes in your property, and then publish your changes by updating your development library.

![Journey Optimizer](./images/oc93.png)

Your changes are now deployed and can be tested.

## 3.4.1.6 Test your order confirmation email using the demo website

Let's test the updated journey by buying a product on the demo website.

Go to [https://dsn.adobe.com](https://dsn.adobe.com). After logging in with your Adobe ID, you'll see this. Click the 3 dots **...** on your website project and then click **Run** to open it.

![DSN](./../../datacollection/module1.1/images/web8.png)

You'll then see your demo website open up. Select the URL and copy it to your clipboard.

![DSN](../../gettingstarted/gettingstarted/images/web3.png)

Open a new incognito browser window.

![DSN](../../gettingstarted/gettingstarted/images/web4.png)

Paste the URL of your demo website, which you copied in the previous step. You'll then be asked to login using your Adobe ID.

![DSN](../../gettingstarted/gettingstarted/images/web5.png)

Select your account type and complete the login process.

![DSN](../../gettingstarted/gettingstarted/images/web6.png)

You'll then see your website loaded in an incognito browser window. For every exercise, you'll need to use a fresh, incognito browser window to load your demo website URL.

![DSN](../../gettingstarted/gettingstarted/images/web7.png)

Have a look at the Profile Viewer panel and the Real-time Customer Profile with the **Experience Cloud ID** as the primary identifier for thi currently unknown customer.
      
![Demo](./../../../modules/datacollection/module1.2/images/pv2.png)

Go to the Register/Login page. Click **CREATE AN ACCOUNT**.
  
![Demo](./../../../modules/datacollection/module1.2/images/pv9.png)
  
Fill out your details and click **Register** after which you'll be redirected to the previous page. 

![Demo](./../../../modules/datacollection/module1.2/images/pv10.png)

Add any product to your cart

![Journey Optimizer](./images/cart1a.png)

Go to the **Cart** page. Click **Checkout**.

![Journey Optimizer](./images/cart1.png)

Next, verify the fields and complete if necessary. Click **Proceed**.

![Journey Optimizer](./images/cart2.png)

Click **Confirm Order**.

![Journey Optimizer](./images/cart2a.png)

Your order is now confirmed.

![Journey Optimizer](./images/cart2b.png)

You'll then receive your order confirmation email within seconds.

![Journey Optimizer](./images/oc98.png)

You have finished this exercise.

Next Step: [3.4.2 Configure a batch-based newsletter journey](./ex2.md)

[Go Back to Module 3.4](./journeyoptimizer.md)

[Go Back to All Modules](../../../overview.md)
