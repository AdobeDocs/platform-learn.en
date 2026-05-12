---
title: Enable cross-domain support - Migrate Target from at.js 2.x to Web SDK
description: Learn how to configure Adobe Target for cross-domain and mobile app to web browser scenarios using Experience Platform Web SDK.
exl-id: 6ec24ddc-8f6d-4331-a3ae-bd0f3a7d6e78
TQID: https://experienceleague.adobe.com/VbyLtur1afR78lNkRNnHjYTNu87dZS4WVP-s1fg4cfs
product_v2:
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
    internal-label: Target
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: adee20bd-51f4-461d-b9db-d215f8756eeb
    internal-label: Audiences
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: c20d46e7-1c7d-476c-a50e-3961d4dce35f
    internal-label: Reporting
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
    internal-label: Implementation
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
subfeature_v2:
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: ee602049-8a18-43df-9299-a689a025a371
    internal-label: Use cases
  - id: fd0ff162-b6d3-4a11-8aeb-e165a01c0f0a
    internal-label: at.js
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
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
>We are committed to helping you be successful with your Target migration from at.js to Web SDK. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
