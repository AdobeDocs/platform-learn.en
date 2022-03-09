---
title: Handle WebViews
description: Learn how to handle data collection with WebViews in a mobile app.
kt: 6987
---
# Handle WebViews

Learn how to handle data collection with WebViews in a mobile app.

## Prerequisites

* Successfully built and run app with SDKs installed and configured.

## Learning objectives

In this lesson, you will:

* Understand why you must take special considerations for WebViews.
* Understand the code required to prevent tracking issues.


## Potential tracking issues

If you send data from the native portion of the app and a WebView, each generates their own Experience Cloud Id (ECID). This results in disconnected hits and inflated visit/visitor data.

To solve for that undesirable situation, it's important to pass the user's ECID from the native portion to the WebView.

The Experience Cloud ID Service JavaScript extension in the WebView extracts the ECID from the URL instead of sending a request to Adobe for a new ID. The ID service uses this ECID to track the visitor.

## Implementation

1. In the Luma sample app, find the `TermsOfService.swift` file (in the `Intro-Login_SignUp` folder).

1. In that file, find the following code:

    ```swift
    // Show tou.html
    let url = Bundle.main.url(forResource: "tou", withExtension: "html")
    let myRequest = URLRequest(url: url!)
    self.webView.load(myRequest)
    ```

    This is a simple way to load a WebView. In this case, it's a local file but the same concepts apply to remote pages.

1. Refactor the webview code as shown here:

    ```swift
    // Adobe Experience Platform - Handle Web View
    let url = Bundle.main.url(forResource: "tou", withExtension: "html")
    AEPIdentity.Identity.appendTo(url: url) {returnedURL, error in
        let myRequest = URLRequest(url: returnedURL!)
        self.webView.load(myRequest)
    }
    ```

You can learn more about `Identity.appendTo` in the [documentation](https://aep-sdks.gitbook.io/docs/foundation-extensions/mobile-core/identity#implementing-visitor-tracking-between-an-app-and-the-mobile-web).

## Validation

1. Review the [setup instructions](assurance.md) section and connect your simulator or device to Assurance.

1. Load the WebView and look for the `IDENTITY_APPENDED_URL` event from the `com.adobe.griffon.mobile` vendor. To load the WebView:
    1. Go to the home screen of the Luma app.
    1. Select the "account" icon.
    1. Select "Terms of Use" in the footer.

1. Select the event and review the `updatedurl` field in the `ACPExtensionEventData` object.
![webview validation](assets/mobile-webview-validation.png)

1. Confirm that the following parameters are present in the URL.
    * adobe_mc
    * MCMID
    * MCORGID

For example:

```
//Original (with escaped characters)
http://www.webview.com?adobe_mc=TS%3D1636526122%7CMCMID%3D79076670946787530005526183384271520749%7CMCORGID%3D7ABB3E6A5A7491460A495D61%40AdobeOrg

//Beautified
http://www.webview.com?adobe_mc=TS=1636526122|MCMID=79076670946787530005526183384271520749|MCORGID=7ABB3E6A5A7491460A495D61@AdobeOrg
```

>[!CAUTION]
>
>Visitor stitching via these URL parameters is currently supported in `VisitorAPI.js` but [not yet available in Platform Web SDK](https://github.com/adobe/alloy/issues/565). Check [this issue](https://github.com/adobe/alloy/issues/565) for the latest status.


Next: **[Identity](identity.md)**