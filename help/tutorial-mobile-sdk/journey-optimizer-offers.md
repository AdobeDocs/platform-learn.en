---
title: Create and display offers with Platform Mobile SDK
description: Learn how to create and display offers with Platform Mobile SDK and Adobe Journey Optimizer Decision Management.
solution: Data Collection,Journey Optimizer
feature-set: Journey Optimizer
feature: Offers
jira: KT-14640
exl-id: c08a53cb-683e-4487-afab-fd8828c3d830
---
# Create and display offers with Decision Management

Learn how to show offers from Journey Optimizer Decision Management in your mobile apps with Experience Platform Mobile SDK.

Journey Optimizer Decision Management helps you to deliver the best offer and experience to your customers across all touchpoints  at the right time. Once designed, target your audience with personalized offers.

![Architecture](assets/architecture-ajo.png){zoomable="yes"}

Decision management makes personalization easy with a central library of marketing offers and a decision engine that applies rules and constraints to rich, real-time profiles created by Adobe Experience Platform. As a result, it enables you to send your customers the right offer at the right time. See [About Decision Management](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioning/get-started-decision/starting-offer-decisioning.html?lang=en) for more information. 




>[!NOTE]
>
>This lesson is optional and only applies to Journey Optimizer users looking to use the Decision Management functionality to display offers in a mobile app.


## Prerequisites

* Successfully built and run app with SDKs installed and configured.
* Set up the app for Adobe Experience Platform.
* Access to Journey Optimizer - Decision Management with the [proper permissions to manage offers and decisions](https://experienceleague.adobe.com/docs/journey-optimizer/using/access-control/privacy/high-low-permissions.html?lang=en#decisions-permissions).


## Learning objectives

In this lesson, you will

* Update your Edge configuration for Decision Management.
* Update your tag property with the Offer Decisioning and Target extension.
* Update your schema to capture proposition events.
* Validate setup in Assurance.
* Create an offer decision, based on offers in Journey Optimizer - Decision Management.
* Update your app to register the Optimizer extension.
* Implement offers from Decision Management in your app.


## Setup

>[!TIP]
>
>If you have set up your environment already as part of the [Setup A/B tests with Target](target.md) lesson, you might already have performed some of the steps in this setup section.

### Update datastream configuration

To ensure data sent from your mobile app to Platform Edge Network is forwarded to Journey Optimizer - Decision Management, update your datastream.

1. In the Data Collection UI, select **[!UICONTROL Datastreams]**, and select your datastream, for example **[!DNL Luma Mobile App]**.
1. Select ![More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_MoreSmallList_18_N.svg) for **[!UICONTROL Experience Platform]** and select ![Edit](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) **[!UICONTROL Edit]** from the context menu.
1. In the **[!UICONTROL Datastreams]** > ![Folder](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) >  **[!UICONTROL Adobe Experience Platform]** screen, ensure **[!UICONTROL Offer Decisioning]**, **[!UICONTROL Edge Segmentation]**, and **[!UICONTROL Adobe Journey Optimizer]** are selected. If you will do the Target lesson, select **[!UICONTROL Personalization Destinations]**, too. See [Adobe Experience Platform settings](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html?lang=en#aep) for more information.
1. To save your datastream configuration, select **[!UICONTROL Save]** .

   ![AEP datastream configuration](assets/datastream-aep-configuration-offers.png){zoomable="yes"}

   


### Install Journey Optimizer - Decisioning tags extension

1. Navigate to **[!UICONTROL Tags]** and find your mobile tag property and open the property.
1. Select **[!UICONTROL Extensions]**.
1. Select **[!UICONTROL Catalog]**.
1. Search for the **[!UICONTROL Offer Decisioning and Target]** extension.
1. Install the extension. The extension does not require additional configuration.

    ![Add Offer Decisioning and Target extension](assets/tag-add-decisioning-extension.png)


### Update your schema

1. Navigate to Data Collection interface and select **[!UICONTROL Schemas]** from the left rail.
1. Select **[!UICONTROL Browse]** from the top bar.
1. Select your schema to open it.
1. In the schema editor, select ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Add]** next to Field groups.
1. In the **[!UICONTROL Add fields groups]** dialog, ![Search](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Search_18_N.svg) search for `proposition`, select **[!UICONTROL Experience Event - Proposition Interactions]** and select **[!UICONTROL Add field groups]**. This field group collects the experience event data relevant to offers: what offer is presented, as part of which collection, decision, and other parameters (see later in this lesson). But also what is happening with the offer? Is it displayed, interacted with, dismissed, and so forth.
   ![Proposition](assets/schema-fieldgroup-proposition.png){zoomable="yes"}
1. Select **[!UICONTROL Save]** to save the changes to your schema.


## Validate setup in Assurance

To validate your setup in Assurance:

1. Go to the Assurance UI.
1. Select **[!UICONTROL Configure]** in left rail and select ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) next to **[!UICONTROL Validate Setup]** underneath **[!UICONTROL OFFER DECISIONING AND TARGET]**.
1. Select **[!UICONTROL Save]**.
1. Select **[!UICONTROL Validate Setup]** in the left rail. Both datastream setup and the SDK setup in your application are validated.
   ![AJO Decisioning validation](assets/ajo-decisioning-validation.png){zoomable="yes"}


