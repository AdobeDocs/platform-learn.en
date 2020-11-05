---
title: Offer Decisioning - Configure your Offers and Offer Activity ID
description: Offer Decisioning - Configure your Offers and Offer Activity ID
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
---

# 14.2 Configure your Offers and Offer Activity

## 14.2.1 Create your Personalized Offers

In this exercise, you'll create four **Personalized Offers**. Here are the details to take into account when creating those offers:

|Name | Date Range | Image Link | Priority | Eligibility  |  Cap/User | Language| 
|-----|------------|------------|:--------:|--------------|:---------:|:-------:|
|**ldap** - Nadia Elements Shell | now - 1 month later | https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/2d46bee7e82aa3583a103ac6405fb3b4_1.jpg | 25 | all - Female Profiles  | 10 | English | 
|**ldap** - Radiant Tee | now - 1 month later  | https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/58ae7e91a9bac17cdf92a178d6e25186_1.jpg | 15 | all - Female Profiles  | 10 | English |
|**ldap** - Zeppelin Yoga Pant | now - 1 month later | https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/108da1111c1a0ce5dbf80fdf9c84508e_1.jpg | 25 | all - Male Profiles | 10 | English |
|**ldap** - Proteus Fitness Jackshirt | now - 1 month later | https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/7bb37821cae9587a969c713a34f92490_1.jpg | 15 | all - Male Profiles | 10 | English |
 
>[!NOTE]
>
>Just like in previous modules, whenever you see **ldap**, you need to replace that by your own specific ldap. 

Go to **Browse**.

![Decision Rule](./images/offers1.png)

Click **+ Create Offer**.

![Decision Rule](./images/createoffer.png)

You'll then see this popup. Select **Personalized offer** and click **Next**.

![Decision Rule](./images/offers2.png)

You're now on the **Details** view. 

![Decision Rule](./images/offers3.png)

In this case, you need to configure the offer **ldap** - Nadia Elements Shell. Use the information in the table above to fill out the fields. Don't forget to replace **ldap** by your ldap. In this example, the name of the Personalized Offer is **vangeluw - Nadia Elements Shell**. 

Once done, you should have this:

![Decision Rule](./images/offers4.png)

Click **Next**.

![Decision Rule](./images/next.png)

You now need to create **Representations**. Representations are a combination of a **Placement** and a real asset.

For **Representation 1**, select:

- Channel: Web
- Placement: Web - Image

Next, you need to add content. In this case that means adding the Image Link.

Click **Add Content**.

![Decision Rule](./images/addcontent1.png)

You'll then see this popup.

![Decision Rule](./images/addcontent2.png)

Fill out these fields:

- Name: use **ldap** - Nadia Elements Shell
- Public Location: use the Image Link from the above table, in this case: https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/2d46bee7e82aa3583a103ac6405fb3b4_1.jpg
- Language: English

You should now see this:

![Decision Rule](./images/addcontent3.png)

Click **Save**.

![Decision Rule](./images/save.png)

Next, click **+ Add representation**.

![Decision Rule](./images/addrep.png)

You'll then see this:

![Decision Rule](./images/addcontentrep20.png)

For **Representation 2**, select:

- Channel: Email
- Placement: Email - Image

Next, you need to add content. In this case that means adding the Image Link.

Click **Add Content**.

![Decision Rule](./images/addcontentrep21.png)

You'll then see this popup.

![Decision Rule](./images/addcontent2.png)

Fill out these fields:

- Name: use **ldap** - Nadia Elements Shell
- Public Location: use the Image Link from the above table, in this case: https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/2d46bee7e82aa3583a103ac6405fb3b4_1.jpg
- Language: English

You should now see this:

![Decision Rule](./images/addcontent3.png)

Click **Save**.

![Decision Rule](./images/save.png)

You'll then see this:

![Decision Rule](./images/addcontentrep3.png)

Click **Next**.

![Decision Rule](./images/next.png)

You'll then see this:

![Decision Rule](./images/constraints.png)

Select **Segment of visitors** and click the **+** icon for the Rule **all - Female Customers**.

![Decision Rule](./images/constraints1.png)

 You'll then see this. Fill out the **Priority** and the **Cap/User** as indicated in the above table.

![Decision Rule](./images/constraints2.png)

Click **Next**.

![Decision Rule](./images/next.png)

You'll then see an overview of your new **Personalized Offer**.

![Decision Rule](./images/offeroverview.png)

Click **Finish**.

![Decision Rule](./images/finish.png)

Finally, click **Save and approve**.

![Decision Rule](./images/saveapprove.png) 

You'll then see your newly created Personalized Offer become available in the Offers Overview:

![Decision Rule](./images/offeroverview.png)  

You should now repeat the above steps to create the three other Personalized Offers for the products Radiant Tee, Zeppelin Yoga Pant and Proteus Fitness Jackshirt.

When done, your **Offer Overviews** screen for **Personalized Offers** should show all your offers.

![Final Offers](./images/finaloffers.png)

## 14.2.2 Create your Fallback Offer

After having created four Personalized Offers, you should now configure a **Fallback Offer**.

Make sure you're in the **Browse** view:

![Final Offers](./images/finaloffers.png)

Click **+ Create Offer**.

![Decision Rule](./images/createoffer.png)

You'll then see this popup. Select **Fallback offer** and click **Next**.

![Decision Rule](./images/foffers2.png)

You'll then see this:

![Decision Rule](./images/foffers3.png)

Provide a name for your fallback offer: `ldap - Fallback Offer`, where `ldap` is your LDAP id, e.g. `vangeluw`.

