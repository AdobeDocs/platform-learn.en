---
title: Bootcamp - Blending physical and digital - Use the mobile app and trigger a beacon entry
description: Bootcamp - Blending physical and digital - Use the mobile app and trigger a beacon entry
jira: KT-5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
exl-id: c33c973b-db8a-49ce-bd6c-a6c4fbe579a0
---
# 3.1 Use the mobile app and trigger a beacon entry

## Install the mobile app

Before you install the app, you need to enable **Tracking** on your iOS device. To do so, go to **Settings** > **Privacy & Security** > **Tracking** and ensure that the option **Allow Apps to Request to Track**.

![DSN](./../uc3/images/app4.png)

Go to the Apple App Store and search for `aepmobile-bootcamp`. Click **Install** or **Download**.

![DSN](./../uc3/images/app1.png)

Once the app is installed, click **Open**.

![DSN](./../uc3/images/app2.png)

Click **OK**.

![DSN](./../uc3/images/app9.png)

Click **Allow**.

![DSN](./../uc3/images/app3.png)

Click **I agree**.

![DSN](./../uc3/images/app7.png)

Click **Allow While Using App**.

![DSN](./../uc3/images/app8.png)

Click **Allow**.

![DSN](./../uc3/images/app5.png)

You're now in the app, on the homepage, ready to go through the customer journey.

![DSN](./../uc3/images/app12.png)

## Customer journey flow

First of all, you need to login. Click **Login**.

![DSN](./images/app13.png)

After creating your account in the previous exercises, you saw this on the website. You now need to reuse the email address of the account you created in the app to login.
  
![Demo](./images/pv1.png)

Enter the email address you used on the website here and click **Login**.

![DSN](./images/app14.png)

You'll then get a confirmation that you're logged in, and you'll receive a push notification.

![DSN](./images/app15.png)

Go back to the homepage in the app, and you'll see additional capabilities appear.

![DSN](./images/app17.png)

First, go to **Products**. Click on any product, in this example **Coffee to go**.

![DSN](./images/app19.png)

You'll see the **Coffee to go** product page in the app.

![DSN](./images/app20.png)

You'll now simulate a beacon entry event in an offline store location. The goal of simulating this is to personalize the customer experience on the in-store screens. To visualize the in-store experience, a page has been created that will dynamically show the information that is relevant to the customer that just entered the store. 

Before continuing, please open this web page on your computer: [https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/screen.html](https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/screen.html)

You'll then see this:

![DSN](./images/screen1.png)

Next, go back to the homepage. Click the **beacon** icon.

![DSN](./images/app23.png)

You'll then see this. First, select **Bootcamp Screen Beacon** and then click the **entry** button. This will allow you to simulate a beacon entry.

![DSN](./images/app21.png)

Now, have a look at the in-store screen. You'll see the last product you viewed appear there within 5 seconds.

![DSN](./images/screen2.png)

Then, go back to **Products**. Click on any product, in this example **Beach blanket Tan**.

![DSN](./images/app22.png)

Next, go back to the homepage. Click the **beacon** icon.

![DSN](./images/app23.png)

You'll then see this. First, select **Bootcamp Screen Beacon** and then click the **entry** button again. This will allow you to simulate a beacon entry.

![DSN](./images/app21.png)

Now, have a look at the in-store screen again. You'll see the last product you viewed appear there within 5 seconds.

![DSN](./images/screen3.png)

Let's also have a look at your Profile Viewer on the website now. You'll see a lot of events that were added there, just to show that any interaction with a customer is collected and stored in Adobe Experience Platform.

![DSN](./images/screen4.png)

In the next exercises, you'll configure and test your own beacon entry journey.

Next Step: [3.2 Create your event](./ex2.md)

[Go Back to User Flow 3](./uc3.md)

[Go Back to All Modules](../../overview.md)
