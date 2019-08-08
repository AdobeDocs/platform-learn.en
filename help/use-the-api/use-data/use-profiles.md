# Lesson 4 - Unified Profile: Querying the Unified Profile

## Objective

Learn how to query Profile and Experience Events from the Unified Profile

## Lesson Context

Much of the value of having all our data integrated with the Adobe Experience Platform is to be able to utilize the Unified Profile. This will give us a real-time customer profile that's built on a user's interactions with various channels (web, physical beacon, email) and can help segment customers better as well as do further analytics using other tools on the Experience Platform. Here we will show how to do a lookup of a user's Unified Profile - namely, the user info we just entered in Lesson 3 - using both an email address as well as an ECID.

## Lesson Resources

Make sure to have the ECID copied from the end of Lesson 3

## Exercise 4.1 - Querying Unified Profiles via the API

1. Go to Postman, and under the `Lesson 4` collection find the `Behavioral Data Point Lookup` call. find the `entityId` Field and paste your copied ECID here from the clipboard. Make sure that the `entityIdNS` field is set to "ecid". Send the `GET` call.

   ![](assets/launch-ecid-lookup-1.png)

1. You should get back a list of all ExperienceEvents associated with your ECID - browsing the homepage and the signup page. Take a look, your streaming data is now in Experience Platform!

   ![](assets/launch-ecid-lookup-2.png)

1. This data is now in Experience Platform! In addition, it's now been ingested into the Unified Profile, since we tagged it for Unified Profile when creating our dataset back in Lesson 2. To confirm this in the API since we're still in Postman, you can take the ECID that you used in the last step and do a similar call with the `GET` call for `Unified Profile Lookup`. You will then be able to see your full Unified Profile associated with your ECID - your sign-up data for Profile data should now be available as a profile view.

   _NOTE: It may take up to 5 minutes for the Unified Profile data to refresh and show your profile data_

   ![](assets/launch-unifiedprofile-1.png)

## Lesson 4 Wrap

Well that was quick and easy - and brings us to the end of our journey for the regular portion of our lab! You were able to observe and perform the most critical and necessary functions of the Adobe Experience Platform completely from a developer or architect's point of view - using APIs and external sources to help complement the Experience Platform UI or to help you integrate Experience Platform's features into your own custom applications. The streaming capabilities of data into Experience Platform are not limited to websites - mobile apps, POS devices, and other points of data capture can all stream behavioral and other types of data into Experience Platform using methods like Launch.

## Lesson 4 Additional Resources

[Unified Profile Overview](https://www.adobe.io/apis/experienceplatform/home/profile-identity-segmentation/profile-identity-segmentation-services.html#!api-specification/markdown/narrative/technical_overview/unified_profile_architectural_overview/unified_profile_architectural_overview.md)