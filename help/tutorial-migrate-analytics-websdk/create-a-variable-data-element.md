---
title: Create a Variable data element
description: Add a data element that will be built up over multiple rules and then sent in to the Edge Network and forwarded to Adobe Analytics
solution: Data Collection, Analytics
feature: Web SDK
jira: KT-16759
exl-id: 0f7f011b-da40-451c-ba01-302f3af18aa6
TQID: https://experienceleague.adobe.com/EzgKbPi9ZZ6bxvXEGCb9lmv0xyqiQZT8PMFy-1qHZvU
product_v2:
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
    internal-label: Analytics
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
    internal-label: Measurement
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
---
# Create a Variable data element

Add a data element that will be built up over multiple rules and then sent in to the Edge Network and forwarded to Adobe Analytics.

This data element will create the "Data" object, which will be used to pass Adobe Analytics variables (props, eVars, events, etc.) back into Adobe Analytics and Adobe Target. So, just like building up the "s object" in an AppMeasurement implementation in Analytics, we will build up this type:Variable object to be accessed and updated across rules, and it can be used to populate props and eVars into Analytics.

1. In the data collection interface, click **Data Elements** in the left-hand navigation. 

    You'll be taken to the data elements landing page where you'll see all of your pre-existing data elements. We need to create a new data element to facilitate the migration. Click **Add Data Element**.

    ![Add data element](assets/add-new-data-alement.jpg)

1. Configure your Data Element.
    1. Name your data element whatever you want to - something that will help you remember that this is building out the data on your page, and that this will be the type "Variable." For this tutorial, we will call it **Page View Data Variable**.
    1. Select **Adobe Experience Platform Web SDK** from the Extension drop-down. 
    1. Select **Variable** from the **Data Element Type** drop-down.  
    1. In the right-hand panel, select the **Data** radio button.  
    1. Check the **Adobe Analytics** solution and either of the other solutions that you are migrating as well, E.g. **Adobe Target** showing in this screenshot.  
1. Click **Save**. 

    ![Configure variable data element](assets/configure-variable-data-element.jpg)