## Create placement

Before you can actually create offers, you have to define how and where these offers can be placed in the mobile app. In Decision Management, you define placements for this purpose and you will define a placement for the mobile channel that supports a JSON payload:

1. In the Journey Optimizer UI, select ![Components](https://spectrum.adobe.com/static/icons/workflow_18/Smock_OfferActivities_18_N.svg)  **[!UICONTROL Components]** from **[!UICONTROL DECISION MANAGEMENT]** in the left rail.

1. Select **[!UICONTROL Placements]** from the top bar. 
   
1. If no placement with name **[!UICONTROL Mobile JSON]**,  **[!UICONTROL Mobile]** as **[!UICONTROL Channel type]** and **[!UICONTROL JSON]** as **[!UICONTROL Content type]** is  listed, you must create a placement. Otherwise, continue to [Create offers](#create-offers).

To create the Mobile JSON placement: 

1. Select ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) Create placement.

   1. in the **[!UICONTROL Details]** section, enter `Mobile JSON` as the **[!UICONTROL Name]**, select **[!UICONTROL Mobile]** from **[!UICONTROL Channel type]** and **[!UICONTROL JSON]** from **[!UICONTROL Content type]**.
   1. Select **[!UICONTROL Save]** to save the placement.

   ![Create placement](assets/ajo-create-placement.png){zoomable="yes"}



## Create offers

1. In the Journey Optimizer UI, select ![Offers](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Offers_18_N.svg)  **[!UICONTROL Offers]** from **[!UICONTROL DECISION MANAGEMENT]** in the left rail.
1. In the **[!UICONTROL Offers]** screen, select **[!UICONTROL Browse]** to see the list of offers.
1. Select **[!UICONTROL Create offer]**.
1. In the **[!UICONTROL New offer]** dialog, select **[!UICONTROL Personalized offer]** and click **[!UICONTROL Next]**.
1. In the **[!UICONTROL Details]** step of **[!UICONTROL Create new personalized offer]**:
   1. Enter a **[!UICONTROL Name]** for the offer, for example `Luma - Juno Jacket`, and enter a **[!UICONTROL Start date and time]** and an **[!UICONTROL End date and time]**. Outside of these dates, the offer won't be selected by the Decisioning engine.
   1. Select **[!UICONTROL Next]**.
      ![Offers - Details](assets/ajo-offers-details.png){zoomable="yes"}

1. In the **[!UICONTROL Add representations]** step of **[!UICONTROL Create new personalized offer]**:
   1. Select ![Mobile](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DevicePhone_18_N.svg) **[!UICONTROL Mobile]** from **[!UICONTROL Channel]** list, and select **[!UICONTROL Mobile JSON]** from the **[!UICONTROL Placement]** list.
   1. Select **[!UICONTROL Custom]** for **[!UICONTROL Content]**.
   1. Select **[!UICONTROL Add content]**. In the **[!UICONTROL Add personalization]** dialog:
      1. In case a [!UICONTROL Mode] selector is available, ensure it is set to **[!UICONTROL JSON]**.
      1. Enter the following JSON:
   
            ```json
            { 
                "title": "Juno Jacket",
                "text": "On colder-than-comfortable mornings, you'll love warming up in the Juno All-Ways Performance Jacket, designed to compete with wind and chill. Built-in Cocona&trade; technology aids evaporation, while a special zip placket and stand-up collar keep your neck protected.", 
                "image": "https://luma.enablementadobe.com/content/dam/luma/en/products/women/tops/jackets/wj06-purple_main.jpg" 
            }  
            ```

      1. Select **[!UICONTROL Save]**.
         ![Offers - Custom content](assets/ajo-offers-customcontent.png){zoomable="yes"}
   1. Select **[!UICONTROL Next]**.
      ![Offer Representations](assets/ajo-offers-representations.png){zoomable="yes"} 

1. In the **[!UICONTROL Add constraints]** step of the **[!UICONTROL Create new personalized offer]**:
   1. Set **[!UICONTROL Priority]** to `10`.
   1. Toggle **[!UICONTROL Include capping]** off.
   1. Select **[!UICONTROL Next]**.
      ![Offers - Constraints](assets/ajo-offers-constraints.png){zoomable="yes"}

1. In the **[!UICONTROL Review]** step of **[!UICONTROL Create new personalized]** offer:
   1. Review the offer, then select **[!UICONTROL Finish]**.
   1. In the **[!UICONTROL Save offer]** dialog, select **[!UICONTROL Save and approve]**.

1. Repeat steps 3 - 8 to create four more offers with different names and content. All other configuration values, for example Start date and time or Priority, are similar to the first offer you created. You can quickly create duplicate and edit offers.

   1. In Journey Optimizer UI, select ![Offers](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Offers_18_N.svg) **[!UICONTROL Offers]** from the left rail, then select Offers from the top bar.
   1. Select the row of the offer that you created.
   1. In the right pane, select ![More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_MoreSmall_18_N.svg) **[!UICONTROL More actions]** and from the context menu select ![Duplicate](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Duplicate_18_N.svg) **[!UICONTROL Duplicate]**.

      Use the table below to define the four other offers.

       | Offer name | Offer content in JSON |
       |---|---|
       | Luma - Affirm Water Bottle | `{ "title": "Affirm Water Bottle", "text": "You'll stay hydrated with ease with the Affirm Water Bottle by your side or in hand. Measurements on the outside help you keep track of how much you're drinking, while the screw-top lid prevents spills. A metal carabiner clip allows you to attach it to the outside of a backpack or bag for easy access.", "image": "https://luma.enablementadobe.com/content/dam/luma/en/products/gear/fitness-equipment/ug06-lb-0.jpg" }` |
       | Luma - Desiree Fitness Tee | `{ "title": "Desiree Fitness Tee", "text": "When you're too far to turn back, thank yourself for choosing the Desiree Fitness Tee. Its ultra-lightweight, ultra-breathable fabric wicks sweat away from your body and helps keeps you cool for the distance.", "image": "https://luma.enablementadobe.com/content/dam/luma/en/products/women/tops/tees/ws05-yellow_main.jpg" }` |
       | Luma - Adrienne Trek Jacket | `{ "title": "Adrienne Trek Jacket", "text": "You're ready for a cross-country jog or a coffee on the patio in the Adrienne Trek Jacket. Its style is unique with stand collar and drawstrings, and it fits like a jacket should.", "image": "https://luma.enablementadobe.com/content/dam/luma/en/products/women/tops/jackets/wj08-gray_main.jpg" }` |
       | Luma - Aero Daily Fitness Tee | `{ "title": "Aero Daily Fitness Tee", "text": "Need an everyday action tee that helps keep you dry? The Aero Daily Fitness Tee is made of 100% polyester wicking knit that funnels moisture away from your skin. Don't be fooled by its classic style; this tee hides premium performance technology beneath its unassuming look.", "image": "https://luma.enablementadobe.com/content/dam/luma/en/products/men/tops/tees/ms01-black_main.jpg" }` |

       {style="table-layout:fixed"}

1. As a final step you must create a fallback offer, which is an offer sent to customers if they are not eligible for other offers.
   1. Select **[!UICONTROL Create offer]**.
   1. In the **[!UICONTROL New offer]** dialog, select **[!UICONTROL Personalized offer]** and select **[!UICONTROL Next]**.
   1. In the **[!UICONTROL Details]** step of **[!UICONTROL Create new fallback offer]**, enter a **[!UICONTROL Name]** for the offer, for example `Luma - Fallback Offer`, and select **[!UICONTROL Next]**.

   1. In the **[!UICONTROL Add representations]** step of  **[!UICONTROL Create new fallback offer]**:
      1. Select ![Mobile](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DevicePhone_18_N.svg) **[!UICONTROL Mobile]** from **[!UICONTROL Channel]** list, and select **[!UICONTROL Mobile JSON]** from **[!UICONTROL Placement]** list.
      1. Select **[!UICONTROL Custom]** for **[!UICONTROL Content]**.
      1. Select **[!UICONTROL Add content]**. 
      1. In the **[!UICONTROL Add personalization]** dialog, enter the following JSON and select **[!UICONTROL Save]**:
      
            ```json
            {  
               "title": "Luma",
               "text": "Your store for sports wear and equipment.", 
               "image": "https://luma.enablementadobe.com/content/dam/luma/en/logos/Luma_Logo.png" 
            }  
            ```

      1. Select **[!UICONTROL Next]**.


1. In the **[!UICONTROL Review]** step of **[!UICONTROL Create new fallback]** offer:
   1. Review the offer, then select **[!UICONTROL Finish]**.
   1. In the **[!UICONTROL Save offer]** dialog, select **[!UICONTROL Save and approve]**.

You should now have the following list of offers:
![Offers list](assets/ajo-offers-list.png){zoomable="yes"}


## Create a collection

To present an offer to your mobile app user, you must define an offer collection, consisting of one or more of the offers you created.

1. In the Journey Optimizer UI, select **[!UICONTROL Offers]** from the left rail.
1. Select **[!UICONTROL Collections]** from the top bar.
1. Select ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Create collection]**.
1. In the **[!UICONTROL New collection]** dialog, enter a **[!UICONTROL Name]** for your collection, for example `Luma - Mobile App Collection`, select **[!UICONTROL Create static collection]**, and click **[!UICONTROL Next]**.
1. In **[!DNL Luma - Mobile App Collection]**, select the offers you want to include in the collection. For this tutorial, pick the five offers you created. You can easily filter the list using the search field, for example by typing **[!DNL Luma]**.
1. Select **[!UICONTROL Save]**.

    ![Offers - Collection](assets/ajo-collection-offersselected.png){zoomable="yes"}


