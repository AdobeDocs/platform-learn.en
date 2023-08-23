---
title: Profile
description: Learn how to collect profile data in a mobile app.
hide: yes
hidefromtoc: yes
---
# Profile

Learn how to collect profile data in a mobile app.

You can use the Profile extension to store attributes about your user on the client. This information can be used later to target and personalize messages during online or offline scenarios, without having to connect to a server for optimal performance. The Profile extension manages the Client-Side Operation Profile (CSOP), provides a way to react to APIs, updates user profile attributes, and shares the user profile attributes with the rest of the system as a generated event.

The Profile data is used by other extensions to perform profile-related actions. An example is the Rules Engine extension that consumes the profile data and runs rules based on the profile data. Learn more about the [Profile extension](https://developer.adobe.com/client-sdks/documentation/profile/) in the documentation

>[!IMPORTANT]
>
>The Profile functionality described in this lesson is separate from the Real-Time Customer Profile functionality in Adobe Experience Platform and Platform-based applications.


## Prerequisites

* Successfully built and run app with SDKs installed and configured.
* Imported the Profile SDK.

    ```swift
    import AEPUserProfile
    ```

## Learning objectives

In this lesson, you will:

* Set or update user attributes.
* Retrieve user attributes.


## Set & update user attributes

It would be helpful for targeting and/or personalization to quickly know if a user has made purchase in the app before. Let's set that up in the Luma app.

1. Navigate to **[!UICONTROL Luma]** > **[!UICONTROL Luma]** > **[!UICONTROL Utils]** >  **[!UICONTROL MobileSDK]** and find the `func updateUserAttribute(attributeName: String, attributeValue: String)` function. Add the following code:

    ```swift
    // Create a profile map
    var profileMap = [String: Any]()
    // Add attributes to profile map
    profileMap[attributeName] = attributeValue
    // Use profile map to update user attributes
    UserProfile.updateUserAttributes(attributeDict: profileMap)
    ```

    This code:

    1. Sets up an empty dictionary named `profileMap`.

    1. Adds an element to the dictionary using `attributeName` (for example `isPaidUser`), and `attributeValue` (for example `yes`).

    1. Uses the `profileMap` dictionary as a value to the `attributeDict` parameter of the `UserProfile.updateUserAttributes` API call.

1. Navigate to **[!UICONTROL Luma]** > **[!UICONTROL Luma]** > **[!UICONTROL Views]** > **[!UICONTROL Products]** > **[!UICONTROL ProductView]** in Xcode Project navigator and find the call to `updateUserAttributes` (within the code for the Purchases <img src="assets/purchase.png" width= 15/> button):

    ```swift
    // Update attributes
    MobileSDK.shared.updateUserAttributes(attributeName: "isPaidUser", attributeValue: "yes")
    ```

Additional documentation can be found [here](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#updateuserattribute).

## Get user attributes

Once you have updated a user's attribute, it is available to other Adobe SDKs but you can also retrieve attributes explicitly.

1. Navigate to **[!UICONTROL Luma]** > **[!UICONTROL Luma]** > **[!UICONTROL Views]** > General > **[!UICONTROL HomeView]** in Xcode Project navigator and find the `.onAppear` modifier. Add the following code:

    ```swift
    // Get attributes
    UserProfile.getUserAttributes(attributeNames: ["isPaidUser"]) { attributes, error in
        if attributes?["isPaidUser"] as! String == "yes" {
            showBadgeForUser = true
        }
        else {
            showBadgeForUser = false
        }
    }
    ```

    This code:
    
    1. Calls the `UserProfile.getUserAttributes` closure with the `iPaidUser` attribute name as single element in the `attributeNames` array.
    1. Then checks for the value of the `isPaidUser` attribute and when `yes`, places a badge on the <img src="assets/paiduser.png" width=20/> icon in the toolbar at the top right.

Additional documentation can be found [here](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#getuserattributes).

## Validate with Assurance

1. Review the [setup instructions](assurance.md) section.
1. Install the app.
1. Launch the app using the Assurance generated URL.
1. Run the app to log in and interact with a product.

   1. Move the Assurance icon to the left.
   1. Select **[!UICONTROL Home]** in the tab bar.
   1. To open the Login sheet, select the <img src="assets/login.png" width=15/> button.
   1. To insert a random email and customer id, select the <img src="assets/insert.png" width=15/> button .
   1. Select **[!UICONTROL Login]**.
   1. Select **[!UICONTROL Products]** in the tab bar.
   1. Select one product.
   1. Select <img src="assets/saveforlater.png" width=15/>.
   1. Select <img src="assets/addtocart.png" width=20/>.
   1. Select <img src="assets/purchase.png" width=15/>.
   1. Return back to **[!UICONTROL Home]** screen. You should see updated values for **[!UICONTROL Email]** and **[!UICONTROL CRM ID]**.

      <img src="./assets/mobile-app-events-1.png" width=200> <img src="./assets/mobile-app-events-2.png" width=200> <img src="./assets/mobile-app-events-3.png" width=200> <img src="./assets/personbadges.png" width=200>

1. In the Assurance UI, you should see a **[!UICONTROL UserProfileUpdate]** and **[!UICONTROL getUserAttributes]** events with the updated `profileMap` value.
   ![validate profile](assets/profile-validate.png)

>[!SUCCESS]
>
>You have now set up your app to update attributes of profiles in the Edge Network and (when set up) with Adobe Experience Platform.<br/>Thank you for investing your time in learning about Adobe Experience Platform Mobile SDK. If you have questions, want to share general feedback, or have suggestions on future content, share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Next: **[Map data to Adobe Analytics](analytics.md)**
