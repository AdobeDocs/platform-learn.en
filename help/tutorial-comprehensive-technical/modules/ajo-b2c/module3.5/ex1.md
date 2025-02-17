---
title: Getting started with AJO Translation Services
description: Getting started with AJO Translation Services
kt: 5342
doc-type: tutorial
exl-id: 28c925dd-8a7b-4b9a-a128-ecbfbfbeaf04
---
# 3.5.1 Translations Provider

## 3.5.1.1 Configure Microsoft Azure Translator

Go to [https://portal.azure.com/#home](https://portal.azure.com/#home).

![Translations](./images/transl1.png)

In the search bar, enter `translators`. Then, click **+ Create**.

![Translations](./images/transl2.png)

Select **Create Translator**.

![Translations](./images/transl3.png)

Choose your **Subscription ID** and **Resource group**.
Set **Region** to **Global**.
Set **Pricing Tier** to **Free F0**.

Select **Review + create**.

![Translations](./images/transl4.png)

Select **Create**.

![Translations](./images/transl5.png)

Select **Go to resource**.

![Translations](./images/transl6.png)

In the left menu, go to **Resource Management** > **Keys and Endpoint**. Click to copy your key.

![Translations](./images/transl7.png)

## 3.5.1.2 Locale Dictionary

Go to [https://experience.adobe.com/](https://experience.adobe.com/). Click **Journey Optimizer**.

![Translations](./images/ajolp1.png)

In the left menu, go to **Translations** and then go to **Locale Dictionary**. If you see this message, click **Add Default Locales**.

![Translations](./images/locale1.png)

You should then see this.

![Translations](./images/locale2.png)

## 3.5.1.3 Configure Translations Provider in AJO

Go to [https://experience.adobe.com/](https://experience.adobe.com/). Click **Journey Optimizer**.

![Translations](./images/ajolp1.png)

In the left menu, go to **Translations** and then go to **Providers**. Click **Add Provider**.

![Translations](./images/transl8.png)

Under **Providers**, select **Microsoft Translator**. Check the checkbox to enable the usage of the translation provider. Paste the key you copied from Microsoft Azure Translators. Then, click **Validate Credentials**.

![Translations](./images/transl9.png)

Your credentials should then be successfully validated. If they are, scroll down to select the languages for translation.

![Translations](./images/transl10.png)

Make sure to select `[en-US] English`, `[es] Spanish`, `[fr] French`, `[nl] Dutch`.

![Translations](./images/transl11.png)

Scroll up and click **Save**.

![Translations](./images/transl12.png)

Your **Translations Provider** is now ready to be used.

![Translations](./images/transl13.png)

## 3.5.1.4 Configure Translations Project

Go to [https://experience.adobe.com/](https://experience.adobe.com/). Click **Journey Optimizer**.

![Translations](./images/ajolp1.png)

In the left menu, go to **Translations** and then go to **Locale Dictionary**. If you see this message, click **Create Project**.

![Translations](./images/ajoprovider1.png)

Enter the name `--aepUserLdap-- - Translations`, set the **Source Locale** to `[en-US] English - United States` and check the checkboxes to enable both **Automatically publish approved translations** and **Enable review workflow**. Next, click **+ Add a locale**.

![Translations](./images/ajoprovider1a.png)

Search for `fr`, enable the checkbox for `[fr] French` and then enable the checkbox for **Microsoft Translator**. Click **+ Add a locale**.

![Translations](./images/ajoprovider2.png)

Search for `es`, enable the checkbox for `[es] Spanish` and then enable the checkbox for **Microsoft Translator**. Click **+ Add a locale**.

![Translations](./images/ajoprovider3.png)

Search for `nl`, enable the checkbox for `[nl] Spanish` and then enable the checkbox for **Microsoft Translator**. Click **+ Add a locale**.

![Translations](./images/ajoprovider6.png)

Click **Save**.

![Translations](./images/ajoprovider8.png)

Your **Translations** project is now ready to be used.

![Translations](./images/ajoprovider9.png)

## 3.5.1.5 Configure Language Settings

Go to **Channels** > **General Settings** > **Language Settings**. Click **Create language settings**.

![Journey Optimizer](./images/camploc6.png)

Use the name `--aepUserLdap--_translations`. Select **Translation project**. Then, click the **edit** icon.

![Journey Optimizer](./images/camploc7.png)

Select the Translations Project that you created in the previous step. Click **Select**.

![Journey Optimizer](./images/camploc8.png)

You should then see this. Set the **Fallback preference** to **English - United Stats**. Click to select **Select profile language preferred attribute**, which will decide which field from the customer profile to use to load the translations. Then, click the **edit** icon to select which field will be used.

![Journey Optimizer](./images/camploc9.png)

Enter **preferred language** in the search bar, then select the field **Preferred language**.

![Journey Optimizer](./images/camploc10.png)

Click the **edit** icon for both **English - United States** and **Dutch** to review its configuration.

![Journey Optimizer](./images/camploc11.png)

Here's the configuration for **English - United States**. Click **Cancel**.

![Journey Optimizer](./images/camploc12.png)

Click to view the configuration for **Dutch**. Click **Cancel**.

![Journey Optimizer](./images/camploc13.png)

Scroll up and click **Submit**.

![Journey Optimizer](./images/camploc14.png)

Your language settings are now configured.

![Journey Optimizer](./images/camploc15.png)

You have finished this exercise.

## Next Steps

Go to [3.5.2 Create your Campaign](./ex2.md)

Go back to [Module 3.5](./ajotranslationsvcs.md){target="_blank"}

Go back to [All modules](./../../../overview.md){target="_blank"}
