---
title: Getting Started - Install the Chrome extension for the Experience League documentation
description: Getting Started - Install the Chrome extension for the Experience League documentation
kt: 5342
doc-type: tutorial
exl-id: da7aa686-7f25-49fd-af3e-d243ffda025f
---
# Install the Chrome extension for the Experience League documentation

## About the Chrome extension

The documentation has been made generic so that it can easily be reused by anyone, using any Adobe Experience Platform instance. 
In order to make the documentation reusable, **Environment Variables** were introduced in the documentation, which means that you'll find the below **placeholders** in the documentation. Every placeholder is a specific variable for a specific environment, and the Chrome extension will change that variable for you to make it easy for you to copy code and text from the tutorial pages and paste it in the various user interfaces that you'll be using as part of the tutorial.

An example of such values can be found below. Currently, these values can't be used yet but as soon as you install and activate the Chrome extension, you'll see these variables change into normal text that you can copy and reuse.

| Name     | Key | Example |
|:-------------:| :---------------:| :---------------:|
| AEP IMS Org ID         | `--aepImsOrgId--` |`907075E95BF479EC0A495C73@AdobeOrg`|
| AEP IMS Org Name         | `--aepImsOrgName--` |`Experience Platform International`|
| AEP Tenant ID         | `--aepTenantId--` | `_experienceplatform` |
| AEP Sandbox Name         | `--aepSandboxName--` | `tech-insiders` |
| Learner Profile LDAP        | `--aepUserLdap--` | `vangeluw`|

As an example, in the below screenshot you can see a reference to `aepTenantId`.

![DSN](./images/mod7before.png)

Once the extension is installed, that same text will be changed automatically to reflect your instance-specific values.

![DSN](./images/mod7.png)

## Install the Chrome extension

To install that Chrome extension, open your Chrome browser and go to: [https://chromewebstore.google.com/detail/tech-insiders-learning-fo/hhnbkfgioecmhimdhooigajdajplinfi](https://chromewebstore.google.com/detail/tech-insiders-learning-fo/hhnbkfgioecmhimdhooigajdajplinfi). You'll then see this. 

Click **Add to Chrome**. 

![DSN](./images/c2.png)

You'll then see this. Click **Add extension**.

![DSN](./images/c3.png)

The extension will then be installed, and you'll see a similar notification.

![DSN](./images/c4.png)

In the **extensions** menu, click the **puzzle piece** icon and pin the **Platform Learn - Configuration** extension to the extension menu.

![DSN](./images/c6.png)

## Configure the Chrome extension

Go to [https://experienceleague.adobe.com/en/docs/platform-learn/tutorial-comprehensive-technical/overview](https://experienceleague.adobe.com/en/docs/platform-learn/tutorial-comprehensive-technical/overview) and then click the extension icon to open it.

![DSN](./images/tuthome.png)

You'll then see this popup. Click the **+** icon.

![DSN](./images/c7.png)

Enter the values as indicated below, which are all related to your Adobe Experience Platform instance. 

![DSN](./images/c8.png)

If you aren't sure what values to enter for these fields, follow the below guidance.

**Adobe Experience Platform IMS Org Name**

When you log in to your Adobe Experience Platform instance on [https://platform.adobe.com/](https://platform.adobe.com/), you'll find the name of your instance in the top right corner of your screen.

![DSN](./images/aepname.png)

**Adobe Experience Platform IMS Org ID**

The IMS Org ID is the unique identifier for your Adobe Experience Cloud instance, and it's referenced in multiple locations throughout this tutorial.

Finding your IMS Org ID can be done in multiple ways. If you're not sure, check with one of the system administrators of your instance to find the ID.

You may be able to find it by going to [Admin Console](https://adminconsole.adobe.com/), where you can find it as part of the URL.

![DSN](./images/aepid1.png)

You may also be able to find it by going to **Data Management > Queries** in your Adobe Experience Platform menu, where you can find it under **Username**.

![DSN](./images/aepid2.png)

Please ensure to copy and paste the **@AdobeOrg** part along with the ID.

**Adobe Experience Platform Tenant ID**

Your Tenant ID is the unique identifier for your organisation's Adobe Experience Platform instance. When you log in to your Adobe Experience Platform instance on [https://platform.adobe.com/](https://platform.adobe.com/), you'll find the tenant id in the URL.

![DSN](./images/aeptenantid.png)

When you enter it in the Chrome extension, you should ensure that an underscore is added as a prefix, so in this example **experienceplatform** becomes **_experienceplatform**. Also, make sure to remove the **@** symbol when copying from the URL.

**Adobe Experience Platform Sandbox Name**

Your sandbox name is the name of the environment you'll be using in your Adobe Experience Platform instance. When you log in to your Adobe Experience Platform instance on [https://platform.adobe.com/](https://platform.adobe.com/), you'll find the tenant id in the URL. 

Before taking the sandbox name from the URL, you should ensure you're in the sandbox that you should use for this tutorial. You can switch to the right sandbox by clicking the sandbox switcher menu in the top right corner of your screen.

![DSN](./images/aepsandboxsw.png)

In this example, the Adobe Experience Platform Sandbox Name is **tech-insiders**.

![DSN](./images/aepsname.png)

**Your LDAP**

This is the username that will be used as part of the tutorial. In this example, the LDAP is based off of the email address of this user. The email address is **vangeluw@adobe.com** so the LDAP becomes **vangeluw**.

The LDAP is used to ensure that the configuration you'll be doing will be linked to you, and won't conflict with other users that may be using the same instance and sandbox that you're using.

Your valus should look similar to these.
Finally, click **Create New**.

![DSN](./images/c8a.png)


In the left menu of the extension, you'll now see a new icon with the initials of your environment. Click it. You'll then see the mapping between the **Environment Variables** and your specific Adobe Experience Platform instance values. Click **Activate Configuration**.

![DSN](./images/c9.png)

After activating your configuration, you'll see a green dot next to the initials of your environment. This means that your environment is now active.

![DSN](./images/c10.png)

## Verify tutorial content

As a test, go to [this page](https://experienceleague.adobe.com/en/docs/platform-learn/tutorial-comprehensive-technical/datadistiller/module51/ex4).

You should now see that all **Environment Variables** have been replaced by their true values, based on the activated environment in the chrome extension.

You should now have a similar view to the below, where the environment variable `aepTenantId` has been replaced by your real Adobe Experience Platform Tenant ID, which in this case is **_experienceplatform**. 

![DSN](./images/mod7.png)

Next Step: [Use Demo System Next to setup your Adobe Experience Platform Data Collection client property](./ex2.md)

[Go Back to Getting Started](./getting-started.md)

[Go Back to All Modules](./../../../overview.md)
