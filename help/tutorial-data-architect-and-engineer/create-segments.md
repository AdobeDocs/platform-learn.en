---
title: Create Segments | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
description: 
feature: data ingestion
topics: 
kt: 4348
audience: data architect,data engineer
doc-type: tutorial
activity: implement
---

# Create segments

## Create a basic segment

1. Go to **Segments** under **customer** section in platform
1. In Attributes tab, Enter **loyalty** in search box
1. You should see **Loyalty** folder , click on the folder and you should see properties available in the loyalty folder
1. Drag and drop , **level** from attribute fields to canvas 
1. Select Level equals 'Gold' or 'Platinum'
1. Provide name of segment ' Luma : Gold or Above'
1. Provide description of segment ' Luma customers with level Gold or Above'
1. Click save to save this segment
   ![Segment](assets/segment-goldOrAbove.png)
1.  In a few minutes , you should see an estimate of existing customers show up.

## Create a dynamic segment

In this we will create a segment where customer has bought same product twice with in 30 days.

1. Create Segment 
1. Drag and Drop **Product Name**
1. Set **Product Name** as exists
1. Drag and Drop another  **Product Name** to right of existing field
1. We need to set it's value to same as product selected in the top. For this we will need to go to events to browse variables in left.
1. Select Product Name 1 > Product name 
1. Drag product name to set value in blue box 'operands'

## Create a multi-entity segment

With the advanced multi-entity segmentation feature, you can create segments using multiple XDM classes thereby adding extensions to person schemas. As a result, Segmentation Service can access additional fields during segment definition as if they were native to the profile data store

This segment is created by leveraging relationship between multiple XDM Schema - Product Catalog Schema and Offline Purchase Schema.

### Pre-Req

Firstly we need to establish relationship between **Luma Offline Purchase Event** schema with **Luma Product Catalog** Schema

1. Go to **Luma Offline Purchase Event**
1. Select **Luma Offline Purchase Event** mixin
1. Navigate to **_tenant > purchase_event > products** 
1. Select **productSku**
1. In field properties, mark checkbox for **Relationship**
1. In **Reference Schema** , Select **Luma Product Catalog**
1. **Reference identity namespace** will be automatically selected as **lumaProductSKU**
   ![Product Relationship](assets/segment-productRelationship.png)
1. Apply & Save.
1. Now go back to **Luma Offline Purchase Event** dataset and re-ingest data

### Segment

1. Go to **Segments** under customer.
1. Click on **Create Segment** in top right corner.
1. Provide Name **Products For Men**
1. Search for **Product category** under **Events**.
1. Drag and drop **Product Category** to center of page.
1. Enter **Men** in textbox after **Product Category** equals.
1. Save.

![Product Category](assets/segment-MultiEntity.png)

## Create a streaming segment

## Create and evaluate segments using API

In this lesson, we will create a new segment of all Luma customer whose loyalty level is Bronze.


1. Open Postman
1. In platform, Go to folder **6-Segmentation**
1. Select request **Create Segment**
1. Verify URL and body

### URL

```
https://platform-va7.adobe.io/data/core/ups/segment/definitions
```

### BODY 

```
{
    "name" : "Luma Bronze Customer",
    "description": "Segment dataset into all bronze customers",
    "expression" : {"type":"PQL", "format":"pql/text", "value":"_wwfovlab011.loyalty.level=\"bronze\""},
    "schema" : {"name": "_xdm.context.profile", "id": "luma_bronze_customers"} ,
    "ttlInDays" : 90
}

```

1. Send Request
1. If successful, you should get **Status : 200 OK**
1. Go to AEP UI , and verify you have new segment named **Luma Bronze Customer**


```
 NOTE TO SME : All the API body or URL referes to _wwfovlab011 tenant , it may change for learners so please educate them about this in video.
``