## Create a decision

The final step is to define a decision, which is the combination of one or more decision scopes and your fallback offer. 

A decision scope is a combination of a specific placement (for example HTML in an email, or JSON in a mobile app) and one or more evaluation criteria. 

An evaluation criterium is the combination of 

* an offer collection,
* eligibility rules: for example, is the offer only available for a specific audience,
* a ranking method: when multiple offers are available to pick from, which method do you use to rank them (for example by offer priority, using a formula, or an AI model).

See [Key steps to create and manage offers](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioning/get-started-decision/key-steps.html?lang=en) if you want to better understand how placements, rules, rankings, offers, representations, collections, decisions, and so on, interact and relate to each other. This lesson is solely focused on using the output of a decision rather than on the flexibility in defining decisions within Journey Optimizer - Decision Management.

1. In the Journey Optimizer UI, select **[!UICONTROL Offers]** from the left rail.
1. Select **[!UICONTROL Decisions]** from the top bar.
1. Select ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Create decision]**.
1. In the **[!UICONTROL Details]** step of **[!UICONTROL Create a new offer decision]**:
   1. Enter a **[!UICONTROL Name]** for the decision, for example `Luma - Mobile App Decision`, enter **[!UICONTROL Start date and time]** and **[!UICONTROL End date and time]**.
   1. Select **[!UICONTROL Next]**.

