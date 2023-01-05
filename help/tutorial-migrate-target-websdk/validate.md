---
title: Validate Target implementations with Web SDK | Migrate Target from at.js 2.x to Web SDK
description: Learn how to validate activities and debug an Adobe Target implementation using the Adobe Experience Platform Web SDK.
---
# Validate the Platform Web SDK implementation

After you have migrated your Target implementation from at.js to Platform Web SDK, it's important to validate everything is working properly before publishing any changes to your production site. Adobe recommends the following, which is covered in detail on this page:

* Perform a technical validation to make sure the basic implementation and Platform Web SDK requests and responses look correct
* Ensure that Target activities are delivered and rendered properly
* Check that reporting works correctly
* Revisit audiences and profile scripts to make sure they are compatible with Platform Web SDK
* Ensure integrations with Adobe or third-party applications work correctly 

Every Target implementation is different depending on site architecture and features used. You may use the tables below as a starting point and add any items unique to your implementation. The [Debugging page](debugging.md) of this tutorial shows you tools you can use to help with this validation.

## Technical validation

| Validation item | Notes |
|---|---|
| The at.js prehiding snippet is no longer present on the page | The Platform Web SDK does not automatically remove the style with ID `at-body-style`. Leaving this old snippet on the page results in hidden content until the snippet timeout is reached. |
| The at.js library is no longer present on the page | Check that there is no "adobe.target" object in your browser's developer tools console. Including both Platform Web SDK and at.js results in unintended rendering behavior |
| Expected parameters are in the XDM and data objects of the `sendEvent` request | | 
| Recommendations catalog is updated as expected if using page requests to populate the catalog | |
| Profile parameters are successfully passed to Target | View Edge traces in the Debugger |
| Parameters mapped to XDM in the datastream mapper are passed correctly to Target | Validate using the Edge Trace feature of the Debugger and/or Assurance | 
| Target content returns in the applicable `sendEvent` responses | Expected when `renderDecisions` option is set to `true` or scopes are requested and the user qualifies for a particular Target activity |
| A `decisioning.propositionDisplay` event fires after VEC-based activities render | Activities rendered automatically and on-demand are expected to have separate event calls |
| A `decisioning.propositionDisplay` event fires after form-based activities render | Only applicable for certain implementations. Requires custom code to execute this call. |
| A `decisioning.propositionDisplay` event fires when an offer is applied on a SPA view change | Only applicable for SPA implementations |
| A `decisioning.propositionDisplay` event does NOT fire when a SPA component re-renders for a given view | Only applicable for SPA implementations |
| A `decisioning.propsitionInteract` event fires after an activity conversion | The "Clicked an element" and custom conversions migrated from at.js `trackEvent` or `sendNotifications` are expected to have separate event calls |
| Response tokens are returned in the `sendEvent` response and have expected values | Response tokens should function normally with Web SDK |
| ECIDs are consistent across pages with Web SDK and at.js | Applies to page-by-page migrations. Redirect offers are not expected to work in these types of migrations |


## Activity delivery and rendering

| Validation item | Notes |
|---|---|
| VEC-based activities render properly on page load | It's best to validate both custom code modifications and basic modifications such as rearranging elements or replacing text |
| VEC-based activities render properly on SPA view changes | Only applicable for SPA implementations |
| Form-based activities render properly | Only applicable for certain implementations. Rendering form based activities requires custom code similar to at.js. |
| Activities that use redirects work properly | Redirects are supported if both the source and destination page use Platform Web SDK. A Target redirect from an at.js page to a Platform Web SDK page or the opposite way is not supported. |
| Activities that use remote offers work properly | Not common, check your Target offer inventory for Remote Offers |
| Flicker is appropriately mitigated | Flicker handling is optional, but ensure any mitigation tactics that you have in place are working as expected for optimal page performance and user experience |
| QA links work as expected | If not working, confirm that the web.webPageDetails.URL exactly matches the URL in the browser |
| All your commonly used offer types are rendered as expected |  |

## Reporting

| Validation item | Notes |
|---|---|
| Visitors are attributed to VEC-based activities | It's best to validate reporting works as expected for both page load modifications and SPA view modifications |
| Visitors are attributed to form-based activities | Depending on the rendering approach used, your implementation may require custom code to execute a `decisioning.propositionDisplay` event |
| Standard conversion goals are properly captured | Applies to either Target or Analytics as the reporting source |
| Order conversions and details are properly captured | Check the Audit report |
| Click-tracking conversions are properly captured |  |
| Custom conversion goals are properly captured | For example, conversion goals migrated from at.js `trackEvent` or `sendNotifications` which are commonly used with the "viewed an mbox" goal |

## Audiences and profile scripts

| Validation item | Notes |
|---|---|
| Audiences used in live activities are compatible with Platform Web SDK | Audiences that use the "Custom" (mbox parameter) component must be updated to include XDM attributes |
| All profile scripts are compatible with Platform Web SDK | Any profile scripts that use mbox parameters must be updated to include XDM attributes |
| Activities return for Target audiences | It's best to perform end-to-end validation on audiences you modify to make compatible with Platform Web SDK |  
| Profile scripts evaluate as expected | View Edge traces in the Debugger |

## Integrations with Adobe applications

| Validation item | Notes |
|---|---|
| Activities return for Experience Cloud audiences | For example, a segment published from Adobe Analytics |
| Activities return for Experience Platform audiences | Only applies if you have a license for an Experience Platform-based application like RTCDP |  
| Activities return for Audience Manager audiences | For example, a segment based on visiting a specific page |
| Target activity data displays in Analysis Workspace | Applies to activities that use Adobe Analytics as the reporting source |

## Integrations with third-party applications

| Validation item | Notes |
|---|---|
| Response token data is properly passed to third-party applications | Integration approaches may vary, but a common method is to use Target response tokens to pass activity and experience information to other analytics tools like Google Analytics |
| Information from third-parties is passed as either XDM or profile data | All relevant information from third-parties should be passed in `sendEvent` calls to Target |

After performing the validation steps above, you can be confident that the Platform Web SDK implementation is ready to move to production.

Next, learn how to [troubleshoot a Target implementation using Platform Web SDK](debugging.md).

>[!NOTE]
>
>We are committed to helping you be successful with your Target migration from at.js to Web SDK. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).