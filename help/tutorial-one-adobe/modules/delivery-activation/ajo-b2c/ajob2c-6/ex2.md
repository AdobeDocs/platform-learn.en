---
title: Landing Pages in Adobe Journey Optimizer
description: Landing Pages in Adobe Journey Optimizer
kt: 5342
doc-type: tutorial
exl-id: bf499aad-91d0-4fb5-a38c-db8fcd56480b
---
# 3.6.2 Landing Pages

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxName--`. You'll then be in the **Home** view of your sandbox `--aepSandboxName--`.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

## 3.6.2.1 Subscription Lists

Landing Pages in Adobe Journey Optimizer work together with **Subscription Lists**. In order to set up landing pages, you need to configure **Subscription Lists** first. 

CitiSignal would like to ask their customers about their interest in the following domains:

- Smart Home
- Work From Home
- Online Gaming

Once a customer has indicated their interest in either one of these domains, that customer should be added to a specific list so that they can be targeted with specific content afterwards as part of upcoming campaigns.

You will now create 3 subscription lists. 

In the left menu, go to **Subscription Lists**. Click **Create subscription list**.

![Landing Pages](./images/lp1.png)

For **Title**, use: `--aepUserLdap--_SL_Interest_in_Smart_Home`. 
For **Description**, use: `Interest in Smart Home`. 

Click **Submit**.

![Landing Pages](./images/lp2.png)

Click **Create subscription list** to create another list.

![Landing Pages](./images/lp3.png)

For **Title**, use: `--aepUserLdap--_SL_Interest_WFH`. 
For **Description**, use: `Interest in Work From Home`. 

Click **Submit**.

![Landing Pages](./images/lp4.png)

Click **Create subscription list** to create another list.

![Landing Pages](./images/lp5.png)

For **Title**, use: `--aepUserLdap--_SL_Interest_Online_Gaming`. 
For **Description**, use: `Interest in Online Gaming`. 

Click **Submit**.

![Landing Pages](./images/lp6.png)

You've now created the 3 lists you need.

![Landing Pages](./images/lp7.png)

## 3.6.2.2 Landing Page Preset

In order to use landing pages in Adobe Journey Optimizer, a preset needs to be created.

In the left menu, go to **Administration** > **Channels** and then select **Landing page presets**. 

Click **Create landing page preset**.

![Landing Pages](./images/lp8.png)

For the field **Name**, use: `--aepUserLdap-- - CitiSignal LP` and select the subdomain that is available in your instance. 

>[!NOTE]
>
>If you don't see a subdomain in your instance, please check with your AJO admin to have one added.

Click **Submit**.

![Landing Pages](./images/lp9.png)

Your landing page preset has now been created.

![Landing Pages](./images/lp10.png)

## 3.6.2.3 Landing Page

You can now create your landing page. In the left menu, go to **Content Management** > **Landing Pages**. 

Click **Create landing page**.

![Landing Pages](./images/lp11.png)

For the field **Title**, use: `vangeluw - CitiSignal Interests`. Next, select the **Landing Page Preset** that you configured in the previous step.

Click **Create**.

![Landing Pages](./images/lp12.png)

You should then see this.

![Landing Pages](./images/lp13.png) 

Change the field **Page Name** to `--aepUserLdap-- - CitiSignal Interests`. 

Enter this custom name uner **Access settings**: `--aepUserLdap---citisignal-interests`.

Click **Open Designer**.

![Landing Pages](./images/lp14.png) 

Select **Design from scratch**.

![Landing Pages](./images/lp15.png) 

You should then see this.

![Landing Pages](./images/lp16.png) 

Add a structure component **1:1 column** to the canvas.

![Landing Pages](./images/lp17.png)

Add a content component **Form** to the canvas.

![Landing Pages](./images/lp18.png)

Update the field **Label** for **Checkbox 1** to `Keep me updated about CitiSignal's offering for Smart Home`.

Ensure that the checkbox **Opt in if checked** is enabled, and that **Subscription Llist** is selected.

Then, click **Select subscription list**.

![Landing Pages](./images/lp19.png)

Next, select the list `--aepUserLdap--_SL_Interest_in_Smart_Home` and click **Select**.

![Landing Pages](./images/lp20.png)

Click **+ Add field** and then select **Checkbox**.

![Landing Pages](./images/lp21.png)

You should then see this.

![Landing Pages](./images/lp22.png)

Update the field **Label** for **Checkbox 2** to `Keep me updated about CitiSignal's offering for Work From Home`.

Ensure that the checkbox **Opt in if checked** is enabled, and that **Subscription Llist** is selected.

Then, click **Select subscription list**.

![Landing Pages](./images/lp23.png)

Next, select the list `--aepUserLdap--_SL_Interest_WFH` and click **Select**.

![Landing Pages](./images/lp24.png)

Click **+ Add field** and then select **Checkbox**.

![Landing Pages](./images/lp25.png)

You should then see this.

![Landing Pages](./images/lp26.png)

Update the field **Label** for **Checkbox 3** to `Keep me updated about CitiSignal's offering for Online Gaming`.

Ensure that the checkbox **Opt in if checked** is enabled, and that **Subscription Llist** is selected.

Then, click **Select subscription list**.

![Landing Pages](./images/lp27.png)

Next, select the list `--aepUserLdap--_SL_Interest_Online_Gaming` and click **Select**.

