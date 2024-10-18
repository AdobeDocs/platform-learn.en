---
title: Replace the SDK - Migrate from the Adobe Target to the Adobe Journey Optimizer - Decisioning Mobile extension
description: Learn how to replace the SDK when migrating from the Adobe Target to the Adobe Journey Optimizer - Decisioning Mobile extension.
---
# Replace the Target SDK with the Optimize SDK

Learn how to replace your on-page Adobe Target implementation to migrate from at.js to Platform Web SDK. A basic replacement consists of the following steps:

* Review your Target administration settings and make note of your IMS Organization ID
* Replace the at.js library with the Platform Web SDK
* Update the prehiding snippet for synchronous library implementations
* Configure the Platform Web SDK

>[!NOTE]
>
>The examples provided are for illustrative purposes and your actual Target implementation may vary. If your existing Target implementation uses Adobe's Data Collection tag manager, you can also refer to the [Platform Web SDK Target implementation tutorial](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/applications-setup/setup-target.html) for additional information.


## Review Target administration settings

The first step to migrate Target to Platform Web SDK is to review your settings in the Target interface's **[!UICONTROL Administration]** section.

### [!UICONTROL Implementation]

#### [!UICONTROL Account details]

* **[!UICONTROL IMS Organization Id]** - Make note of this value since it is required to configure the Platform Web SDK.
* **[!UICONTROL On-Device Decisioning]** - This feature is not supported by the Platform Web SDK. This setting can be disabled after you migrate and if no longer use at.js on any of your websites or have any server-side use cases for On-Device Decisioning.

#### [!UICONTROL Implementation methods]

All editable settings in the **[!UICONTROL Implementation methods]** section apply to at.js only. These settings are used to generate a customized at.js library for your implementation. Review these settings to check if you have any custom code or are setting 1st and 3rd party cookies for cross-domain use cases.

The **[!UICONTROL Profile Lifetime]** setting can only be changed by Adobe Customer Care. The Target visitor profile lifetime is not impacted by your implementation approach. Both at.js and Platform Web SDK use the same visitor profile lifetime.

#### [!UICONTROL Privacy]

* **[!UICONTROL Obfuscate Visitor IP addresses]** - This setting impacts geotargeting capabilities. Both at.js and Platform Web SDK use the same backend IP obfuscation settings for the purposes of geotargeting.

### [!UICONTROL Environments]

The Platform Web SDK uses a datastream configuration which allows you to explicitly define an [!UICONTROL Environment ID] for separate development, staging, and production datastreams. The main use case for this configuration is for mobile app implementations where URLs don't exist to easily distinguish environments. The setting is optional, but can be used to ensure that all requests are properly associated with the specified environment. This differs from an at.js implementation where you must assign Target environments based on domains and host group rules.

>[!NOTE]
>
>If an Environment ID is not specified in the datastream configuration, then Target uses the domain-to-environment mapping as specified in the **Hosts** section. 

