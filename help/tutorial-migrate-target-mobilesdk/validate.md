---
title: Validate and troubleshoot the Decisioning extension implementation
description: Learn how to validate and troubleshoot an Adobe Target mobile implementation using the Decisioning extension.
exl-id: edc6e25a-58d7-4145-97c3-bf48e980914f
---
# Validate and troubleshoot the Decisioning extension implementation

After you have migrated your Target implementation from the Target extension to the Decisioning extension, it's important to validate everything is working properly before publishing any changes to your production app. Adobe recommends the following, which is covered in detail on this page:

* Perform a technical validation to make sure the basic implementation and Platform Mobile SDK requests and responses look correct
* Ensure that Target activities are delivered and rendered properly
* Check that reporting works correctly
* Revisit audiences and profile scripts to make sure they are compatible with Platform Mobile SDK and the Optimie extension
* Ensure integrations with Adobe or third-party applications work correctly 

Every Target implementation is different depending on site architecture and features used. You may use the tables below as a starting point and add any items unique to your implementation.

## Technical validation and troubleshooting

Technical validation and troubleshooting with Platform Mobile SDK and the Decisioning extension is greatly enhanced with Assurance. Please see the following documentation pages to learn about this essential tool:

* [Setting up Decisioning plugins in Assurance](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/assurance-setup/){target=_blank}

* [Validating Optimize SDK setup](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/optimize-configuration-view/){target=_blank}

* [Review requests and simulate different experiences](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/review-simulate/){target=_blank}

After performing the validation steps above, you can be confident that the Platform Mobile SDK implementation with the Decisioning extension is ready to move to production.

Congratulations, you've reached the end of the tutorial! Good luck migrating your Adobe Target implementation to the Decisioning extension!

>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Decisioning extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
