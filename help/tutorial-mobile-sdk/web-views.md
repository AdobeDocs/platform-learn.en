---
title: Handle WebViews with Platform Mobile SDK
description: Learn how to handle data collection with WebViews in a mobile app.
jira: KT-14632
exl-id: 9b3c96fa-a1b8-49d2-83fc-ece390b9231c
TQID: https://experienceleague.adobe.com/kiMEk4e6nR-MZjObdCgTpUuCVT25QiLLh22yle9PEZ0
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
    internal-label: CX Enterprise
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
  - id: f002a92a-b99f-47a4-90c8-65e0e415bc7a
    internal-label: Pass
feature_v2:
  - id: d833d0ef-8ed5-4cff-a5e7-9f12abd02a31
    internal-label: SDKs
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: c1f1ac67-ccab-4be9-a93a-b7faba1192c4
    internal-label: Assurance
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
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# Handle WebViews

Learn how to handle data collection with WebViews in a mobile app.

## Prerequisites

* Successfully built and run app with SDKs installed and configured.

## Learning objectives

In this lesson, you will:

* Understand why you must take special consideration for WebViews in your app.
* Understand the code required to prevent tracking issues.

## Potential tracking issues

Separate (Experience Cloud Identity) ECIDs are generated when you send data from the native portion of your app and from a WebView within the app. These separate ECIDs result in disconnected hits and inflated visit and visitor data. More information about the ECID can be found in the [ECID overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/ecid).

To solve the disconnected hits and inflated data, you need to pass the user's ECID from the native portion of your app to a WebView that you might want to use in your app.

The AEP Edge Identity extension used within the WebView collects the current ECID and adds it to the URL instead of sending a request to Adobe for a new ID. The implementation then uses this ECID to request the URL.

## Implementation

To implement the web view:

>[!BEGINTABS]

>[!TAB iOS]

Navigate to **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Views]** > **[!DNL Info]** > **[!DNL TermsOfServiceSheet]**, and locate the `func loadUrl()` function in the `final class SwiftUIWebViewModel: ObservableObject` class. Add the following call to handle the web view:

```swift
// Handle web view
AEPEdgeIdentity.Identity.getUrlVariables {(urlVariables, error) in
    if let error = error {
        print("Error with Webview", error)
        return;
    }
    
    if let urlVariables: String = urlVariables {
        urlString.append("?" + urlVariables)
        guard let url = URL(string: urlString) else {
            return
        }
        DispatchQueue.main.async {
            self.webView.load(URLRequest(url: url))
        }
    }
    Logger.aepMobileSDK.info("Successfully retrieved urlVariables for WebView, final URL: \(urlString)")
}
```

The [`AEPEdgeIdentity.Identity.getUrlVariables`](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#geturlvariables) API sets up the variables for the URL to contain all relevant information, like ECID, and more. In the example, you are using a local file but the same concepts apply to remote pages.

You can learn more about the `Identity.getUrlVariables` API in the [Identity for Edge Network extension API reference guide](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#geturlvariables).


>[!TAB Android]

Navigate to **[!UICONTROL Android]** ![ChevronDown](/help/assets/icons/ChevronDown.svg) > **[!DNL app]** > **[!DNL kotlin+java]** > **[!DNL com.adobe.luma.tutorial.android]** > **[!DNL views]** > **[!DNL WebViewModel]**, and locate the `fun loadUrl()` function in the `class WebViewModel: ViewModel()`. Add the following call to handle the web view:

```kotlin
// Handle web view
Identity.getUrlVariables {
    urlVariables = it
    val baseUrl = getHtmlFileUrl("tou.html")

    val finalUrl = if (urlVariables.isNotEmpty()) {
        "$baseUrl?$urlVariables"
    } else {
        baseUrl
    }

    Handler(Looper.getMainLooper()).post {
        webView.loadUrl(finalUrl)
    }
    MobileSDK.shared.logInfo("TermsOfServiceSheet - loadUrl: Successfully loaded WebView with URL: $finalUrl")
}
```

The [`Identity.getUrlVariables`](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#geturlvariables) API sets up the variables for the URL to contain all relevant information, like ECID, and more. In the example, you are using a local file but the same concepts apply to remote pages.

You can learn more about the `Identity.getUrlVariables` API in the [Identity for Edge Network extension API reference guide](https://developer.adobe.com/client-sdks/documentation/identity-for-edge-network/api-reference/#geturlvariables).

>[!ENDTABS]

## Validate in the app

To execute the code:

1. Review the [setup instructions](assurance.md#connecting-to-a-session) section to connect your simulator or device to Assurance.
1. Go to the **[!UICONTROL Settings]** in the app
1. Tap the **[!DNL View...]** button to show the **[!DNL Terms of Use]**.

>[!BEGINTABS]

>[!TAB iOS]

<img src="./assets/tou1.png" width=300> <img src="./assets/tou2.png" width=300> 

>[!TAB Android]

<img src="./assets/tou1-android.png" width=300> <img src="./assets/tou2-android.png" width=300>

>[!ENDTABS]


## Validate with Assurance

1. In the Assurance UI, look for the **[!UICONTROL Edge Identity Response URL Variables]** event from the **[!UICONTROL com.adobe.griffon.mobile]** vendor. 
1. Select the event and review the **[!UICONTROL urlvariable]** field in the **[!UICONTROL ACPExtensionEventData]** object, confirming the following parameters are present in the URL: `adobe_mc`, `mcmid`, and `mcorgid`.

    ![webview validation](assets/webview-validation.png){zoomable="yes"}

    A sample `urvariables` field can be seen below:

    * Original (with escaped characters)

      ```html
      adobe_mc=TS%3D1636526122%7CMCMID%3D79076670946787530005526183384271520749%7CMCORGID%3D7ABB3E6A5A7491460A495D61%40AdobeOrg
      ```

    * Beautified

      ```html
      adobe_mc=TS=1636526122|MCMID=79076670946787530005526183384271520749|MCORGID=7ABB3E6A5A7491460A495D61@AdobeOrg
      ```

Unfortunately, debugging the web session is limited. For example, you can't use the Adobe Experience Platform Debugger in your browser to continue debugging the webview session.

>[!NOTE]
>
>Visitor stitching via these URL parameters is supported in the Platform Web SDK (versions 2.11.0 or later) and when using `VisitorAPI.js`.


>[!SUCCESS]
>
>You have now set up your app to show content based on a URL in a webview using the same ECID as the ECID already issued by the Adobe Experience Platform Mobile SDK.
>
>Thank you for investing your time in learning about Adobe Experience Platform Mobile SDK. If you have questions, want to share general feedback, or have suggestions on future content, share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Next: **[Identity](identity.md)**
