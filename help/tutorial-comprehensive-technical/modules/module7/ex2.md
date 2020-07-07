---
title: Query Service - Using the Query Service
description: Query Service - Using the Query Service
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst, BI Expert
doc-type: tutorial
activity: 
---

# 7.2 Using the Query Service

## Objective

- Find and explore datasets
- Learn how to address Experience Data Models objects and attributes in your queries

## Context

In this you will learn how to use PSQL to retrieve information about the available datasets, how to write a queries for Experience Data Model (XDM), and write your first simple reporting queries using the Query Service and Luma Telco datasets.

## 7.2.1 Basic Queries

In this you will learn about the methods to retrieve information about the available datasets and how to properly retrieve data with a query from an XDM dataset.

All the datasets hat we have explored via Adobe Experience Platform in the beginning of 1, are also available for access via a SQL interface as tables. To list those tables you can use the **show tables;** command.

Execute **show tables;** in your **PSQL command-line interface**. (do not forget to end your command with a semicolon).

Copy the command **show tables;** and paste it at the **prod:all >** prompt:

![command-prompt-show-tables.png](./images/command-prompt-show-tables.png)

You will see the following result:

```text
prod:all=> show tables;
                   name                    |        dataSetId         |                  dataSet                  | description | resolved
-------------------------------------------+--------------------------+-------------------------------------------+-------------+----------
 aam_profile_dataset_userprofile           | 5e1d3d905f3bbe18a8ed1ca8 | AAM Devices Data                          |             | false
 aam_realtime                              | 5e1d3d8d93db9218a8f3a850 | AAM Realtime                              |             | false
 adobe_target_experience_events            | 5c8b1929bc73871516b71fdf | Adobe Target Experience Events            |             | false
 aep_demo_account_creation                 | 5ea04d5bfbb8fc18a99d8255 | AEP Demo - Account Creation               |             | false
 aep_demo_beacon_store_entry_activity      | 5ea04d5b47f95318a8203a87 | AEP Demo - Beacon Store Entry Activity    |             | false
 aep_demo_call_center_interactions         | 5ea04d5b20c37e18a8aeb17c | AEP Demo - Call Center Interactions       |             | false
 aep_demo_car_insurance_interactions       | 5ea04d5b0fe7df18a8b32790 | AEP Demo - Car Insurance Interactions     |             | false
 aep_demo_flight_booking_interactions      | 5ea04d5b5450d518a85f1e2e | AEP Demo - Flight Booking Interactions    |             | false
 aep_demo_fsi_interactions                 | 5ea04d5b20c37e18a8aeb17d | AEP Demo - FSI Interactions               |             | false
 aep_demo_loyalty_data                     | 5ea04d5b86d86f18a7a6eb2e | AEP Demo - Loyalty Data                   |             | false
 aep_demo_loyalty_data_m16                 | 5ea04d5be365ff18a86bede8 | AEP Demo - Loyalty Data (M16)             |             | false
 aep_demo_media_entertainment              | 5ea04d5b436b0b18a740bef9 | AEP Demo - Media & Entertainment          |             | false
 aep_demo_ml_predictions                   | 5ea04d5b85d1fc18a78a9136 | AEP Demo - ML Predictions                 |             | false
 aep_demo_mobile_app_interactions          | 5ea04d5ba99d6e18a83c59c3 | AEP Demo - Mobile App Interactions        |             | false
 aep_demo_optin_out                        | 5ea04d5b7c61c518a8eae22b | AEP Demo - OptIn/Out                      |             | false
 aep_demo_recommendations_input            | 5ea04d5b7f917418a8b7994c | AEP Demo - Recommendations Input          |             | false
 aep_demo_recommendations_output           | 5ea04d5b07f2c818a9716c64 | AEP Demo - Recommendations Output         |             | false
 aep_demo_website_interactions             | 5ea04d5b5c640f18a85a7b6b | AEP Demo - Website Interactions           |             | false
 aep_demo_website_registrations            | 5ea04d5b005a6e18a8bc88ae | AEP Demo - Website Registrations          |             | false
 cross_industry_demo_data_midvalues        | 5e1d3e7512aa2018a880bd66 | Cross-Industry Demo Data midValues        |             | false
 profile_export_for_destinations           | 5e1e4f61f48e2018a81a829e | Profile Export For Destinations           |             | false
:
```

At the colon, press space bar to see the next page of the resultset, or enter `q` to revert to the command prompt.

Every dataset in Platform has its corresponding Query Service table. You can find a dataset's table via the Datasets ui:

![ui-dataset-tablename.png](./images/ui-dataset-tablename.png)