1. In the **[!UICONTROL Add decision scopes]** step of **[!UICONTROL Create a new offer decision]**:
   1. Select **[!UICONTROL Mobile JSON]** from **[!UICONTROL Placement]** list.
   1. In the **[!UICONTROL Evaluation Criteria]** tile, select ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Add]**.
      1. In the **[!UICONTROL Add Offer Collection]** dialog, select your offer collection. For example, **[!DNL Luma - Mobile App Collection]**.
      1. Select **[!UICONTROL Add]**.
   
         ![Decision - Select collection](assets/ajo-decision-selectcollection.png){zoomable="yes"}

   1. Ensure that **[!UICONTROL None]** is selected for **[!UICONTROL Eligibility]**, and **[!UICONTROL Offer priority]** is selected as the **[!UICONTROL Ranking method]**. 
   1. Select **[!UICONTROL Next]**.
   
      ![Decision scopes](assets/ajo-decision-scopes.png){zoomable="yes"}

1. In the **[!UICONTROL Add fallback offer]** step of **[!UICONTROL Create a new offer decision]**:
   1. Select your fallback offer, for example the **[!DNL Luma - Fallback offer]**.
   1. Select **[!UICONTROL Next]**.
1. In the **[!UICONTROL Summary]** step of **[!UICONTROL Create a new offer decision]**:
   1. Select **[!UICONTROL Finish]**.
   1. In the **[!UICONTROL Save offer decision]** dialog, select **[!UICONTROL Save and activate]**.
   1. In the **[!UICONTROL Decisions]** tab, you see your decision with status **[!UICONTROL Live]**.

