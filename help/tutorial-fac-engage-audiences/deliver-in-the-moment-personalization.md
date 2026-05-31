---
title: Deliver "in-the moment" personalization using Edge Network
seo-title: Deliver "in-the moment" personalization using Edge Network | Engage with audiences directly from your data warehouse using Federated Audience Composition
breadcrumb-title: Deliver "in-the moment" personalization using Edge Network
description: In this exercise, the federated audience is evaluated on the Edge for instant "in-the-moment" retargeting.
role: Developer
jira: KT-18743
thumbnail: 18743-drive-in-the-moment-personalization.jpg
exl-id: 20bfafb1-1d1b-48d8-84eb-97d4c9e03b76
TQID: https://experienceleague.adobe.com/qTkC0rREIzTlqdvFIkid2wY-rsOX5vm8pysh5yRM01Y
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
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
# Deliver "in-the moment" personalization using Edge Network

Federated Audience Composition enables you to enrich existing audiences in Adobe Experience Platform (AEP) by utilizing composed audience data that has been federated from the enterprise data warehouse. This data will not be persisted in Adobe Experience Platform but you can use the [event forwarding](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview){target="_blank"} capabilities to send this data straight to your data warehouse.

In this exercise, we use a federated audience queried with credit score and loan activity to enrich the behavioral audience of loan application web page visitors.

By evaluating this audience on the Edge, we instantly retarget the preapproved loan application page visitors with personalized offers on the site.

![edge-audience-enrich](assets/edge-audience-enrich.png)

## Steps

1. **Save and Start** your federated audience composition. Once the composition has run, the federated audience will appear in the audience portal.
2. **Build an audience rule** using profile attributes and experience events from Profile Service, incorporating your federated audience.

Let's wrap this up with a [summary of learnings and final takeaways](conclusion.md)!
