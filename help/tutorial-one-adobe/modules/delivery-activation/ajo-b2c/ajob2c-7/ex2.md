---
title: Offer Decisioning - Configure your Offers and Decision ID
description: Offer Decisioning - Configure your Offers and Decision ID
kt: 5342
doc-type: tutorial
---
# 3.7.2 Configure your offers and decision

## 3.7.2.1 Create your personalized offers

In this exercise, you'll create four **Personalized Offers**. Here are the details to take into account when creating those offers:

|Name | Date Range | Image Link for Email | Image Link for Web | Text | Priority | Eligibility  | Language| Capping Frequency| Image Name|
|-----|------------|----------------------|--------------------|------|:--------:|--------------|:-------:|:-------:|:-------:|
|`--aepUserLdap-- - AirPods Max` | today - 1 month later | https://bit.ly/4a9RJ5d | Choose from Assets Library |`{{ profile.person.name.firstName }}, 10% discount on AirPods Max`| 25 | all - Female Customers   | English (United States) | 3|Apple AirPods Max- Female.jpg|
|`--aepUserLdap-- - Galaxy S24` | today - 1 month later  | https://bit.ly/3W8yuDv | Choose from Assets Library|`{{ profile.person.name.firstName }}, 5% discount on Galaxy S24`| 15 | all - Female Customers   | English (United States) | 3| Galaxy S24 – Female.jpg|
|`--aepUserLdap-- - Apple Watch` | today - 1 month later | https://bit.ly/4fGwfxX | https://bit.ly/4fGwfxX|`{{ profile.person.name.firstName }}, 10% discount on Apple Watch`| 25 | all - Male Customers | English (United States) | 3| Apple Watch - Male.jpg|
|`--aepUserLdap-- - Galaxy Watch 7` | today - 1 month later | https://bit.ly/4gTrkeo | Choose from Assets Library| `{{ profile.person.name.firstName }}, 5% discount on Galaxy Watch 7`| 15 | all - Male Customers  | English (United States) | 3| Galaxy Watch7 - Male.jpg|

{style="table-layout:auto"}

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxName--`. You'll then be in the **Home** view of your sandbox `--aepSandboxName--`.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

## Next Steps

Go to [3.7.3 Web SDK setup for Experience Decisioning](./ex3.md){target="_blank"}

Go back to [Experience Decisioning](ajo-decisioning.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
