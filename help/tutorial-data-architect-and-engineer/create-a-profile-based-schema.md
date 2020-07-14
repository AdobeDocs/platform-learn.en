---
title: Create a Profile-based Schema | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
description: 
feature: data ingestion
topics: 
kt: 4348
audience: data-architect,data-engineer
doc-type: tutorial
activity: implement
---

# Creating Schemas

## Intro to XDM

Explain Schemas, Mixins, Fields, and Datatypes

Data Type
Mixin
Schema

## Luma's goals

## Exercise: Create Luma Loyalty Members schema

Schemas 
* Luma Loyalty Members (UI)
  * Profile Person Details
  * Profile Personal Details
  * Custom Luma Loyalty Mixin
    * loyaltyId primary Id from data type
    * level
    * points
    * memberSince
  * Create Identity data type
* Luma CRM (API)
* Luma Web Events (UI)
  * AEP Web SDK Mixin
  * Commerce Mixin
* Luma Offline Purchases (API)
* Create Class
* Luma Products
* Relationship schema


# Create a Profile-based Schema

In this tutorial we will be ingesting data from the following sources:

Abhishek
* Schema: Luma Loyalty Members
  * Profile Personal Details
  * Profile Person Details
  * Custom Mixin
    * loyalty object
    * loyaltyId
    * joiningDate
    * points
    * loyaltyLevel
* Data Type - Luma Product Item
  * productSKU
  * productName
  * productPrice
  * quantityPurchased
  * productTotal
  * productSize
* Mixin with API-- Luma Identities
* Schema: Luma Offline Purchase Event
  * Luma Identities
  * Luma Product Purchase Event Mixin
    * purchase_event
    * receipt_number
    * receipt_date
    * products (uses Luma Product Item data type)
    * receipt_total
* Schema with Custom Class: 
  * Schema: Luma Product Catalog
  * Custom Class: Luma Product Class
  * productName
  * productCategory
  * productColor
  * productSku
  * productSize
* Schema with API
  * CRM Schema
    * Luma Identities Mixin
    * Profile Personal Details
    * Profile Person Details
    * Profile Preferences Details
    * 

DMA
* CRM Schema
  * Profile work details
  * Profile person details
  * Profile personal details
  * Custom Identity Mixin
    * crmid
    * declaredId
    * emailId
    * phoneNbr
* Loyalty Schema
  * Custom Identity Mixin
    * add loyaltyId
  * Custom Loyalty Mixin
    * lifeTimeValue
    * loyaltyExpDate
    * loyaltyPoints
    * loyaltyStatus
* Offline Purchase Schema
  * SKU
  * Product Name
  * Price
  * Quantity
  * priceTotal
  * currencyCode
  * loyaltyId
  * receipt_nbr
  * Order Date
  * timestamp

* Website
* CRM system
* Loyalty system
* Offline purchases

We'll be starting with the CRM schema because we can build it quickly using a few standard mixins. For Luma, the fields they want to onboard into Platform from their own CRM system are:
Id
crmId
person_first_name
person_last_name
birthdate
gender
work_country
work_countryCode
work_postalCode
work_Street
work_email
home_address_city
home_address_country
home_address_country_code
home_address_country_street
home_address_country_label
home_address_country_state
home_phone
mobile_phone
personalEmail
As you go through these steps, see if you can determine which CRM fields match to which XDM fields.

