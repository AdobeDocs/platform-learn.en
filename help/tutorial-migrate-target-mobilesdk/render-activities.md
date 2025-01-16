---
title: Render Target activities - Migrate from the Adobe Target to the Adobe Journey Optimizer - Decisioning Mobile extension
description: Learn how to migrate an Adobe Target implementation from at.js 2.x to Adobe Experience Platform Web SDK. Topics include library overview, implementation differences, and other noteworthy callouts.
exl-id: 39569088-a254-4e64-9956-0c6e1a8ed2a5
---
# Render Target activities that use the form-based composer

Some Target implementations may use regional mboxes (now known as "scopes") to deliver content from activities that use the form-based Experience Composer. If your at.js Target implementation uses mboxes, then you need to do the following:

* Update any references from your at.js implementation that use `getOffer()` or `getOffers()` to the equivalent Platform Web SDK methods.
* Add code to trigger a `propositionDisplay` event so that an impression is counted.

## Request and apply content on demand

Activities created using Target's form-based composer and delivered to regional mboxes cannot be rendered automatically by the Platform Web SDK. Similar to at.js, offers delivered to specific Target locations need to be rendered on demand. 


+++at.js Example using `getOffer()` and `applyOffer()`:

1. Execute `getOffer()` to request an offer for a location
1. Execute `applyOffer()` to render the offer to a specified selector
1. An activity impression is automatically incremented at the time of the `getOffer()` request

```JavaScript
// Retrieve an offer for the homepage-hero location
adobe.target.getOffer({
  "mbox": "homepage_hero",

  // Render offer to the #hero-banner selector
  "success": function(offers) {
    adobe.target.applyOffer({
      "mbox": "homepage_hero",
      "selector": "#hero-banner",
      "offer": offers
    });
  },
  "error": {
    console.log(error);
  },
  "timeout": 3000
});
```

+++

+++Platform Web SDK equivalent using the `applyPropositions` command: 

1. Execute `sendEvent` command to request offers (propositions) for one or more locations (scopes)
1. Execute `applyPropositions` command with metadata object which supplies instructions for how to apply content to the page for each scope
1. Execute `sendEvent` command with eventType of `decisioning.propositionDisplay` to track an impression 

```JavaScript
// Retrieve propositions for homepage_hero location (scope)
alloy("sendEvent", {
  "decisionScopes": ["homepage_hero"]
}).then(function(result) {
  var retrievedPropositions = result.propositions;
    
  // Render offer (proposition) to the #hero-banner selector by supplying extra metadata
  return alloy("applyPropositions", {
    "propositions": retrievedPropositions,
    "metadata": {
      // Specify each regional mbox or scope name along with a selector and actionType
      "homepage_hero": {
        "selector": "#hero-banner",
        "actionType": "setHtml"
      }
    }
  }).then(function(applyPropositionsResult) {
    var renderedPropositions = applyPropositionsResult.propositions;

    // Send the display notifications via sendEvent command
    alloy("sendEvent", {
      "xdm": {
        "eventType": "decisioning.propositionDisplay",
        "_experience": {
          "decisioning": {
            "propositions": renderedPropositions
          }
        }
      }
    });
  });
});
```

+++

The Platform Web SDK offers greater control for applying form-based activities to the page using the `applyPropositions` command with a `actionType` specified:

| `actionType` | Description | at.js `applyOffer()` | Platform Web SDK `applyPropositions`|
| --- | --- | --- | --- |
| `setHtml` | Clear the content of the container, then add the offer to the container | Yes (always used) | Yes |
| `replaceHtml` | Remove the container and replace it with the offer | No | Yes |
| `appendHtml` | Appends the offer after the selector specified | No | Yes |

Refer to the [dedicated documentation](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/rendering-personalization-content.html) about rendering content using the Platform Web SDK for additional rendering options and examples.

## Implementation example

The example page below builds upon the implementation outlined in the previous section, only it adds additional scopes to the `sendEvent` command.

+++Platform Web SDK example with multiple scopes

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

  <!--Prehiding snippet for Target with asynchronous deployment-->
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
  <script src="https://cdn1.adoberesources.net/alloy/2.6.4/alloy.min.js" async></script>
  
  <!--Configure Platform Web SDK then send event-->
  <script>
    alloy("configure", {
      "edgeConfigId": "ebebf826-a01f-4458-8cec-ef61de241c93",
      "orgId":"ADB3LETTERSANDNUMBERS@AdobeOrg"
    });
    alloy("sendEvent", {
      // Request and render VEC-based activities
      "renderDecisions": true,
      // Request content for form-based activities using the "homepage_hero" scope
      "decisionScopes": ["homepage_hero"]
    }).then(function(result) {
      var retrievedPropositions = result.propositions;
        
      // Render offer (proposition) to the #hero-banner selector by supplying extra metadata
      return alloy("applyPropositions", {
        "propositions": retrievedPropositions,
        "metadata": {
          // Specify each regional mbox or scope name along with a selector and actionType
          "homepage_hero": {
            "selector": "#hero-banner",
            "actionType": "setHtml"
          }
        }
      }).then(function(applyPropositionsResult) {
        var renderedPropositions = applyPropositionsResult.propositions;

        // Send the display notifications via sendEvent command
        alloy("sendEvent", {
          "xdm": {
            "eventType": "decisioning.propositionDisplay",
            "_experience": {
              "decisioning": {
                "propositions": renderedPropositions
              }
            }
          }
        });
      });
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

Next, learn how to [pass Target parameters using the Platform Web SDK](send-parameters.md).

>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Decisioning extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
