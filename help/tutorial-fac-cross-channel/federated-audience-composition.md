---
title: Enrich Experience Platform audiences with federated data
seo-title: Enrich Experience Platform audiences with federated data | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Enrich Experience Platform audiences with federated data
description: In this visual exercise, an Experience Platform audience is enriched with federated data.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-enrich-audience-with-federated-data.jpg
hide: true
exl-id: 3f6aa121-0dbd-4ad9-b136-d1455eed03ca
---
# Enrich Experience Platform Audiences with Federated Data

Federated Audience Composition enables you to enrich existing audiences in Adobe Experience Platform (AEP) by utilizing composed audience data that has been federated from the enterprise data warehouse. This data will not be persisted in Adobe Experience Platform customer profiles.

## Reading an AEP Audience within a Federated Composition

In this visual exercise, we use the **SecurFinancial Loan Application Page Visitor** audience stored in AEP's Profile Service to start our federated composition. It uses the federated data in Snowflake to determine pre-approval based on credit score and loan activity.

![federated-composition-example](assets/snowflake-preapproval.png)

### Steps

1. **Map AEP audience** to the Federated Audience Composition destination.
2. **Build your composition** with the mapped audience as a Read audience.
3. **Reconcile the identities** in your read audience to join with federated data.

 ![federated-method-1-1](assets/federated-method-1-1.png)

 ![federated-method-1-2](assets/federated-method-1-2.png)

We'll look at another example of using federated data to [support "in-the-moment" personalization](drive-in-the-moment-personalization.md)!
