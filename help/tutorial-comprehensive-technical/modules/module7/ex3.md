---
title: Query Service - Queries, queries, queries...  and churn analysis
description: Query Service - Queries, queries, queries...  and churn analysis
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst, BI Expert
doc-type: tutorial
activity: develop
exl-id: 6f05f54d-390b-4b42-9b79-be6f5d686b5a
---
# 7.3 Queries, queries, queries...  and churn analysis

## Objective

* Write queries for data analyses
* Write SQL queries combining online, call center and loyalty data available in Adobe Experience Platform
* Learn about Adobe Defined Functions

## Context

In this exercises you will write queries to analyze product views, product funnels, churn etc.

All queries listed in this chapter will be executed in your **PSQL command-line interface**. You should copy (CTRL-c) the statement blocks indicated with **SQL** and paste (CTRL-v)them in the **PSQL command-line interface**. The **Query Result** blocks show the pasted SQL statement and the associated query result.

## 7.3.1 Write basic queries for data analysis

### Timestamp

Data captured in Adobe Experience Platform is time stamped. The **timestamp** attribute allows you to analyze data over time.

How many product views do we have on a daily basis? 

**SQL**

```sql
select date_format( timestamp , 'yyyy-MM-dd') AS Day,
       count(*) AS productViews
from   aep_demo_website_interactions
where  --aepTenantId--.brand.brandName IN ('Luma Telco', 'Citi Signal')
and    --aepTenantId--.productData.productInteraction = 'productView'
group by Day
limit 10;
```

Copy the statement above and execute it in your **PSQL command-line interface**.

**Query Result**

```text
module7:all=> select date_format( timestamp , 'yyyy-MM-dd') AS Day,
module7:all->        count(*) AS productViews
module7:all-> from   aep_demo_website_interactions
module7:all-> where  --aepTenantId--.brand.brandName IN ('Luma Telco', 'Citi Signal')
module7:all-> and    --aepTenantId--.productData.productInteraction = 'productView'
module7:all-> group by Day
module7:all-> limit 10;
    Day     | productViews 
------------+--------------
 2020-04-20 |         2138
(1 row)
```

### Top 5 products viewed

What are the top 5 products viewed?

#### SQL

```sql
select --aepTenantId--.productData.productName, count(*)
from   aep_demo_website_interactions
where  --aepTenantId--.brand.brandName IN ('Luma Telco', 'Citi Signal')
and    --aepTenantId--.productData.productInteraction = 'productView'
group  by --aepTenantId--.productData.productName
order  by 2 desc
limit 5;
```

Copy the statement above and execute it in your **PSQL command-line interface**.

**Query Result**

```text
module7:all=> select --aepTenantId--.productData.productName, count(*)
module7:all-> from   aep_demo_website_interactions
module7:all-> where  --aepTenantId--.brand.brandName IN ('Luma Telco', 'Citi Signal')
module7:all-> and    --aepTenantId--.productData.productInteraction = 'productView'
module7:all-> group  by --aepTenantId--.productData.productName
module7:all-> order  by 2 desc
module7:all-> limit 5;
              productname              | count(1)
---------------------------------------+----------
 Google Pixel XL 32GB Black Smartphone |      838
 Samsung Galaxy S8                     |      456
 Samsung Galaxy S7 32GB Black          |      431
 SIM Only                              |      413
(4 rows)
```

### Product Interaction funnel, from viewing to buying

**SQL**

```sql
select --aepTenantId--.productData.productInteraction, count(*)
from   aep_demo_website_interactions
where  --aepTenantId--.brand.brandName IN ('Luma Telco', 'Citi Signal')
and    --aepTenantId--.productData.productInteraction is not null
and    --aepTenantId--.productData.productInteraction <> ''
group  by --aepTenantId--.productData.productInteraction;
```

Copy the statement above and execute it in your **PSQL command-line interface**.

**Query Result**

```text
module7:all=> select --aepTenantId--.productData.productInteraction, count(*)
module7:all-> from   aep_demo_website_interactions
module7:all-> where  --aepTenantId--.brand.brandName IN ('Luma Telco', 'Citi Signal')
module7:all-> and    --aepTenantId--.productData.productInteraction is not null
module7:all-> group  by --aepTenantId--.productData.productInteraction;
 productinteraction | count(1) 
--------------------+----------
 productView        |     2138
 productAddToCart   |      262
 productPurchase    |      506
(3 rows)
```

