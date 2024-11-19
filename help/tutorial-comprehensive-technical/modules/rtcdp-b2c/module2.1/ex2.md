---
title: Foundation - Real-time Customer Profile - Visualize your own Real-time Customer Profile - UI
description: Foundation - Real-time Customer Profile - Visualize your own Real-time Customer Profile - UI
kt: 5342
doc-type: tutorial
---
# 2.1.2 Visualize your own Real-time Customer Profile - UI

In this exercise, you'll login to Adobe Experience Platform and view your own Real-time Customer Profile in the UI.
 
## Context

In the Real-time Customer Profile, all profile data is shown alongside event data, as well as existing segment memberships. The data shown can come from anywhere, from Adobe applications and external solutions. This is the most powerful view in Adobe Experience Platform, the true experience system of record.

## Use the Customer Profile View in Adobe Experience Platform

Go to [Adobe Experience Platform](https://experience.adobe.com/platform). After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](../../datacollection/module1.2/images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxName--``. After selecting the appropriate [!UICONTROL sandbox], you'll see the screen change and now you're in your dedicated [!UICONTROL sandbox].

![Data Ingestion](../../datacollection/module1.2/images/sb1.png)

In the left menu, go to **Profiles** and to **Browse**.

![Customer Profile](./images/homemenu.png)

On the Profile Viewer panel on your website, you can find multiple identities. Every Identity is linked to a namespace. 

![Customer Profile](./images/identities.png)

On the Profile Viewer panel, you can see these combinations of IDs and Namespaces:

| Identity     | Namespace       |
|:-------------:| :---------------:|
| Experience Cloud ID (ECID)          | 79943948563923140522865572770524243489 |
| Experience Cloud ID (ECID)          | 70559351147248820114888181867542007989 |
| Email ID          | woutervangeluwe+18112024-01@gmail.com|
| Mobile Number ID          | +32473622044+18112024-01|

With Adobe Experience Platform, all IDs are equally important. Previously, the ECID was the most important ID in the Adobe context and all other IDs were linked to the ECID in a hierarchical relation. With Adobe Experience Platform this is no longer the case, and every ID can be considered a primary identifier. 

Typically, the primary identifier depends on the context. If you ask your Call Center, **What is the most important ID?** they will probably answer, **the phone number!** But if you ask your CRM team, they will answer, **the email address!**  Adobe Experience Platform understands this complexity and manages it for you. Every application, whether an Adobe application or non-Adobe application, will speak with Adobe Experience Platform by referring to the ID they consider primary. And it simply works.

For the field **Identity namespace**, select **Email** and for the field **Identity Value** enter the email address you used to register in the previous exercise. Click **View**. You'll then see your profile in the list. Click the **Profile ID** to open your profile.

![Customer Profile](./images/popupecid.png)

You now see an overview of a couple of important **Profile Attributes** of your customer profile. To see all available profile attributes for your profile, click **Attributes**.

![Customer Profile](./images/profile.png)

You'll then see a complete list of all attributes.

![Customer Profile](./images/profilattr.png)

Go to **Events**, where you can see entries for every experience event that is linked to your Profile.    

![Customer Profile](./images/profileee.png)

Finally, go to the menu option **Audience membership**. Here, you'll find all qualifying audiences for this customer. The list may currently be empty, but that will change in the next modules.

![Customer Profile](./images/profileseg.png)

Now that you've learnt how to view any customer's real-time profile by making use of Adobe Experience Platform's User Interface, let's do the same thing through the APIs by making use of Postman and Adobe I/O to query against Adobe Experience Platform's APIs.

Next Step: [2.1.3 Visualize your own real-time customer profile - API](./ex3.md)

[Go Back to Module 2.1](./real-time-customer-profile.md)

[Go Back to All Modules](../../../overview.md)
