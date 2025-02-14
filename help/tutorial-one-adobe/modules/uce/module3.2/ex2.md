---
title: Create your Campaign with AJO Translation Services
description: Create your Campaign with AJO Translation Services
kt: 5342
doc-type: tutorial
exl-id: a9d674f4-6f49-4d4d-a24d-84751f3a438e
---
# 3.2.2 Create your Campaign

Go to [https://experience.adobe.com/](https://experience.adobe.com/). Click **Journey Optimizer**.

![Translations](./images/ajolp1.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxName--`.

![ACOP](./images/ajolp2.png)

## 3.2.2.1 Create your Header fragment

In the left menu, click **Fragments**. A Fragment is a reusable component within Journey Optimizer, which avoids duplication and facilitates future changes that should impact all messages, such as changes to a header or footer in an email message.

Click **Create fragment**.

![ACOP](./images/fragm1.png)

Enter the name `--aepUserLdap-- - CitiSignal - Header` and select the **Type: Visual Fragment**. Click **Create**.

![ACOP](./images/fragm2.png)

You'll then see this. In the left menu, you'll find the structure components that you can use to define the structure of the email (rows and columns).

Drag and drop a **1:1 column** from the menu into the canvas. This will be the placeholder for the logo image.

![Journey Optimizer](./images/fragm3.png)

Next, you can use Content Components to add content inside these blocks. Drag and drop an **Image** component in the first cell on the first row. Click **Browse**.

![Journey Optimizer](./images/fragm4.png)

You'll then see a popup opening, showing you your AEM Assets Media Library. Go to the folder **citi-signal-images**, click to select the image **CitiSignal-Logo-White.png** and click **Select**.

>[!NOTE]
>
>If you don't see the Citi Signal images in your AEM Assets Library, you can find them [here](../../../assets/ajo/CitiSignal-images.zip). Download them to your desktop, create the folder **citi-signal-images** and upload all the images in that folder.

![Journey Optimizer](./images/fragm5.png)

You'll then see this. Your image is white, and isn't showing yet. You should now define a background color to make the image show correctly. Click **Styles**, then click the **Background color** box.

![Journey Optimizer](./images/fragm6.png)

In the popup, change the **Hex** color code to **#8821F4** and then change focus by clicking into the **100%** field. You'll then see the new color applied to the image.

![Journey Optimizer](./images/fragm7.png)

The image is also a bit to big right now. Let's change the width by sliding the **Width** switcher to **40%**.

![Journey Optimizer](./images/fragm8.png)

Your header fragment is now ready. Click **Save** and then click the arrow to go back to the previous screen.

![Journey Optimizer](./images/fragm9.png)

Your fragment needs to be published before it can be used. Click **Publish**.

![Journey Optimizer](./images/fragm10.png)

After a couple of minutes, you'll see that you fragment's status has changed to **Live**. 
Next, you should create a new fragment for the footer of your email messages. Click **Create fragment**.

![Journey Optimizer](./images/fragm11.png)

## 3.2.2.2 Create your Footer fragment

Click **Create fragment**.

![Journey Optimizer](./images/fragm11.png)

Enter the name `--aepUserLdap-- - CitiSignal - Footer` and select the **Type: Visual Fragment**. Click **Create**.

![Journey Optimizer](./images/fragm12.png)

You'll then see this. In the left menu, you'll find the structure components that you can use to define the structure of the email (rows and columns).

Drag and drop a **1:1 column** from the menu into the canvas. This will be the placeholder for the footer content.

![Journey Optimizer](./images/fragm13.png)

Next, you can use Content Components to add content inside these blocks. Drag and drop an **HTML** component in the first cell on the first row. Click the component to select it and then, click the **</>** icon to edit the HTML source code.

![Journey Optimizer](./images/fragm14.png)

You'll then see this.

![Journey Optimizer](./images/fragm15.png)

Copy the below HTML code fragment and paste it in the **Edit HTML** window in Journey Optimizer.

```html
<!--[if mso]><table cellpadding="0" cellspacing="0" border="0" width="100%"><tr><td style="text-align: center;" ><![endif]-->
<table style="width: auto; display: inline-block;">
  <tbody>
    <tr class="component-social-container">
      <td style="padding: 5px">
        <a style="text-decoration: none;" href="https://www.facebook.com" data-component-social-icon-id="facebook">
        
        </a>
      </td>
      <td style="padding: 5px">
        <a style="text-decoration: none;" href="https://x.com" data-component-social-icon-id="twitter">
        
        </a>
      </td>
      <td style="padding: 5px">
        <a style="text-decoration: none;" href="https://www.instagram.com" data-component-social-icon-id="instagram">
         
        </a>
      </td>
    </tr>
  </tbody>
</table>
<!--[if mso]></td></tr></table><![endif]-->
```

You'll then have this. On lines 7, 12 and 17 you now need to insert a image file, using the assets in your AEM Assets library.

![Journey Optimizer](./images/fragm16.png)

Make sure that your cursor is located on line 7, and then click **Assets** in the left menu. Click **Open asset selector** to select your image.

![Journey Optimizer](./images/fragm17.png)

Open the folder **citi-signal-images** and click to select the image **Icon_Facebook.png**. Click **Select**.

![Journey Optimizer](./images/fragm18.png)

Make sure that your cursor is located on line 12, and then click **Open asset selector** to select your image.

![Journey Optimizer](./images/fragm19.png)

Open the folder **citi-signal-images** and click to select the image **Icon_X.png**. Click **Select**.

![Journey Optimizer](./images/fragm20.png)

Make sure that your cursor is located on line 17, and then click **Open asset selector** to select your image.

![Journey Optimizer](./images/fragm21.png)

Open the folder **citi-signal-images** and click to select the image **Icon_Instagram.png**. Click **Select**.

![Journey Optimizer](./images/fragm22.png)

You'll then see this. Click **Save**.

![Journey Optimizer](./images/fragm23.png)

You'll then be back in the editor. Your icons aren't visible yet because the background and the image files are all in white. To change the background color, go to **Styles** and click the **Background color** checkbox.

![Journey Optimizer](./images/fragm24.png)

Change the **Hex** color code to **#000000**.

![Journey Optimizer](./images/fragm25.png)

Change the alignment to be centered.

![Journey Optimizer](./images/fragm26.png) 

Let's add some other parts to the footer. Drag and drop an **Image** component above the HTML component you just created. Click **Browse**.

![Journey Optimizer](./images/fragm27.png) 

Click to select the image file **`CitiSignal_Footer_Logo.png`** and click **Select**.

![Journey Optimizer](./images/fragm28.png)

Go to **Styles** and click the **Background color** checkbox, let's change it to black again. Change the **Hex** color code to **#000000**.

![Journey Optimizer](./images/fragm29.png) 

Change the width to **20%** and verify that the alignment is set to be centered.

![Journey Optimizer](./images/fragm30.png)

Next, drag and drop a **Text** component under the HTML component you created. Click **Browse**.

![Journey Optimizer](./images/fragm31.png)

Copy and paste the below text by replacing the placeholder text.

```

1234 N. South Street, Anywhere, US 12345

Unsubscribe

©2024 CitiSignal, Inc and its affiliates. All rights reserved.

```

Set the **Text alignment** to be centered.

![Journey Optimizer](./images/fragm32.png)

Change the **Font color** to white, **#FFFFFF**.

![Journey Optimizer](./images/fragm33.png)

Change the **Background color** to black, **#000000**.

![Journey Optimizer](./images/fragm34.png)

Select the text **Unsubscribe** in the footer, and click the **Link** icon in the menu bar. Set the **Type** to **External Opt-out/Unsubscription** and set the url to **https://aepdemo.net/unsubscribe.html** (it's not allowed to have a blank URL for the unsubscribe link).

![Journey Optimizer](./images/fragm35.png)

You'll then have this. Your footer is now ready. Click **Save** and then click the arrow to go back to the previous page.

![Journey Optimizer](./images/fragm36.png)

Click **Publish** to publish your footer so it can be used in an email.

![Journey Optimizer](./images/fragm37.png)

After a couple of minutes, you'll see that the status of your footer has changed to **Live**.

![Journey Optimizer](./images/fragm38.png)

## 3.2.2.3 Create Fiber campagn

You'll now create a campaign. Unlike the event-based journey of the previous exercise which relies on incoming experience events or audience entries or exits to trigger a journey for 1 specific customer, campaigns target a whole audience once with unique content like newsletters, one-off promotions, or generic information or periodically with similar content sent on a regular basis like for instance birthday campaigns and reminders. 

In the menu, go to **Campaigns** and click **Create campaign**.

![Journey Optimizer](./images/oc43.png)

Select **Scheduled - Marketing** and click **Create**.

![Journey Optimizer](./images/campaign1.png)

On the campaign creation screen, configure the following:

- **Name**: `--aepUserLdap-- - CitiSignal Fiber`.
- **Description**: Fiber campaign
- **Identity type**: change to Email

![Journey Optimizer](./images/campaign2.png)

Scroll down to **Action**. For the **Action**, select **Email**. 

![Journey Optimizer](./images/campaign3.png)

Then, select an existing **Email configuration**. You'll edit the content in a couple of minutes.

![Journey Optimizer](./images/campaign3a.png)

Scroll up to **Audience**. Click **Select audience**.

![Journey Optimizer](./images/campaign2b.png)

For the **Audience**, select the audience you created in the previous step, `--aepUserLdap-- - CitiSignal Eligible for Fiber`. Click **Save**.

![Journey Optimizer](./images/campaign2a.png)

Scroll down to **Schedule**. For the **Schedule**, choose **On a specific date and time** and set a time of choice.

![Journey Optimizer](./images/campaign4.png)

You can now start creating the email message itself. Scroll up, and click **Edit content**.

![Journey Optimizer](./images/campaign5.png)

You'll then see this. For the **Subject line**, use this: 

```
{{profile.person.name.firstName}}, here's your Fiber offer!
```

Next, click **Edit email body**.

![Journey Optimizer](./images/campaign6.png)

Choose **Design from scratch**.

![Journey Optimizer](./images/campaign7.png)

You'll then see this. In the left menu, you'll find the structure components that you can use to define the structure of the email (rows and columns).

Drag and drop 4 times a **1:1 column** on the canvas, which should give you this structure:

![Journey Optimizer](./images/campaign8.png)

In the left menu, go to **Fragments**. Drag the header you created earlier onto the first component in the canvas. Drag the footer you created earlier onto the last component in the canvas.

![Journey Optimizer](./images/campaign9.png)

Click the **+** icon in the left menu. Go to **Contents** to start adding content onto the canvas.

![Journey Optimizer](./images/campaign10.png)

Drag and drop a **Text** component on the second row. 

![Journey Optimizer](./images/campaign11.png)

Select the default text in that component **Please type your text here.** and replace it by the below text. Change the alignment to **Center alignment**.

```javascript

Hi {{profile.person.name.firstName}}

As a CitiSignal customer, you're in pole position to discover our new Fiber offering. Have a look at the below offer and update your contract!

Stay connected.

```

![Journey Optimizer](./images/campaign12.png)

Drag and drop an **Image** component on the 3rd row. Click **Browse**.

![Journey Optimizer](./images/campaign13.png)

Select the AEM Assets repository that you created as part of previous modules. That repository should be named `--aepUserLdap-- - Citi Signal dev`. Click to open the folder `--aepUserLdap-- - Workfront Assets`.

![Journey Optimizer](./images/campaign15a.png)

Click to select the image **2048x2048_buynow.png**, and click **Select**.

![Journey Optimizer](./images/campaign14.png)

Your basic newsletter email is now ready. Click **Save**.

![Journey Optimizer](./images/ready.png)

Go back to the campaign dashboard by clicking the **arrow** next to the subject line text in the top-left corner.

![Journey Optimizer](./images/campaign19.png)

Click **Review to activate**.

![Journey Optimizer](./images/campaign20.png)

You may then get this error. If that is the case, then you may need to wait up to 24 hours until the audience has been evaluated, and then try to activate your campaign again. You may also need to update the schedule of your campaign to run at a later time.

![Journey Optimizer](./images/campaign21a.png)

Click **Activate**.

![Journey Optimizer](./images/campaign21.png)

Once activated, your campaign will then be scheduled to run.

![Journey Optimizer](./images/campaign22.png)

You have finished this exercise.

## Next Steps

Go to [3.2.3 Add Languages to your Email](./ex3.md)

Go back to [Module 3.2](./ajotranslationsvcs.md){target="_blank"}

Go back to [All modules](./../../../overview.md){target="_blank"}
