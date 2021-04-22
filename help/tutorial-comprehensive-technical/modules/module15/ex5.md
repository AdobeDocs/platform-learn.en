---
title: Data Science Workspace - Car Insurance Sales Propensity - Publish your Recipe as a Scheduled Service
description: Data Science Workspace - Car Insurance Sales Propensity - Publish your Recipe as a Scheduled Service
kt: 5342
audience: Data Engineer, Data Architect, Data Scientist
doc-type: tutorial
activity: develop
exl-id: 19261ef0-f717-435b-b806-709d88fb3a92
---
# 15.5 Publish your Recipe as a Scheduled Service

Finally, you can select your best experiment and Publish it as a Scheduled Service which will score customers and their propensity to buy on a recurring basis.

Login to Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)

![DSW](./images/aeph.png)

From the left menu, click on **Models**.

![DSW](./images/mlmodels.png)

In this exercise, we'll use a prebuilt recipe to create a model for car insurance sales predictions.

In the top menu, click on **Recipes**.

![DSW](./images/recipes.png)

In Recipes, you'll find multiple recipes. Look for your own recipe in the list, which should be named `ldapCarInsurancePropensity`.

![DSW](./images/prrecipe.png)

Click the `ldapCarInsurancePropensity` recipe to open it.

![DSW](./images/prservice.png)

Click to open the Model you created in the previous exercise, `ldap - CarInsurancePropensity Model`.

You'll then see this:

![DSW](./images/prservice1.png)

Click the button **+ Publish**.

![DSW](./images/publish.png)

You then have to name your Service.

As a name, use `ldap` - Car Insurance Propensity Service.

In this example, for ldap `vangeluw`, the name should be `vangeluw - Car Insurance Propensity Service`.

![DSW](./images/publishservicename.png)

Click **Next**.

![DSW](./images/next.png)

In the next screen, you need to select a Training Run to run as part of this Service.

![DSW](./images/selecttrrun.png)

Next, click **Finish**.

![DSW](./images/finish.png)

Your service is now almost created.

![DSW](./images/serv.png)

Click **Set Schedule** to configure your schedule for this service.

Configure your schedule so that your Service runs in the weekend, on Saturday or Sunday. You can choose the time yourself.

![DSW](./images/servsch.png)

Next, you need to select the **Scoring Dataset** and the **Scoring Results Dataset**.

The **Scoring Dataset** should be `AEP Demo - Car Insurance Interactions`.

The **Scoring Results Dataset** should be `AEP Demo - ML Predictions`.

![DSW](./images/servsch2.png)

Next, click **Create**.

![DSW](./images/create.png)

And you're done. Your service is now created and the schedule is set.

![DSW](./images/createdone.png)

Next Step: [Summary & benefits](./summary.md)

[Go Back to Module 15](./data-science-workspace-car-insurance-sales-propensity.md)

[Go Back to All Modules](../../overview.md)
