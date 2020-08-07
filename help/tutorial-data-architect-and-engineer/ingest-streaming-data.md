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

Streaming data ingestion allows you to send data from client-side and server-side devices in real-time.

First, watch this short video to learn more about streaming data ingestion:
>[!VIDEO](https://video.tv.adobe.com/v/28425?quality=12&learn=on)

## Permissions required

In the [Configure Permissions](configure-permissions.md) lesson, you setup all the access controls you need to complete this lesson, specifically:

* Permission item Datasets > View Datasets
* Permission item Datasets > Data Monitoring
* Permission item Sources > View Sources
* Permission item Sources > Manage Sources
* Permission item Sandboxes > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
* Developer-role access to the `Luma Tutorial Platform` product profile (for API)

## Create a Launch Configuration

Next we’re going to create an Edge Configuration. This configuration will generate a Configuration ID. This ID will be added to the AEP Web SDK configuration in Launch and will be used to route data appropriately when it hits the Experience Edge.

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