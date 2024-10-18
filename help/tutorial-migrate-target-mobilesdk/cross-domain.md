---
title: Enable cross-domain support - Migrate from the Adobe Target to the Adobe Journey Optimizer - Decisioning Mobile extension
description: Learn how to configure Adobe Target for cross-domain and mobile app to web browser scenarios using Experience Platform Web SDK.
---
# Enable cross-domain visitor profiles

The Platform Web SDK supports visitor ID sharing capabilities that enable customers to deliver personalized experiences more accurately across your domains. This capability allows you to deliver consistent personalization across domains and enhances the accuracy of your visitor activity reporting, without relying on third-party cookies.

## Prerequisites

To use cross-domain ID sharing, you must use Platform Web SDK version 2.11.0 or later. This capability is also compatible with VisitorAPI.js version 1.7.0 or later. 

Cross-domain ID sharing works by appending a special `adobe_mc` query string parameter to the URL of the destination domain. This parameter is used for specifying the visitor ID instead of generating a new ID or using an existing ID.

The destination domain must use either of these libraries for cross-domain ID sharing to process the `adobe_mc` parameter and share the visitor ID properly.

## Approach comparison

Before implementing, first determine if your existing implementation uses the `visitor.appendVisitorIDsTo()` function. Any custom code using this function should be updated to use the new `appendIdentityToUrl` Web SDK command.

| VisitorAPI.js | Platform Web SDK |
| --- | --- |
| `visitor.appendVisitorIDsTo(*url*)` |  `alloy("appendIdentityToUrl", { url: *url* })` |

## Using the `appendIdentityToURL` command

For cross-domain ID sharing, Web SDK version 2.11.0 adds support for the `appendIdentityToUrl` command. When used, this command generates the `adobe_mc` query string parameter.

The command accepts an object with one property, `url`, and returns an object with the property url.

This command does not wait for any consent update. If consent has not been provided, the URL is returned unchanged.

If an ECID is not provided, the `/acquire` endpoint is called to generate an ECID.

Below is an example of how you can implement cross-domain ID sharing.

This code adds an event listener for all the clicks on the page. If the click was on a link to a matching domain, in this case adobe.com or behance.com, it adds the identity to the URL and redirects the user there.

```Javascript
document.addEventListener("click", event => {
  const anchor = event.target.closest("a");
  if (!anchor || !anchor.href) {
    return;
  }
  const url = new URL(anchor.href);
  if (!url.hostname.endsWith("adobe.com") && !url.hostname.endsWith("behance.com")) {
    return;
  }
  event.preventDefault();
  alloy("appendIdentityToUrl", { url: anchor.href }).then(result => {
    document.location = result.url;
  });
});
```

>[!TIP]
>
>When using the tags feature (formerly Launch) to implement Web SDK, cross-domain ID sharing can be accomplished without custom code. Refer to the [dedicated documentation](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/id-sharing.html#tags-extension) for more details.

>[!NOTE]
>
>The Platform Web SDK also supports mobile-to-web ID sharing for native mobile app use cases. For more information, refer to the dedicated documentation about [mobile-to-web and cross-domain ID sharing](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/id-sharing.html).

Next, learn how to [update audiences and profile scripts](update-audiences.md) to ensure compatibility with Platform Web SDK.

>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Decisioning extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