The `aep_demo_website_interactions` table is the Query Service table that corresponds with the `AEP Demo - Website Interactions` dataset.

To query some information about where a product was viewed, we will select the **geo** information.

Copy the statement below and paste it at the **prod:all >** prompt in your **PSQL command-line interface** and hit enter:

```sql
select placecontext.geo
from   aep_demo_website_interactions
where  --aepTenantId--.productData.productInteraction = 'productView'
limit 1;
```

In your query result, you will notice that columns in the Experience Data Model (XDM) can be complex types and not just scalar types. In the query above we would like to identify geo locations where a **productView** did occur. To identify a **productView** we have to navigate through the XDM model using the **.** (dot) notation.

```text
prod:all=> select placecontext.geo
prod:all-> from   aep_demo_website_interactions
prod:all-> where  --aepTenantId--.productData.productInteraction = 'productView'
prod:all-> limit 1;
                 geo                 
-------------------------------------
 ("(50.4198861,4.9246444)",Namur,BE)
(1 row)
```

Notice the result is a flat object rather than a single value? The **placecontext.geo** object contains four attributes: schema, country and city. And when an object is declared as a column it will return the entire object as a string. The XDM schema may be more complex than what you are familiar with but it's very powerful and was architected to support many solutions, channels, and use cases.

To select the individual properties of an object, you use the **.** (dot) notation.

Copy the statement below and paste it at the **prod:all >** prompt in your **PSQL command-line interface**:

```sql
select placecontext.geo._schema.longitude
      ,placecontext.geo._schema.latitude
      ,placecontext.geo.city
      ,placecontext.geo.countryCode
from   aep_demo_website_interactions
where  --aepTenantId--.productData.productInteraction = 'productView'
limit 1;
```

The result of the above query should look like this.
The result is now a set simple values:

```text
prod:all=> select placecontext.geo._schema.longitude
prod:all->       ,placecontext.geo._schema.latitude
prod:all->       ,placecontext.geo.city
prod:all->       ,placecontext.geo.countryCode
prod:all-> from   aep_demo_website_interactions
prod:all-> where  --aepTenantId--.productData.productInteraction = 'productView'
prod:all-> limit 1;
 longitude |  latitude  | city  | countrycode 
-----------+------------+-------+-------------
 4.9246444 | 50.4198861 | Namur | BE
(1 row)
```

Don't worry, there is an easy way to obtain the path towards a specific property. In the following part you will learn how. 

You will need to edit a query, so let's first open an editor.

On Windows

Click the **search** icon in the windows toolbar, type **notepad** in the **search** field, click the **notepad** result:

![windows-start-notepad.png](./images/windows-start-notepad.png)

On Mac

Install [Brackets](https://github.com/adobe/brackets/releases/download/release-1.14/Brackets.Release.1.14.dmg) or use another Text Editor of choice if you don't have it installed and follow the instructions. After installation, search for **Brackets** via Mac's spotlight search and open it.

Copy the following statement to notepad or brackets:

```sql
select your_attribute_path_here
from   aep_demo_website_interactions
where  --aepTenantId--.productData.productInteraction = 'productView'
limit 1;
```

Go back to your Adobe Experience Platform UI (should be open in your browser) or navigate to [http://platform.adobe.com](http://platform.adobe.com).

Select **Schemas**, enter `AEP Demo - Website Interactions` in the **search** field and select `AEP Demo - Website Interactions Schema` from the list.

![browse-schema.png](./images/browse-schema.png)

Explore the XDM model for **POT4 Website Interaction Data (EE)**, by clicking on an object. Expand the tree for **placecontext**, **geo** and **schema**. When you select the actual attribute **longitude**, you will see the complete path in the highlighted red box. To copy the attribute's path, click on the copy path icon.

![explore-schema-for-path.png](./images/explore-schema-for-path.png)

Switch to your notepad/brackets and remove **your_attribute_path_here** from the first line. Position your cursor after **select** on the first line and paste (CTRL-V). 

Copy the modified statement from notepad/brackets and paste it at the **prod:all >** prompt in your **PSQL command-line interface** and hit enter.

The result should look like:

```text
prod:all=> select placeContext.geo._schema.longitude
prod:all-> from   aep_demo_website_interactions
prod:all-> where  --aepTenantId--.productData.productInteraction = 'productView'
prod:all-> limit 1;
 longitude
-----------
 4.9246444
(1 row)
```

Next Step: [7.3 - Queries, queries, queries...  and churn analysis](./ex3.md)

[Go Back to Module 7](./query-service.md)

[Go Back to All Modules](../../overview.md)
