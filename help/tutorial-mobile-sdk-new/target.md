---
title: Perform A/B Tests with Target
description: Learn how to use a Target A/B test in your mobile app with Platform Mobile SDK and Adobe Target.
solution: Data Collection,Target
feature-set: Target
feature: A/B Tests
hide: yes
exl-id: 87546baa-2d8a-4cce-b531-bec3782d2e90
---
# Optimize and personalize with Adobe Target

Learn how to optimize and personalize the experiencies in your mobile apps with Platform Mobile SDK and Adobe Target.

Target provides everything that you must tailor and personalize your customers' experiences. Target helps you maximize revenue on your web and mobile sites, apps, social media, and other digital channels. Target can perform A/B tests, multivariate tests, recommend products and content, target content, auto-personalize content with AI, and much more. The focus in this lesson is on the A/B test functionality of Target.  See the [A/B Test overview](https://experienceleague.adobe.com/docs/target/using/activities/abtest/test-ab.html?lang=en) for more information. 

![Architecture](assets/architecture-at.png)

Before you can perform A/B tests with Target, you must ensure that the proper configurations and integrations are in place.

>[!NOTE]
>
>This lesson is optional and only applies to Adobe Target users looking to perform A/B tests. 


## Prerequisites

* Successfully built and run app with SDKs installed and configured.
* Access to Adobe Target with permissions, properly configured roles, workspaces, and properties as described [here](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/property-channel.html?lang=en).


## Learning objectives

In this lesson, you will:

* Update your datastream for Target integration.
* Update your tag property with the Journey Optimizer - Decisioning extension.
* Update your schema to capture propositon events.
* Validate setup in Assurance.
* Create a simple A/B test in Target.
* Update your app to register the Optimizer extension.
* Implement the A/B test in your app.
* Validate implementation in Assurance.


## Setup

>[!TIP]
>
>If you have set up your app already as part of the [Journey Optimizer offers](journey-optimizer-offers.md) lesson, you might already have performed some of the steps in this setup section.

### Update datastream configuration

#### Adobe Target

To ensure data send from your mobile app to Experience Platform Edge Network is forwarded to Adobe Target, you must update you datastream configuration.

