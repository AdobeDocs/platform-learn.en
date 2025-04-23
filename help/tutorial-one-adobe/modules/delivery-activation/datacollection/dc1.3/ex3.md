---
title: Data Collection - FAC - Create a federated composition
description: Foundation - FAC - Create a federated composition
kt: 5342
doc-type: tutorial
exl-id: 6c1773d1-ca2e-43e5-bfa7-6e5e0fbcf859
---
# 1.3.3 Create a federated composition

You can now configure your federated audience composition in AEP.

Log in to Adobe Experience Platform by going to this URL: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./../dc1.2/images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named `--aepSandboxName--`. After selecting the appropriate sandbox, you'll see the screen change and now you're in your dedicated sandbox.

![Data Ingestion](./../dc1.2/images/sb1.png)

## 1.3.3.1 Create your audience

In the left menu, go to **Audiences** and then go to **Federated compositions**. Click **Create composition**.

![FAC](./images/fedcomp1.png)

For the label, use this: `--aepUserLdap-- - CitiSignal Fiber`. Select the data model that you created in the previous exercise, which is named `--aepUserLdap-- - CitiSignal Snowflake Data Model`. Click **Create**.

![FAC](./images/fedcomp2.png)

You'll then see this.

![FAC](./images/fedcomp3.png)

Click the **+** icon and click **Build audience**.

![FAC](./images/fedcomp4.png)

You'll then see this. Select **Create audience**. Click the **search** icon to select a schema.

![FAC](./images/fedcomp5.png)

Select the schema **`--aepUserLdap--_HOUSEHOLDS`**. Click **Confirm**.

![FAC](./images/fedcomp6.png)

Next, click **Continue**.

![FAC](./images/fedcomp7.png)

You can now start building the query that will be sent to Snowflake. Click the **+** icon and then click **Custom condition**.

![FAC](./images/fedcomp8.png)

Select the attribute **ISELIGIBLEFORFIBER** Click **Confirm**. 

![FAC](./images/fedcomp9.png)

You'll then see this. Set the field **Value** to **True**. Click **Calculate** to push the query down to Snowflake and get an estimation of the profiles that now qualify.

![FAC](./images/fedcomp10.png)

Then, click the **+** icon again and click **Custom condition** again to add another condition.

![FAC](./images/fedcomp11.png)

The second condition to add, is: `Is the user an existing CitiSignal Mobile subscriber?`. The way to answer that question is to use the relationship between the household and the primary customer in the household, which is defined in another table, **`--aepUserLdap--_PERSONS`**. You can drill down in the attribute menu using the **household2person** link.

![FAC](./images/fedcomp12.png)

Select the attribute **ISMOBILESUB** and click **Confirm**.

![FAC](./images/fedcomp13.png)

Set the field **Value** to **True** Click **Calculate** again to update the number of profiles that will be targeted. Click **Confirm**.

![FAC](./images/fedcomp14.png)

Click the **+** icon and then click **Save Audience**.

![FAC](./images/fedcomp15.png)

Set the **Audience label** to `--aepUserLdap-- - CitiSignal Eligible for Fiber`.

Click **+ Add Audience Mapping**.

![FAC](./images/fedcomp16.png)

Select **HOUSEHOLD_ID** and click **Confirm**.

![FAC](./images/fedcomp17.png)

Click **+ Add Audience Mapping**.

![FAC](./images/fedcomp18.png)

Drill down by clicking **Targeting dimension**.

![FAC](./images/fedcomp18a.png)

Drill down by clicking the link **household2person**. 

![FAC](./images/fedcomp18b.png)

Select the field **NAME**. Click **Confirm**.

![FAC](./images/fedcomp18c.png)

Click **+ Add Audience Mapping**.

![FAC](./images/fedcomp20.png)

Drill down by clicking **Targeting dimension**.

![FAC](./images/fedcomp20a.png)

Drill down by clicking the link **household2person**. 

![FAC](./images/fedcomp20b.png)

Select the field **EMAIL**. Click **Confirm**.

![FAC](./images/fedcomp20c.png)

You'll then see this. You now need to set the **Primary identity field**, set it to **Household2person_EMAIL**. Set **Identity Namespace** to **Email**.

Click **Save**.

![FAC](./images/fedcomp21.png)

Your composition is now finished. Click **Start** to run it.

![FAC](./images/fedcomp21a.png)

The query will now be pushed down into Snowflake, which will query the source data there. The results will be pushed back into AEP but source data remains in Snowflake. 

The audience is now populated, and the audience is targetable from within the AEP ecosystem.

![FAC](./images/fedcomp22.png)

## Next Steps

Go to [Summary & benefits](./summary.md){target="_blank"}

Go back to [Federated Audience Composition](./fac.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