### Identify visitors with risk to Churn (visit page => Cancel Service)

**SQL**

```sql
select distinct --aepTenantId--.identification.ecid
from   aep_demo_website_interactions
where  --aepTenantId--.brand.brandName IN ('Luma Telco', 'Citi Signal')
and    web.webPageDetails.name = 'Cancel Service'
group  by --aepTenantId--.identification.ecid
limit 10;
```

Copy the statement above and execute it in your **PSQL command-line interface**.

**Query Result**

```text
module7:all=> select distinct --aepTenantId--.identification.ecid
module7:all-> from   aep_demo_website_interactions
module7:all-> where  --aepTenantId--.brand.brandName IN ('Luma Telco', 'Citi Signal')
module7:all-> and    web.webPageDetails.name = 'Cancel Service'
module7:all-> group  by --aepTenantId--.identification.ecid
module7:all-> limit 10;
               ecid               
----------------------------------
 93575149630203476634619363680088
 16761464641996441029061082282035
 23358297324246635890277155477598
 18489066043732494167359682769116
 44274389221416021082013783816917
 41719542101354167295677853076691
 24723468609932276115055785872822
 35829005708305278814582267427556
 44190333154814000913344976333301
 49093808822916497953751096412772
(10 rows)
```

In the next set of queries we will extend the above query, in order to get a complete view on the customers and their behavior that have been visiting the "Cancel Service" page. You will learn how to use the Adobe Defined Function to sessionize information, identify the sequence and timing of events. You will also join datasets together to further enrich and prepare the data for analysis in Microsoft Power BI.

## 7.3.2 Advanced Queries

The majority of the business logic requires gathering the touch-points for a customer and ordering them by time. This support is provided by Spark SQL in the form of window functions. Window functions are part of standard SQL and are supported by many other SQL engines.

### Adobe Defined Functions

