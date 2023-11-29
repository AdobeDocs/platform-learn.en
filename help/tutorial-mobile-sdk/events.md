---
title: Track event data
description: Learn how to track event data in a mobile app.
exl-id: 4779cf80-c143-437b-8819-1ebc11a26852
---
# Track event data

Learn how to track events in a mobile app.

The Edge Network extension provides an API to send Experience Events to Platform Edge Network. An Experience Event is an object that contains data conforming to the XDM ExperienceEvent schema definition. More simply, they capture what people do in your mobile app. Once data is received by Platform Edge Network, it can be forwarded to applications and services configured in your datastream, such as Adobe Analytics and Experience Platform. Learn more about the [Experience Events](https://developer.adobe.com/client-sdks/documentation/getting-started/track-events/) in the product documentation.

## Prerequisites

* All package dependencies are in place in your Xcode project.
* Registered extensions in **[!UICONTROL AppDelegate]**.
* Configured MobileCore extension to use your development `appId`.
* Imported SDKs.
* Successfully built and run the app with the above changes.

## Learning objectives

In this lesson, you will

* Understand how to structure XDM data based on a schema.
* Send an XDM event based on a standard field group.
* Send an XDM event based on a custom field group.
* Send an XDM purchase event.
* Validate with Assurance.

## Constructing an Experience Event 

The Adobe Experience Platform Edge extension can send events that follow a previously defined XDM schema to Adobe Experience Platform Edge Network. 

The process goes like this...

1. Identify the mobile app interaction that you are trying to track.

1. Review your schema and identify the appropriate event.

1. Review your schema and identify any additional fields that should be used to describe the event.

1. Construct & populate the data object.

1. Create & send event.

1. Validate.


### Standard field groups 

For the standard field groups, the process looks like:

* In your schema, identify the events that you are trying to collect. In this example, you are tracking commerce experience events, for example a product view (**[!UICONTROL productViews]**) event.
  
  ![product view schema](assets/datacollection-prodView-schema.png)

* To construct object containing the experience event data in your app, you would use code like:

  ```swift
  var xdmData: [String: Any] = [
      "eventType": "commerce.productViews",
      "commerce": [
          "productViews": [
            "value": 1
          ]
      ]
  ]
  ```

   * `eventType`: Describes the event that occurred, use a [known value](https://github.com/adobe/xdm/blob/master/docs/reference/classes/experienceevent.schema.md#xdmeventtype-known-values) when possible.
   * `commerce.productViews.value`: the numeric or boolean value of the event. If it's a Boolean (or "Counter" in Adobe Analytics), the value is always set to 1. If it's a numeric or currency event, the value can be > 1.

* In your schema, identify any additional data associated with the commerce product view event. In this example, include **[!UICONTROL productListItems]** which is a standard set of fields used with any commerce-related event:
      
   ![product list items schema](assets/datacollection-prodListItems-schema.png)
   * Notice that **[!UICONTROL productListItems]** is an array so multiple products could be provided.

* To add this data, expand your `xdmData` object to include supplementary data:

    ```swift
    var xdmData: [String: Any] = [
        "eventType": "commerce.productViews",
            "commerce": [
            "productViews": [
                "value": 1
            ]
        ],
        "productListItems": [
            [
                "name":  productName,
                "SKU": sku,
                "priceTotal": priceString,
                "quantity": 1
            ]
        ]
    ]
    ```

* You now can use this data structure to create an `ExperienceEvent`:

  ```swift
  let productViewEvent = ExperienceEvent(xdm: xdmData)
  ```

* And send the event and data to Platform Edge Network using the `sendEvent` API:

  ```swift
  Edge.sendEvent(experienceEvent: productViewEvent)
  ```

The [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent) API is the AEP Mobile SDK equivalent to the [`MobileCore.trackAction`](https://developer.adobe.com/client-sdks/documentation/mobile-core/api-reference/#trackaction) and [`MobileCore.trackState`](https://developer.adobe.com/client-sdks/documentation/mobile-core/api-reference/#trackstate) API calls. See [Migrate from Analytics mobile extension to Adobe Experience Platform Edge Network](https://developer.adobe.com/client-sdks/documentation/adobe-analytics/migrate-to-edge-network/) for more information.

You are now going to actually implement this code in your Xcode project.
You have different commerce product-related actions in your app and you want to send events, based on these actions as performed by the user:

* view: occurs when a user views a specific product,
* add to cart: when a user taps <img src="assets/addtocart.png" width=20/> in a product detail screen,
* save for later: when a user taps <img src="assets/saveforlater.png" width=15/> in a product detail screen,
* purchase: when a user taps <img src="assets/purchase.png" width=20/> in a product detail screen.

To implement the sending of commerce-related experience events in a reusable way, you use a dedicated function:

1. Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** in Xcode Project navigator, and add the following to the `func sendCommerceExperienceEvent(commerceEventType: String, product: Product)` function.

    ```swift
    // Set up a data dictionary, create an experience event and send the event.
    let xdmData: [String: Any] = [
        "eventType": "commerce." + commerceEventType,
        "commerce": [
            commerceEventType: [
                "value": 1
            ]
        ],
        "productListItems": [
            [
                "name": product.name,
                "priceTotal": product.price,
                "SKU": product.sku
            ]
        ]
    ]

    let commerceExperienceEvent = ExperienceEvent(xdm: xdmData)
    Edge.sendEvent(experienceEvent: commerceExperienceEvent)
    ```

    This function takes the commerce experience event type and product as parameters and 

    * sets up the XDM payload as a dictionary, using the parameters from the function,
    * sets up an experience event using the dictionary,
    * sends the experience event using the [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent) API.

1. Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Products]** > **[!UICONTROL ProductView]** in Xcode Project navigator and add various calls to the `sendCommerceExperienceEvent` function:

   1. At the `.task` modifier, within the `ATTrackingManager.trackingAuthorizationStatus` closure. This `.task` modifier is called when product view is initialized and shown, so you want to send a product view event at that specific moment.

      ```swift
      // Send productViews commerce experience event
      MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "productViews", product: product)
      ```  

   1. For each of the buttons (<img src="assets/saveforlater.png" width=15/>, <img src="assets/addtocart.png" width=20/> and <img src="assets/purchase.png" width=20/>) in the toolbar, add the relevant call within the `ATTrackingManager.trackingAuthorizationStatus == .authorized` closure:

      1. For <img src="assets/saveforlater.png" width=15/>:

            ```swift
            // Send saveForLater commerce experience event
            MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "saveForLaters", product: product)
            ```

      1. For <img src="assets/addtocart.png" width=20/>:

            ```swift
            // Send productListAdds commerce experience event
            MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "productListAdds", product: product)
            ```

      1. For <img src="assets/purchase.png" width=20/>:

            ```swift
            // Send purchase commerce experience event
            MobileSDK.shared.sendCommerceExperienceEvent(commerceEventType: "purchases", product: product)
            ```

>[!TIP]
>
>In case you are developing for Android&trade;, use Map (`java.util.Map`) as the foundational interface to construct your XDM payload.


### Custom field groups 

Imagine you want to track screen views and interactions in the app itself. Remember you have defined a custom field group for this type of events.

* In your schema, identify the events you are trying to collect. 
  ![app interaction schema](assets/datacollection-appInteraction-schema.png)

* Begin constructing your object. 

  >[!NOTE]
  >
  >* Standard field groups always begin in the object root. 
  >
  >* Custom fields groups always begin under an object unique to your Experience Cloud Org, `_techmarketingdemos` in this example.

  For the app interaction event, you would construct an object like:

  ```swift
  let xdmData: [String: Any] = [
    "eventType": "application.interaction",
    "_techmarketingdemos": [
      "appInformation": [
          "appInteraction": [
              "name": "login",
              "appAction": [
                  "value": 1
                  ]
              ]
          ]
      ]
  ]
  ```

  For the screen tracking event, you would construct an object like:

  ```swift
  var xdmData: [String: Any] = [
    "eventType": "application.scene",
    "_techmarketingdemos": [
        "appInformation": [
            "appStateDetails": [
                "screenType": "App",
                    "screenName": "luma: content: ios: us: en: login",
                    "screenView": [
                        "value": 1
                    ]
                ]
            ] 
        ]
  ]
  ```


* You now can use this data structure to create an `ExperienceEvent`.

    ```swift
    let event = ExperienceEvent(xdm: xdmData)
    ```

* Send the event and data to Platform Edge Network.

    ```swift
    Edge.sendEvent(experienceEvent: event)
    ```


Again, lets actually implement this code in your Xcode project. 

1. For convenience, you define two functions in **[!UICONTROL MobileSDK]**. Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** in your Xcode Project navigator.

   1. One for app interactions. Add this code to the `func sendAppInteractionEvent(actionName: String)` function:

        ```swift 
        // Set up a data dictionary, create an experience event and send the event.
        let xdmData: [String: Any] = [
            "eventType": "application.interaction",
            tenant : [
                "appInformation": [
                    "appInteraction": [
                        "name": actionName,
                        "appAction": [
                            "value": 1
                        ]
                    ]
                ]
            ]
        ]
        let appInteractionEvent = ExperienceEvent(xdm: xdmData)
        Edge.sendEvent(experienceEvent: appInteractionEvent)
        
        ```

       This function uses the action name as a parameter and

       * sets up the XDM payload as a dictionary, using the parameter from the function,
       * sets up an experience event using the dictionary,
       * sends the experience event using the [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent) API.


   1. And one for screen tracking. Add this code to the `func sendTrackScreenEvent(stateName: String) ` function:
  
        ```swift
        // Set up a data dictionary, create an experience event and send the event.
        let xdmData: [String: Any] = [
            "eventType": "application.scene",
            tenant : [
                "appInformation": [
                    "appStateDetails": [
                        "screenType": "App",
                        "screenName": stateName,
                        "screenView": [
                            "value": 1
                        ]
                    ]
                ]
            ]
        ]
        let trackScreenEvent = ExperienceEvent(xdm: xdmData)
        Edge.sendEvent(experienceEvent: trackScreenEvent)
        ```
       
       This function uses the state name as a parameter and

       * sets up the XDM payload as a dictionary, using the parameter from the function,
       * sets up an experience event using the dictionary,
       * sends the experience event using the [`Edge.sendEvent`](https://developer.adobe.com/client-sdks/documentation/edge-network/api-reference/#sendevent) API.

1. Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL General]** > **[!UICONTROL LoginSheet]**.

   1. Add the following highlighted code to the Login button closure: 

        ```swift                              
        // Send app interaction event
        MobileSDK.shared.sendAppInteractionEvent(actionName: "login")
        ```

   1. Add the following highlighted code to `onAppear` modifier:

        ```swift
        // Send track screen event
        MobileSDK.shared.sendTrackScreenEvent(stateName: "luma: content: ios: us: en: login")
        ```

## Validation

1. Review the [setup instructions](assurance.md#connecting-to-a-session) section to connect your simulator or device with Assurance.

   1. Move the Assurance icon to the left.
   1. Select **[!UICONTROL Home]** in the tab bar and verify you see an **[!UICONTROL ECID]**, **[!UICONTROL Email]**, and **[!UICONTROL CRM ID]** in the Home screen.
   1. Select **[!DNL Products]** in the tab bar.
   1. Select a product.
   1. Select <img src="assets/saveforlater.png" width=15/>.
   1. Select <img src="assets/addtocart.png" width=20/>.
   1. Select <img src="assets/purchase.png" width=15/>.

       <img src="./assets/mobile-app-events-3.png" width=300>
 

1. In the Assurance UI, look for the **[!UICONTROL hitReceived]** events from the **[!UICONTROL com.adobe.edge.konductor]** vendor.
1. Select the event and review the XDM data in the **[!UICONTROL messages]** object. Alternatively, you can use ![Copy](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) **[!UICONTROL Copy Raw Event]** and use a text or code editor of your preference to paste and inspect the event.
   
   ![data collection validation](assets/datacollection-validation.png)


## Next steps

You should now have all the tools to start adding data collection to your app. You can add more intelligence to how the user interacts with your products in the app and you can add more app interaction and screen tracking calls to the app:

* Implement order, checkout, empty basket, and other functionality to the app and add relevant commerce experience events to this functionality.
* Repeat the call to `sendAppInteractionEvent` with the appropriate parameter to track other app interactions by the user. 
* Repeat the call to `sendTrackScreenEvent` with the appropriate parameter to track screens viewed by the user in the app.

>[!TIP]
>
>Review the [finished app](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App) for more examples.


## Send events to Analytics and Platform

Now that you have collected the events and sent them to Platform Edge Network, they are sent to the applications and services configured in your [datastream](create-datastream.md). In later lessons, you map this data to [Adobe Analytics](analytics.md), [Adobe Experience Platform](platform.md), and other Adobe Experience Cloud solutions like [Adobe Target](target.md) and Adobe Journey Optimizer. 

>[!SUCCESS]
>
>You have now set up your app to track commerce, app interaction, and screen tracking events to the Adobe Experience Platform Edge Network and all services you have defined in your datastream.
>
>Thank you for investing your time in learning about Adobe Experience Platform Mobile SDK. If you have questions, want to share general feedback, or have suggestions on future content, share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Next: **[Handle WebViews](web-views.md)**