For more information, refer to the [datastream configuration](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#target) guide and Target [Hosts](https://experienceleague.adobe.com/docs/target/using/administer/hosts.html) documentation.

## Deploy the Platform Web SDK

Target functionality is provided by both at.js and Platform Web SDK. If both libraries are used at the same time, you may experience rendering and tracking issues. To successfully migrate to Platform Web SDK, the first step is to remove at.js and replace it with Platform Web SDK (alloy.js).

Assume a simple Target implementation with at.js:

* A data layer near the top of the page provides information for Target and other applications
* One or more third-party helper libraries whose capabilities may be used in Target activities (for example, jQuery)
* A prehiding snippet to mitigate flicker
* The Target at.js library loads asynchronously with default settings to automatically request and render activities:

+++at.js example implementation on an HTML page

```HTML
<!doctype html>
<html>
<head>
  <title>Example page</title>
  <!--Data Layer to enable rich data collection and targeting-->
  <script>
    var digitalData = { 
      // Data layer information goes here
    };
  </script>
  <!--Third party libraries that may be used by Target offers and modifications-->
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.1/jquery.min.js"></script>
  <!--prehiding snippet for Target with asynchronous deployment-->
  <script>
    ;(function(win, doc, style, timeout) {
      var STYLE_ID = 'at-body-style';

      function getParent() {
        return doc.getElementsByTagName('head')[0];
      }

      function addStyle(parent, id, def) {
        if (!parent) {
          return;
        }
        var style = doc.createElement('style');
        style.id = id;
        style.innerHTML = def;
        parent.appendChild(style);
      }

      function removeStyle(parent, id) {
        if (!parent) {
          return;
        }
        var style = doc.getElementById(id);
        if (!style) {
          return;
        }
        parent.removeChild(style);
      }
      addStyle(getParent(), STYLE_ID, style);
      setTimeout(function() {
        removeStyle(getParent(), STYLE_ID);
      }, timeout);
    }(window, document, "body {opacity: 0 !important}", 3000));
  </script>
  <!--Target at.js library loaded asynchonously-->
  <script src="/libraries/at.js" async></script>
</head>
<body>
  <h1 id="title">Home Page</h1><br><br>
  <p id="bodyText">Navigation</p><br><br>
  <a id="home" class="navigationLink" href="#">Home</a><br>
  <a id="pageA" class="navigationLink" href="#">Page A</a><br>
  <a id="pageB" class="navigationLink" href="#">Page B</a><br>
  <a id="pageC" class="navigationLink" href="#">Page C</a><br>
  <div>Homepage Hero Banner Content</div>
</body>
</html>
```

+++

To upgrade Target to use Platform Web SDK, first remove at.js:

```HTML
<!--Target at.js library loaded asynchonously-->
<script src="/libraries/at.js" async></script>
```

And replace with either alloy JavsScript library or your tags embed code and the Adobe Experience Platform Web SDK extension:

>[!BEGINTABS]

>[!TAB JavaScript] 

```HTML
<!--Platform Web SDK base code-->
<script>
  !function(n,o){o.forEach(function(o){n[o]||((n.__alloyNS=n.__alloyNS||
  []).push(o),n[o]=function(){var u=arguments;return new Promise(
  function(i,l){n[o].q.push([i,l,u])})},n[o].q=[])})}
  (window,["alloy"]);
</script>
<!--Platform Web SDK loaded asynchonously. Change the src to use the latest supported version.-->
<script src="https://cdn1.adoberesources.net/alloy/2.13.1/alloy.min.js" async></script>
```

>[!TAB Tags]

```HTML
<!--Tags Header Embed Code: REPLACE WITH THE INSTALL CODE FROM YOUR OWN ENVIRONMENT-->
<script src="//assets.adobedtm.com/launch-EN93497c30fdf0424eb678d5f4ffac66dc.min.js" async></script>
``` 

In the tag property, add the Adobe Experience Platform Web SDK extension:

<!--![Add the Adobe Experience Platform Web SDK extension](assets/library-tags-addExtension.png){zoomable="yes"}-->


>[!ENDTABS]

The prebuilt standalone version requires a "base code" added directly to the page which creates a global function named alloy. Use this function to interact with the SDK. If you would like to name the global function something else, change the `alloy` name.

Refer to the [Installing the Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/installing-the-sdk.html) documentation for additional details and deployment options.


## Update content-prehiding approach

The Platform Web SDK implementation may require a prehiding snippet depending on whether the library is loaded asynchronously or synchronously.

### Asynchronous implementation

Just like with at.js, if the Platform Web SDK library loads asynchronously, the page may finish rendering before Target has performed a content swap. This behavior can lead to what is known as "flicker" where default content briefly displays before being replaced by the personalized content specified by Target. If you want to avoid this flicker, Adobe recommends adding a special prehiding snippet immediately before the asynchronous Platform Web SDK script reference or tags embed code.

If your implementation is asynchronous like the examples above, replace the at.js prehiding snippet with the version below compatible with the Platform Web SDK:

```HTML
<!--Prehiding snippet for Target with asynchronous Web SDK deployment-->
<script>
  !function(e,a,n,t){var i=e.head;if(i){
  if (a) return;
  var o=e.createElement("style");
  o.id="alloy-prehiding",o.innerText=n,i.appendChild(o),setTimeout(function(){o.parentNode&&o.parentNode.removeChild(o)},t)}}
  (document, document.location.href.indexOf("mboxEdit") !== -1, "body { opacity: 0 !important }", 3000);
</script>
```

The prehiding snippet creates a style tag in the head of the page with the CSS definition of your choosing. This style tag is removed when a response from Target is received, or the timeout is reached.

The prehiding behavior is controlled by two configurations at the very end of the snippet.

* `body { opacity: 0 !important }` specifies the CSS definition to use for the prehiding until Target loads. By default, the whole page is hidden. You can update this definition to the selectors you want to prehide along with how you want to hide them. You may include multiple definitions since this value is simply what is inserted into the prehiding style tag. If you have an easily identifiable container element wrapping the content below your navigation, you could use this setting to limit the prehiding to that container element.

* `3000` specifies the timeout in milliseconds for the prehiding. If a response from Target is not received before the timeout, the prehiding style tag is removed. Reaching this timeout should be rare.

>[!IMPORTANT]
>
>Be sure to use the correct snippet for the Platform Web SDK since it uses a different style ID of `alloy-prehiding`. If the prehiding snippet for at.js is used, it may not work properly.

### Synchronous implementation

Adobe recommends implementing the Platform Web SDK asynchronously for the best overall page performance. However, if the alloy.js library or tags embed code is loaded synchronously, then the prehiding snippet is not required. Instead, the prehiding style is specified in the Platform Web SDK configuration.

The prehiding style for synchronous implementations can be configured using the [`prehidingStyle`](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html#prehidingStyle) option. Platform Web SDK configuration is covered in the next section.

To learn more about how the Platform Web SDK can manage flicker, you can refer to the guide section:  [managing flicker for personalized experiences](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/manage-flicker.html)

## Configure the Platform Web SDK

The Platform Web SDK must be configured on every page load. The following example assumes that the entire site is being upgraded to Platform Web SDK in a single deployment:

>[!BEGINTABS]

>[!TAB JavaScript] 

The `configure` command must always be the first SDK command called. The `edgeConfigId` is the [!UICONTROL Datastream ID]

```JavaScript
alloy("configure", {
  "edgeConfigId": "ebebf826-a01f-4458-8cec-ef61de241c93",
  "orgId":"ADB3LETTERSANDNUMBERS@AdobeOrg"
});
```

>[!TAB Tags] 

In tags implementations, many fields are auto-populated or can be selected from dropdown menus. Note that different Platform [!UICONTROL sandboxes] and [!UICONTROL datastreams] can be selected for each environment. The datastream will change based on the state of the tag library in the publishing process.

<!--![configuring the Web SDK tag extension](assets/tags-config.png){zoomable="yes"}-->
>[!ENDTABS]

If you plan to migrate from at.js to Platform Web SDK on a page-by-page basis, then the following configuration options are required:


>[!BEGINTABS]

>[!TAB JavaScript] 

```JavaScript
alloy("configure", {
  "edgeConfigId": "ebebf826-a01f-4458-8cec-ef61de241c93",
  "orgId":"ADB3LETTERSANDNUMBERS@AdobeOrg",
  "targetMigrationEnabled":true,
  "idMigrationEnabled":true
});
```

>[!TAB Tags] 

<!--![configuring the Web SDK tag extension migration options](assets/tags-config-migration.png){zoomable="yes"}-->

>[!ENDTABS]

The noteworthy configuration options related to Target are outlined below:

| Option | Description | Example value |
| --- | --- | --- |
| `edgeConfigId` | The datastream ID | `ebebf826-a01f-4458-8cec-ef61de241c93` |
| `orgId` | Adobe Experience Cloud organization ID | `ADB3LETTERSANDNUMBERS@AdobeOrg` |
| `targetMigrationEnabled` | Use this option to enable the Web SDK to read and write the legacy mbox and mboxEdgeCluster cookies that are used by at.js. This helps you keep the visitor profile while moving from a page that uses the Web SDK to a page that uses the at.js library and the opposite way. | `true` |
| `idMigrationEnabled` | If true, the SDK reads and sets old AMCV cookies. This option helps with transitioning to using Platform Web SDK while some parts of the site might still use Visitor.js. | `true` |
| `thirdPartyCookiesEnabled` | Enables the setting of Adobe third-party cookies. The SDK can persist the visitor ID in a third-party context to enable the same visitor ID to be used across sites. Use this option if you have multiple sites; however, sometimes this option is not desired for privacy reasons. | `true` |
| `prehidingStyle` | Used to create a CSS style definition that hides content areas of your web page while personalized content is loaded from the server. This is only used with synchronous deployments of the SDK.| `body { opacity: 0 !important }` |

For a complete list of options, refer to the [configuring Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/configuring-the-sdk.html) guide.

## Implementation example

Once the Platform Web SDK is properly in place, the example page would look like this.

>[!BEGINTABS]

>[!TAB JavaScript] 

```HTML
<!doctype html>
<html>
<head>
  <title>Example page</title>
  <!--Data Layer to enable rich data collection and targeting-->
  <script>
    var digitalData = { 
      // Data layer information goes here
    };
  </script>

  <!--Third party libraries that may be used by Target offers and modifications-->
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.1/jquery.min.js"></script>

  <!--Prehiding snippet for Target with asynchronous Web SDK deployment-->
  <script>
    !function(e,a,n,t){var i=e.head;if(i){
    if (a) return;
    var o=e.createElement("style");
    o.id="alloy-prehiding",o.innerText=n,i.appendChild(o),setTimeout(function(){o.parentNode&&o.parentNode.removeChild(o)},t)}}
    (document, document.location.href.indexOf("mboxEdit") !== -1, ".body { opacity: 0 !important }", 3000);
  </script>

  <!--Platform Web SDK base code-->
  <script>
    !function(n,o){o.forEach(function(o){n[o]||((n.__alloyNS=n.__alloyNS||
    []).push(o),n[o]=function(){var u=arguments;return new Promise(
    function(i,l){n[o].q.push([i,l,u])})},n[o].q=[])})}
    (window,["alloy"]);
  </script>

  <!--Platform Web SDK loaded asynchonously. Change the src to use the latest supported version.-->
  <script src="https://cdn1.adoberesources.net/alloy/2.13.1/alloy.min.js" async></script>
  
  <!--Configure Platform Web SDK-->
  <script>
    alloy("configure", {
      "edgeConfigId": "ebebf826-a01f-4458-8cec-ef61de241c93",
      "orgId":"ADB3LETTERSANDNUMBERS@AdobeOrg"
    });
  </script>
</head>
<body>
  <h1 id="title">Home Page</h1><br><br>
  <p id="bodyText">Navigation</p><br><br>
  <a id="home" class="navigationLink" href="#">Home</a><br>
  <a id="pageA" class="navigationLink" href="#">Page A</a><br>
  <a id="pageB" class="navigationLink" href="#">Page B</a><br>
  <a id="pageC" class="navigationLink" href="#">Page C</a><br>
  <div id="homepage-hero">Homepage Hero Banner Content</div>
</body>
</html>
```

>[!TAB Tags] 

Page code:

```HTML
<!doctype html>
<html>
<head>
  <title>Example page</title>
  <!--Data Layer to enable rich data collection and targeting-->
  <script>
    var digitalData = { 
      // Data layer information goes here
    };
  </script>

  <!--Third party libraries that may be used by Target offers and modifications-->
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.1/jquery.min.js"></script>

  <!--Prehiding snippet for Target with asynchronous Web SDK deployment-->
  <script>
    !function(e,a,n,t){var i=e.head;if(i){
    if (a) return;
    var o=e.createElement("style");
    o.id="alloy-prehiding",o.innerText=n,i.appendChild(o),setTimeout(function(){o.parentNode&&o.parentNode.removeChild(o)},t)}}
    (document, document.location.href.indexOf("mboxEdit") !== -1, ".body { opacity: 0 !important }", 3000);
  </script>

    <!--Tags Header Embed Code: REPLACE WITH THE INSTALL CODE FROM YOUR OWN ENVIRONMENT-->
    <script src="//assets.adobedtm.com/launch-EN93497c30fdf0424eb678d5f4ffac66dc.min.js" async></script>
</head>
<body>
  <h1 id="title">Home Page</h1><br><br>
  <p id="bodyText">Navigation</p><br><br>
  <a id="home" class="navigationLink" href="#">Home</a><br>
  <a id="pageA" class="navigationLink" href="#">Page A</a><br>
  <a id="pageB" class="navigationLink" href="#">Page B</a><br>
  <a id="pageC" class="navigationLink" href="#">Page C</a><br>
  <div id="homepage-hero">Homepage Hero Banner Content</div>
</body>
</html>
```

In tags, add the Adobe Experience Platform Web SDK extension:

<!--![Add the Adobe Experience Platform Web SDK extension](assets/library-tags-addExtension.png){zoomable="yes"}-->

And add the desired configurations:
<!--![configuring the Web SDK tag extension migration options](assets/tags-config-migration.png){zoomable="yes"}-->


>[!ENDTABS] 


 
It's important to note that simply including and configuring the Platform Web SDK library as shown above does not execute any network calls to the Adobe Edge Network. 

Next, learn how to [request and apply Form-based activities](render-activities.md) to the page.

>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Decisioning extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
