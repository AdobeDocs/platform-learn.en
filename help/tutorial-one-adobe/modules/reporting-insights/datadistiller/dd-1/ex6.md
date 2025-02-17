---
title: Query Service - Explore the dataset with Power BI
description: Query Service - Explore the dataset with Power BI
kt: 5342
doc-type: tutorial
exl-id: f1125d91-2fe6-456c-9d4a-802e3f288fc0
---
# 2.1.6 Query Service and Power BI

Open Microsoft Power BI Desktop.

![start-power-bi.png](./images/startpowerbi.png)

Click **Get Data**.

![power-bi-get-data.png](./images/powerbigetdata.png)

Search for **postgres** (1), select **Postgres** (2) from the list and **Connect** (3).

![power-bi-connect-progress.png](./images/powerbiconnectprogress.png)

Go to Adobe Experience Platform, to **Queries** and to **Credentials**.

![query-service-credentials.png](./images/queryservicecredentials.png)

From the **Credentials** page in Adobe Experience Platform, copy the **Host** and paste it in the **Server** field, and copy the **Database** and paste it in the **Database** field in PowerBI, then click OK (2).

>[!IMPORTANT]
>
>Make sure to include port **:80** at the end of the Server value because the Query Service does not currently use the default PostgreSQL port of 5432.

![power-bi-connect-server.png](./images/powerbiconnectserver.png)

In the next dialog populate the User name and Password with your Username and Password found in the **Credentials** of Queries in Adobe Experience Platform.

![query-service-credentials.png](./images/queryservicecredentials.png)

In the Navigator dialog, put your **LDAP** in the search field (1) to locate your CTAS datasets and check the box next to each (2). Then click Load (3).

![power-bi-load-churn-data.png](./images/powerbiloadchurndata.png)

Make sure the **Report** tab (1) is selected.

![power-bi-report-tab.png](./images/powerbireporttab.png)

Select the map (1) and after it is added to the reporting canvas, enlarge the map (2).

![power-bi-select-map.png](./images/powerbiselectmap.png)

Next we need to define the measures and the dimensions, you do this by dragging fields from the **fields** section onto the corresponding placeholders (located under **visualizations**) as indicated below:

![power-bi-drag-lat-lon.png](./images/powerbidraglatlon.png)

As measure we will use a count of **customerId**. Drag the **crmid** field from the **fields** section into the **Size** placeholder:

![power-bi-drag-crmid.png](./images/powerbidragcrmid.png)

Finally, to do some **callTopic** analysis, let's drag the **callTopic** field on to the **Page level filters** placeholder (you might have to scroll in the **visualizations** section);

![power-bi-drag-calltopic.png](./images/powerbidragcalltopic.png)

Select/unselect **callTopics** to investigate:

![power-bi-report-select-calltopic.png](./images/powerbireportselectcalltopic.png)

You've now finished this exercise.

## Next Steps

Go to [2.1.8 Query Service API](./ex8.md){target="_blank"}

Go back to [Query Service](./query-service.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
