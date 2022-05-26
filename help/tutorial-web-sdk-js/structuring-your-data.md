---
title: Structuring your data
description: Structuring your data
---
# Structuring your data

Businesses have their own language for communicating about their domain. Car dealerships deal with makes, models, and cylinders. Airlines deal with flight numbers, class of service, and seating assignments. Some of these terms are unique to a specific company, some are shared amongst an industry vertical, and some are shared by almost all businesses. For terms that are shared amongst an industry vertical or even broader, you can start doing powerful things with your data when you name and structure these terms in a common way.

For example, many businesses deal with orders. What if collectively these businesses decided to model an order in a similar way. For example, what if the data model consisted of an object with a `priceTotal` property that represented the total price of the order. What if that object also had properties named `currencyCode` and `purchaseOrderNumber`. Maybe the order object contains a property named `payments` that would be an array of payment objects. Each object would represent a payment for the order. For example, perhaps a customer paid for part of the order with a gift card and paid for the rest using a credit card. You can start to construct a model that looks something like this:

```json
{
  "order": {
    "priceTotal": 89.50,
    "currencyCode": "EUR",
    "purchaseOrderNumber": "JWN20192388410012",
    "payments": [
      {
        "paymentType": "gift_card",
        "paymentAmount": 50
      },
      {
        "paymentType": "credit_card",
        "paymentAmount": 39.50
      }
    ]
  }
}
```

If all businesses dealing with orders decided to model their order data in a consistent way for terms that are common in the industry, magical things could start to happen. Information could more fluidly be exchanged inside and outside your organization instead of constantly interpreting and translating the data (props and evars, anyone?). Machine learning could more easily understand what your data _means_ and provide actionable insights. User interfaces for surfacing relevant data could become more intuitive. Your data could be seamlessly integrated with partners and vendors who are following the same modeling.

## XDM

This is the goal of Adobe's [Experience Data Model](https://business.adobe.com/products/experience-platform/experience-data-model.html). XDM provides prescriptive modeling for data that is common in the industry, while also allowing you to extend the model for your specific needs. Adobe Experience Platform is built around XDM and, as such, data sent into Experience Platform will need to be in XDM. Rather than thinking about where and how you can transform your current data models into XDM before sending the data to Experience Platform, consider more pervasively adopting XDM across your organization so that translation will rarely need to occur.
