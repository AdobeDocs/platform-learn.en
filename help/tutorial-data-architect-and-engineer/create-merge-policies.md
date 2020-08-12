---
title: Create Merge Policies | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
description: 
feature: profile
topics: 
kt: 4348
audience: data architect,data engineer
doc-type: tutorial
activity: implement
---

# Create Merge Policies

In this lesson you will learn how to create merge policies to determine how data merges into profiles. 

The good news is that this will be a quick lesson and we'll stick to the UI.

Adobe Experience Platform enables you to bring data together from multiple sources and combine it in order to see a complete view of each of your individual customers. When bringing this data together, merge policies are the rules that Platform uses to determine how data will be prioritized and what data will be combined to create that unified view.

**Data Architects** will need to create merge policies outside of this tutorial.

<!--Should this be part of Profile lesson-->

<!-->[!VIDEO]()-->

## Permissions required

In the [Configure Permissions](configure-permissions.md) lesson, you setup all the access controls you need to complete this lesson, specifically:


* Permission item Profiles > Manage Profiles
* Permission item Sandboxes > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
* Developer-role access to the `Luma Tutorial Platform` product profile (for API)


## About Merge policies and Union Schema

You may recall in the lesson on batch ingestion, we uploaded two records with slightly different information for the same customer. In the [!DNL Loyalty] data, the customer's first name was `Daniel` and he lived in `New York City`, but in the CRM data the customer's first name was `Danny` and he lived in `Portland`. Profile data changes over time. Perhaps he moved from `Portland` to `New York City` or vice versa. Other things change too, such as phone numbers, email addresses, etc. Merge policies help you decide how to handle these types of conflicts when two data sources are giving different information for the same user.

So, why did `Danny` win out as the first name? Let's take a look:

1. In the Platform UI, click **[!UICONTROL Profiles]** in the left navigation
1. Click the **[!UICONTROL Merge Polices]** tab
1. Note that the default Merge Policy is timestamp ordered. Because you uploaded the CRM data after the Loyalty data, `Danny` and `Portland` won out as the first name and city in the profile:

![Merge Policy screen](assets/mergepolicies-default.png)

When multiple schema are enabled for profile, a [!UICONTROL Union Schema] is automatically created for all profile-enabled, record schema sharing the same base class. You can view the [!UICONTROL Union Schemas] by clicking on the **[!UICONTROL Union Schema]** tab.

![Merge Policy screen](assets/mergepolicies-unionSchema.png)

Note that there isn't a union schema for the ExperienceEvent class. While ExperienceEvent data still lands in profile, because it is time-series based, each event includes a timestamp and collisions are not a problem.

Now what if you don't like that default merge policy? What if Luma decides their CRM system should be the source of truth when there is a conflict? For that, we will create a merge policy.

## Create a merge policy in the UI

1. On the Merge Policies screen, click the **[!UICONTROL Create Merge Policy]** button on the top right
1. As the **[!UICONTROL Name]**, enter  `Loyalty Prioritized`
1. As the **[!UICONTROL Schema]**, select **[!UICONTROL XDM Profile]** (note that your custom class&mdash;since it is record data&mdash;is available for merge policies, too)
1. For **[!UICONTROL Id Stitching]**, select **[!UICONTROL Private Graph]**
1. For **[!UICONTROL Attribute Merge]**, select **[!UICONTROL Dataset precedence]**
1. Drag and drop `Luma Loyalty Dataset` and `Luma CRM Dataset` to **[!UICONTROL Selected Dataset]** panel.
1. Make sure `Luma Loyalty Dataset` is on top by drag and dropping it above the `Luma CRM Dataset`
1. Click the **[!UICONTROL Save]** button

![Merge Policy](assets/mergepolicies-newPolicy.png)

## Validate the merge policy

Let's see if the merge policy is doing what we would expect:

1. Click the **[!UICONTROL Browse]** tab
1. Change the **[!UICONTROL Merge policy]** to your new `Loyalty Prioritized` policy
1. As the **[!UICONTROL Identity namespace]**, use your `Luma CRM Id`
1. As the **[!UICONTROL Identity value]** use `112ca06ed53d3db37e4cea49cc45b71e`
1. Click the **[!UICONTROL Show profile]** button
1. `Daniel` is back!

![Viewing a profile with a different merge policy](assets/mergepolicies-lookupProfileWithMergePolicy.png)

## More about merge policies

In the profile search, change the merge policy used back to `Default Timebased` and click the **[!UICONTROL Show profile]** button. Danny is back!

What is going on here? Well, profile merging is not a one time thing. Real-time customer profiles are assembled on the fly, based on a number of factors, including which merge policy is used. You can create multiple merge policies to use in different contexts, depending on which view of the customer you want.

Merge policies also tie into data governance and segmentation, which you will see shortly.

![Viewing a profile with a different merge policy](assets/mergepolicies-backToDanny.png)


## Additional Resources

* [Merge Policies documentation](https://docs.adobe.com/help/en/experience-platform/profile/ui/merge-policies.html)
* [Merge Policies API (part of Real-time Customer Profile API) reference](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#/Merge_policies)

Now let's move on to the [data governance framework](apply-data-governance-framework.md).