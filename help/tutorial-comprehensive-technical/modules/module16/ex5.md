---
title: Ingest & Analyze Google Analytics data in Adobe Experience Platform with the BigQuery Source Connector - Analyze Google Analytics Data using Customer Journey Analytics
description: Ingest & Analyze Google Analytics data in Adobe Experience Platform with the BigQuery Source Connector - Analyze Google Analytics Data using Customer Journey Analytics
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: fad8213d-4d9a-4fec-8fe8-f87088245d7c
---
# 16.5 Analyze Google Analytics Data using Customer Journey Analytics 

## Objectives

- Connect our BigQuery Data Set to Customer Journey Analytics (CJA)
- Connect and join Google Analytics with Loyalty Data.
- Become familiar with CJA UI

## 16.5.1 Create a Connection

Go to [analytics.adobe.com](https://analytics.adobe.com) to access Customer Journey Analytics.

![demo](./images/1a.png)

On the Customer Journey Analytics homepage, go to **Connections**. 

![demo](./images/1.png)

Here you can see all the different connections made between CJA and Platform. These connections have the same goal as report suites in Adobe Analytics. However, the collection of the data is totally different. All data is coming from Adobe Experience Platform datasets. 

![demo](./images/2.png)

Click **Create new connection**.

![demo](./images/3.png)

You'll then see the **Create Connection** UI.

![demo](./images/5.png)

In the left menu, you can see all available Adobe Experience Platform datasets. Search for the dataset `AEP Demo - BigQuery Website Interactions`. Click **+** to add the dataset to this connection.

![demo](./images/6.png)

After adding it, you'll see the dataset inside the connection.

![demo](./images/7.png)

You now have to select the **Person ID**. Please select the **crmId** as person id.

![demo](./images/8.png)

You'll now enrich the Google Analytics Website Interaction data with another Adobe Experience Platform dataset. 

Search for the dataset `AEP Demo - Loyalty Data (M16)` data set and add it to this connection.

![demo](./images/10.png)

You'll then see this:

![demo](./images/10a.png)

In order to merge both datasets, you need to select a **Person ID** that contains the same type of IDs. The dataset `AEP Demo - Loyalty Data (M16)` uses the **loyaltyId** as Person ID, which contains the same type of IDs as the `AEP Demo - BigQuery Website Interactions`, which uses the **crmId** as a Person ID. 

![demo](./images/12.png)

Click **Next**.

![demo](./images/14.png)

You'll then see this:

![demo](./images/15.png)

Here you need to give a name to your connection. 

Please use this naming convention: `ldap - GA + Loyalty Data Connection`. 

Example: `vangeluw - GA + Loyalty Data Connection`

Before finishing, please also activate **Automatically import all new data for all datasets in this connection, beginning today.** as in the image below. 

![demo](./images/16.png)

This will start a data flow from Adobe Experience Platform to CJA every 60 minutes, however with high volumes of data it can take up to 24 hours. 

You also need to backfill historical data, so please check the checkbox for **Import all existing data**.

![demo](./images/17.png)

After having created your **Connection** it may take a few hours before your data is available in CJA.

Click **Save** and go to the next exercise. 

![demo](./images/cjasave.png)

You'll then see your connection in the list of available connections.

![demo](./images/18.png)

## 16.5.2 Create a data view

With your connection done, you can now progress to influencing visualization. A difference between Adobe Analytics and CJA, is that CJA needs a data view in order to clean and prepare the data before visualization. 

A data view is similar to the concept of virtual report suites in Adobe Analytics, where you define context-aware visit definitions, filtering and also, how the components are called. 

You'll need a minimum of one data view per connection. However, for some use-cases, it's great to have multiple data views for the same connection, with the goal of giving different insights to different teams. 

If you want your company to become data-driven, you should adapt how data is viewed in each team. Some examples:

- UX metrics only for the UX Design team
- Use the same names for KPIs and Metrics for Google Analytics as for Customer Journey Analytics so that the digital analytics team can speak 1 language only.
- data view filtered to show for instance data for 1 market only, or 1 brand, or only for Mobile Devices.

On the **Connections** screen, check the checkbox in front of the connection you just created.

![demo](./images/exta.png)

Now click **Create Data View**.

![demo](./images/extb.png)

You'll be redirected to the **Create Data View** workflow.

![demo](./images/extc.png)

You can now configure the basic definitions for your data view. Things like Time zone, Session Timeout or the data view filtering (the segmentation part similar to Virtual Report Suites in Adobe Analytics).

The **Connection** you created in the previous exercise is already selected. Your connection is named `ldap - GA + Loyalty Data Connection`.

![demo](./images/ext5.png)

Next, give your data view a name following this naming convention: `ldap - GA + Loyalty Data View`. 

Enter the same value for the description: `ldap - GA + Loyalty Data View`.

Before doing any analysis or visualization we need to create a data view with all the fields, dimensions and metrics and their attribution settings.

| Field      | Naming Convention|  Example|   
| ----------------- |-------------|-------------|  
| Name Connection | ldap - GA + Loyalty Data View| vangeluw - GA + Loyalty Data View |
| Description | ldap - GA + Loyalty Data View | vangeluw - GA + Loyalty Data View |

![demo](./images/22.png)

Click **Continue**.

![demo](./images/23.png)

You can now add components to your data view.

![demo](./images/24.png)

Click **Add All Components** to add all available components to the data view.

![demo](./images/25.png)

You need to make some changes to the Person and Session context for some of these components by changing the **Attribution Settings**.

![demo](./images/26.png)

Please change the **Attribution Settings** for the below components:

| Component        |   
| -----------------|
| exitpage | 
| trafficsource | 
| marketingchannel | 
| browser | 
| trafficmedium | 
| device | 
| landingpage | 
| gaid | 
| crmId | 
| loyaltyStatus | 
| loyaltyPoints | 

To do that, select the component, click **Use custom attribution model** and set the **Model** to **Last Touch**, and the **Expiration** to **Person (Reporting Window)**. Repeat this for all of the above mentioned components.

![demo](./images/27a.png)

You should then have this view:

![demo](./images/27.png)

Your data view is now configured. Click **Save**.

![demo](./images/30.png)

You are now ready to to analyze Google Analytics data within Adobe Analytics Analysis Workspace. Let's move to the next exercise.

## 16.5.3 Create your Project

In Customer Journey Analytics, go to **Projects**.

![demo](./images/pro1.png)

You'll then see this:

![demo](./images/pro2.png)

Create a Project by clicking **Create New Project**.

![demo](./images/pro3.png)

You now have a blank Project:

![demo](./images/pro4.png)

First, save your project and give it a name. You can use the following command to save:

|  OS        | Short cut   | 
| ----------------- |-------------| 
| Windows | Control + S          | 
| Mac | Command + S          | 

You'll see this popup: 

![demo](./images/prsave.png)

Please use this naming convention:

|  Name       | Description    | 
| ----------------- |-------------| 
| ldap – GA + Loyalty Workspace| ldap – GA + Loyalty Workspace|

Next, click **Save Project**.

![demo](./images/prsave2.png)

Next, make sure to select the correct data view in the upper right corner of your screen. This is the data view you created in the previous exercise, with the naming convention `ldap - GA + Loyalty Data View`. In this example, the Data View to select is `ldap - GA + Loyalty Data View`.

![demo](./images/prdvlist.png)

![demo](./images/prdv.png)

### 16.5.3.1 Freeform Tables

Freeform tables work, more or less, as pivot tables within Excel. You pick something from the left bar and you drag and drop it into the Freeform and you'll get a table report.

Freeform tables are almost limitless. You can do (almost) anything and this brings so much value when compared to Google Analytics (since this tool has some analysis limitations). This is one of the reasons to load Google Analytics data into another analysis tool.

Let see two examples where you need to use SQL, BigQuery and some time to answer simple questions that are not possible to do within the Google Analytics UI or Google Data Studio:

- How many people arrive to the checkout from my main landing page split by marketing channel? Please see that the checkout metric is being filtered by the Google Online Store LandingPage. We just dragged and dropped the variable landingpage = Google Online Store on top of the checkout column.

- As an analyst, I can see the Social Marketing Channel has low conversions. I'm using Last Touch attribution as default, but what about First touch? Hovering over any metric, the metric settings are displayed. There I can select the attribution model I want. You can do Attribution in GA (not in data studio) as a standalone activity, but you can't have other metrics or dimensions not related to attribution analysis within the same table.

Let's answer this questions and some more with Analysis Workspace in CJA.

First, select the right date range on the right side of the panel.

![demo](./images/pro11.png)

The apply the date range. Remember this step for next exercises.

![demo](./images/12.png)

NOTE. If you just created the **Data connection** and **Data view** you might need to wait a couple of hours. CJA takes some time to import historical data when there is a huge amount of data records. 

Let's drag and drop some dimensions and metrics to analysis the Marketing channels. First use the dimension of **marketingchannel** and drag and drop it to the canvas of the **Freeform table**. (Click on **Show All** in case you don't see the metric immediately in the Metrics menu)

