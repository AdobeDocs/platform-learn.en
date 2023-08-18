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


## Set & update

It would be helpful for targeting and/or personalization to quickly know if a user has made purchase in the app before. Let's set that up in the Luma app.

1. Navigate to **[!UICONTROL ProductView]** (in **[!UICONTROL Views]** > **[!UICONTROL Products]**) in the Xcode Luma app project and find the call to `updateUserAttributes` (within the Purchases button):

    ```swift {highlight="8-9"}
    Button {
        Task {
            if ATTrackingManager.trackingAuthorizationStatus == .authorized {
                // Send purchase commerce experience event
                MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "purchases", product: product)
                // Update attributes
                MobileSDK.shared.updateUserAttributes(attributeName: "isPaidUser", attributeValue: "yes")
            }
        }
        showPurchaseDialog.toggle()
    } label: {
        Label("", systemImage: "creditcard")
    }
    .alert(isPresented: $showPurchaseDialog, content: {
        Alert(title: Text( "Purchases"), message: Text("The selected item is purchased…"))
    })
    ```

2. Navigate to **[!UICONTROL MobileSDK]** and find the `updateUserAttributes` function. Add the following highlighted code:

    ```swift {highlight="2-4"}
    func updateUserAttributes(attributeName: String, attributeValue: String) {
        var profileMap = [String: Any]()
        profileMap[attributeName] = attributeValue
        UserProfile.updateUserAttributes(attributeDict: profileMap)
    }
    ```

    This code:

    1. Sets up an empty dictionary named `profileMap`.

    1. Adds an element to the dictionary using `attributeName` (for example `isPaidUser`), and `attributeValue` (for example `yes`).

    1. Uses the `profileMap` dictionary as a value to the `attributeDict` parameter of the `UserProfile.updateUserAttributes` API call.


Additional `updateUserAttributes` documentation can be found [here](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#updateuserattribute).

## Get

Once you have updated a user's attribute, it is available to other Adobe SDKs but you can also retrieve attributes explicitly.

1. Navigate to **[!UICONTROL HomeView]** (in **[!UICONTROL Views]** > **[!UICONTROL General]**) and find the `.onAppear` modifier. Add the following code:

    ```swift {highlight="3-11"}
    .onAppear {
        // Track view screen
        MobileSDK.shared.sendTrackScreenEvent(stateName: "luma: content: ios: us: en: home")
        // Get attributes
        UserProfile.getUserAttributes(attributeNames: ["isPaidUser"]) { attributes, error in
            if attributes?["isPaidUser"] as! String == "yes" {
                showBadgeForUser = true
            }
            else {
                showBadgeForUser = false
            }
        }
    }
    ```

    This code:
    
    1. Calls the `UserProfile.getUserAttributes` closure with the `iPaidUser` attribute name as single element in the `attributeNames` array.
    1. Then checks for the value of the `isPaidUser` attribute and when `yes`, places a badge on the Person icon in the top right.

Additional `getUserAttributes` documentation can be found [here](https://developer.adobe.com/client-sdks/documentation/profile/api-reference/#getuserattributes).

## Validate with Assurance

1. Review the [setup instructions](assurance.md) section.
1. Install the app.
1. Launch the app using the Assurance generated URL.
1. Run the app to log in and interact with a product.

   1. Move the Assurance icon to the left.
   1. Select **[!UICONTROL Home]** in the tab bar.
   1. To open the Login sheet, select the **[!UICONTROL Login]** button.
   1. To insert a random email and customer id, select the **[!UICONTROL A|]** button .
   1. Select **[!UICONTROL Login]**.
   1. Select **[!UICONTROL Products]** in the tab bar.
   1. Select one product.
   1. Select **[!UICONTROL Save for Later]**.
   1. Select **[!UICONTROL Add to Cart]**.
   1. Select **[!UICONTROL Purchase]**.
   1. Return back to **[!UICONTROL Home]** screen. You should see an updated Login button.

      <img src="./assets/mobile-app-events-1.png" width=200> <img src="./assets/mobile-app-events-2.png" width=200> <img src="./assets/mobile-app-events-3.png" width=200> <img src="./assets/personbadges.png" width=200>

1. You should see a **[!UICONTROL UserProfileUpdate]** and **[!UICONTROL getUserAttributes]** events in the Assurance UI with the updated `profileMap` value.
   ![validate profile](assets/profile-validate.png)

>[!SUCCESS]
>
>You have now set up your app to update attributes of profiles in the Edge Network and (when set up) with Adobe Experience Platform.<br/>Thank you for investing your time in learning about Adobe Experience Platform Mobile SDK. If you have questions, want to share general feedback, or have suggestions on future content, share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Next: **[Map data to Adobe Analytics](analytics.md)**
