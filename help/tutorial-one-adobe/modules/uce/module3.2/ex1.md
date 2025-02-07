---
title: Getting started with AJO Translation Services
description: Getting started with AJO Translation Services
kt: 5342
doc-type: tutorial
exl-id: ee0b8650-a59f-4888-8228-4caafe4143e4
---
# 3.2.1 Translations Provider

## 3.2.1.1 Configure Microsoft Azure Translator

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

## 3.2.1.2 Locale Dictionary

Go to [https://experience.adobe.com/](https://experience.adobe.com/). Click **Journey Optimizer**.

![Translations](./images/ajolp1.png)

In the left menu, go to **Translations** and then go to **Locale Dictionary**. If you see this message, click **Add Default Locales**.

![Translations](./images/locale1.png)

You should then see this.

![Translations](./images/locale2.png)

## 3.2.1.3 Configure Translations Provider in AJO

In the left menu, go to **Translations** and then go to **Providers**. Click **Add Provider**.

![Translations](./images/transl8.png)

Under **Providers**, select **Microsoft Translator**. Check the checkbox to enable the usage of the translation provider. Paste the key you copied from Microsoft Azure Translators. Then, click **Validate Credentials**.

![Translations](./images/transl9.png)

Your credentials should then be successfully validated. If they are, scroll down to select the languages for translation.

![Translations](./images/transl10.png)

Make sure to select `[es] Spanish`, `[fr] French`, `[nl] Dutch`.

![Translations](./images/transl11.png)

Scroll up and click **Save**.

![Translations](./images/transl12.png)

Your Translations Provider is now ready to be used.

![Translations](./images/transl13.png)

[Go Back to Module 3.2](./ajotranslationsvcs.md)

[Go Back to All Modules](../../../overview.md)