Adobe has added a set of **Adobe Defined Functions** to the standard SQL syntax that allow you to better understand your experience data. In the next couple of queries you will learn about these ADF functions. You can find more information and the complete list [in the documentation](https://experienceleague.adobe.com/docs/experience-platform/query/sql/adobe-defined-functions.html).

### What do people do on the site before reaching the "Cancel Service" page as the 3rd page in a session?

With this query you will discover the first two Adobe Defined Functions **SESS_TIMEOUT** and **NEXT**

> The **SESS_TIMEOUT()** reproduces the visit groupings found with Adobe Analytics. It performs a similar time-based grouping, but customizable parameters.
>
> **NEXT()** and **PREVIOUS()** help you to understand how customers navigate your site.

**SQL**

```sql
SELECT
  webPage,
  webPage_2,
  webPage_3,
  webPage_4,
  count(*) journeys
FROM
  (
      SELECT
        webPage,
        NEXT(webPage, 1, true)
          OVER(PARTITION BY ecid, session.num
                ORDER BY timestamp
                ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING).value
          AS webPage_2,
        NEXT(webPage, 2, true)
          OVER(PARTITION BY ecid, session.num
                ORDER BY timestamp
                ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING).value
          AS webPage_3,
        NEXT(webPage, 3, true)
           OVER(PARTITION BY ecid, session.num
                ORDER BY timestamp
                ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING).value
          AS webPage_4,
        session.depth AS SessionPageDepth
      FROM (
            select a.--aepTenantId--.identification.ecid as ecid,
                   a.timestamp,
                   web.webPageDetails.name as webPage,
                    SESS_TIMEOUT(timestamp, 60 * 30) 
                       OVER (PARTITION BY a.--aepTenantId--.identification.ecid 
                             ORDER BY timestamp 
                             ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) 
                  AS session
            from   aep_demo_website_interactions a
            where  a.--aepTenantId--.identification.ecid in ( 
                select b.--aepTenantId--.identification.ecid
                from   aep_demo_website_interactions b
                where  b.--aepTenantId--.brand.brandName IN ('Luma Telco', 'Citi Signal')
                and    b.web.webPageDetails.name = 'Cancel Service'
            )
        )
)
WHERE SessionPageDepth=1
and   webpage_3 = 'Cancel Service'
GROUP BY webPage, webPage_2, webPage_3, webPage_4
ORDER BY journeys DESC
LIMIT 10;
```

Copy the statement above and execute it in your **PSQL command-line interface**.

**Query Result**

```text
                webPage                |               webPage_2               |   webPage_3    | webPage_4  | journeys 
---------------------------------------+---------------------------------------+----------------+------------+----------
 Telco Home                            | TV & Broadband Deals                  | Cancel Service | Call Start |        4
 Google Pixel XL 32GB Black Smartphone | Samsung Galaxy S8                     | Cancel Service | Call Start |        3
 TV & Broadband Deals                  | Google Pixel XL 32GB Black Smartphone | Cancel Service | Call Start |        2
 Samsung Galaxy S7 32GB Black          | Google Pixel XL 32GB Black Smartphone | Cancel Service | Call Start |        2
 Google Pixel XL 32GB Black Smartphone | Google Pixel XL 32GB Black Smartphone | Cancel Service |            |        2
 Google Pixel XL 32GB Black Smartphone | Broadband Deals                       | Cancel Service | Call Start |        2
 Telco Home                            | Citi Signal Sport                      | Cancel Service |            |        2
 Google Pixel XL 32GB Black Smartphone | Broadband Deals                       | Cancel Service |            |        1
 Google Pixel XL 32GB Black Smartphone | Citi Signal Sport                      | Cancel Service | Call Start |        1
 Google Pixel XL 32GB Black Smartphone | Citi Signal Shop                       | Cancel Service |            |        1
(10 rows)
```

### How much time do we have before a visitor calls the call center after visiting the "Cancel Service" Page?

To answer this kind of query will we use the **TIME_BETWEEN_NEXT_MATCH()** Adobe Defined Function.

> Time-between previous or next match functions provide a new dimension, which measures the time that has elapsed since a particular incident.

**SQL**

```sql
select * from (
       select --aepTenantId--.identification.ecid as ecid,
              web.webPageDetails.name as webPage,
              TIME_BETWEEN_NEXT_MATCH(timestamp, web.webPageDetails.name='Call Start', 'seconds')
              OVER(PARTITION BY --aepTenantId--.identification.ecid
                  ORDER BY timestamp
                  ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING)
              AS contact_callcenter_after_seconds
       from   aep_demo_website_interactions
       where  --aepTenantId--.brand.brandName IN ('Luma Telco', 'Citi Signal')
       and    web.webPageDetails.name in ('Cancel Service', 'Call Start')
) r
where r.webPage = 'Cancel Service'
limit 15;
```

Copy the statement above and execute it in your **PSQL command-line interface**.

**Query Result**

```text
               ecid               |    webPage     | contact_callcenter_after_seconds 
----------------------------------+----------------+----------------------------------
 16761464641996441029061082282035 | Cancel Service |                             -199
 93575149630203476634619363680088 | Cancel Service |                             -745
 23358297324246635890277155477598 | Cancel Service |                              -34
 18489066043732494167359682769116 | Cancel Service |                                 
 44274389221416021082013783816917 | Cancel Service |                                 
 41719542101354167295677853076691 | Cancel Service |                                 
 24723468609932276115055785872822 | Cancel Service |                                 
 35829005708305278814582267427556 | Cancel Service |                             -550
 44190333154814000913344976333301 | Cancel Service |                              -63
 49093808822916497953751096412772 | Cancel Service |                             -130
 98370517719603434123172269831130 | Cancel Service |                                 
 31436015569607325592734977406945 | Cancel Service |                             -359
 10372274867563903933405478991002 | Cancel Service |                                 
 21847925317814042696901094422064 | Cancel Service |                                 
 67170357691539269238490319628276 | Cancel Service |                                 
(15 rows)
```

### And what is the outcome of that contact?

Explain that we are joining datasets together, in this case we join our `aep_demo_website_interactions` with `aep_demo_call_center_interactions`. We do this to know the outcome of the call center interaction.

**SQL**

```sql
select distinct r.*,
       c.--aepTenantId--.callDetails.callFeeling,
       c.--aepTenantId--.callDetails.callTopic,
       c.--aepTenantId--.callDetails.contractCancelled
from (
       select --aepTenantId--.identification.ecid ecid,
              web.webPageDetails.name as webPage,
              TIME_BETWEEN_NEXT_MATCH(timestamp, web.webPageDetails.name='Call Start', 'seconds')
              OVER(PARTITION BY --aepTenantId--.identification.ecid
                  ORDER BY timestamp
                  ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING)
              AS contact_callcenter_after_seconds
       from   aep_demo_website_interactions
       where  --aepTenantId--.brand.brandName IN ('Luma Telco', 'Citi Signal')
       and    web.webPageDetails.name in ('Cancel Service', 'Call Start')
) r
, aep_demo_call_center_interactions c
where r.ecid = c.--aepTenantId--.identification.ecid
and r.webPage = 'Cancel Service'
limit 15;
```

Copy the statement above and execute it in your **PSQL command-line interface**.

**Query Result**

```text
               ecid               |    webPage     | contact_ call center_after_seconds | callfeeling | calltopic | contractcancelled 
----------------------------------+----------------+----------------------------------+-------------+-----------+-------------------
 16761464641996441029061082282035 | Cancel Service |                             -199 | negative    | contract  | no
 93575149630203476634619363680088 | Cancel Service |                             -745 | negative    | contract  | no
 23358297324246635890277155477598 | Cancel Service |                              -34 | neutral     | contract  | yes
 18489066043732494167359682769116 | Cancel Service |                                  | none        | none      | no
 44274389221416021082013783816917 | Cancel Service |                                  | none        | none      | no
 41719542101354167295677853076691 | Cancel Service |                                  | none        | none      | no
 24723468609932276115055785872822 | Cancel Service |                                  | none        | none      | no
 35829005708305278814582267427556 | Cancel Service |                             -550 | neutral     | contract  | yes
 44190333154814000913344976333301 | Cancel Service |                              -63 | neutral     | contract  | no
 49093808822916497953751096412772 | Cancel Service |                             -130 | positive    | contract  | yes
 98370517719603434123172269831130 | Cancel Service |                                  | none        | none      | no
 31436015569607325592734977406945 | Cancel Service |                             -359 | neutral     | contract  | no
 10372274867563903933405478991002 | Cancel Service |                                  | none        | none      | no
 21847925317814042696901094422064 | Cancel Service |                                  | none        | none      | no
 67170357691539269238490319628276 | Cancel Service |                                  | none        | none      | no
(15 rows)
```

### What is the loyalty profile of these customers?

In this query we join loyalty data that we have onboarded in Adobe Experience Platform. This allows to enrich the churn analysis with loyalty data.

**SQL**

```sql
select r.*,
       c.--aepTenantId--.callDetails.callFeeling,
       c.--aepTenantId--.callDetails.callTopic,
       l.--aepTenantId--.loyalty.loyaltyStatus,
       l.--aepTenantId--.identification.crmid
from (
       select --aepTenantId--.identification.ecid ecid,
              web.webPageDetails.name as webPage,
              TIME_BETWEEN_NEXT_MATCH(timestamp, web.webPageDetails.name='Call Start', 'seconds')
              OVER(PARTITION BY --aepTenantId--.identification.ecid
                  ORDER BY timestamp
                  ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING)
              AS contact_callcenter_after_seconds
       from   aep_demo_website_interactions
       where  --aepTenantId--.brand.brandName IN ('Luma Telco', 'Citi Signal')
       and    web.webPageDetails.name in ('Cancel Service', 'Call Start')
) r
, aep_demo_call_center_interactions c
, aep_demo_loyalty_data l
where r.ecid = c.--aepTenantId--.identification.ecid
and r.webPage = 'Cancel Service'
and l.--aepTenantId--.identification.ecid = r.ecid
limit 15;
```

Copy the statement above and execute it in your **PSQL command-line interface**.

**Query Result**

```text
               ecid               |    webPage     | contact_callcenter_after_seconds | callfeeling | calltopic | loyaltystatus |   crmid   
----------------------------------+----------------+----------------------------------+-------------+-----------+---------------+-----------
 16761464641996441029061082282035 | Cancel Service |                             -199 | negative    | contract  | Bronze        | 677195942
 93575149630203476634619363680088 | Cancel Service |                             -745 | negative    | contract  | Gold          | 482673001
 23358297324246635890277155477598 | Cancel Service |                              -34 | neutral     | contract  | Gold          | 235826127
 18489066043732494167359682769116 | Cancel Service |                                  | none        | none      | Bronze        | 572510210
 44274389221416021082013783816917 | Cancel Service |                                  | none        | none      | Bronze        | 642110733
 41719542101354167295677853076691 | Cancel Service |                                  | none        | none      | Bronze        | 024195749
 24723468609932276115055785872822 | Cancel Service |                                  | none        | none      | Bronze        | 751092928
 35829005708305278814582267427556 | Cancel Service |                             -550 | neutral     | contract  | Gold          | 654415596
 44190333154814000913344976333301 | Cancel Service |                              -63 | neutral     | contract  | Gold          | 929560238
 49093808822916497953751096412772 | Cancel Service |                             -130 | positive    | contract  | Silver        | 907661997
 98370517719603434123172269831130 | Cancel Service |                                  | none        | none      | Bronze        | 256000335
 31436015569607325592734977406945 | Cancel Service |                             -359 | neutral     | contract  | Gold          | 929573407
 10372274867563903933405478991002 | Cancel Service |                                  | none        | none      | Gold          | 179650113
 21847925317814042696901094422064 | Cancel Service |                                  | none        | none      | Bronze        | 535538788
 67170357691539269238490319628276 | Cancel Service |                                  | none        | none      | Bronze        | 773572750
(15 rows)
```

### From what region do they visit us?

Lets include the geographical info, like longitude, attitude, city, countrycode, captured by the Adobe Experience Platform in order to get some geographical insights about churning customers.

**SQL**

```sql
       select r.ecid,
              r.city,
              r.countrycode,
              r.lat as latitude,
              r.lon as longitude,
              r.contact_callcenter_after_seconds as seconds_to_contact_callcenter,
              c.--aepTenantId--.callDetails.callFeeling,
              c.--aepTenantId--.callDetails.callTopic,
              c.--aepTenantId--.callDetails.contractCancelled,
              l.--aepTenantId--.loyalty.loyaltyStatus,
              l.--aepTenantId--.identification.crmid
       from (
              select --aepTenantId--.identification.ecid ecid,
                     placeContext.geo._schema.latitude lat,
                     placeContext.geo._schema.longitude lon,
                     placeContext.geo.city,
                     placeContext.geo.countryCode,
                     web.webPageDetails.name as webPage,
                     TIME_BETWEEN_NEXT_MATCH(timestamp, web.webPageDetails.name='Call Start', 'seconds')
                     OVER(PARTITION BY --aepTenantId--.identification.ecid
                         ORDER BY timestamp
                         ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING)
                     AS contact_callcenter_after_seconds
              from   aep_demo_website_interactions
              where  --aepTenantId--.brand.brandName IN ('Luma Telco', 'Citi Signal')
              and    web.webPageDetails.name in ('Cancel Service', 'Call Start')
       ) r
       , aep_demo_call_center_interactions c
       , aep_demo_loyalty_data l
       where r.ecid = c.--aepTenantId--.identification.ecid
       and r.webPage = 'Cancel Service'
       and l.--aepTenantId--.identification.ecid = r.ecid
       limit 15;
```

Copy the statement above and execute it in your **PSQL command-line interface**.

**Query Result**

```text
               ecid               |   city    | countrycode |  latitude  | longitude | seconds_to_contact_callcenter | callfeeling | calltopic | contractcancelled | loyaltystatus |   crmid   
----------------------------------+-----------+-------------+------------+-----------+-------------------------------+-------------+-----------+-------------------+---------------+-----------
 16761464641996441029061082282035 | Ath       | BE          | 50.6302806 | 3.8861843 |                          -199 | negative    | contract  | no                | Bronze        | 677195942
 93575149630203476634619363680088 | Momignies | BE          | 50.0109884 | 4.1638985 |                          -745 | negative    | contract  | no                | Gold          | 482673001
 23358297324246635890277155477598 | Bruxelles | BE          | 50.7881573 | 4.4180065 |                           -34 | neutral     | contract  | yes               | Gold          | 235826127
 18489066043732494167359682769116 | Ath       | BE          | 50.6302806 | 3.8861843 |                               | none        | none      | no                | Bronze        | 572510210
 44274389221416021082013783816917 | Bruxelles | BE          | 50.7881573 | 4.4180065 |                               | none        | none      | no                | Bronze        | 642110733
 41719542101354167295677853076691 | Ath       | BE          | 50.6302806 | 3.8861843 |                               | none        | none      | no                | Bronze        | 024195749
 24723468609932276115055785872822 | Antwerpen | BE          | 51.2472392 | 4.4403455 |                               | none        | none      | no                | Bronze        | 751092928
 35829005708305278814582267427556 | Mons      | BE          | 50.4271996 |  3.989666 |                          -550 | neutral     | contract  | yes               | Gold          | 654415596
 44190333154814000913344976333301 | Namur     | BE          | 50.4198861 | 4.9246444 |                           -63 | neutral     | contract  | no                | Gold          | 929560238
 49093808822916497953751096412772 | Antwerpen | BE          | 51.2472392 | 4.4403455 |                          -130 | positive    | contract  | yes               | Silver        | 907661997
 98370517719603434123172269831130 | Charleroi | BE          | 50.4315612 | 4.4472854 |                               | none        | none      | no                | Bronze        | 256000335

```

## Call Center Interaction Analysis

In the queries above we only looked at the visitors that ended up contacting the call center in case of service cancellation. We want to take this a bit broader and take into account all call center interaction including (wifi, promo, invoice, complaint and contract).  

You will need to edit a query, so let's first open notepad or brackets.

On Windows click "search"-icon (1) in the windows toolbar, type **notepad** in the "search"-field (2), click (3) the "notepad" result:

![windows-start-notepad.png](./images/windows-start-notepad.png)

On Mac

![osx-start-brackets.png](./images/osx-start-brackets.png)

Copy the following statement to notepad/brackets:

```sql
select /* enter your name */
       e.--aepTenantId--.identification.ecid as ecid,
       e.placeContext.geo.city as city,
       e.placeContext.geo._schema.latitude latitude,
       e.placeContext.geo._schema.longitude longitude,
       e.placeContext.geo.countryCode as countrycode,
       c.--aepTenantId--.callDetails.callFeeling as callFeeling,
       c.--aepTenantId--.callDetails.callTopic as callTopic,
       c.--aepTenantId--.callDetails.contractCancelled as contractCancelled,
       l.--aepTenantId--.loyalty.loyaltyStatus as loyaltystatus,
       l.--aepTenantId--.loyalty.loyaltyPoints as loyaltypoints,
       l.--aepTenantId--.identification.crmid as crmid
from   aep_demo_website_interactions e
      ,aep_demo_call_center_interactions c
      ,aep_demo_loyalty_data l
where  e.--aepTenantId--.brand.brandName IN ('Luma Telco', 'Citi Signal')
and    e.web.webPageDetails.name in ('Cancel Service', 'Call Start')
and    e.--aepTenantId--.identification.ecid = c.--aepTenantId--.identification.ecid
and    l.--aepTenantId--.identification.ecid = e.--aepTenantId--.identification.ecid;
```

And replace 

```text
enter your name
```

Do not remove `/\*` and `\*/`. Your modified statement in notepad should look like:

![edit-query-notepad.png](./images/edit-query-notepad.png)

Copy your modified statement from **notepad** into the **PSQL command line window** and hit enter. You should see the following result in the PSQL command line window:

```text
module7:all=> select /* vangeluw */
module7:all->        e.--aepTenantId--.identification.ecid as ecid,
module7:all->        e.placeContext.geo.city as city,
module7:all->        e.placeContext.geo._schema.latitude latitude,
module7:all->        e.placeContext.geo._schema.longitude longitude,
module7:all->        e.placeContext.geo.countryCode as countrycode,
module7:all->        c.--aepTenantId--.callDetails.callFeeling as callFeeling,
module7:all->        c.--aepTenantId--.callDetails.callTopic as callTopic,
module7:all->        c.--aepTenantId--.callDetails.contractCancelled as contractCancelled,
module7:all->        l.--aepTenantId--.loyalty.loyaltyStatus as loyaltystatus,
module7:all->        l.--aepTenantId--.loyalty.loyaltyPoints as loyaltypoints,
module7:all->        l.--aepTenantId--.identification.crmid as crmid
module7:all-> from   aep_demo_website_interactions e
module7:all->       ,aep_demo_call_center_interactions c
module7:all->       ,aep_demo_loyalty_data l
module7:all-> where  e.--aepTenantId--.brand.brandName IN ('Luma Telco', 'Citi Signal')
module7:all-> and    e.web.webPageDetails.name in ('Cancel Service', 'Call Start')
module7:all-> and    e.--aepTenantId--.identification.ecid = c.--aepTenantId--.identification.ecid
module7:all-> and    l.--aepTenantId--.identification.ecid = e.--aepTenantId--.identification.ecid;
               ecid               |   city    |  latitude  | longitude | countrycode | callFeeling | callTopic | contractCancelled | loyaltystatus | loyaltypoints |   crmid   
----------------------------------+-----------+------------+-----------+-------------+-------------+-----------+-------------------+---------------+---------------+-----------
 49087868469032502526716380562417 | Namur     | 50.4198861 | 4.9246444 | BE          | neutral     | contract  | no                | Bronze        |         413.0 | 475749237
 87651063498084356835271211895835 | Bouillon  | 49.8417042 | 5.1214901 | BE          | positive    | contract  | yes               | Bronze        |         865.0 | 512065611
 87651063498084356835271211895835 | Bouillon  | 49.8417042 | 5.1214901 | BE          | positive    | contract  | yes               | Bronze        |         865.0 | 512065611
 76140226992684181838626022667165 | Charleroi | 50.4315612 | 4.4472854 | BE          | none        | none      | no                | Gold          |         505.0 | 249612312
 86156638208701051669153370559814 | Mons      | 50.4271996 |  3.989666 | BE          | none        | none      | no                | Gold          |         912.0 | 513158784
 03088687764152132537341567008527 | Bruxelles | 50.7881573 | 4.4180065 | BE          | positive    | contract  | yes               | Silver        |         550.0 | 383044165
 03088687764152132537341567008527 | Bruxelles | 50.7881573 | 4.4180065 | BE          | positive    | contract  | yes               | Silver        |         550.0 | 383044165
 59575112158310530775742124914957 | Ath       | 50.6302806 | 3.8861843 | BE          | positive    | contract  | yes               | Bronze        |         692.0 | 505149979
 59575112158310530775742124914957 | Ath       | 50.6302806 | 3.8861843 | BE          | positive    | contract  | yes               | Bronze        |         692.0 | 505149979
 98475273464040330810135321898542 | Gent      | 51.0003903 | 3.7139045 | BE          | neutral     | invoice   | no                | Gold          |         360.0 | 663679501
 88215105592148903586325561022208 | Ath       | 50.6302806 | 3.8861843 | BE          | none        | none      | no                | Gold          |          23.0 | 904361935
 44274389221416021082013783816917 | Bruxelles | 50.7881573 | 4.4180065 | BE          | none        | none      | no                | Bronze        |         460.0 | 642110733
 58711172636230293859653630118156 | Péruwelz  | 50.5474037 | 3.5567339 | BE          | none        | none      | no                | Bronze        |          76.0 | 585019143
 86333712479643379743248506674701 | Péruwelz  | 50.5474037 | 3.5567339 | BE          | negative    | contract  | no                | Silver        |         109.0 | 098670925
 86333712479643379743248506674701 | Péruwelz  | 50.5474037 | 3.5567339 | BE          | negative    | contract  | no                | Silver        |         109.0 | 098670925
 02118089160196275228181685121155 | Bruxelles | 50.8235717 | 4.3766927 | BE          | neutral     | contract  | yes               | Bronze        |         160.0 | 687540423
 02118089160196275228181685121155 | Bruxelles | 50.8235717 | 4.3766927 | BE          | neutral     | contract  | yes               | Bronze        |         160.0 | 687540423
 28708968043311272698861112077433 | Antwerpen | 51.2472392 | 4.4403455 | BE          | neutral     | wifi      | no                | Bronze        |         675.0 | 969112374
 97639077126350781312522721809627 | Antwerpen | 51.2472392 | 4.4403455 | BE          | none        | none      | no                | Bronze        |         665.0 | 513481309
 89628353861135270637685259116315 | Bruxelles | 50.8235717 | 4.3766927 | BE          | none        | none      | no                | Bronze        |         963.0 | 642076729
 13323897771642101619467458209454 | Péruwelz  | 50.5474037 | 3.5567339 | BE          | positive    | promo     | no                | Silver        |         984.0 | 043844508
 21257785085666488624247959294728 | Mons      | 50.4271996 |  3.989666 | BE          | positive    | contract  | no                | Bronze        |         337.0 | 210926597
 21257785085666488624247959294728 | Mons      | 50.4271996 |  3.989666 | BE          | positive    | contract  | no                | Bronze        |         337.0 | 210926597
 08069151049227862353292320341420 | Bruxelles | 50.7881573 | 4.4180065 | BE          | neutral     | invoice   | no                | Silver        |         512.0 | 049132258
:
```

In the next you will persist your query (also known as **create table as select** or **CTAS**) as a new dataset that you will use in Microsoft Power BI.

Next Step: [7.4 - Power BI/Tableau](./ex4.md)

[Go Back to Module 7](./query-service.md)

[Go Back to All Modules](../../overview.md)
module7:all