Your offer decision, consisting of a set of offers, is now ready for use. To use the decision in your app, you have to refer in your code to the decision scope.

1. In the Journey Optimizer UI, select **[!UICONTROL Offers]**.
1. Select **[!UICONTROL Decisions]** from the top bar.
1. Select your decision, for example **[!DNL Luma - Mobile App Decision]**.
1. In the **[!UICONTROL Decision scopes]** tile, select ![Copy](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) **[!UICONTROL Copy]**.
1. From the contextual menu, select **[!UICONTROL Decision scope]**.
   
   ![Copy decision scope](assets/ajo-copy-decisionscope.png){zoomable="yes"} 

1. Use any text editor to paste the decision scope for later use. The decision scope has the following JSON format.

    ```json
    {
        "xdm:activityId":"xcore:offer-activity:xxxxxxxxxxxxxxx",
        "xdm:placementId":"xcore:offer-placement:xxxxxxxxxxxxxxx"
    }
    ```

## Implement offers in your app

As discussed in previous lessons, installing a mobile tag extension only provides the configuration. Next you must install and register the Optimize SDK. If these steps aren't clear, review the [Install SDKs](install-sdks.md) section.

>[!NOTE]
>
>If you completed the [Install SDKs](install-sdks.md) section, then the SDK is already installed and you can skip this step.
>

>[!BEGINTABS]

>[!TAB iOS]

1. In Xcode, ensure that [AEP Optimize](https://github.com/adobe/aepsdk-messaging-ios) is added to the list of packages in Package Dependencies. See [Swift Package Manager](install-sdks.md#swift-package-manager).
1. Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!UICONTROL AppDelegate]** in the Xcode Project navigator.
1. Ensure `AEPOptimize` is part of your list of imports.

   ```swift
   import AEPOptimize
   ```
   
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

1. Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Model]** > **[!DNL Data]** > **[!UICONTROL decisions]** in the Xcode Project navigator. Update the `activityId` and `placementId` values with the decision scope details you copied from the Journey Optimizer interface.

1. Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** in the Xcode Project navigator. Find the `func updatePropositionOD(ecid: String, activityId: String, placementId: String, itemCount: Int) async` function. Add the following code:

   ```swift
   // set up the XDM dictionary, define decision scope and call update proposition API
   Task {
      let ecid = ["ECID" : ["id" : ecid, "primary" : true] as [String : Any]]
      let identityMap = ["identityMap" : ecid]
      let xdmData = ["xdm" : identityMap]
      let decisionScope = DecisionScope(activityId: activityId, placementId: placementId, itemCount: UInt(itemCount))
      Optimize.clearCachedPropositions()
      Optimize.updatePropositions(for: [decisionScope], withXdm: xdmData) { data, error in
            if let error = error {
               Logger.aepMobileSDK.error("MobileSDK - updatePropositionsAT: Error updating propositions: \(error.localizedDescription)")
            }
      }
   }
   ```

   This function:
   
   * sets up an XDM dictionary `xdmData`, containing the ECID to identify the profile for which you have to present the offers. 
   * defines `decisionScope`, an object that is based on the decision you have defined in the Journey Optimizer - Decision Management interface and is defined using the copied decision scope from [Create a decision](#create-a-decision).  The Luma app uses a configuration file (`decisions.json`) that retrieves the scope parameters, based on the following JSON format:

       ```json
       "scopes": [
           {
               "name": "name of the scope",
               "activityId": "xcore:offer-activity:xxxxxxxxxxxxxxx",
               "placementId": "xcore:offer-placement:xxxxxxxxxxxxxxx",
               "itemCount": 2
           }
       ]
       ```

      However, you can use any kind of implementation to ensure the Optimize APIs get the proper parameters (`activityId`, `placementId` and, `itemCount`), to construct a valid [`DecisionScope`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#decisionscope) object for your implementation. <br/>For your information: the other key-values in the `decisions.json` file are for future use and not relevant and used currently in this lesson and as as part of the tutorial.

   * calls two APIs: [`Optimize.clearCachePropositions`](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/api-reference/#clearpropositions)  and [`Optimize.updatePropositions`](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/api-reference/#updatepropositionswithcompletionhandler).  These functions clear any cached propositions and update the propositions for this profile.

1. Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!UICONTROL Personalization]** > **[!UICONTROL EdgeOffersView]** in the Xcode Project navigator. Find the `func onPropositionsUpdateOD(activityId: String, placementId: String, itemCount: Int) async` function and inspect the code of this function. The most important part of this function is the [`Optimize.onPropositionsUpdate`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#onpropositionsupdate) API call, which 
   
    * retrieves the propositions for the current profile based on the decision scope (which you have defined in Journey Optimizer - Decision Management), 
    * retrieves the offer from the proposition,
    * unwraps the content of the offer so it can be displayed properly in the app, and
    * triggers the `displayed()` action on the offer which sends an event back to the Edge Network informing the offer is displayed. 

1. Still in **[!DNL EdgeOffersView]**, add the following code to the `.onFirstAppear` modifier. This code ensures that the callback for updating the offers is registered only once.

    ```swift
    // Invoke callback for offer updates
    Task {
        await self.onPropositionsUpdateOD(activityId: decision.activityId, placementId: decision.placementId, itemCount: decision.itemCount)
    }
    ```

1. Still in **[!UICONTROL EdgeOffersView]**, add the following code to the `.task` modifier. This code updates the offers when the view is refreshed.

    ```swift
    // Clear and update offers
    await self.updatePropositionsOD(ecid: currentEcid, activityId: decision.activityId, placementId: decision.placementId, itemCount: decision.itemCount)
    ```

>[!TAB Android]


1. In Android Studio, ensure that [aepsdk-optimize-android](https://github.com/adobe/aepsdk-optimize-android) is part of the depencencies in **[!UICONTROL build.gradle.kts (Module :app)]** in **[!UICONTROL Android]** ![ChevronDown](/help/assets/icons/ChevronDown.svg) > **[!UICONTROL Gradle Scripts]**. See [Gradle](install-sdks.md#gradle).
1. Navigate to **[!UICONTROL Android]** ![ChevronDown](/help/assets/icons/ChevronDown.svg) > **[!DNL app]** > **[!DNL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL MainActivity]** in the Android Studio navigator.
1. Ensure `Optimize` is part of your list of imports.

   ```kotlin
   import com.adobe.marketing.mobile.optimize.Optimize
   ```
   
1. Ensure `Optimize.EXTENSION` is part of the array of extensions that you are registering.

   ```kotlin
   val extensions = listOf(
      Identity.EXTENSION,
      Lifecycle.EXTENSION,
      Signal.EXTENSION,
      Edge.EXTENSION,
      Consent.EXTENSION,
      UserProfile.EXTENSION,
      Places.EXTENSION,
      Messaging.EXTENSION,
      Optimize.EXTENSION,
      Assurance.EXTENSION
   )
   ```

1. Navigate to **[!UICONTROL Android]** ![ChevronDown](/help/assets/icons/ChevronDown.svg) > **[!DNL app]** > **[!DNL assets]** > **[!DNL data]** > **[!UICONTROL decisions.json]** in the Xcode Project navigator. Update the `activityId` and `placementId` values with the decision scope details you copied from the Journey Optimizer interface.

1. Navigate to **[!UICONTROL Android]** ![ChevronDown](/help/assets/icons/ChevronDown.svg) > **[!DNL app]** > **[!DNL kotlin+java]** > **[!DNL com.adobe.luma.tutorial.android]** > **[!UICONTROL models]** > **[!UICONTROL MobileSDK]** in the Android Studio navigator. Find the `suspend fun updatePropositionsOD(ecid: String,        activityId: String, placementId: String, itemCount: Int) ` function. Add the following code:

   ```kotlin
   // set up the XDM dictionary, define decision scope and call update proposition API
   withContext(Dispatchers.IO) {
      val ecidMap = mapOf("ECID" to mapOf("id" to ecid, "primary" to true))
      val identityMap = mapOf("identityMap" to ecidMap)
      val xdmData = mapOf("xdm" to identityMap)
      val decisionScope = DecisionScope(activityId, placementId, itemCount)
      Optimize.clearCachedPropositions()
      Optimize.updatePropositions(listOf(decisionScope), xdmData, null, object :
            AdobeCallbackWithOptimizeError<MutableMap<DecisionScope?, OptimizeProposition?>?> {
            override fun fail(optimizeError: AEPOptimizeError?) {
               val responseError = optimizeError
               Log.i("MobileSDK", "updatePropositionsOD error: ${responseError}")
            }
            override fun call(propositionsMap: MutableMap<DecisionScope?, OptimizeProposition?>?) {
               val responseMap = propositionsMap
               Log.i("MobileSDK", "updatePropositionsOD call: ${responseMap}")
            }
      })
   }
   ```

   This function:
   
   * sets up an XDM dictionary `xdmData`, containing the ECID to identify the profile for which you have to present the offers. 
   * defines `decisionScope`, an object that is based on the decision you have defined in the Journey Optimizer - Decision Management interface and is defined using the copied decision scope from [Create a decision](#create-a-decision).  The Luma app uses a configuration file (`decisions.json`) that retrieves the scope parameters, based on the following JSON format:

       ```json
       "scopes": [
           {
               "name": "name of the scope",
               "activityId": "xcore:offer-activity:xxxxxxxxxxxxxxx",
               "placementId": "xcore:offer-placement:xxxxxxxxxxxxxxx",
               "itemCount": 2
           }
       ]
       ```

      However, you can use any kind of implementation to ensure the Optimize APIs get the proper parameters (`activityId`, `placementId` and, `itemCount`), to construct a valid [`DecisionScope`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#decisionscope) object for your implementation. <br/>For your information: the other key-values in the `decisions.json` file are for future use and not relevant and used currently in this lesson and as as part of the tutorial.

   * calls two APIs: [`Optimize.clearCachePropositions`](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/api-reference/#clearpropositions)  and [`Optimize.updatePropositions`](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/api-reference/#updatepropositionswithcompletionhandler).  These functions clear any cached propositions and update the propositions for this profile.

1. Navigate to **[!UICONTROL Android]** ![ChevronDown](/help/assets/icons/ChevronDown.svg) > **[!DNL app]** > **[!DNL kotlin+java]** > **[!DNL com.adobe.luma.tutorial.android]** > **[!UICONTROL views]** > **[!UICONTROL EdgeOffers.kt]** in the Xcode Project navigator. Find the `suspend fun onPropositionsUpdateOD(ecid: String, activityId: String, placementId: String, itemCount: Int)` function and inspect the code of this function. The most important part of this function is the [`Optimize.onPropositionsUpdate`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#onpropositionsupdate) API call, which 
   
    * retrieves the propositions for the current profile based on the decision scope (which you have defined in Journey Optimizer - Decision Management), 
    * retrieves the offer from the proposition,
    * unwraps the content of the offer so it can be displayed properly in the app, and
    * returns the offers.

1. Still in **[!DNL EdgeOffers.kt]**, add the `LaunchedEffect` function to ensure offers are refreshed upon launching the Personalization tab.

    ```kotlin
    // recompose the view when the number of received offers changes
    LaunchedEffect(offersOD.count()) {
        updatePropositionsOD(
            currentEcid,
            decision.activityId,
            decision.placementId,
            decision.itemCount
        )
        offersOD =
            onPropositionsUpdateOD(decision.activityId, decision.placementId, decision.itemCount)
    }
    ```

>[!ENDTABS]

## Validate using the app

>[!BEGINTABS]

>[!TAB iOS]

1. Rebuild and run the app in the simulator or on a physical device from Xcode, using ![Play](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Play_18_N.svg).

1. Go to the **[!DNL Personalisation]** tab.

1. Scroll to the top, and you see two random offers displayed  from the collection that you have defined in the **[!DNL DECISION LUMA - MOBILE APP DECISION]** tile.

    <img src="assets/ajo-app-offers.png" width=300>

   The offers are random, as you have given all offers the same priority and the ranking for the decision is based on priority.


>[!TAB Android]

1. Rebuild and run the app in the simulator or on a physical device from Android Studio, using ![Play](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Play_18_N.svg).

1. Go to the **[!DNL Personalisation]** tab.

1. Scroll to the top, and you see two random offers displayed in the upper box from the collection that you have defined in the **[!DNL DECISION LUMA - MOBILE APP DECISION]** tile.

    <img src="assets/ajo-app-offers-android.png" width=300>

   The offers are random, as you have given all offers the same priority and the ranking for the decision is based on priority.

>[!ENDTABS]

## Validate implementation in Assurance

To validate the offers implementation in Assurance:

1. Review the [setup instructions](assurance.md#connecting-to-a-session) section to connect your simulator or device to Assurance.
1. Select **[!UICONTROL Configure]** in left rail and select ![Add](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) next to **[!UICONTROL Review & Simulate]** underneath **[!UICONTROL ADOBE JOURNEY OPTIMIZER DECISIONING]**.
1. Select **[!UICONTROL Save]**.
1. Select **[!UICONTROL Review & Simulate]** in the left rail. Both datastream setup is validated and the SDK setup in your application.
1. Select **[!UICONTROL Requests]** at the top bar. You see your **[!UICONTROL Offers]** requests.
   ![AJO Decisioning validation](assets/assurance-decisioning-requests.png){zoomable="yes"}

1. You can explore **[!UICONTROL Simulate]** and **[!UICONTROL Event List]** tabs for further functionality, checking your setup of Journey Optimizer Decision Management.

## Next steps

You should now have all the tools to start adding more functionality to your Journey Optimizer - Decision Management implementation. For example:

* apply different parameters to your offers (for example, priority, capping)
* collect profile attributes in the app (see [Profile](profile.md)) and use these profile attributes to build audiences. Then use these audiences as part of the eligibility rules in your decision.
* combine more than one decision scope.

>[!SUCCESS]
>
>You have enabled the app to display offers using the Offer Decisioning and Target extension for the Experience Platform Mobile SDK.
>
>Thank you for investing your time in learning about Adobe Experience Platform Mobile SDK. If you have questions, want to share general feedback, or have suggestions on future content, share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Next: **[Perform A/B tests](target.md)**
