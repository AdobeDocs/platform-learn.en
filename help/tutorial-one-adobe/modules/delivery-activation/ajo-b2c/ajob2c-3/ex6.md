---
title: Offer Decisioning - Test your Decision using the API
description: Test your Decision using the API
kt: 5342
doc-type: tutorial
exl-id: 52f90b9f-32ea-49c2-af5d-8742ca8b3b4e
---
# 3.3.6 Test your decision using the API

## 3.3.6.1 Work with the Offer Decisioning API using Postman

>[!IMPORTANT]
>
>If you're an Adobe employee, please follow the instructions here to use [PostBuster](./../../../../modules/getting-started/gettingstarted/ex8.md).

Download [this Postman Collection for Offer Decisioning](./../../../../assets/postman/postman_offer-decisioning.zip) to your desktop and unzip it. You'll then have this:

![OD API](./images/unzip.png)

You now have this file on your desktop:

- `_AJO- Decisioning Service.postman_collection.json`

In [Exercise 2.1.3 - Postman authentication to Adobe I/O](./../../../../modules/delivery-activation/rtcdp-b2c/rtcdpb2c-1/ex3.md) you installed Postman. You'll need to use Postman again for this exercise.

Open Postman and import the file `_AJO- Decisioning Service.postman_collection.json`. You'll then have this collection available in Postman.

![Adobe I/O New Integration](./images/postmanui.png)

You now have everything you need in Postman to start interacting with Adobe Experience Platform through the APIs.

Before you can use the below APIs, be sure to reauthenticate using the collection **Adobe IO - OAuth** which you configured in Exercise 2.1.3.

![Adobe I/O New Integration](./images/postmanui1.png)


### 3.3.6.2 Get Offers for Customer Profile

Click to open the request **POST - Get Offers for Customer Profile**. The first thing to update is the **Header** variable for **x-sandbox-name**. You should set it to `--aepSandboxName--`.

![OD API](./images/api23.png)

For this request, there are a number of fields that need to be updated. Go to **Body**.

- **xdm:placementId**
- **xdm:activityId** 
- **xdm:id** 
- **xdm:itemCount** (change it to a value of choice)

![OD API](./images/api24.png)

The field **xdm:activityId** needs to be filled out. You can retrieve that in the Adobe Experience Platform UI, as indicated below.

![OD API](./images/activityid.png)

The field **[!UICONTROL xdm:placementId]** needs to be filled out. You can retrieve that in the Adobe Experience Platform UI, as indicated below. In the below example, you can see the placementId for the placement **[!UICONTROL Web - Image]**.

![OD API](./images/placementid.png)

For the field **xdm:id**, enter the email address of the customer profile for whom you'd like to request an offer. Once all the values are set as desired, click **[!UICONTROL Send]**.

![OD API](./images/api24a.png)

Finally, you'll then see the result of what kind of personalized offer and what assets need to be displayed to this customer. In this example 2 items were requested, and as you can see, 2 personalized offers have been returned. 1 offer for Apple Watch and another offer for Galaxy Watch 7.

![OD API](./images/api25.png)

You've now completed this exercise.

## Next Steps

Go to [Summary and benefits](./summary.md){target="_blank"}

Go back to [Offer Decisioning](offer-decisioning.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
