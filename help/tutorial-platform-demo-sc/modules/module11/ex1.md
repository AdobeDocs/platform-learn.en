---
title: Real-time CDP - Build a segment and take action - Build a segment and enable Streaming Segmentation
description: Real-time CDP - Build a segment and take action - Build a segment and enable Streaming Segmentation
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: 
---

# 11.1 Build a segment and enable Streaming Segmentation

In this exercise, you'll create a segment by making use of Adobe Experience Platform's segment builder.

The URL to login to Adobe Experience Platform is: [https://platform.adobe.com](https://platform.adobe.com)

## Story

In today's world, responding to a customer's behavior needs to be real-time. One of the ways of responding to customer behavior in real-time is by using a segment, on the condition that the segment qualifies in real-time. In this exercise, you need to build out a segment, taking into account real activity on the website that we've been using.

## Identify the behavior you want to react to

Go to your Platform Demo website.

You'll be redirected to the **Admin** page

![Demo](./images/1.png)
  
On the **Admin** page, go to **Select LDAP** (for Module 11, selecting an LDAP is a requirement). Select your LDAP and click **Save**.

![Demo](./images/ldap.png)

Go back to the **Admin** page.

![Demo](./images/1a.png)

Go to **Select Brand**.
  
![Demo](./images/2.png)
  
Select a brand from the list of available brands. Click **Save**. In this example, we'll use **Luma Retail**.
  
![Demo](./images/3.png)
  
Wait 10 seconds for the brand to load. You'll be redirect to the Admin Home.
  
From Admin Home, click the logo of your brand.

![Demo](./images/adm_home.png)

You'll then be redirected to the **Luma Retail** homepage.

![Demo](./images/lb_home.png)

In this example, I want to respond to a specific customer viewing a specific product.
By scrolling down on the **Luma Retail** homepage, I can see multiple products and I'm going to pick the product **Zeppelin Yoga Pant**.

![Data Ingestion](./images/homenadia.png)

So when somebody visits the product page for **Zeppelin Yoga Pant**, I want to be able to take action. The first thing to do to take action, is define a segment.

![Data Ingestion](./images/homenadiapp.png)

## Create the Segment

To create the segment as defined above, log in to Adobe Experience Platform by going to this URL: [https://platform.adobe.com](https://platform.adobe.com)

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./images/home.png)

In the menu on the left side, go to **Segments**.

![Segmentation](./images/menuseg.png)

On this page, you can see an overview of all existing segments.

![Segmentation](./images/segmentation.png)

Click on the **Create Segment** button to start creating a new segment.

![Segmentation](./images/createnewsegment.png)

As mentioned above, I'd like to build a segment out of all customers that have viewed the product **Zeppelin Yoga Pant**.

To build out this segment, you need to add an event. You can find all events by clicking on the **Events** icon in the **Segments** menu bar.

Next, you'll see the top level **XDM ExperienceEvent** node.

To find customers that have visited the **Zeppelin Yoga Pant** product, click on **XDM ExperienceEvent**.

![Segmentation](./images/findee.png)

Scroll down to **Product List Items** and click it.

![Segmentation](./images/see.png)

Select **Name** and drag and drop the **Name** object from the left **Product List Items** menu onto the segment builder canvas into the **Events** section.

![Segmentation](./images/eewebpdtlname1.png)

The comparison parameter should be **equals** and in the input field, enter `Zeppelin Yoga Pant`.

![Segmentation](./images/pv.png)

Every time you add an element to the segment builder, you can click the **Refresh Estimate** button to get a new estimate of the population in your segment.

As we're using a shared environment, you also need to add your **ldap** as a filter for this segment.

In the **Events** search box, enter **ldap**. Take the second result, which references the path **XDM ExperienceEvent > Apac Sc > brand > ldap**.

![Segmentation](./images/ldap1.png)

Drag and drop **ldap** onto your Segment Rule, under the `Zeppelin Yoga Pant` rule.

![Segmentation](./images/ldap2.png)

Enter your ldap:

![Segmentation](./images/ldap3.png)

Your **Rules** should now look like this:

![Segmentation](./images/ldap4.png)

Finally, let's give your segment a name and save it.

As a naming convention, we'll use:

* `dap - Interest in Zeppelin Yoga Pant (RTCDP - ldap)`

Please replace **ldap** with your assigned number, like this:
`vangeluw - Interest in Zeppelin Yoga Pant (RTCDP - vangeluw)`

![Segmentation](./images/segmentname.png)

It's also important to note the **Streaming** switch.

![Segmentation](./images/streaming.png)

By enabling the **Streaming** switch, your segment will qualify in real-time and will be available for activation in real-time.

Then, click the **Save** button to save your segment, after which you'll be taken back to the Segment overview  page.

![Segmentation](./images/savedsegment.png)

When you now go back to the Platform Demo - website and refresh the homepage, you should see the Streaming Segment that you just built already qualify for your profile on the X-Ray panel.

![Segmentation](./images/xraystrseg.png)

Next Step: [11.2 Review how to configure DV360 Destination using Destinations](./ex2.md)

[Go Back to Module 11](./real-time-cdp-build-a-segment-take-action.md)

[Go Back to All Modules](../../overview.md)