![Landing Pages](./images/lp28.png)

You should then see this.

![Landing Pages](./images/lp29.png)

Go to the form field **CALL TO ACTION**.

Update the following fields:

- **Text** - Button label: `Save`.
- **Confirmation action**: select **Confirmation text**.
- **Confirmation text**: use: `Thanks for updating your preferences!`
- **Error action**: select **Error text**.
- **On error text**: use: `There was an error updating your preferences.`

Click **Save** and then click the arrow in the top left corner to go back to the previous screen.

![Landing Pages](./images/lp30.png)

Click **Publish**.

![Landing Pages](./images/lp31.png)

Click **Publish** again.

![Landing Pages](./images/lp32.png)

Your landing page is now published and can be used in an email.

![Landing Pages](./images/lp33.png)

## 3.6.2.4 Include Landing Page in Email

In exercise 3.1 you created a journey that is called `--aepUserLdap-- - Registration Journey`.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/published.png)

You should now update the email message in that journey to include the link to the landing page.

In the left menu, go to **Journeys** and click to open the journey `--aepUserLdap-- - Registration Journey`.

![Landing Pages](./images/lp34.png)

Click **More...** and then select **Create a new version**.

![Landing Pages](./images/lp35.png)

Click **Create a new version**.

![Landing Pages](./images/lp36.png)

Click to select the **Email** action, and then select **Edit content**.

![Landing Pages](./images/lp37.png)

Click **Edit email body**.

![Landing Pages](./images/lp38.png)

You should then see something like this. Add a new structure component **1:1 column** to the canvas.

![Landing Pages](./images/lp39.png)

Add a new content component **Text** in the newly created structure component.

![Landing Pages](./images/lp40.png)

Paste the following text in the **Text** content component.

`Would you like to hear from us about Smart Home news? Do you work from home and would you like to hear our tips? Or are you an avid online gamer and do you want to receive our game reviews? Click here to update your preferences and interests!`

Style your text to look like this, and then select the word `here`. Click the **link** icon.

Set the **Type** of the link to **Landing page** and set the field **Target** to **Blank**.

Click the **edit** icon to select the landing page to link.

![Landing Pages](./images/lp41.png)

Select the landing page `--aepUserLdap-- - CitiSignal Interests`. Click **Select**.

![Landing Pages](./images/lp42.png)

You should then see this. Click **Save**.

![Landing Pages](./images/lp43.png)

Click the arrow in the top left corner to go back to the previous screen.

![Landing Pages](./images/lp44.png)

Click the arrow in the top left corner to go back to the previous screen again.

![Landing Pages](./images/lp45.png)

Click **Save**.

![Landing Pages](./images/lp46.png)

Click **Publish**.

![Landing Pages](./images/lp47.png)

Click **Publish** again.

![Landing Pages](./images/lp48.png)

Your changes have now been published and you can test your journey.

![Landing Pages](./images/lp49.png)

## 3.6.2.5 Test your journey and landing page

Go to [https://dsn.adobe.com](https://dsn.adobe.com). After logging in with your Adobe ID, you'll see this. Click the 3 dots **...** on your website project and then click **Run** to open it.

![DSN](./../../datacollection/dc1.1/images/web8.png)

You'll then see your demo website open up. Select the URL and copy it to your clipboard.

![DSN](../../../getting-started/gettingstarted/images/web3.png)

Open a new incognito browser window.

![DSN](../../../getting-started/gettingstarted/images/web4.png)

Paste the URL of your demo website, which you copied in the previous step. You'll then be asked to login using your Adobe ID.

![DSN](../../../getting-started/gettingstarted/images/web5.png)

Select your account type and complete the login process.

![DSN](../../../getting-started/gettingstarted/images/web6.png)

You'll then see your website loaded in an incognito browser window. For every exercise, you'll need to use a fresh, incognito browser window to load your demo website URL. Go to **Sign In**

![DSN](../../../getting-started/gettingstarted/images/web7.png)

Click **CREATE AN ACCOUNT**. Fill out your details and click **Register**.
  
![Demo](./../../../../modules/delivery-activation/datacollection/dc1.2/images/pv9.png)
  
You'll now be redirected to the homepage. Open the Profile Viewer panel and go to Real-time Customer Profile. On the Profile Viewer panel, you should see all of your personal data displayed, like your newly added email and phone identifiers.

![Demo](./../../../../modules/delivery-activation/datacollection/dc1.2/images/pv10.png)
  
1 minute after having created your account, you'll receive your account creation email from Adobe Journey Optimizer.

Click the link in the email to update your preferences.

![Launch Setup](./images/email.png)

You should then see the form that you created. Enable some checkboxes and click **Save**.

![Launch Setup](./images/email1.png)

You should then see a confirmation message.

![Launch Setup](./images/email2.png)

## 3.6.2.6 Subscription List Reporting

To view the available reporting on subcription lists, go to **Subscription lists** in the left menu and click to open one pf the subscription lists you configured before.

![Landing Pages](./images/lp50.png)

Click **Report**.

![Landing Pages](./images/lp51.png)

You should then see the overview of the list, with the quantity of people that have subscribed or unsubscribed from it.

![Landing Pages](./images/lp52.png)

## Next Steps

Go to [3.6.3 AJO and GenStudio for Performance Marketing](./ex3.md)

Go back to [Adobe Journey Optimizer: Content Management](./ajocontent.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
