# Module 7: Adobe Experience Platform Query Service

**Authors: [Marc Meewis](https://www.linkedin.com/in/marcmeewis/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

---

**In Module 7**, you will get a hands-on preview of Adobe Experience Platform Query Service. Query Service lets you perform omnichannel queries across all Adobe Experience Cloud product data, joining and analyzing data across Adobe Campaign, Analytics, Audience Manager, Target, and Advertising Cloud and other customer data loaded/inserted into Adobe Experience Platform.

Query Service is a serverless tool. It supports SQL queries and connectivity from multiple client applications through its PostgreSQL compatibility.
We will use data that has been injected into platform using either Web Interaction Data, Call Center Interactions in combination with Customer Loyalty Data uploaded into platform.

## Key Takeaways

* Become familiar with the Adobe Experience Platform UI
* Connect to Query Service and run your SQL queries
* Explore datasets in Adobe Experience Platform
* Connect Tableau or Power BI to the Adobe Experience Platform Query Service to create visualizations and reports

## Prerequisites

* Some familiarity with SQL is preferred, but not required
* Access to Adobe Experience Platform
* Datasets (dataset used during lab, pre-loaded for you)
* Installation and configuration of PostgreSQL compliant client or command line interface
* Tableau or Microsoft Power BI Desktop

## Your Environment Variables

This documentation has been created to be reused across multiple Adobe Experience Platform instances for enablement purposes.
In order to complete some of the modules, you'll need to change some variables and replace them by your specific ``Environment Variables``.

You can view these variables [here](../../environment.md).

## Content

### [Exercise 7.0 - Pre-requisites](./ex0.md)

You will need to install psql to execute the queries in this enablement exercise. Depending on your operating system you will have to install Microsoft Power BI or Tableau. Windows users can choose between Power BI or Tableau. Mac users should install Tableau.

### [Exercise 7.1 - Getting Started](./ex1.md)

In this exercise you will explore the Adobe Experience Platform Query Service User Interface, learn about data sets, find your queries and finally setup a connection from PSQL.

### [Exercise 7.2 - Using the Query Service](./ex2.md)

In this exercise you will learn about the basic Query Service syntax and you can identify the attributes of the XDM schema in your query.

### [Exercise 7.3 - Queries, queries, queries...  and churn analysis](./ex3.md)

In this exercise you will be doing queries, you will learn about the Adobe Defined Functions while doing some churn analysis. At the end of this exercise you will write a query to prepare a dataset for use in Microsoft Power BI.

### [Exercise 7.4 - Power BI/Tableau](./ex4.md)

In this exercise you will generate a dataset from a query executed in the previous exercise and you will use this dataset in Power BI or Tableau to to Callcenter Interaction Analysis.

---

[Go Back to Hands-On Lab Content](../../README.md)
