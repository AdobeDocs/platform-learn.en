---
title: Implement Brand Concierge using Data Collection Tags
description: Implement Brand Concierge using Data Collection Tags
kt: 5342
doc-type: tutorial
---
# 1.4.3 Implement Brand Concierge using Data Collection Tags

>[!IMPORTANT]
>
>This exercise is being worked on and isn't finished yet.

## Data Collection Tags property

Brand Concierge needs to send data to Adobe Experience Platform. To do that, Web SDK (or alloy.js) needs to be deployed to your website. 

To make that possible, you now need to create a Data Collection Tags property.

Go to [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Open **Data Collection**.

![Brand Concierge](./images/aep101.png)

Click **New Property**.

![Brand Concierge](./images/aep102.png)

Enter the name: `--aepUserLdap-- - CitiSignal Website + Brand Concierge` and also enter the domain of your website.

Click **Save**.

![Brand Concierge](./images/aep103.png)

Search for your property and then open it.

![Brand Concierge](./images/aep104.png)

Go to **Extensions** and then to **Catalog**.

![Brand Concierge](./images/aep105.png)

Search for `web sdk` and then click the extension **Adobe Experience Platform Web SDK**. Click **Install**.

![Brand Concierge](./images/aep106.png)

You should then see this. You only need to provide the details for your datastream here. To do that, scroll down a little bit.

![Brand Concierge](./images/aep107.png)

For all 3 environments **Production**, **Staging** and **Development**, please select the following:

- **Sandbox**: `--aepUserLdap-- - bc`
- **Datastream**: `--aepUserLdap-- - Brand Concierge`

Clck **Save**.

![Brand Concierge](./images/aep108.png)

You should then see this. Go to **Rules**.

![Brand Concierge](./images/aep108a.png)

Click **Create New Rule**.

![Brand Concierge](./images/aep109.png)

Enter the name: `Homepage`. Then, click **+ Add** under **EVENTS**.

![Brand Concierge](./images/aep110.png)

Select the following options:

- **Extension**: **Core**
- **Event Type**: **Library Loaded (Page Top)**

Click **Keep Changes**.

![Brand Concierge](./images/aep111.png)

You should then see this. Click **+ Add** under **CONDITIONS**.

![Brand Concierge](./images/aep112.png)

Select the following options:

- **Logic Type**: **Regular**
- **Extension**: **Core**
- **Condition Type**: **Path Without Query String**
- **path equals ...**: enter your website domain, in this case `https://vangeluw.adobedemosystem.com/`

Click **Keep Changes**.

![Brand Concierge](./images/aep113.png)

You should then see this. Click **+ Add** under **ACTIONS**.

![Brand Concierge](./images/aep114.png)

Select the following options:

- **Extension**: **Core**
- **Action Type**: **Custom Code**
- **Language**: **JavaScript**

Click **Open Editor**.

![Brand Concierge](./images/aep115.png)

Paste the following code:

```javascript
window["alloy"]("sendEvent", {
        conversation: {fetchConversationalExperience: true}
    }).then(result=> {
        console.log("Conversation experience fetched", result);
        window["alloy"]("bootstrapConversationalExperience", {
            selector: "#brand-concierge-mount",
						// src: "main.js",
            src: "https://experience-stage.adobe.net/solutions/experience-platform-brand-concierge-web-agent/static-assets/main.js",
            stylingConfigurations: window.styleConfiguration,
						stickySession: true
        })
    });
```

Click **Save**.

![Brand Concierge](./images/aep116.png)

You should then see this. Click **Keep Changes**.

![Brand Concierge](./images/aep117.png)

You should then see this. Click **Save**.

![Brand Concierge](./images/aep118.png)

Go to **Publishing Flow**. Click **Add Library**.

![Brand Concierge](./images/aep119.png)

Enter the name: `Dev`, select **Development (development)** for the environment and then click **Add All Changed Resources**.

Click **Save & Build for Development**.

![Brand Concierge](./images/aep120.png)

After a couple of minutes your library will be built. Wait until you see the **green dot** next to **Dev**. Then, go to **Environments**.

![Brand Concierge](./images/aep121.png)

Click the **Install** icon for the **Development** environment.

![Brand Concierge](./images/aep122.png)

You shoudl then see this. Click the **copy** button to copy the path of your library. You will need to implement this on your website.

The library path should look like this: 
`<script src="https://assets.adobedtm.com/XXXXXXX/XXXXXXXX/launch-XXXXXXXXX-development.min.js" async></script>`

![Brand Concierge](./images/aep123.png)

Go Back to [Brand Concierge](./brandconcierge.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}