---
title: Create And Display Offers With Journey Optimizer Experience Decisioning 
description: Learn how to create and display offers with Platform Mobile SDK and Adobe Journey Optimizer Decisioning.
solution: Data Collection,Journey Optimizer
feature-set: Journey Optimizer
feature: Offers
jira: KT-14640
TQID: https://experienceleague.adobe.com/cogzxUba6Z6ZCQ3ZOu3oXXSuxqe05OAP5FICWPs-Jhc
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
    internal-label: Journey Optimizer
feature_v2:
  - id: b3538224-471e-4c63-a444-9b19d89ae29c
    internal-label: Activities
  - id: d556b755-390a-43f0-be32-a08cf6236126
    internal-label: Configuration
  - id: fe338112-e2ce-4876-8989-fc4d497613f1
    internal-label: Email
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
    internal-label: Measurement
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
---
# Create and display offers with Decisioning

Learn how to show offers from Journey Optimizer Decisioning in your mobile apps with Experience Platform Mobile SDK.

Journey Optimizer Decisioning is the next generation of offer management and successor of [Decision Management](./journey-optimizer-offers.md). The Decisioning feature empowers you to deliver personalized marketing offers by combining a centralized catalog of decision items with a powerful decision engine. Whether you're tailoring content for individual audiences or optimizing strategies with AI-powered rankings, Decisioning provides the tools to make data-driven decisions at scale. Dive into the key concepts such as decision items, rules, and policies, and explore how these elements work together to select and prioritize the best content for your campaigns. From managing collections and placements to leveraging Adobe Experience Platform data, this comprehensive guide helps you unlock smarter personalization and drive impactful customer experiences.

![Architecture](assets/architecture-ajo.png){zoomable="yes"}

Decisioning simplifies personalization by offering a centralized catalog of marketing offers known as 'decision items' and a sophisticated decision engine. This engine leverages rules and ranking criteria to select and present the most relevant decision items to each individual. These decision items are seamlessly integrated into messages and experiences across Adobe Journey Optimizer channels: code-based experience, email, SMS, push notifications, and more. 

In this lesson, the focus is on the use of the code-based experience channel to deliver offers in the mobile app. See [Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/experience-decisioning/experience-decisioning-landing-page) for more information. 


>[!NOTE]
>
>This lesson is optional and only applies to Journey Optimizer users looking to use the Decision Management functionality to display offers in a mobile app.


## Prerequisites

* Successfully built and run app with SDKs installed and configured.
* Set up the app for Adobe Experience Platform.
* Access to Journey Optimizer - Decisioning with the [proper permissions to manage offers and decisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/access-control/high-low-permissions).


## Learning objectives

In this lesson, you will

* Update your Edge configuration for Decisioning.
* Create a schema to represent offers.
* Validate setup in Assurance.
* Configure a code-based experience channel configuration.
* 
* Create a code-based experience campaign, based on offers in Journey Optimizer - Decision Management.
* Implement offers from Decisioning in your app.


## Setup

>[!TIP]
>
>If you have set up your environment already as part of the [Setup A/B tests with Target](target.md) lesson, you might already have performed some of the steps in this setup section.

### Update datastream configuration

To ensure data sent from your mobile app to Platform Edge Network is forwarded to Journey Optimizer - Decision Management, update your datastream.

1. In the Data Collection UI, select **[!UICONTROL Datastreams]**, and select your datastream, for example **[!DNL Luma Mobile App]**.
1. Select ![More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_MoreSmallList_18_N.svg) for **[!UICONTROL Experience Platform]** and select ![Edit](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) **[!UICONTROL Edit]** from the context menu.
1. In the **[!UICONTROL Datastreams]** > ![Folder](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) >  **[!UICONTROL Adobe Experience Platform]** screen, ensure **[!UICONTROL Offer Decisioning]**, **[!UICONTROL Edge Segmentation]**, and **[!UICONTROL Adobe Journey Optimizer]** are enabled. 
   * If you plan to only do the Decisioning lesson and not the Decision management lesson, you do not need to enable **[!UICONTROL Offer Decisioning]**.
   * If you do the Target lesson, select **[!UICONTROL Personalization Destinations]**, too. See [Adobe Experience Platform settings](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) for more information.
1. To save your datastream configuration, select **[!UICONTROL Save]** .

   ![AEP datastream configuration](assets/datastream-aep-configuration-offers.png){zoomable="yes"}


### Define your schema