![demo](./images/pro14.png)

You'll then see this:

![demo](./images/pro14a.png)

Next is adding the Metrics. You should add these Metrics: **People**, **Sessions**, **productdetail**, **checkout**, **purchase**, **Conversion Rate** (Calculated Metric).

Before you can do that, you need to create the Calculated Metric **Conversion Rate**. To do that, click the **+** icon next to Metrics:

![demo](./images/procalc1.png)

As a name for the Calculated Metric, use **Conversion Rate**. Then drag the Metrics **purchase** and **Sessions** onto the canvas. Set **Format** to **Percent** and **Decimal Places** to **2**. Finally, click **Save**.

![demo](./images/procalc2.png)

Next, in order to use all these Metrics in the **Freeform Table**, drag and drop them one by one onto the **Freeform Table**. See the example below.

![demo](./images/pro16.png)

You'll end up with a table like this one:

![demo](./images/pro16a.png)

As mentioned above, **Freeform tables** give you the freedom you need to perform deep dive analysis. For instance, you can pick any other Dimension to break down a specific Metric inside the table.

As an example, go to dimensions and open the **landingpage** variable. (Click on **Show All** in case you don't see the dimension immediately in the Dimensions menu)

![demo](./images/pro17.png)

You'll then see an overview of available values for this Dimension.

![demo](./images/pro18.png)

Pick the Dimension **Google Online Store** and drag and drop it on top of a Metric, for example **checkout**.

![demo](./images/pro19.png)

You'll then see this:

![demo](./images/pro19a.png)

Doing this, we just answered the first question we had: How many people arrive to the checkout from the main landing page, split by Marketing Channel?

Let's now answer the Attribution question.

Find the **Purchase** metric in the table.

![demo](./images/pro20.png) 

Hover over the metric and a **Settings** icon will appear. Click it.

![demo](./images/pro21.png)

A contextual menu will appear. Please use a **non-default attribution model**.

![demo](./images/pro22.png)

Within the new layer that will appear you can change easily the attribution models and lookback window. Something quite complicated with SQL by the way.

![demo](./images/pro23.png)

Now choose the **First Touch** model.

![demo](./images/pro24.png)

An choose **Person** as lookback window.

![demo](./images/pro25.png)

Now click **Apply**.

![demo](./images/pro26.png)

You can see now that the attribution for that particular metric is now First Touch. 

![demo](./images/pro27.png)

You can do as much breakdown as you want, without limits of types of variable, segments, dimension or date ranges.

Something even more special is the ability to bring together other datasets from Platform to enrich the digital behaviour data from Google Analytics. For example, offline, call center, loyalty or CRM data.

To showcase that functionality, let's configure your first breakdown thats combines offline data with online data. Pick the dimension **loyaltyStatus** and drag and drop it into any **marketingchannel** for example Organic:

![demo](./images/pro28.png)

Next, let's analyze which **device** is used by customers that came to the site using **Organic Search** with a **loyaltyStatus** that is **Bronze**. Take the Dimension **device** and drag and drop it onto **Bronze**.

![demo](./images/pro29.png)

You'll then see this:

![demo](./images/pro30.png)

You can see that for your first breakdown, loyalty status is used. This dimension comes from a different dataset and different schema than the one that you used for the BigQuery connector. The Person ID **crmId** (BigQuery Schema) and **loyaltyID** (Loyalty Schema) match with each other. Therefore, we can combine Experience Events from Google Analytics with Profile Data from the Loyalty System.

We can keep splitting the rows with segments or specific date ranges (maybe to reflect particular TV campaigns) to ask questions to Customer Journey Analytics and get the answers on the go.

Achieving the same end result with SQL and then a third-party visualization tool is quite a challenge. Especially when you're asking questions and trying to get the answers on the fly. Customer Journey Analytics doesn't have this challenge and allows Data Analysts to query the data flexibly and in real-time.

## 16.5.3.2 Funnel or fallout analysis

Funnels are a great mechanism to understand the main steps in a customer journey. These steps can also come from offline interactions (for example, from the call center) and then you can combine them with digital touch-points in the same funnel.

Customer Journey Analytics allows you to do that and much more. If you remember Module 13, we where able to right click and do things like:

- Analyze where the users are going after a fallout step
- Create a segment from any point of the funnel
- See the Trend at any stage in a Line Graph visualization


Let's see another thing you can do: How is my Customer Journey Funnel this month against the previous month? What about mobile vs desktop? 

Below you'll create two panels:

- Funnel Analysis (January)
- Funnel Analysis (February)

You'll see that we are comparing a funnel over different periods of time (January and February) split by Device Type.

This type of analysis is not possible within the Google Analytics UI, or is very limited. So CJA again adds lot of value to the data captured by Google Analytics.

To create your first fallout visualization. Please close the current panel to start from with a new one. 

Look at the right side of the panel and click the arrow to close it.

![demo](./images/pro33.png)

Next, click **+** to create a new panel.

![demo](./images/pro35.png) 

Now select the **Fallout** Visualization.

![demo](./images/pro36.png)

As an analyst, you want to understand what's happening with your main ecommerce funnel: Home > Internal Search > Product Detail > Checkout > Purchase.

Let's start by adding some new steps to the funnel. To do that, open the **pagetitle** dimension.

![demo](./images/pro37.png) 

You'll then see all available pages that have been visited.

![demo](./images/pro38.png)

Drag and drop **Home** to the first step.

![demo](./images/pro39.png) 

As second step, use the **Store search results**

![demo](./images/pro40.png)

Now you need to add some ecommerce actions. In the Dimensions, search for the Dimension **actiontype** dimension.

![demo](./images/pro41.png) 

Open the dimension.

![demo](./images/pro42.png) 

Select **Product_Detail_Views** and drag and drop it into the next step.

![demo](./images/pro43.png)

Do the same with **Product_Checkouts**.

![demo](./images/pro44.png)

Resize your Fallout visualization.

![demo](./images/pro45.png)

Your fallout visualization is now ready.

To start analyzing and documenting the insights, it's always a good idea to a **Text** visualization. To add a **Text** visualization, click on the **Graph** icon in the left menu to see all available visualizations. Then drag and drop the **Text** visualization onto the canvas. Resize and move it so that it looks like the below image.

![demo](./images/pro48.png)

And again, resize it to fit the dashboard:

![demo](./images/pro49.png)

Fallouts visualizations also allow breakdowns. Use the **device** dimension by opening it and drag and drop some of the values on by one onto the visualization:

![demo](./images/pro50.png)

You'll end up with a more advanced visualization:

![demo](./images/pro51.png)


Customer Journey Analytics allows you to do that and much more. By right-clicking anywhere in the fallout, you can...

- Analyze where the users are going from a fallout step
- Create a segment from any point of the funnel
- Trend any step in a Line visualization
- Compare any funnel to different periods of time in a visual way.

As an example, do a right-click in any step of the fallout to see some of these analysis options. 

![demo](./images/pro52.png)

Building this out within Google Analytics isn't no possible, or if it is, functionality is limited and presents analysts with a big challenge. So using Customer Journey Analytics to analyze data collected by Google Analytics is a great idea that add lots of value!

## 16.5.3.3 Flow Analysis & Visualization

If you want to do advanced flow analysis using Google Analytics, you need to use SQL to extract the data  and then use a third-party solution for the visualization part. Customer Journey Analytics will help with that.

In this step, you'll configure a flow analysis to answer this question: What are the main contributing channels before a specific Landing Page.  With two drag and drops and one click, as an analyst, you can discover the flow of the user towards the Landing Page with the two last touches of marketing channels.

Other questions that Customer Journey Analytics can help you answer:

- What is the main combination of channels before a specific Landing Page? 
- What causes a user to exit the session when he/she arrives to the Product_Checkout? What where the previous steps?

Let's start with a blank panel again to answers these questions. Close the current panel and click **+**.

![demo](./images/pro53.png)

Now select the **Flow** visualization. 

![demo](./images/pro54.png)

Let's now setup a multi-path Marketing Channel Flow Analysis. Drag and drop the **marketingchannel** dimension onto the **Entry Dimensions** area.

![demo](./images/pro55.png)

You can now see the first entry paths: 

![demo](./images/pro56.png)

Click the first path to drill down on it.

![demo](./images/pro58.png)

You can now see the next path (Marketing Channel). 

![demo](./images/pro59.png)

Let's do a third drill-down. Click on the first option within the new path, **Referral**.

![demo](./images/pro60.png)

Now you should see the visualization like this:

![demo](./images/pro61.png)

Let's complicate things. Imagine you want to analyze what the landing page was after two marketing paths? To do this you can use a secondary dimension to change the last path. Find the **landingpage** dimension and drag and drop it like this:

![demo](./images/pro62.png)

You'll now see this:

![demo](./images/pro63.png)

Let's do another flow analysis. This time you'll analyze what happened after a specific exit point. Other Analytics-solutions require the use of SQL/ETL and again, a third-party visualization tool to achieve the same thing. 

Bring a new **Flow Visualization** to the panel. 

![demo](./images/pro64.png)

You'll then have this:

![demo](./images/pro64a.png)

Find the Dimension **actiontype** and drag and drop it to the **Exit dimension** area. 

![demo](./images/pro65.png)

Now you can see which **actiontype**-paths drove customers to the exit. 

![demo](./images/pro66.png)

Let's investigate what happened before the exit from the checkout-action. Click on the **Product_Checkouts** path:

![demo](./images/pro67.png)

A new action path will appear with some data that is not insightful. 

![demo](./images/pro68.png)

Let's analyze further! Search the Dimension **pagetitle** and drag and drop it to the new generated path.

![demo](./images/pro69.png)

You have now an advanced flow analysis done in minutes. You can click the different paths to see how they connect from the exit to the previous steps.

![demo](./images/pro70.png)

You now have a powerful kit to analyze funnels and explore paths of customer behavior across digital but also, offline touch points.

## 16.5.4 Share the project

>[!IMPORTANT]
>
>The below content is intended as FYI - You do **NOT** have to share your project with anyone else.

FYI - You can share this project with colleagues to collaborate or to analyze business questions together.

![demo](./images/pro99.png)

![demo](./images/pro100.png)

Next Step: [Summary & benefits](./summary.md)

[Go Back to Module 16](./customer-journey-analytics-bigquery-gcp.md)

[Go Back to All Modules](./../../overview.md)
