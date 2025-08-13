---
title: Map a federated audience to S3
seo-title: Map a federated audience to S3 | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Map a federated audience to S3
description: In this visual exercise, we will map a federated audience to a downstream Real-Time CDP destination to support a personalized offline experience.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-create-an-audience.jpg
exl-id: a47b8f7b-7bd0-43a0-bc58-8b57d331b444
---
# Map Federated Audience to S3 to Leverage Audience Attributes for Enrichment

You can leverage audience attributes in your data warehouse to enrich your audience's experience in downstream activation workflows using RTCDP destinations. For SecurFinancial, these federated attributes can be used to enhance the customer audience's personalization experience offline. Below, the federated audience is mapped to a pre-configured Amazon S3 destination.

## Steps

1. Navigate to the **Destinations** portal.

2. Click the **3 dot menu** button next to the pre-configured Amazon S3 destination, then click **Activate Audiences**.

   ![activate-audiences](assets/activate-audiences.png)

3. Select the **S3 destination**, then click **Next**.

   ![select-s3-destination](assets/select-s3-destination.png)

4. Select the appropriate audience. In our example: **SecureFinancial Customers - No Loans, Good Credit** audience.

    ![select-s3-audience](assets/select-s3-audience.png)

5. In the **Scheduling** section, use the default settings and click **Next**.

6. In the **Mapping** step, choose the de-duplication key. In our example, `xdm: personalEmail.address` is included and selected as the **De-duplication Key**. Then click **Next**:
   
   ![deduplication-key](assets/deduplication-key.png)

7. In the mapping step, select enrichment attributes based on audience field mappings in the federated audience composition. Click the **pencil (edit)** icon to view the pre-selected attributes.

   ![edit-attributes](assets/edit-attributes.png)

   ![final-attributes](assets/final-attribution.png)

8. Review your audience mapping and hit **Finish**.

>[**SUMMARY**]
>
> We successfully built an audience and activated it to an S3 destination with ease. The platform's user-friendly interface allows marketing teams to quickly build and activate audiences, reducing time to value. Customers taking this approach have gone live with there first use case in under two months.

We're ready to move on to [building a journey](build-journey-federated-audience.md).
