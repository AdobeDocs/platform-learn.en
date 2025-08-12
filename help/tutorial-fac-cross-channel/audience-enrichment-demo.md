---
title: Enrich Experience Platform audiences with federated data
seo-title: Enrich Experience Platform audiences with federated data | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Enrich Experience Platform audiences with federated data
description: In this lesson, we enrich an Experience Platform audience with federated data.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-enrich-audience-with-federated-data.jpg
hide: true
exl-id: aa228bab-cdfe-40fc-93e0-2fa5015b54de
---
# Enrich Experience Platform Audiences with Federated Data

Federated Audience Composition enables you to enrich existing audiences in Adobe Experience Platform (AEP) by utilizing composed audience data that has been federated from the enterprise data warehouse. This data will not be persisted in Adobe Experience Platform customer profiles.

## Ways to Enrich a Federated Audience Composition

There are two primary methods to enrich a Federated Audience Composition. 

### 1. Reading an AEP Audience within a Federated Composition

In this first example, we'll use the **SecurFinancial Loan Application Page Visitor** audience stored in AEP's Profile Service to start our federated composition. We will enrich the audience using federated data in Snowflake to determine pre-approval based on credit score and loan activity.

![federated-composition-example](assets/snowflake-preapproval.png)

1. **Map AEP audience** to the Federated Audience Composition destination.
2. **Build your composition** with the mapped audience as a Read audience.
3. **Reconcile the identities** in your read audience to join with federated data.

 ![federated-method-1-1](assets/federated-method-1-1.png)

 ![federated-method-1-2](assets/federated-method-1-2.png)

### 2. Enriching Experience Platform Audience Rule with a Federated Audience

In the second example, we'll use the federated audience queried with credit score and loan activity to enrich the behavioral audience of loan application web page visitors.

By evaluating this audience on the Edge, we can instantly retarget the preapproved loan application page visitors with personalized offers on the site.

![edge-audience-enrich](assets/edge-audience-enrich.png)

1. **Save and Start** your federated audience composition. Once the composition has run, your federated audience will appear in the audience portal.
2. **Build an audience rule** using profile attributes and experience events from Profile Service, incorporating your federated audience.

Let's wrap this up with a [summary of learnings and final takeaways](conclusion.md)!