1. Navigate to the Data Collection interface and select **[!UICONTROL Schemas]** from the left rail.
1. Select **[!UICONTROL Browse]** from the top bar.
1. Open the **[!UICONTROL Personalized Offer Items - Experience Decisioning]** schema. This schema is the dedicated schema to configure your offer items, their attributes and metadata.
1. Add additional field groups to your schema that represent how you want to use offers in Decisioning. Refer to [Create schema](./create-schema.md) to understand how you can create schemas. For this lesson, two field groups are created as part of the sandbox configuration: **[!UICONTROL Offer]** and **[!UICONTROL Offer Metadata]**. You can see the full structure of the schema below. All **[!UICONTROL mediaAssets]** fields, like **[!UICONTROL image]** or **[!UICONTROL imageLowRes]** are of type **[!UICONTROL DesignAssets]**. All other fields are either of type **[!UICONTROL Object]** or **[!UICONTROL String]**.
   
   ![Schema experience decisioning](assets/schema-experience-decisioning.png){zoomable="yes"}

   You can define your **[!UICONTROL Personalized Offer Items - Experience Decisioning]** schema any way you want. The above is just an example that is used for the remainder of this lesson.

1. Ensure you select **[!UICONTROL Save]** to save any changes you make to the **[!UICONTROL Personalized Offer Items - Experience Decisioning]** schema.


### Install Journey Optimizer tags extension

For your app to work with Journey Optimizer, you must update your tag property.

1. Navigate to **[!UICONTROL Tags]** > **[!UICONTROL Extensions]** > **[!UICONTROL Catalog]**. 
1. Open your property, for example **[!DNL Luma Mobile App Tutorial]**.
1. Select **[!UICONTROL Catalog]**.
1. Search for the **[!UICONTROL Adobe Journey Optimizer]** extension.
1. Install the extension.

When *only* using offers based on Decisioning in your app, in **[!UICONTROL Install Extension]** or **[!UICONTROL Configure Extension]**, you do not need to configure anything. If you already have followed the [Push notifications](journey-optimizer-push.md) lesson in the tutorial, you see that for the **[!UICONTROL Development]** environment, the **[!UICONTROL AJO Push Tracking Experience Event Dataset]** dataset is selected from the **[!UICONTROL Event Dataset]** list.


### Implement Journey Optimizer in the app

As discussed in previous lessons, installing a mobile tag extension only provides the configuration. Next you must install and register the Messaging SDK. If these steps aren't clear, review the [Install SDKs](install-sdks.md) section.

>[!NOTE]
>
>If you completed the [Install SDKs](install-sdks.md) section, then the SDK is already installed and you can skip this step.
>

>[!BEGINTABS]

>[!TAB iOS]

1. In Xcode, ensure that [AEP Messaging](https://github.com/adobe/aepsdk-messaging-ios) is added to the list of packages in Package Dependencies. See [Swift Package Manager](install-sdks.md#swift-package-manager).
1. Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!UICONTROL AppDelegate]** in the Xcode Project navigator.
1. Ensure `AEPMessaging` is part of your list of imports.

    `import AEPMessaging`

1. Ensure `Messaging.self` is part of the array of extensions that you are registering.

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

>[!TAB Android]

