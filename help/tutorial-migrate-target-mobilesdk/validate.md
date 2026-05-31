---
title: Validate and troubleshoot the Offer Decisioning and Target extension implementation
description: Learn how to validate and troubleshoot an Adobe Target mobile implementation using the Offer Decisioning and Target extension.
exl-id: edc6e25a-58d7-4145-97c3-bf48e980914f
TQID: https://experienceleague.adobe.com/fNbW6fZkcTW-Kqm54vV3FdBroJR1FHxQRlVVtVriwY8
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
  - id: ed0d8d0e-04b9-4326-be72-a0fbca265377
    internal-label: Integrations
  - id: f7c7de77-382f-4f48-8b36-61a170f06d3d
    internal-label: Integrations
subfeature_v2:
  - id: ae2cba0e-54f2-464b-a3b3-ad371e8a886a
    internal-label: Catalog
  - id: c3d7a45c-ad17-435d-8b71-882abbe8f27e
    internal-label: Troubleshooting
  - id: d051910f-2bda-47ea-a969-6ade9fcd71f1
    internal-label: Implement mobile
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
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# Validate and troubleshoot the Offer Decisioning and Target extension implementation

After you have migrated your Target implementation from the Target extension to the Offer Decisioning and Target extension, it's important to validate everything is working properly before publishing any changes to your production app. Adobe recommends the following, which is covered in detail on this page:

* Perform a technical validation to make sure the basic implementation and Platform Mobile SDK requests and responses look correct
* Ensure that Target activities are delivered and rendered properly
* Check that reporting works correctly
* Revisit audiences and profile scripts to make sure they are compatible with Platform Mobile SDK and the Optimie extension
* Ensure integrations with Adobe or third-party applications work correctly 

Every Target implementation is different depending on site architecture and features used. You may use the tables below as a starting point and add any items unique to your implementation.

## Technical validation and troubleshooting

Technical validation and troubleshooting with Platform Mobile SDK and the Offer Decisioning and Target extension is greatly enhanced with Assurance. Please see the following documentation pages to learn about this essential tool:

* [Setting up Decisioning plugins in Assurance](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/assurance-setup/){target=_blank}

* [Validating Optimize SDK setup](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/optimize-configuration-view/){target=_blank}

* [Review requests and simulate different experiences](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/review-simulate/){target=_blank}

After performing the validation steps above, you can be confident that the Platform Mobile SDK implementation with the Offer Decisioning and Target extension is ready to move to production.

Congratulations, you've reached the end of the tutorial! Good luck migrating your Adobe Target implementation to the Offer Decisioning and Target extension!

>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Offer Decisioning and Target extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
