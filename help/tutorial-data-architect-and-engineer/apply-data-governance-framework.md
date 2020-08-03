---
title: Create Governance Policies | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
description: 
feature: governance
topics: 
kt: 4348
audience: data architect,data engineer
doc-type: tutorial
activity: implement
---

# Create Governance Policies

Lorem Ipsum

First, watch these short videos about data governance:
>[!VIDEO](https://video.tv.adobe.com/v/36653?quality=12&learn=on)
>[!VIDEO](https://video.tv.adobe.com/v/29708?quality=12&learn=on)

## Permissions required

In the [Configure Permissions](configure-permissions.md) lesson, you setup all the access controls you need to complete this lesson, specifically:

* Permission item Sandbox Management > Manage Sandboxes
* Permission item Sandbox Management > View Sandboxes
* Permission item Sandboxes > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
* Developer-role access to the `Luma Tutorial Platform` product profile (for API)


In this video we will apply DULE labels on Schema e.g. Luma Loyalty Schema


### Apply Data Governance Labels

1. Go to Data Management and select Datasets option
1. Select **Luma Offline Purchase Dataset**
1. Select **Data Governance** tab for the dataset
1. Find and select **email_id** field in the list
1. Click **Edit Governance labels** pencil icon in right 
1. Select I1 as address field contains email address and it is directly identifiable data that can identify or contact a specific person, rather than a device.

![Data Governance Label](assets/datasets-dule.png)

1. Click Save changes


Repeat similar steps for other Schemas as well and identify appropriate fields and appropriate labels.

```
Note For SME : In this video you will be also explain what other labels are and when to use which label. You may ask learners to add more DULE label as they think would be right for the Schema. 

```

Use content from Mathieu's demo

## Additional Resources

* [Data Governance documentation](https://docs.adobe.com/content/help/en/experience-platform/data-governance/home.html)
* [Dataset Service API reference](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/dataset-service.yaml)
* [Governance Policy Service API reference](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/dule-policy-service.yaml)