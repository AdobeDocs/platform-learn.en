---
title: Introduction to Journey Orchestration
description: The Real-Time Customer Profile powers cross channel personalization at scale through each phase of the customer journey. Batch or Streaming data can be enabled for the Real-time Customer Profile by enabling both the schema and corresponding dataset.
feature: Journey Orchestration
topics: Introduction
kt: KT-2773
audience: user, developer
doc-type: video
activity: understand
---

# Introduction to Journey Orchestration

Journey Orchestration allow real-time orchestration powered by contextual data from events, information from the Adobe Experience Platform, or data from third-party solutions.
The feature determines in multistep flows called journeys the next best actions specific to the consumer, based on their profile and behaviors. This comprises both the optimal timing, as well as the type action, such as sending the consumer an update via push notification or the notification of a third party system. These decisions are made based on rules and Sensei scores.

Journey orchestration leverages data stored on the Experience Platform, data stored in any third party service that can be queried through an API call, and contextual information shared through the payload of the event triggering the journeys.

>[!VIDEO](https://video.tv.adobe.com/v/29307?quality=12)

## How to Configure a Journey

The main steps in preparation for building journeys:

1. [Configure Streaming Events](/help/journey-orchestration/journey-orchestration-configuring-streaming-events.md): This configuration is mandatory, as Triggered Journeys is designed to listen to events.
2. [Configure Data Sources](/help/journey-orchestration/journey-orchestration-configuring-data-sources.md):This configuration is not required if your journeys only leverage local data coming from an event payload.
3. [Configure Actions](/help/journey-orchestration/journey-orchestration-configuring-actions.md): Required if you want to us a service from any provider that can be called through a REST API with a Jason formatted payload

>[!NOTE]
>These configuration steps require technical knowledge. You will need to be familiar with the [Experience Data Model (XDM)](/help/schemas/understanding-the-xdm-system-and-experience-data-model.md) and [how to compose XDM Experience EventSchemas](/help/schemas/create-your-first-schema-with-out-of-the-box-components.md).

## How to Create, Publish, and Analyze a Journey

1. [Create a Journey](/help/journey-orchestration/journey-orchestration-create-a-journey.md)
2. Validate a Journey
3. [Analyze a Journey via Reporting Tools](/help/journey-orchestration/journey-orchestration-reporting.md)

## Additional Resources

* [Journey Orchestration Documentation](https://docs.adobe.com/content/help/en/journeys/using/journey-orchestration-home.html)
