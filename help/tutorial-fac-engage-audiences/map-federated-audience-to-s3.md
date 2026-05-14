---
title: Map a Federated Audience to an S3 Destination
seo-title: Map a Federated Audience to an S3 Destination | Engage with audiences directly from your data warehouse using Federated Audience Composition
breadcrumb-title: Map a Federated Audience to S3
description: In this exercise, we will map a federated audience to a downstream Real-Time CDP destination to support a personalized offline experience.
role: Developer
jira: KT-18743
thumbnail: 18743-create-an-audience.jpg
exl-id: a47b8f7b-7bd0-43a0-bc58-8b57d331b444
TQID: https://experienceleague.adobe.com/ZtFfOs294oDWm5tK1ENkgwRhhLEFIGLABEUbFjlhmeE
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
---
# Map a Federated Audience to an S3 destination to leverage audience attributes for enrichment

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

### SUMMARY

 We successfully built an audience and activated it to an S3 destination with ease. Any other solution can pick up this Audience and use it straightaway. The user-friendly interface allows marketing teams to quickly build and activate audiences without moving underlying data. Customers taking this approach have gone LIVE with their first use case in about a month. 


Now we'll [build a journey](build-journey-federated-audience.md).
