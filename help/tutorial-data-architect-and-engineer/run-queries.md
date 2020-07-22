
# Setup and Run Query

In this chapter we will learn how to setup,write and execute queries.


1. Go to **Data Management** section and select **Queries**
1. Go to top-right and click **Create Query** , this will open a textbox to run and execute query.
1. Write following Query Editor and press Shift+Enter or Shift+Return to execute the query. This will show list of available tables

    ```
    SHOW TABLES
    ```

1. Copy following query and verify if table names and column name matches.
   
    ```
    SELECT person.name.lastName,_wwfovlab011.loyalty.level
    FROM luma_loyalty_dataset
    WHERE _wwfovlab011.loyalty.level ='gold'

    ```

1. Click Play button on text editor and you should get result in bottom result tab. If there is any error you could find it in consoles tab.
1. Provide name of the Query as **Luma Gold Level Customer**
1. Click Save.


## Join Datasets

In this exercise, we will join two datasets **Luma Loyalty Dataset** & **Luma Offline Purchase** to get list of gold customers who have spend over $500 dollars in one purchase.

1. Copy and Paste following query in Query Editor and Execute.
    
    ```
    SELECT DISTINCT lopd._wwfovlab011.purchase_event.receipt_date as PurchaseDate ,
        lld.person.name.firstName as LastName ,
        lld.person.name.lastName as LastName ,
        lopd._wwfovlab011.identities.email.address as email,
        lopd._wwfovlab011.purchase_event.receipt_total as Total

    FROM luma_loyalty_dataset lld
    JOIN luma_offline_purchase lopd
    ON lopd._wwfovlab011.identities.loyaltyId = lld._wwfovlab011.loyalty.loyaltyId

    WHERE lld._wwfovlab011.loyalty.level ='gold' AND lopd._wwfovlab011.purchase_event.receipt_total >500;
    ```

1. You should get list of Gold Customers who have spend over $500 in single purchase.


## Using Adobe-defined functions

## Generate Dataset From Query Result

In this chapter we will learn how to setup,write and execute queries.


In this exercise, we will join two datasets **Luma Loyalty Dataset** & **Luma Offline Purchase** to get list of gold customers who have spend over $500 dollars in one purchase.

1. Copy and Paste following query in Query Editor and Execute.

    ```
    SELECT DISTINCT lopd._wwfovlab011.purchase_event.receipt_date as PurchaseDate ,
        lld.person.name.firstName as LastName ,
        lld.person.name.lastName as LastName ,
        lopd._wwfovlab011.identities.email.address as email,
        lopd._wwfovlab011.purchase_event.receipt_total as Total

    FROM luma_loyalty_dataset lld
    JOIN luma_offline_purchase lopd
    ON lopd._wwfovlab011.identities.loyaltyId = lld._wwfovlab011.loyalty.loyaltyId

    WHERE lld._wwfovlab011.loyalty.level ='gold' AND lopd._wwfovlab011.purchase_event.receipt_total >500;
    ```

1. You should get list of Gold Customers who have spend over $500 in single purchase.
1. Click on Output Dataset button
1. Provide name and description to the dataset
1. Save.
1. Go to **Datasets** under **Data Management** to find new dataset created .