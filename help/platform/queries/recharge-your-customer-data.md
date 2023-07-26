---
title: Recharge your customer data to deliver electrifying experiences
description: Learn how to mitigate the impact of low-quality data, reduce time to value, and multiply ROI by using the same data for multitude of use cases.
feature: Queries
role: Data Engineer, Data Architect, Developer
level: Beginner
jira: KT-10323
thumbnail: 342533.jpeg
exl-id: 30574cc5-66fa-4ab8-83ed-7af710294dbf
---
# Recharge your customer data to deliver electrifying experiences

Omnichannel data is a critical ingredient to power actionable customer profiles used by marketers to orchestrate activation and measure the resulting customer journeys. However, organizations face challenges in managing the quality, scale, and variety of this data. They require streamlined solutions to mitigate the impact of low-quality data, reduce time to value, and multiply ROI by using the same data for multitude of use cases.

This video explores:

* Adobe Experience Platform data preparation capabilities that you can leverage
* Increasing ROI from Adobe Real-Time CDP, Adobe Journey Optimizer, and Customer Journey Analytics

>[!VIDEO](https://video.tv.adobe.com/v/342533?quality=12&learn=on)

## SQL example

``` sql
INSERT INTO summit_adv_data_prep_dataset
SELECT STRUCT(
customerId AS crmCustomerId, struct(sku AS sku, price AS sku_price, abandonTS AS abandonTS) AS abandonBrowse) AS _pfreportingonprod
FROM
(SELECT
B.personKey.sourceID AS customerId,
A.productListItems[0].SKU AS sku,
max(A.timestamp) AS abandonTS,
max(C._pfreportingonprod.price) AS price
FROM summit_adobe_analytics_dataset A,profile_attribute_14adf268_2a20_4dee_bee6_a6b0e34616a9 B,summit_product_dataset C
WHERE A._experience.analytics.customDimensions.eVars.eVar1 = B.personKey.sourceID
AND A.productListItems[0].sku = C._pfreportingonprod.sku
AND A.web.webpagedetails.URL NOT LIKE '%orderconfirmation%'
AND timestamp > current_date - interval '4 day'
GROUP BY customerId,sku
order by price desc)D;
```

For  more information, please visit the [Query Service documentation](https://experienceleague.adobe.com/docs/experience-platform/query/home.html).

>[!NOTE]
>
>This video is an excerpt from the Adobe Summit 2020 session *[Recharging Omnichannel Data for Electrifying Experiences](https://business.adobe.com/summit/2022/sessions/recharging-omnichannel-data-for-electrifying-exper-s409.html)*.
