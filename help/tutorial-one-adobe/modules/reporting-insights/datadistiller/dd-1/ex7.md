---
title: Query Service - Explore the dataset with Tableau
description: Query Service - Explore the dataset with Tableau
kt: 5342
doc-type: tutorial
---
# 2.1.7 Query Service and Tableau

Open Tableau.

![start-tableau.png](./images/starttableau.png)

In **Connect To a Server**, click **More** and then click **PostgreSQL**.

![tableau-connect-postgress.png](./images/tableauconnectpostgress.png)

If you haven't used PostgeSQL with Tableau yet, you may see this. Click **Download Driver**.

![tableau-connect-postgress.png](./images/tableauconnectpostgress1.png)

Follow the instructions to download and install the PostgreSQL driver.

![tableau-connect-postgress.png](./images/tableauconnectpostgress2.png)

Once you're finished installing the driver, quit and restart Tableau Desktop. Then after the restart, go to **Connect To a Server** again, click **More** and then click **PostgreSQL** again.

![tableau-connect-postgress.png](./images/tableauconnectpostgress.png)

You'll then see this.

![tableau-connect-postgress.png](./images/tableauconnectpostgress3.png)

Go to Adobe Experience Platform, to **Queries** and to **Credentials**.

![query-service-credentials.png](./images/queryservicecredentials.png)

From the **Credentials** page in Adobe Experience Platform, copy the **Host** and paste it in the **Server** field, copy the **Database** and paste it in the **Database** field in Tableau, copy the **Port** and paste it in the field **Port**in Tableau, do the same for **Username** and **Password**. Next, click **Sign In**.

![tableau-connection-dialog.png](./images/tableauconnectiondialog.png)

In thelist of available tables, locate the table you created in the previous exercise, which is called `--aepUserLdap--_callcenter_interaction_analysis`. Drag it onto the canvas.

![tableau-drag-table.png](./images/tableaudragtable.png)

You'll then see this. Click **Update Now**.

![tableau-drag-table.png](./images/tableaudragtable1.png)

You'll then see the data from AEP becoming available in Tableau. Click **Sheet 1** to start working with the data.

![tableau-drag-table.png](./images/tableaudragtable2.png)

To visualize your data on the map you need to convert longitude and latitude to dimensions. In **Measures**,  right-click **Latitude**, select **Convert to Dimension** in the menu. Do the same for the **Longitude** measure.

![tableau-convert-dimension.png](./images/tableauconvertdimension.png)

Drag the **Longitude** measure to the **Columns** and the **Latitude** measure to **Rows**. Automatically the map of **Belgium** will appear with little dots representing the cities in out data set.

![tableau-drag-lon-lat.png](./images/tableaudraglonlat.png)

Select **Measure Names**, click **Add to Sheet**.

![tableau-select-measure-names.png](./images/selectmeasurenames.png)

You will now have a map, with dots of various sizes. The size indicates the number of call center interactions for that specific city. To vary the size of the dots, navigate to the right panel and open **Measure Values** (using the drop down icon). From the drop down list select **Edit Sizes**. Play around with different sizes.

![tableau-vary-size-dots.png](./images/tableauvarysizedots.png)

To further display the data per **Call Topic**, drag the **Call Topic** dimension onto **Pages**. Navigate through the different **Call topics** using the **Call Topic** on the right side of the screen:

![tableau-call-topic-navigation.png](./images/tableaucalltopicnavigation.png)

You've now finished this exercise.

## Next Steps

Go to [2.1.8 Query Service API](./ex8.md){target="_blank"}

Go back to [Query Service](./query-service.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}