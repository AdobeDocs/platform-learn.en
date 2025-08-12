---
title: Map a federated audience to S3
seo-title: Map a federated audience to S3 | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Map a federated audience to S3
description: In this lesson, we will map a federated audience to a downstream Real-Time CDP destination to support a personalized offline experience.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-create-an-audience.jpg
hide: true
---

# Map Federated Audience to S3 to Leverage Audience Attributes for Enrichment

In this exercise, you'll learn how to leverage audience attributes in your data warehouse to enrich your audience's experience in downstream activation workflows using RTCDP destinations. For SecurFinancial, these federated attributes can be used to enhance the customer audience's personalization experience offline. In this example, we will map the federated audience to a pre-configured Amazon S3 destination.

## Steps

1. Navigate to the **Destinations** portal.

2. Click the **3 dot menu** button next to the pre-configured Amazon S3 destination, then click **Activate Audiences**.

   ![activate-audiences](assets/activate-audiences.png)

3. Select the **S3 destination**, then click **Next**.

   ![select-s3-destination](assets/select-s3-destination.png)

4. Select the **SecureFinancial Customers - No Loans, Good Credit** audience.

    ![select-s3-audience](assets/select-s3-audience.png)

5. In the **Scheduling** section, leave all default settings and click **Next**.

6. In the **Mapping** step, ensure the following is included and selected as the **Deduplication Key**. Then click **Next**:
   - `xdm: personalEmail.address`

   ![deduplication-key](assets/deduplication-key.png)

7. In the following mapping step, you can select enrichment attributes based on audience field mappings in the federated audience composition. Click the **pencil (edit)** icon to view the pre-selected attributes.

   ![edit-attributes](assets/edit-attributes.png)

   ![final-attributes](assets/final-attribution.png)

8. Review your audience mapping and hit **Finish**.

We're ready to move on to [building a journey](build-journey-federated-audience.md).
