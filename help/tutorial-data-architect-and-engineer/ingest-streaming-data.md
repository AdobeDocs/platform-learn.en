---
title: Ingest Streaming Data | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
description: 
feature: data ingestion
topics: 
kt: 4348
audience: data architect,data engineer
doc-type: tutorial
activity: implement
---

# Ingest Streaming Data

In this lesson we are going to stream data into Platform using the Web SDK.

There are two main tasks we need to complete in the Adobe Experience Platform Launch interface:

* First, we need to create an Edge configuration, which tells the Adobe servers where data should go (e.g. Platform, Adobe Analytics, Adobe Target, etc) after it has been sent to the Edge by Web SDK. This step needs to be taken by all Web SDK customers, regardless of how they are deploying Web SDK
* Second, we need to implement Web SDK. Web SDK can be deployed via the Launch interface or it can be deployed using the raw javascript file, alloy.js. In this tutorial, we will use the Launch interface. This tutorial will just focus on the minimal amount of features needed to deploy a simple Web SDK implementation specifically to stream data into Experience Platform and is not meant to be a complete Launch tutorial.

First, watch these two short video to learn more about streaming data ingestion and Web SDK:
>[!VIDEO](https://video.tv.adobe.com/v/28425?quality=12&learn=on)

>[!VIDEO](https://video.tv.adobe.com/v/34141?quality=12&learn=on)

## Permissions required

In the [Configure Permissions](configure-permissions.md) lesson, you setup all the access controls you need to complete this lesson, specifically:

* Permission item Launch > Property Rights > Approve, Develop, Manage Environments, Manage Extensions, and Publish
* Permission item Launch > Company Rights > Manage Properties
* User-role access to the `Luma Tutorial Launch` product profile

## Create a Launch Configuration

First, we are going to create an Edge Configuration. This configuration will generate a Configuration ID. This ID will be added to the AEP Web SDK configuration in Launch and will be used to route data appropriately when it hits the Experience Edge.

1. Navigate to launch.adobe.com
    <!--when will the edge config go live?-->

1. Select the Edge Configuration icon from the left-hand rail

    ![Click Edge Configuration icon in the left navigation](assets/launch-edgeConfig-clickNav.png)

1. Click the **[!UICONTROL New Edge Configuration]** button in the upper-right hand corner

1. Give your Configuration a Name and Description (optional) and click Save

## Install the Web SDK Extension

## Create Rules to Send Data

## Use the Data Layer to XDM Mapper

## Additional Resources

* [Streaming Ingestion documentation](https://docs.adobe.com/content/help/en/experience-platform/ingestion/streaming/overview.html)
* [Data Ingestion API reference](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/ingest-api.yaml)