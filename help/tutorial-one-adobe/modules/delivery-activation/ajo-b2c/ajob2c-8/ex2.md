---
title: Create your orchestrated campaign
description: Create your orchestrated campaign
kt: 5342
doc-type: tutorial
---
# 3.8.2 Create your orchestrated campaign

## 3.8.2.1 Create your Orchestrated Campaign

Go to **Campaigns**. Click **Create campaign**.

![AJO OC](./images/ajooc1.png)

Select **Orchestration - Marketing** and click **Confirm**.

![AJO OC](./images/ajooc2.png)

Enter the campaign name: `--aepUserLdap-- - CitiSignal Family Account Optimization Campaign` and click **Save**.

![AJO OC](./images/ajooc3.png)

You should then see this. Click the **+** icon.

![AJO OC](./images/ajooc4.png)

Select **Fork**.

![AJO OC](./images/ajooc5.png)

### Build audience 1

Click the **+** icon and then select **Build Audience**.

![AJO OC](./images/ajooc6.png)

Click to open the folder for **Targeting dimension**.

![AJO OC](./images/ajooc7.png)

Select **`--aepUserLdap--_citisignal_recipients`** and click **Confirm**.

![AJO OC](./images/ajooc8.png)

Click **Create audience**.

![AJO OC](./images/ajooc9.png)

Click **Add condition**.

![AJO OC](./images/ajooc10.png)

Select **recipient_type** and click **Confirm**.

![AJO OC](./images/ajooc11.png)

Enter **`account_holder`** in the field **Value** and click **Calculate**.

![AJO OC](./images/ajooc12.png)

You should then see a number for **profiles targeted**. Click somewhere in the grey area as indicated.

![AJO OC](./images/ajooc13.png)

Click **Add condition**.

![AJO OC](./images/ajooc14.png)

Drill down to **`citisignal_accounts`**.

![AJO OC](./images/ajooc15.png)

Select **`account_status`** and click **Confirm**.

![AJO OC](./images/ajooc16.png)

Enter **`active`** in the field **Value**. Then, click somewhere in the grey area as indicated.

![AJO OC](./images/ajooc17.png)

Click **Add condition**.

![AJO OC](./images/ajooc18.png)

Drill down to **`citisignal_mobile_subscriptions`**.

![AJO OC](./images/ajooc19.png)

Select **`subscription_id`** and click **Confirm**.

![AJO OC](./images/ajooc20.png)

Enable the switcher for **Aggregate data**. Then select the followibg:

- **Aggregate function**: **Count**
- **Operator**: **greater than or equal to**
- **Value**: **1**

Click **Confirm**.

![AJO OC](./images/ajooc21.png)

You should then see this. Click **Confirm**.

![AJO OC](./images/ajooc22.png)

### Build audience 2

Click the **+** icon on the next node in the other path.

![AJO OC](./images/ajooc23.png)

Select **Build audience**.

![AJO OC](./images/ajooc24.png)

Click to open the folder for **Targeting dimension**.

![AJO OC](./images/ajooc25.png)

Select **`--aepUserLdap--_mobile_subscriptions`** and click **Confirm**.

![AJO OC](./images/ajooc26.png)

Click **Create audience**.

![AJO OC](./images/ajooc27.png)

Click **Add condition**.

![AJO OC](./images/ajooc28.png)

Select **subscription_status** and click **Confirm**.

![AJO OC](./images/ajooc29.png)

Enter **`active`** in the field **Value**. Then, click **Add condition**.

![AJO OC](./images/ajooc30.png)

Select **`is_upgrade_eligible`** and click **Confirm**.

![AJO OC](./images/ajooc31.png)

Set the **Value** to **true**

![AJO OC](./images/ajooc32.png)

Click **Calculate** to see an estimation of the profiles that qualify for this audience. Then, click **Confirm**

![AJO OC](./images/ajooc33.png)

### Split

Click the **+** icon and then select **Split**.

![AJO OC](./images/ajooc34.png)

Change the field **Label** to **90/10 Treatment vs Control**. Click to open the object **Subset**.

![AJO OC](./images/ajooc35.png)

Enable the switcher for **Enable limit** and set the **Limit size** to **10 perecent**.

![AJO OC](./images/ajooc36.png)

Click **Add segment** and then you should see the **Result** object being added.

Click **Save**.

![AJO OC](./images/ajooc37.png)

### Save audience

Click the **+** icon and then select **Save audience**.

![AJO OC](./images/ajooc38.png)

Set the field **Audience label** to **`--aepUserLdap-- - Control Group`**. Click **Add Audience Mapping**.

![AJO OC](./images/ajooc39.png)

Drill down to **targeting dimension**.

![AJO OC](./images/ajooc40.png)

Select **`account_id`** and click **Confirm**.

![AJO OC](./images/ajooc41.png)

### Enrichment: Internet Subscription

Click the **+** icon.

![AJO OC](./images/ajooc42.png)

Select **Enrichment**.

![AJO OC](./images/ajooc43.png)

You should then see this. Click **Add enrichment data**.

![AJO OC](./images/ajooc44.png)

Drill down to **`Targeting dimension`**.

![AJO OC](./images/ajooc44a.png)

Drill down to **`citisignal_accounts`**.

![AJO OC](./images/ajooc45.png)

Drill down to **`citisignal_internet_subscriptions`**.

![AJO OC](./images/ajooc45a.png)

Select **`account_id`** and click **Confirm**.

![AJO OC](./images/ajooc46.png)

You should then see this. Click **Add attribute**.

![AJO OC](./images/ajooc47.png)

Select **`subscription_status`** and click **Confirm**.

