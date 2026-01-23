---
title: CJA & ChatGPT with MCP server
description: CJA & ChatGPT with MCP server
kt: 5342
doc-type: tutorial
---
# 1.5.1 CJA & ChatGPT with MCP server

>[!IMPORTANT]
>
>This lab uses a feature that hasn't been released yet. The feature is still being developed so it isn't generally available yet.


>[!NOTE]
>
>This exercise on setting up and using an MCP Server with ChatGPT to connect to CJA is related to this exercise [1.1 Customer Journey Analytics: Build a dashboard using Analysis Workspace on top of Adobe Experience Platform](./../../../modules/reporting-insights/cja-b2c/cjab2c-1/customer-journey-analytics-build-a-dashboard.md). The CJA dataview and connection that is being used in the below exercise is the dataview and connection that was set up in that exercise. If you want to replicate the below results,  you should follow those instructions first.

## Video

In this video, you'll get an explanation and demonstration of all the steps involved in this exercise.

>[!VIDEO](https://video.tv.adobe.com/v/3479159?quality=12&learn=on)

## 1.5.1.1 Create custom app in ChatGPT for CJA 

>[!NOTE]
>
>Using CJA in ChatGPT requires the following:
>- a paid version of OpenAI's ChatGPT
>- using the ChatGPT web client

Go to [https://chatgpt.com/](https://chatgpt.com/){target="_blank"} and log in using your account details. Once you're logged in, you should see this. Click your username.

![ChatGPT](./images/chatgpt1.png)

Select **Settings**.

![ChatGPT](./images/chatgpt2.png)

Go to **Apps** and then select **Advanced settings**.

![ChatGPT](./images/chatgpt3.png)

Turn on **Developer mode** and then click **Back**.

![ChatGPT](./images/chatgpt4.png)

Click **Create app**.

![ChatGPT](./images/chatgpt5.png)

Fill out the fields like this:

- **Name**: `CJA`
- **MCP Server URL**: check with your Adobe representative
- **Authentication**: `OAuth`

Check the checkbox for **I understand and want to continue**.

Click **Create**.

![ChatGPT](./images/chatgpt6.png)

Once you've logged in successfully, you should see that your CJA app is now connected successfully.

![ChatGPT](./images/chatgpt8.png)

## 1.5.1.2 Set context in CJA 

Close this window.

![ChatGPT & CJA](./images/chatgpt9.png)

You should then see this. Click the **+** icon, go to **More** and then select **CJA**.

![ChatGPT & CJA](./images/chatgpt10.png)

Before interacting further with CJA through ChatGPT, the context needs to be set.

For this exercise, the context needs to be set to use:

- **Dataview**: **--aepUserLdap-- - Omnichannel Data View**

The Dataview setting helps to identify which dataview ChatGPT should look at when asking questions.

Enter the following **Prompt** and click the **send** button.

```javascript
list dataviews
```

![ChatGPT & CJA](./images/chatgpt11.png)

You should then see a similar list of available dataviews. 

![ChatGPT & CJA](./images/chatgpt11a.png)

To change that to the dataview that needs to be used, enter the following **Prompt** and click the **send** button.

```javascript
switch to dataview --aepUserLdap-- - Omnichannel Data View
```

![ChatGPT & CJA](./images/chatgpt12.png) 

You should then see this.

![ChatGPT & CJA](./images/chatgpt16.png)

Your context is now properly set, so you can start sending specific prompts next.

## 1.5.1.3 Explore the dataview

>[!NOTE]
>
>The dataview being used here has been set up as part of exercise [Create a dataview](./../../../modules/reporting-insights/cja-b2c/cjab2c-1/ex3.md). 

Enter the following **Prompt** and click the **send** button to explore which metrics and dimensions are available to you.

```javascript
list the available metrics and dimensions
```

![ChatGPT & CJA](./images/chatgpt101.png)

You should then see this response, which includes the metrics and dimensions that were set up as part of the exercise [Create a dataview](./../../../modules/reporting-insights/cja-b2c/cjab2c-1/ex3.md). 

![ChatGPT & CJA](./images/chatgpt102.png)

## 1.5.1.4 Freeform Table - Product Views

You can now start exploring the data. Start by entering the below prompt and click **send** to submit your report request.

```javascript
how many product views happened on January 21?
```

![ChatGPT & CJA](./images/chatgpt103.png)

Select **RunReport**.

![ChatGPT & CJA](./images/chatgpt104.png)

You should then see a response like this.

![ChatGPT & CJA](./images/chatgpt105.png)

You can now break down the response by adding a dimension. Enter the following **prompt** and click the **send** button.

```javascript
break down product views by product name
```

![ChatGPT & CJA](./images/chatgpt106.png)

You should then see a response like this.

![ChatGPT & CJA](./images/chatgpt107.png)

You can now also create a visualization. Enter the following **prompt** and click the **send** button.

```javascript
create a line visualization by hour for product views on January 21
```

![ChatGPT & CJA](./images/chatgpt108.png)

Select **UpsertProject**.

![ChatGPT & CJA](./images/chatgpt109.png)

Select **RunReport**.

![ChatGPT & CJA](./images/chatgpt110.png)

You should then see this.

![ChatGPT & CJA](./images/chatgpt111.png)

Scroll down.

![ChatGPT & CJA](./images/chatgpt112.png)

You can now also download this line graph. Enter the following **prompt** and click the **send** button.

```javascript
export this chart to PNG
```

![ChatGPT & CJA](./images/chatgpt113.png)

You should then see this. Click **Download the PNG**.

![ChatGPT & CJA](./images/chatgpt114.png)

Enter the following **prompt** and click the **send** button.

```javascript
can you breakdown product views by user agent?
```

![ChatGPT & CJA](./images/chatgpt115.png)

Select **RunReport**.

![ChatGPT & CJA](./images/chatgpt116.png)

You should then see this.

![ChatGPT & CJA](./images/chatgpt117.png)

## 1.5.1.5 Fallout Visualization

Enter the following **prompt** and click the **send** button.

```javascript
can you create a fallout visualization for the product interaction funnel, starting with all traffic and then in the next steps add Product Views, Add to Cart and purchases?
```

![ChatGPT & CJA](./images/chatgpt118.png)

Select **UpsertProject**.

![ChatGPT & CJA](./images/chatgpt119.png)

Select **RunReport**.

![ChatGPT & CJA](./images/chatgpt120.png)

You should then see something like this. Enter the following **prompt** and click the **send** button.

```javascript
can you show me a visualization of the above fallout analysis?
```

![ChatGPT & CJA](./images/chatgpt120a.png)

Click **Download the PNG**.

![ChatGPT & CJA](./images/chatgpt121.png)

You now see the visualization of your fallout analysis.

![ChatGPT & CJA](./images/chatgpt122.png)

Enter the following **prompt** and click the **send** button.

```javascript
break down the fallout analysis at the touchpoint of the add to carts
```

![ChatGPT & CJA](./images/chatgpt123.png)

Select **RunReport**.

![ChatGPT & CJA](./images/chatgpt124.png)

Go Back to [Analytics & Agents](./analyticsagents.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}