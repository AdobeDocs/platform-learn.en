---
title: Migrate from the Adobe Analytics Tags extension to the Web SDK Tags extension
description: Learn the steps you will take during the migration to Web SDK, as well as decisions that will need to be made along the way.
solution: Data Collection, Analytics
feature: Web SDK
jira: KT-16755
exl-id: e578b669-42b4-46ae-b6e6-6688e5c5c772
---
# Migrate from the Adobe Analytics Tags extension to the Web SDK Tags extension

Learn the steps to migrate an Adobe Analytics implementation using the Analytics extension in Experience Platform Tags (formerly known as Launch) to Web SDK, using the Web SDK extension also in Tags. When the Adobe Analytics extension in Tags is used, behind the scenes the "AppMeasurement.js" code is being used. Therefore, you can think of this as a tutorial that is migrating AppMeasurement to Web SDK, but this tutorial is fully in Tags and does NOT cover moving to or from a JavaScript implementation (with the exception of JavaScript code that is used within the Tags UI). For migration of JavaScript implementations, please see the [documentation](https://experienceleague.adobe.com/en/docs/analytics/implementation/aep-edge/web-sdk/appmeasurement-to-web-sdk).

## What you will get out of this tutorial

Before we jump into the steps for migrating your Analytics implementation, it is important that you understand exactly what you will be doing, which is changing/updating the _implementation_ for Analytics. At the end of this tutorial when you go into your reports and when everything is the same, you might ask yourself, "Now, why did I do all that?" There are other documents to outline the benefits of using the Web SDK for your Analytics implementation, but a few are:

1. Support for First Party Device ID
1. Better performance
1. Future proofing your implementation as you move toward using the Adobe Experience Platform applications (enabling  new use cases)

Please talk to your Adobe Analytics representative to learn more about how the Web SDK can help you. As we move ahead with this tutorial, we will focus on _how_ to do the migration.

>[!IMPORTANT]
>
>It is important to note that one of the main reasons that you are doing this migration of your implementation is to prepare to use Adobe Experience Platform applications, like Customer Journey Analytics, Real-Time CDP, or Journey Optimizer (as noted in #3 above). Using your website data for this purpose will include additional steps that are not included in this tutorial, but this tutorial will certainly be a prerequisite for that further progression of your implementation. Therefore, do complete this tutorial, and then you can go on to perform the steps necessary to send this same website data to the Experience Platform as well.

## Migration Method

There are probably many ways that you could do this migration process, but we need to talk about two right here:

**Method 1:** Update your existing Tags property to Web SDK, creating new data elements, and making changes to the rules that already exist in your property.

**Method 2:** You could also create a new property (by copying your existing one or creating one brand new), and then configure that new property with Web SDK instead of the Adobe Analytics extension.

**For this migration tutorial, we are going to use Method 1.** That way the embed codes associated with the property are already embedded on your development, staging, and production sites, so there won't be a need to change any embed codes. If you decide to go with Method 2, don't forget to get the new embed codes for each environment from the **Environments** section of the new property and place them into the head section of your site.

>[!NOTE]
>
>Even though we are going to just edit our existing property in Tags during this migration, it is still a good idea to be careful. Therefore, it is highly suggested that you make a copy of your current property before starting your migration. That way, you could always go into the copy and look at how things were before you changed them, pull code from it, etc. 
>It's just good to be careful, just in case. Go ahead and make the copy of your property. I'll wait here until you get back.

## Steps for migrating your Analytics implementation to Web SDK

As you go through the steps, there are a couple of caveats that are important to understand:

1. First, you may or may not need all of these steps. For example, there is a lesson regarding migrating custom code. If you have a Tags implementation that doesn't use custom code (including using Plug-ins), then you won't need this lesson. We tried to include the lessons that would be needed by most everyone, so at least read through the lessons to see if you need to make any adjustments to your site during your migration.
1. Also, there's just no way for us to create a migration tutorial that will cover 100% of the use cases that everyone is using. As stated in the previous item, we tried to include the lessons that most people will need, and that will cover most of the main use cases. However, there will undoubtedly be use cases that are not covered in this tutorial. In this case, see if the included lessons give you a good idea of how you should migrate for your use case. You can also ask your peers in the [Experience League Community for data collection](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/ct-p/adobe-launch-community).

The migration process involves the following key steps:

1. Create a migration validation report suite.
1. Create and configure a datastream.
1. Add and configure the Web SDK extension in Tags (formerly Adobe Launch).
1. Create a new data element to send data in via the Web SDK.
1. Migrate your default page load rule to use the Web SDK data element and actions.
1. Migrate custom code in rules or for plug-ins.
1. Publish your implementation changes.
1. Understand how to debug and validate your changes, and validate your default page load rule and the variables associated with it. This validation should then continue throughout the migration as you make changes.
1. Migrate additional page load rules.
1. Migrate custom link rules.
1. After full validation, remove references to the Analytics extension and remove the extension itself.
1. Having made all of the changes, push the library through to staging and then to production.
1. After everything is completed, test again. This is necessary because you have made changes by removing the references to old Analytics code and you want to make sure that everything still works correctly.


### NOTE FOR DOUG - after tutorial testing, put a link here to a Community post where clients can ask questions about the tutorial and migrating to Web SDK.