1. In the Data Collection UI, select **[!UICONTROL Datastreams]**, and select your datastream, for example **[!DNL Luma Mobile App]**.
1. Select **[!UICONTROL Add Service]** and select **[!UICONTROL Adobe Target]** from the **[!UICONTROL Service]** list.
1. If you are a Target Premium customer and would like to use property tokens, enter the Target **[!UICONTROL Property Token]** value that you want to use for this integration. Target Standard users can skip this step. 

   You can find your properties in the Target UI, in **[!UICONTROL Administration]** > **[!UICONTROL Properties]**. Select ![Code](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Code_18_N.svg) to reveal the property token for the property you want to use. The property token has a format like `"at_property": "xxxxxxxx-xxxx-xxxxx-xxxx-xxxxxxxxxxxx"`; you must only enter the value `xxxxxxxx-xxxx-xxxxx-xxxx-xxxxxxxxxxxx`.

   Optionally, you can specify a Target Environment ID. Target uses environments to organize your sites and pre-production environments for easy management and seperated reporting. The preset environments include Production, Staging, and Development. See [Environments](https://experienceleague.adobe.com/docs/target/using/administer/environments.html?lang=en) and [Target Environment ID](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/applications-setup/setup-target.html?lang=en#target-environment-id) for more information.

   Optionally, you can specify a Target third-party ID namespace to support profile syncing on an identity namespace (for example CRM ID). See [Target Third Party ID namespace](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/applications-setup/setup-target.html?lang=en#target-third-party-id-namespace) for more information.

1. Select **[!UICONTROL Save]**.

    ![Add Target to datastream](assets/edge-datastream-target.png)


#### Adobe Journey Optimizer

To ensure data send from your mobile app to the Edge Network is forwarded to Journey Optimizer - Decision Management, update your datastream configuration.

1. In the Data Collection UI, select **[!UICONTROL Datastreams]**, and select your datastream, for example **[!DNL Luma Mobile App]**.
1. Select ![More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_MoreSmallList_18_N.svg) for **[!UICONTROL Experience Platform]** and select ![Edit](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) **[!UICONTROL Edit]** from the context menu.
1. In the **[!UICONTROL Datastreams]** > ![Folder](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) >  **[!UICONTROL Adobe Experience Platform]** screen, ensure **[!UICONTROL Offer Decisioning]**, **[!UICONTROL Edge Segmentation]**, and **[!UICONTROL Personalization Destinations]** are selected. If you also follow the Journey Optimizer lessons, you should select **[!UICONTROL Adobe Journey Optimizer]** as well. See [Adobe Experience Platform settings](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html?lang=en#aep) for more information.
1. To save your datastream configuration, select **[!UICONTROL Save]** .

   ![AEP datastream configuration](assets/datastream-aep-configuration-target.png)


### Install Adobe Journey Optimizer - Decisioning tags extension

1. Navigate to **[!UICONTROL Tags]**, find your mobile tag property, and open the property.
1. Select **[!UICONTROL Extensions]**.
1. Select **[!UICONTROL Catalog]**.
1. Search for the **[!UICONTROL Adobe Journey Optimizer - Decisioning]** extension.
1. Install the extension. The extension does not require additional configuration.

    ![Add Decisioning extension](assets/tag-add-decisioning-extension.png)


### Update your schema

1. Navigate to Data Collection interface and select **[!UICONTROL Schemas]** from the left rail.
1. Select **[!UICONTROL Browse]** from the top bar.
1. Select your schema to open it.
1. In the schema editor, select ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Add]** next to **[!UICONTROL Field groups]**.
1. In the Add fields groups dialog, search for `proposition`, select **[!UICONTROL Experience Event - Proposition Interactions]** and select **[!UICONTROL Add field groups]**.
   ![Proposition](assets/schema-fieldgroup-proposition.png)
1. To save the changes to your schema, select **[!UICONTROL Save]**.


### Validate setup in Assurance

To validate your setup in Assurance:

1. Go to the Assurance UI.
1. Select **[!UICONTROL Configure]** in left rail and select ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) next to **[!UICONTROL Validate Setup]** underneath **[!UICONTROL ADOBE JOURNEY OPTIMIZER DECISIONING]**.
1. Select **[!UICONTROL Save]**.
1. Select **[!UICONTROL Validate Setup]** in the left rail. Both datastream setup is validated and the SDK setup in your application.
   ![AJO Decisioning validation](assets/ajo-decisioning-validation.png) 

## Create an A/B Test

There are many types of activities you can create in Adobe Target and implement in a mobile app, as mentioned in the introduction. For this lesson, you will focus on creating an implementing an A/B test.

1. In the Target UI, select **[!UICONTROL Activities]** from the top bar.
1. Select **[!UICONTROL Create Activity]** and **[!UICONTROL A/B Test]** from the context menu.
1. In the **[!UICONTROL Create A/B Test Activity]** dialog, select **[!UICONTROL Mobile]** as the **[!UICONTROL Type]**, select a workspace from the **[!UICONTROL Choose Workspace]** list, and select your property from the **[!UICONTROL Choose property]** list if you are a Target Premium customer and specified a property token in the datastream. 
1. Select **[!UICONTROL Create]**.
   ![Create Target activity](assets/target-create-activity1.png)

1. In the **[!UICONTROL Untitled Activity]** screen, at the **[!UICONTROL Experiences]** step:

   1. Enter `luma-mobileapp-abtest` in **[!UICONTROL Select Location]** underneath **[!UICONTROL LOCATION 1]**. This location name (often referred to as an mbox) is used later in the app implementation.
   1. Select ![Chrevron down](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ChevronDown_18_N.svg) next to **[!UICONTROL Default Content]** and select **[!UICONTROL Create JSON Offer]** from the context menu.
   1. Copy the following JSON into **[!UICONTROL Enter a valid JSON object]**.

        ```json
        { 
            "title": "Luma Anaolog Watch",
            "text": "Designed to stand up to your active lifestyle, this women's Luma Analog Watch features a tasteful brushed chrome finish and a stainless steel, water-resistant construction for lasting durability.", 
            "image": "https://luma.enablementadobe.com/content/dam/luma/en/products/gear/watches/Luma_Analog_Watch.jpg" 
        }
        ```

   1. Select **[!UICONTROL + Add Experience]**.
   
       ![Experience A](assets/target-create-activity-experienceA.png)

   1. Repeat step b and c for  experience Experience B, but instead use the following JSON:

        ```json
        { 
            "title": "Aim Analog Watch",
            "text": "The flexible, rubberized strap is contoured to conform to the shape of your wrist for a comfortable all-day fit. The face features three illuminated hands, a digital read-out of the current time, and stopwatch functions.", 
            "image": "https://luma.enablementadobe.com/content/dam/luma/en/products/gear/watches/Aim_Watch.jpg" 
        }

        ```

   1. Select **[!UICONTROL Next]**.
      
      ![Experience B](assets/target-create-activity-experienceB.png)

1. In the **[!DNL Targeting]** step, review the setup of your A/B test. By default, both offers are allocated equally across all visitors. Select **[!UICONTROL Next]** to continue.

   ![Targeting](assets/taget-targeting.png)

1. In the **[!UICONTROL Goals & Settings]** step:

    1. Rename your Untitled Activity, for example  to `Luma Mobile SDK Tutorial - A/B Test Example`.
    1. Enter an **[!UICONTROL Objective]** for your A/B test, for example `A/B Test for Luma mobile app tutorial`.
    1. Select **[!UICONTROL Conversion]**, **[!UICONTROL Viewed an mbox]** in the **[!UICONTROL Goal Metric]** > **[!UICONTROL MY PRIMARY GOAL]** tile and enter your location (mbox) name, for example `luma-mobileapp-abtest`.
    1. Select **[!UICONTROL Save & Close]**.

       ![Goals Settings](assets/target-goals.png)

1. Back in the **[!UICONTROL All Activities]** screen:

    1. Select ![More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_MoreSmallList_18_N.svg) at your activity.
    1. Select ![Play](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Play_18_N.svg) **[!UICONTROL Activate]** to activate your A/B test.

    ![Activate](assets/target-activate.png)


## Implement Target in your app

As discussed in previous lessons, installing a mobile tag extension only provides the configuration. Next you must install and register the Optimize SDK. If these steps aren't clear, review the [Install SDKs](install-sdks.md) section.

>[!NOTE]
>
>If you completed the [Install SDKs](install-sdks.md) section, then the SDK is already installed and you can skip this step.
>

1. In Xcode, ensure that [AEP Optimize](https://github.com/adobe/aepsdk-messaging-ios.git) is added to the list of packages in Package Dependencies. See [Swift Package Manager](install-sdks.md#swift-package-manager).
1. Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL AppDelegate]** in the Xcode Project navigator.
1. Ensure `AEPOptimize` is part of your list of imports.

    `import AEPOptimize`

1. Ensure `Optimize.self` is part of the array of extensions that you are registering.

    ```swift
    let extensions = [
        AEPIdentity.Identity.self,
        Lifecycle.self,
        Signal.self,
        Edge.self,
        AEPEdgeIdentity.Identity.self,
        Consent.self,
        UserProfile.self,
        Places.self,
        Messaging.self,
        Optimize.self,
        Assurance.self
    ]
    ```

1. Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!DNL MobileSDK]** in the Xcode Project navigator. Find the ` func updatePropositionAT(ecid: String, location: String) async` function. Add the following code:

    ```swift
    // set up the XDM dictionary, define decision scope and call update proposition API
    Task {
        let ecid = ["ECID" : ["id" : ecid, "primary" : true] as [String : Any]]
        let identityMap = ["identityMap" : ecid]
        let xdmData = ["xdm" : identityMap]
        let decisionScope = DecisionScope(name: location)
        Optimize.clearCachedPropositions()
        Optimize.updatePropositions(for: [decisionScope], withXdm: xdmData)
    }

    ```

    This function:  

      * sets up an XDM dictionary `xdmData`, containing the ECID to identify the profile for which you have to present the A/B test, and 
      * defines a `decisionScope`, an array of locations on where to present the A/B test. 

    Then the function calls two API's: [`Optimize.clearCachedPropositions`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#clearpropositions) and [`Optimize.updatePropositions`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#updatepropositions). These functions clear any cached propositions and update the propositions for this profile. A proposition in this context is the experience (offer) that is selected from the Target activity (your A/B test) and which you defined in [Create an A/B test](#create-an-ab-test).

1. Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Personalization]** > **[!DNL TargetOffersView]** in the Xcode Project navigator. Find the `func onPropositionsUpdateAT(location: String) async {` function and inspect the code of this function. The most important part of this function is the  [`Optimize.onPropositionsUpdate`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#onpropositionsupdate) API call, which: 
   * retrieves the propositions for the current profile based on the decision scope (which is the location you have defined in the A/B Test),
   * retrieves the offer from the proposition,
   * unwraps the content of the offer so it can be displayed properly in the app, and
   * triggers the `displayed()` action on the offer which will send an event back to the Edge Network informing the offer is displayed. 

1. Still in **[!DNL TargetOffersView]**, add the following code to the `.onFirstAppear` modifier. This code will ensure the callback for updating the offers is registered only once.

    ```swift
    // Invoke callback for offer updates
    Task {
        await self.onPropositionsUpdateAT(location: location)
    }
    ```

1. Still in **[!DNL TargetOffersView]**, add the following code to the `.task` modifier. This code will update the offers when the view is refreshed.

    ```swift
    // Clear and update offers
    await self.updatePropositionsAT(ecid: currentEcid, location: location)
    ```

You can send additional Target parameters (like mbox, profile, product, or order parameters) in a personalization query request to the Experience Edge network, by adding them in a data dictionary when calling the [`Optimize.updatePropositions`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#updatepropositions) API. See for more information [Target Parameters](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/#target-parameters).


## Validate using the app

1. Rebuild and run the app in the simulator or on a physical device from Xcode, using ![Play](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Play_18_N.svg).

1. Go to the **[!UICONTROL Personalisation]** tab.

1. Scroll down to the bottom, and you see one of the two offers that you have defined in your A/B test displayed in the **[!UICONTROL TARGET]** tile.

    <img src="assets/target-app-offer.png" width=300>


## Validate implementation in Assurance

To validate the A/B test in Assurance:

1. Review the [setup instructions](assurance.md#connecting-to-a-session) section to connect your simulator or device to Assurance.
1. Select **[!UICONTROL Configure]** in left rail and select ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) next to **[!UICONTROL Review & Simulate]** underneath **[!UICONTROL ADOBE JOURNEY OPTIMIZER DECISIONING]**.
1. Select **[!UICONTROL Save]**.
1. Select **[!UICONTROL Review & Simulate]** in the left rail. Both datastream setup is validated and the SDK setup in your application.
1. Select **[!UICONTROL Requests]** at the top bar. You see your **[!DNL Target]** requests.
   ![AJO Decisioning validation](assets/assurance-decisioning-requests.png)

1. You can explore **[!UICONTROL Simulate]** and **[!UICONTROL Event List]** tabs for further functionality checking your setup for Target offers.

## Next steps

You should now have all the tools to start adding more A/B tests or other Target activities (such as Experience Targeting, Multivariate Test), where relevant and applicable, to your app. There is more in depth information available in the [Github repo for the Optimize extension](https://github.com/adobe/aepsdk-optimize-ios) where you can also find a link to a dedicated [tutorial](https://opensource.adobe.com/aepsdk-optimize-ios/#/tutorials/README) on how to track Adobe Target offers.

>[!SUCCESS]
>
>You have enabled the app for A/B tests and displayed the results of an A/B test using Adobe Target and the Adobe Journey Optimizer - Decisioning extension for the Adobe Experience Platform Mobile SDK.<br/>Thank you for investing your time in learning about Adobe Experience Platform Mobile SDK. If you have questions, want to share general feedback, or have suggestions on future content, share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Next: **[Conclusion and next steps](conclusion.md)**