![Decision Rule](./images/foffers4.png)

Click **Next**.

![Decision Rule](./images/next.png)

You now need to create **Representations**. Representations are a combination of a **Placement** and a real asset.

For **Representation 1**, select:

- Channel: Web
- Placement: Web - Image

Next, you need to add content. In this case that means adding the Image Link.

Click **Add Content**.

![Decision Rule](./images/addcontent1.png)

You'll then see this popup.

![Decision Rule](./images/addcontent2.png)

Fill out these fields:

- Name: use **ldap** - Set of Sprite Yoga Straps
- Public Location: use this Image Link: https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/747f7399476859141d760fa122aca600_1.jpg
- Language: English

You should now see this:

![Decision Rule](./images/faddcontent3.png)

Click **Save**.

![Decision Rule](./images/save.png)

Next, click **+ Add representation**.

![Decision Rule](./images/addrep.png)

For **Representation 2**, select:

- Channel: Email
- Placement: Email - Image

Next, you need to add content. In this case that means adding the Image Link.

Click **Add Content**.

![Decision Rule](./images/addcontentrep21.png)

You'll then see this popup.

![Decision Rule](./images/addcontent2.png)

Fill out these fields:

- Name: use **ldap** - Set of Sprite Yoga Straps
- Public Location: use this Image Link: https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/747f7399476859141d760fa122aca600_1.jpg
- Language: English

You should now see this:

![Decision Rule](./images/faddcontent3.png)

Click **Save**.

![Decision Rule](./images/save.png)

You'll then see this:

![Decision Rule](./images/faddcontentrep3.png)

Click **Next**.

![Decision Rule](./images/next.png)

You'll then see an overview of your new **Fallback Offer**.

![Decision Rule](./images/fofferoverview.png)

Click **Finish**.

![Decision Rule](./images/finish.png)

Finally, click **Save and approve**.

![Decision Rule](./images/saveapprove.png) 

In your **Offer Overviews** screen, you'll now see this:

![Final Offers](./images/ffinaloffers.png)

## 14.2.3 Create your Collection

A Collection is used to **filter** out a sub-set of offers from the personalized offer list and use that as part of an offer activity in order to speed up the decision process. 

Go to **Collections**.

![Decision Rule](./images/collections.png)

Click **+Create Collection**.

![Decision Rule](./images/createcollection.png)

You'l then see this popup:

![Decision Rule](./images/createcollectionpopup.png)

Configure your Collection like this:

- Collection name: use **ldap** - Luma Retail Collection
- Select **Create static collection**.

![Decision Rule](./images/createcollectionpopup1.png)

Click **Next**.

![Decision Rule](./images/next.png)

In the next screen, select the four **Personalized Offers** you created in the previous exercises.

![Decision Rule](./images/createcollectionpopup2.png)

Click **Save**.

![Decision Rule](./images/save.png)

You'll now see this:

![Decision Rule](./images/colldone.png)

## 14.2.4 Create your Offer Activity

An activity combines Placements, a Collection of Personalized Offers and a Fallback Offer to ultimately be used by the Offer Decisioning engine to find the best offer for a specific profile, based on each of the individual personalized offer characteristics like priority, eligibility constraint and total / user capping.

To configure your **Activity**, go to **Activities** in the left menu in Adobe Experience Platform.

![Decision Rule](./images/activity.png)

Click **+ Create Activity**.

![Decision Rule](./images/createactivity.png)

You'll then see this:

![Decision Rule](./images/activity1.png)

Fill out the fields like this:

- Name: **ldap** - Luma Retail Offer Activity
- Start date and time: today
- End date and time: today + 1 month

![Decision Rule](./images/activity2.png) 

Click **Next**.

![Decision Rule](./images/next.png)

In the next screen, you need to add Placements to the canvas. Select the Placements **Web - Image** and **Email - Image** by clicking the **+** icon on the Placement.

![Decision Rule](./images/addplacements.png)

You'll then see this:

![Decision Rule](./images/activity3.png) 

In the **Decision for placement Web - Image**, click **Add collection**.

![Decision Rule](./images/activity4.png) 

Select your collection **ldap** - Luma Retail Collection.

![Decision Rule](./images/activity5.png) 

Click **Add**.

![Decision Rule](./images/add.png)

You'll then see this:

![Decision Rule](./images/activity6.png)

Next, in the **Decision for placement Email - Image**, click **Add collection**.

![Decision Rule](./images/activity7.png) 

Select your collection **ldap** - Luma Retail Collection.

![Decision Rule](./images/activity8.png) 

Click **Add**.

![Decision Rule](./images/add.png)

You'll then see this:

![Decision Rule](./images/activity9.png)

Click **Next**.

![Decision Rule](./images/next.png)

You now need to select your **Fallback Offer**.

![Decision Rule](./images/activity10.png)

Click **Next**.

![Decision Rule](./images/next.png)

Review your offer activity.

![Decision Rule](./images/activity11.png)

Click **Finish**.

![Decision Rule](./images/finish.png)

In the popup, click **Save and activate**.

![Decision Rule](./images/activity12.png)

And finally, you'll now see your Offer Activity in the overview:

![Decision Rule](./images/activity13.png)

You've now successfully configured your Offer Activity. Your Offer Activity is now live, and can be used to deliver optimized and personalized offers to your customers, in real-time.

Next Step: [14.3 Test your Offer Activity](./ex3.md)

[Go Back to Module 14](./offer-decisioning.md)

[Go Back to All Modules](./../../overview.md)