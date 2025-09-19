---
title: Connect ACCS to AEM Assets CS
description: Connect ACCS to AEM Assets CS
kt: 5342
doc-type: tutorial
---
# 1.5.3 Connect ACCS to AEM Assets CS

>[!IMPORTANT]
>
>In order to complete this exercise, you need to have access to a working AEM Sites and Assets CS with EDS environment. 
>
>If you don't have such an environment yet, go to exercise [Adobe Experience Manager Cloud Service & Edge Delivery Services](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"}. Follow the instructions there, and you'll have access to such an environment.

>[!IMPORTANT]
>
>If you have previously configured an AEM CS Program with an AEM Sites and Assets CS environment, it may be that your AEM CS sandbox was hibernated. Given that dehibernating such a sandbox takes 10-15 minutes, it would be a good idea to start the dehibernation process now so that you don't have to wait for it at a later time.

![ACCS+AEM Assets](./images/accsaemassets1.png)


## 1.5.3.4 Update config.json

Add the below code snippet under line 6 `"ac-environment-id":XXX`:

```json
 "commerce-assets-enabled": "true",
```
 


Next Step: [Summary & Benefits](./summary.md){target="_blank"}

Go Back to [Adobe Commerce as a Cloud Service](./accs.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