![AJO OC](./images/ajooc48.png)

Click **Add attribute**.

![AJO OC](./images/ajooc49.png)

Select **`connection_type`** and click **Confirm**.

![AJO OC](./images/ajooc50.png)

Click **Add attribute**.

![AJO OC](./images/ajooc51.png)

Select **`service_city`** and click **Confirm**.

![AJO OC](./images/ajooc52.png)

Click **Add attribute**.

![AJO OC](./images/ajooc53.png)

Select **`avg_dowload_usage_gb`** and click **Confirm**.

![AJO OC](./images/ajooc54.png)

Click **Add attribute**.

![AJO OC](./images/ajooc55.png)

Select **`data_cap_gb`** and click **Confirm**.

![AJO OC](./images/ajooc56.png)

Click **Add attribute**.

![AJO OC](./images/ajooc57.png)

Select **`advertised_speed_mbps`** and click **Confirm**.

![AJO OC](./images/ajooc58.png)

Click **Add attribute**.

![AJO OC](./images/ajooc59.png)

Select **`monthly_recurring_charge`** and click **Confirm**.

![AJO OC](./images/ajooc60.png)

Click **Save**.

![AJO OC](./images/ajooc61.png)

Scroll up and change the field **Label** to `Enrichment: Internet Subscription`.

![AJO OC](./images/ajooc61a.png)

### Enrichment: Mobile Devices Subscription

Click the **+** icon on the next node and select **Enrichment**.

![AJO OC](./images/ajooc62.png)

Change the field **Label** to `Enrichment: Mobile Devices Subscription` and then click **Add enrichment data**.

![AJO OC](./images/ajooc63.png)

Drill down to **Targeting dimension**.

![AJO OC](./images/ajooc64.png)

Drill down to **`citisignal_mobile_subscriptions`**.

![AJO OC](./images/ajooc65.png)

Select **`account_id`** and click **Confirm**.

![AJO OC](./images/ajooc66.png)

Click **Add attribute**.

![AJO OC](./images/ajooc67.png)

Select **`subscription_id`** and click **Confirm**.

![AJO OC](./images/ajooc68.png)

Click **Add attribute**.

![AJO OC](./images/ajooc69.png)

Select **`phone_number`** and click **Confirm**.

![AJO OC](./images/ajooc70.png)

Click **Add attribute**.

![AJO OC](./images/ajooc71.png)

Select **`renewal_eligibility_date`** and click **Confirm**.

![AJO OC](./images/ajooc72.png)

Click **Add attribute**.

![AJO OC](./images/ajooc73.png)

Select **`line_user_recipient_id`** and click **Confirm**.

![AJO OC](./images/ajooc74.png)

Click **Add attribute**.

![AJO OC](./images/ajooc75.png)

Select **`is_upgrade_eligible`** and click **Confirm**.

![AJO OC](./images/ajooc76.png)

Click **Add attribute**.

![AJO OC](./images/ajooc77.png)

Select **`current_device_id`** and click **Confirm**.

![AJO OC](./images/ajooc78.png)

Click **Add attribute**.

![AJO OC](./images/ajooc79.png)

Select **`contract_start_date`** and click **Confirm**.

![AJO OC](./images/ajooc80.png)

Click **Add attribute**.

![AJO OC](./images/ajooc81.png)

Drill down to **`citisignal_equipment_subscriptions`**.

![AJO OC](./images/ajooc82.png)

Select **`model`** and click **Confirm**.

![AJO OC](./images/ajooc83.png)

Click **Add attribute**.

![AJO OC](./images/ajooc86.png)

Drill down to **`citisignal_equipment_subscriptions`**.

![AJO OC](./images/ajooc87.png)

Select **`manufacturer`** and click **Confirm**.

![AJO OC](./images/ajooc88.png)

Click **Add attribute**.

![AJO OC](./images/ajooc89.png)

Drill down to **`citisignal_equipment_subscriptions`**.

![AJO OC](./images/ajooc90.png)

Select **`device_age_months`** and click **Confirm**.

![AJO OC](./images/ajooc91.png)

Click **Add attribute**.

![AJO OC](./images/ajooc92.png)

Drill down to **`citisignal_equipment_subscriptions`**.

![AJO OC](./images/ajooc93.png)

Select **`is_upgrade_eligible`** and click **Confirm**.

![AJO OC](./images/ajooc94.png)

Click **Add attribute**.

![AJO OC](./images/ajooc95.png)

Drill down to **`citisignal_equipment_subscriptions`**.

![AJO OC](./images/ajooc96.png)

Select **`recommended_upgrade_product_id`** and click **Confirm**.

![AJO OC](./images/ajooc97.png)

Click **Add attribute**.

![AJO OC](./images/ajooc98.png)

Drill down to **`citisignal_equipment_subscriptions`**.

![AJO OC](./images/ajooc99.png)

Select **`monthly_payment`** and click **Confirm**.

![AJO OC](./images/ajooc100.png)

Click **Add attribute**.

![AJO OC](./images/ajooc101.png)

Drill down to **`citisignal_equipment_subscriptions`**.

![AJO OC](./images/ajooc102.png)

Enable the switch for **Enable Sorting**. Click the **Edit** icon.

![AJO OC](./images/ajooc103.png)

Select **`phone_number`** and click **Confirm**.

![AJO OC](./images/ajooc104.png)

You should then have this.

![AJO OC](./images/ajooc105.png)




You should then have this. Click **Save**.

![AJO OC](./images/ajooc80a.png)














![AJO OC](./images/ajooc103.png)


## Next Steps

Go back to [Adobe Journey Optimizer: Orchestrated Campaigns](./ajocampaigns.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
