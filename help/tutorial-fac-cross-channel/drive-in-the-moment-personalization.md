---
title: Drive "in-the moment" personalization on the Edge 
seo-title: Drive "in-the moment" personalization on the Edge | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Drive "in-the moment" personalization on the Edge
description: In this visual exercise, the federated audience is evaluated on the Edge for instant "in-the-moment" retargeting.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-drive-in-the-moment-personalization.jpg
---

# Drive "in-the moment" personalization on the Edge

Federated Audience Composition enables you to enrich existing audiences in Adobe Experience Platform (AEP) by utilizing composed audience data that has been federated from the enterprise data warehouse. This data will not be persisted in Adobe Experience Platform customer profiles.

In this visual exercise, we use a federated audience queried with credit score and loan activity to enrich the behavioral audience of loan application web page visitors.

By evaluating this audience on the Edge, we instantly retarget the preapproved loan application page visitors with personalized offers on the site.

![edge-audience-enrich](assets/edge-audience-enrich.png)

## Steps

1. **Save and Start** your federated audience composition. Once the composition has run, the federated audience will appear in the audience portal.
2. **Build an audience rule** using profile attributes and experience events from Profile Service, incorporating your federated audience.

Let's wrap this up with a [summary of learnings and final takeaways](conclusion.md)!
