---
title: Content Cards in Adobe Journey Optimizer
description: Content Cards in Adobe Journey Optimizer
kt: 5342
doc-type: tutorial
---
# 3.6.1 Content Cards

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxName--`. You'll then be in the **Home** view of your sandbox `--aepSandboxName--`.

![ACOP](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

## 3.6.1.1 Content Cards Channel configuration

In the left menu, go to **Channels** and then select **Channel configurations**. Click **Create channel configuration**.

![Content Cards](./images/contentcard1.png)

Enter the name: `--aepUserLdap--_Content_Cards_Web`, select the channel **Content Cards** and then enable the platform **Web**.

![Content Cards](./images/contentcard2.png)

Scroll down, and make sure that the option **Single page** is enabled.

Enter the URL of the website that was created earlier as part of the **Getting Started** module, which looks like this: `https://dsn.adobe.com/web/--aepUserLdap---XXXX`. Don't forget to change the **XXXX** to the unique code of your website.

>[!IMPORTANT]
>
>The above reference to your CitiSignal demo website URL `https://dsn.adobe.com/web/--aepUserLdap---XXXX` needs to be changed to your actual URL. You can find the URL by going to your website project on [https://dsn.adobe.com/](https://dsn.adobe.com/).

Set the field **Location on page** to `CitiSignalContentCardContainer`.

![Content Cards](./images/contentcard4.png)

Scroll up and click **Submit**.

![Content Cards](./images/contentcard5.png)

Your channel configuration is now ready to be used.

![Content Cards](./images/contentcard6.png)

## 3.6.1.2 Configure a scheduled campaign for Content Cards

In the left menu, go to **Campaigns** and then click **Create campaign**.

![InApp](./images/contentcard7.png)

Select **Scheduled - Marketing** and then click **Create**.

![InApp](./images/contentcard8.png)

Enter the name `--aepUserLdap-- - CitiSignal Fiber Max Content Cards` and then click **Actions**.

![InApp](./images/contentcard9.png)

Click **+ Add action** and then select **Content Card**.

![InApp](./images/contentcard10.png)

Select the content cards channel configuration that you created in the previous step, which is named: `--aepUserLdap--_Content_Cards_Web`. 

Next, click **Edit Rules**.

![InApp](./images/contentcard11.png)

Click the **X** to remove the current rule.

![InApp](./images/contentcard11b.png)

Click **+ Add Condition**.

![InApp](./images/contentcard11c.png)

Select the condition **Sent data to Platform**. Click **Done**

![InApp](./images/contentcard11d.png)

You should then see this. Click **Edit content**.

![InApp](./images/contentcard11e.png)

You should then see this.

![InApp](./images/contentcard12.png)

Configure the following settings:

- **Title**: `CitiSignal Fiber Max`
- **Body**: `Lightning speed for gamers`
- **Target URL**: `https://dsn.adobe.com/web/--aepUserLdap---XXXX/plans`

>[!IMPORTANT]
>
>The above reference to your CitiSignal demo website URL `https://dsn.adobe.com/web/--aepUserLdap---XXXX/plans` needs to be changed to your actual URL. You can find the URL by going to your website project on [https://dsn.adobe.com/](https://dsn.adobe.com/).

Click the icon to change the URL, by selecting an asset from AEM Assets.

![InApp](./images/contentcard13.png)

Go to the folder**citisignal-imaes** and select the file **`neon_rabbit_banner.jpg`**. Click **Select**.

![InApp](./images/contentcard14.png)

You should then have this. Click **+ Add button**.

![InApp](./images/contentcard15.png)

Configure the following settings for the button:

- **Button Title**: `Upgrade now!`
- **Interaction event**: `click`
- **Target**: `https://dsn.adobe.com/web/--aepUserLdap---XXXX/plans`

>[!IMPORTANT]
>
>The above reference to your CitiSignal demo website URL `https://dsn.adobe.com/web/--aepUserLdap---XXXX/plans` needs to be changed to your actual URL. You can find the URL by going to your website project on [https://dsn.adobe.com/](https://dsn.adobe.com/).

Click **Review to activate**.

![InApp](./images/contentcard16.png)

Click **Activate**.

![InApp](./images/contentcard17.png)

Your campaign will then be activated, which may take a couple of minutes.

![InApp](./images/contentcard18.png)

After a couple of minutes, your campaign will be live.

![InApp](./images/contentcard19.png)

## 3.6.1.3 Update your DSN website

In order to show the content card on the website, you need to make a change to the design of the homepage of your CitiSignal demo website.

Go to [https://dsn.adobe.com/](https://dsn.adobe.com/). Click the **3 dots** on your website and click **Edit**.

![InApp](./images/contentcard20.png)

Click to select the page **Home**. Click **Edit content**.

![InApp](./images/contentcard21.png)

Hover over the hero image and click the **+** button.

![InApp](./images/contentcard22.png)

Go to **General**, select **Banner** and then click **Add**.

![InApp](./images/contentcard23.png)

Click to select the newly created banner. Go to **Style** and enter `CitiSignalContentCardContainer` in the field **Custom CSS Classes**.

![InApp](./images/contentcard24.png)

Go to **Alignment**. Set the field **Alignment** to `left` and set the field **Vertical Alignment** to `middle`.

Click the **X** icon to close the dialog window.

![InApp](./images/contentcard25.png)

The changes to your website design have now been made.

If you open your site in a new browser window now, it should look like this. the gray area is the newly created banner, but it doesn't have any content yet.

![InApp](./images/contentcard25a.png)

To ensure the content is loaded dynamically in the newly created banner, a change is needed in your Data Collection Tags property.

## 3.6.1.4 Update your Data Collection Tags property

Go to [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/), to **Tags**. As part of the [Getting Started](./../../../../modules/getting-started/gettingstarted/ex1.md) module, Data Collection Tags properties were created. 

You've been using these Data Collection Tags properties already as part of previous modules. 

Click to open the Data Collection property for web.

![DSN](./images/launchprop.png)

In the left menu, go to **Rules** and click to open the rule **Page View**.

![InApp](./images/contentcard101.png)

Click the action **Send "Page View" Experience Event**. 

![InApp](./images/contentcard102.png)

As part of the **Page View** rule, it is required to request the personalisation instructions from the Edge for a specific surface. The surface is the banner that you configured in the previous step. To do that, scroll down to **Personalization** and enter `web://dsn.adobe.com/web/--aepUserLdap---XXXX#CitiSignalContentCardContainer` under **Surfaces**.

>[!IMPORTANT]
>
>The above reference to your CitiSignal demo website URL `web://dsn.adobe.com/web/--aepUserLdap---XXXX#CitiSignalContentCardContainer` needs to be changed to your actual URL. You can find the URL by going to your website project on [https://dsn.adobe.com/](https://dsn.adobe.com/).

Click **Keep Changes**.

![InApp](./images/contentcard103.png)

Click **Save** or **Save to Library**.

![InApp](./images/contentcard104.png)


In the left menu, go to **Rules** and click **Add rule**.

![InApp](./images/contentcard26.png)

Enter the name: `Display AJO Content Cards`. Click **+ Add** to add a new event.

![InApp](./images/contentcard27.png)

Select the **extension**: **Adobe Experience Platform Web SDK**, and the select the **Event Type**: **Subscribe ruleset items**.

Under **Schemas**, select **Content Card**.

Under **Surfaces**, enter `web://dsn.adobe.com/web/--aepUserLdap---XXXX#CitiSignalContentCardContainer`

>[!IMPORTANT]
>
>The above reference to your CitiSignal demo website URL `web://dsn.adobe.com/web/--aepUserLdap---XXXX#CitiSignalContentCardContainer` needs to be changed to your actual URL. You can find the URL by going to your website project on [https://dsn.adobe.com/](https://dsn.adobe.com/).

Click **Keep Changes**.

![InApp](./images/contentcard28.png)

You should then see this. Click **+ Add** to add a new action.

![InApp](./images/contentcard29.png)

Select the **Extension**: **Core**, and select the **Action Type**: **Custom Code**.

Enable the checkbox for the **Language**: **JavaScript** and then click **Open Editor**.

![InApp](./images/contentcard30.png)

You should then see an empty editor window.

![InApp](./images/contentcard31.png)

Paste the below code into the editor, and click **Save**.

```javascript
if (!Array.isArray(event.propositions)) {
  console.log("No personalization content");
  return;
}

console.log(">>> Content Card response from Edge: ", event.propositions);

event.propositions.forEach(function (payload) {
  payload.items.forEach(function (item) {
    if (!item.data || !item.data.content || item.data.content === "undefined") {
      return;
    }
    console.log(">>> Content Card response from Edge: ", item);
    const { content } = item.data;
    const { title, body, image, buttons } = content;
    const titleValue = title.content;
    const description = body.content;
    const imageUrl = image.url;
    const buttonLabel = buttons[0]?.text.content;
    const buttonLink = buttons[0]?.actionUrl;
    const html = `<div  class="Banner Banner--alignment-left Banner--verticalAlignment-left hero-banner ContentCardContainer"  oxygen-component-id="cmp-0"  oxygen-component="Banner"  role="presentation"  style="color: rgb(255, 255, 255); height: 60%;">  <div class="Image" role="presentation">    <img src="${imageUrl}" style="object-fit: cover; height: 100%"    />  </div>  <div class="Banner__content">    <div class="Title Title--alignment-left Title--textAlignment-left">      <div class="Title__content" role="presentation">        <strong class="Title__pretitle">${titleValue}</strong>        <h2>${description}</h2>      </div>    </div>    <div class="Button Button--alignment-left Button--variant-cta">              <button          class="Dniwja_spectrum-Button Dniwja_spectrum-BaseButton Dniwja_i18nFontFamily Dniwja_spectrum-FocusRing Dniwja_spectrum-FocusRing-ring"          type="button"          data-variant="accent"          data-style="fill"          onclick="window.open('${buttonLink}')"       style="color:#FFFFFF;padding: 12px 28px;font-size: 24px;font-family: adobe-clean;font-weight: bolder;" >          <span            id="react-aria5848951631-49"            class="Dniwja_spectrum-Button-label"            >${buttonLabel}</span          >        </button>            </div>  </div></div>`;
    if (document.querySelector(".CitiSignalContentCardContainer")) {
      const contentCardContainer = document.querySelector(
        ".CitiSignalContentCardContainer"
      );
      contentCardContainer.innerHTML = html;
      contentCardContainer.style.height = "60%";
    }
  });
});
```

![InApp](./images/contentcard32.png)

Click **Keep Changes**.

![InApp](./images/contentcard33.png)

Click **Save** or **Save to Library**.

![InApp](./images/contentcard34.png)

In the left menu, go to **Publishing Flow** and click to open the **Main** library.

![InApp](./images/contentcard35.png)

Click **Add All Changed Resources** and then click **Save & Build to Development**.

![InApp](./images/contentcard36.png)

## 3.6.1.5 Test your content card on your website

Go to [https://dsn.adobe.com](https://dsn.adobe.com). After logging in with your Adobe ID, you'll see this. Click the 3 dots **...** on your website project and then click **Run** to open it.

![DSN](./../../datacollection/dc1.1/images/web8.png)

You'll then see your demo website open up. Select the URL and copy it to your clipboard.

![DSN](../../../getting-started/gettingstarted/images/web3.png)

Open a new incognito browser window.

![DSN](../../../getting-started/gettingstarted/images/web4.png)

Paste the URL of your demo website, which you copied in the previous step. You'll then be asked to login using your Adobe ID.

![DSN](../../../getting-started/gettingstarted/images/web5.png)

Select your account type and complete the login process.

![DSN](../../../getting-started/gettingstarted/images/web6.png)

You should now the CitiSignal website being loaded, and the content card that you configured should now be shown instead of the empty gray area that you had there before.

![InApp](./images/contentcard37.png)

## Next Steps

Go to [3.6.2 Landing Pages](./ex2.md)

Go back to [Adobe Journey Optimizer: Content Management](./ajocontent.md){target="_blank"}

Go back to [All modules](./../../../../overview.md){target="_blank"}