1. In Android Studio, ensure that [aepsdk-messaging-android](https://github.com/adobe/aepsdk-messaging-android) is part of the dependencies in **[!UICONTROL build.gradle.kts]** in **[!UICONTROL Android]** ![ChevronDown](/help/assets/icons/ChevronDown.svg) > **[!UICONTROL Gradle Scripts]**. See [Gradle](install-sdks.md#gradle).
1. Navigate to **[!UICONTROL Android]** ![ChevronDown](/help/assets/icons/ChevronDown.svg) **[!DNL app]** > **[!DNL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL LumaApplication]** in the Android Studio project navigator.
1. Ensure `com.adobe.marketing.mobile.Messaging` is part of your list of imports.

    `import import com.adobe.marketing.mobile.Messaging`

1. Ensure `Messaging.EXTENSION` is part of the array of extensions that you are registering.

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

>[!ENDTABS]

## Validate setup in Assurance

You do not need to validate the setup for Decisioning in Assurance. Decisioning does not use a specific Experience Platform Data Collection Tag extension, nor does Decisioning require an additional package for your app. Decisioning relies on the Messaging extension in your app, which you already should have added as part of the [Install Adobe Experience Platform Mobile SDKs](./install-sdks.md) and [Create and send in-app messagesless](./journey-optimizer-inapp.md) lessons in this tutorial.


## Create code-based experience channel configuration

To display offers in the screens of your app, you need to configure a dedicated code-based experience channel. This code-based experience channel defines the surface (the location) where you render your offers.

To create a code-based experience channel.

1. In the Journey Optimizer UI, select ![Channel](/help/assets/icons2/Channel.svg) **[!UICONTROL Channels]** from **[!UICONTROL Administration]** in the left rail.
1. Select **[!UICONTROL Channel configurations]** from **[!UICONTROL General Settings]**.
1. Select **[!UICONTROL Create channel configuration]**.
1. In **[!UICONTROL Channel configuration details]**:

   ![Channel configuration details](assets/ajo-code-based-experience-channel-configuration.png)

   1. Enter a **[!UICONTROL Name]**. For example: `LumaMobileAppCodeBased`.
   1. Enter a **[!UICONTROL Description]**. For example: `Code-based experience for Luma app used in Mobile SDK tutorial`.
   1. Select **[!UICONTROL Code-based experience]** from the **[!UICONTROL Select channel]** drop-down menu.
   1. Select one or more marketing actions from the **[!UICONTROL Select one or multiple marketing actions]**. For example **[!UICONTROL Onsite Personalization]**.
   1. Select the platforms for which you want to configure the code-based experience. For this tutorial, select **[!UICONTROL iOS]** or **[!UICONTROL Android]** or both.
      * For **[!UICONTROL iOS]**:
        1. Enter of select **[!UICONTROL App id]**. For example: `com.adobe.luma.tutorial.swiftui`.
        1. Enter of select a location for **[!UICONTROL Location or path inside the app]**. For example: `offersLocation`.
        1. Enter a **[!UICONTROL Preview URL]**. For example: `lumatutorialswiftui://`.
      * For **[!UICONTROL Android]**:
        1. Enter of select **[!UICONTROL App id]**. For example: `com.adobe.luma.tutorial.android`.
        1. Enter of select a location for **[!UICONTROL Location or path inside the app]**. For example: `offersLocation`.
        1. Enter a **[!UICONTROL Preview URL]**. For example: `lumatutorialandroid://default`.
      * **[!UICONTROL Content]**
        * Select **[!UICONTROL JSON]** for the **[!UICONTROL Format]**. 
1. Select **[!UICONTROL Submit]** to submit your code-based experience.



## Create offers

In this section you create offers for Decisioning. 

1. In the Journey Optimizer UI, select ![DecisionItems](/help/assets/icons2/DecisionItems.svg) **[!UICONTROL Catalogs]** from **[!UICONTROL Decisioning]** in the left rail.
1. Select **[!UICONTROL Offers]** from **[!UICONTROL Catalogs]** to see the list of **[!UICONTROL Offers]**.
1. Select **[!UICONTROL Create item]**.

   1. In the ➊ **[!UICONTROL Attributes]** step of creating an offer (decision item):

      ![Attributes for an offer in Decisioning](assets/ajo-decisioning-offer-attributes.png){zoomable="yes"}

      * In the **[!UICONTROL Standard attributes]** section:
        1. Enter an **[!UICONTROL Offer name]**. For example: `Luma - Desiree Fitness Tee`.
        2. Enter a **[!UICONTROL Start date]** or select one using ![Calendar](/help/assets/icons2/Calendar.svg). For example: `7/1/2026, 12:00 AM`. 
        3. Enter a **[!UICONTROL End date]** or select one using ![Calendar](/help/assets/icons2/Calendar.svg). For example: `12/31/2026, 12:00 AM`.
        4. Enter a **[!UICONTROL Priority]**. For example: `10`.
        5. Select one or more appropriate tags from the **[!UICONTROL Tags]** drop-down menu. For example: **[!UICONTROL Luma - Mobile App]**.
      * In the **[!UICONTROL Custom attributes]** section, enter values for the offer content and metadata. What data you can enter and how you can enter that data is entirely determined by how you havwve defined your [schema](#define-your-schema) for offers. In this tutorial, you want to provide a title, text and an image for each offer.
        1. In the **[!UICONTROL Offer]** container, within the **[!UICONTROL Media Assets]** subcontainer:
           1. Select **[!UICONTROL Add from URL]** for **[!UICONTROL Image]** and enter an appropriate value for E**[!UICONTROL nter source URL]**. For example: `https://newluma.enablementadobe.com/images/ws05-yellow_main.jpg`.
           1. Select **[!UICONTROL Add from URL]** for **[!UICONTROL Image (high resolution)]** and enter an appropriate value for **[!UICONTROL Enter source URL]**. For example: `https://newluma.enablementadobe.com/images/ws05-yellow_main.jpg`.
        1. In the **[!UICONTROL Offer]** container, within the **[!UICONTROL Text]** subcontainer:
           1. Enter a value for **[!UICONTROL Full description]**. For example: `When you're too far to turn back, thank yourself for choosing the Desiree Fitness Tee. Its ultra-lightweight, ultra-breathable fabric wicks sweat away from your body and helps keeps you cool for the distance`.
           1. Enter a value for **[!UICONTROL Title]**. For example: **[!UICONTROL Desiree Fitness Tee]**.
      1. Select **[!UICONTROL Next]**.
   1. In the ➋ **[!UICONTROL Elgibility]** step of the creation of an offer (decision item):

      ![Create offer item - Eligibility](assets/ajo-decisioning-offer-eligibility.png){zoomable="yes"}

      1. In **[!UICONTROL Eligibility]**, ensure **[!UICONTROL All visitors]** is selected.
      1. You do not need to create a capping in the **[!UICONTROL Capping]** section.
      1. Select **[!UICONTROL Next]**.
   1. In the ➌ Review step op the creation of an offer (decision item):
      
      ![Create offer item - Review](assets/ajo-decisioning-offer-review.png){zoomable="yes"}

      1. Review the offer. You can use ![Edit](/help/assets/icons/Edit.svg) to change **[!UICONTROL Standard attributes]**, **[!UICONTROL Customer attributes]**, or **[!UICONTROL Profile constraints]**.
      1. Select **[!UICONTROL Save]**.

1. Repeat step 3 for the following additional offers:

   | Name | Title | Full description | Image and Image (high resolution) |
   |---|---|---|---|
   | `Luma - Affirm Water Bottle` | `Affirm Water Bottle` | `You'll stay hydrated with ease with the Affirm Water Bottle by your side or in hand. Measurements on the outside help you keep track of how much you're drinking, while the screw-top lid prevents spills. A metal carabiner clip allows you to attach it to the outside of a backpack or bag for easy access.` | `https://newluma.enablementadobe.com/images/ug06-lb-0.jpg` |
   | `Luma - Aero Daily Fitness Tee` | `Aero Daily Fitness Tee` | `Need an everyday action tee that helps keep you dry? The Aero Daily Fitness Tee is made of 100% polyester wicking knit that funnels moisture away from your skin. Don't be fooled by its classic style; this tee hides premium performance technology beneath its unassuming look.` | `https://newluma.enablementadobe.com/images/ms01-black_main.jpg` |
   | `Luma - Adrienne Trek Jacket` | `Adrienne Trek Jacket` | `You're ready for a cross-country jog or a coffee on the patio in the Adrienne Trek Jacket. Its style is unique with stand collar and drawstrings, and it fits like a jacket should.` | `https://newluma.enablementadobe.com/images/wj08-gray_main.jpg` |
   | `Luma - Juno Jacket` | `Juno Jacket` | `On colder-than-comfortable mornings, you'll love warming up in the Juno All-Ways Performanc Jacket, designed to compete with wind and chill. Built-in Cocona&trade; technology aids evaporation, while a special zip placket and stand-up collar keep your neck protected.` | `https://newluma.enablementadobe.com/images/wj06-purple_main.jpg` | 

   All other values, like **[!UICONTROL Start date]**, **[!UICONTROL End date]**, **[!UICONTROL Priority]**, **[!UICONTROL Capping]**, **[!UICONTROL Eligibility]**, and more should be the same across all offers.

You should now have the following list of offers:

![Offers list](assets/ajo-decisioning-offers-list.png){zoomable="yes"}


## Create a collection

To present an offer to your mobile app user, you must create an offer collection, consisting of one or more of the offers you created. You use rules to select which offers belong to a collection. 

1. In the Journey Optimizer UI, select ![DecisionItems](/help/assets/icons2/DecisionItems.svg) **[!UICONTROL Catalogs]** from **[!UICONTROL Decisioning]** in the left rail.
1. Select **[!UICONTROL Collections]** from **[!UICONTROL Catalogs]** to see the list of **[!UICONTROL Collections]**.
1. Select **[!UICONTROL Create collection]**.

   ![Create a decisioning collection]
1. In the **[!UICONTROL Details]** section:
   1. Enter a **[!UICONTROL Name]** for the collection. For example: `Luma - Mobile App Collection`.
   1. Enter a **[!UICONTROL Description]** for the collection. For example:  `Collection of Luma mobile app offers`.
1. In the **[!UICONTROL Collection rules]** section, underneath **[!UICONTROL NUMBER OF ITEMS]**:
   1. Select C**[!UICONTROL lick to create a decision item…]**
   1. Use **[!UICONTROL Select attribute]** to select an attribute. 
      1. In the **[!UICONTROL Select an attribute]** dialog select a **[!UICONTROL Decision attribute]**. For example **[!UICONTROL Offer name]**.
      1. Select **[!UICONTROL Save]**.
   1. Use the **[!UICONTROL Equals]** drop-down menu to select a condition. For example **[!UICONTROL Starts with]**.
   1. In the textfield enter the value for the condition. For example: `Luma -`. Thi value will select all offers which name starts with `Luma -` to be part of the collection. You can create any kind of rule and also combine rules, using ![AddCircle](/help/assets/icons/AddCircle.svg) Add rule.
1. Select **[!UICONTROL Create]** to create the collection.


    ![Offers - Collection](assets/ajo-decisioning-collecton-create.png){zoomable="yes"}

## Create a campaign

You now create a campaign that uses both your offer collection and your code-based experience configuration channel.

1. In the Journey Optimizer UI, select ![Claxon](/help/assets/icons2/Claxon.svg) **[!UICONTROL Campaigns]** from **[!UICONTROL Journey management]** in the left rail.

## Create a decision

The final step is to define a decision, which is the combination of one or more decision scopes and your fallback offer. 

A decision scope is a combination of a specific placement (for example HTML in an email, or JSON in a mobile app) and one or more evaluation criteria. 

An evaluation criterium is the combination of 

* an offer collection,
* eligibility rules: for example, is the offer only available for a specific audience,
* a ranking method: when multiple offers are available to pick from, which method do you use to rank them (for example by offer priority, using a formula, or an AI model).

See [Key steps to create and manage offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/key-steps) if you want to understand how placements, rules, rankings, offers, representations, collections, decisions, and so on, interact and relate to each other. This lesson is solely focused on using the output of a decision rather than on the flexibility in defining decisions within Journey Optimizer - Decision Management.

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

1. Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Model]** > **[!DNL Data]** > **[!UICONTROL decisions]** in the Xcode Project navigator. Update the `activityId` and `placementId` values with the decision scope details that you copied from the Journey Optimizer interface.

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

      However, you can use any kind of implementation to ensure the Optimize APIs get the proper parameters (`activityId`, `placementId` and, `itemCount`), to construct a valid [`DecisionScope`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#decisionscope) object for your implementation. <br/>For your information: the other key-values in the `decisions.json` file are for future use and not relevant and used currently in this lesson and as part of the tutorial.

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


1. In Android Studio, ensure that [aepsdk-optimize-android](https://github.com/adobe/aepsdk-optimize-android) is part of the dependencies in **[!UICONTROL build.gradle.kts (Module :app)]** in **[!UICONTROL Android]** ![ChevronDown](/help/assets/icons/ChevronDown.svg) > **[!UICONTROL Gradle Scripts]**. See [Gradle](install-sdks.md#gradle).
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

1. Navigate to **[!UICONTROL Android]** ![ChevronDown](/help/assets/icons/ChevronDown.svg) > **[!DNL app]** > **[!DNL assets]** > **[!DNL data]** > **[!UICONTROL decisions.json]** in the Xcode Project navigator. Update the `activityId` and `placementId` values with the decision scope details that you copied from the Journey Optimizer interface.

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

      However, you can use any kind of implementation to ensure the Optimize APIs get the proper parameters (`activityId`, `placementId` and, `itemCount`), to construct a valid [`DecisionScope`](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer-decisioning/api-reference/#decisionscope) object for your implementation. <br/>For your information: the other key-values in the `decisions.json` file are for future use and not relevant and used currently in this lesson and as part of the tutorial.

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

1. Go to the **[!DNL Personalization]** tab.

1. Scroll to the top, and you see two random offers displayed  from the collection that you have defined in the **[!DNL DECISION LUMA - MOBILE APP DECISION]** tile.

    <img src="assets/ajo-app-offers.png" width=300>

   The offers are random, as you have given all offers the same priority and the ranking for the decision is based on priority.


>[!TAB Android]

1. Rebuild and run the app in the simulator or on a physical device from Android Studio, using ![Play](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Play_18_N.svg).

1. Go to the **[!DNL Personalization]** tab.

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
