---
title: Module 0, Exercise 1 - Setup of Webserver and Website
description: 
kt: 5342
audience: 
doc-type: tutorial
activity: 
---

# Exercise 1: Setup of Webserver and Website

In this exercise, the goal is to install the AEP Demo-website.

## Exercise 1.1 - Download and Install MAMP

MAMP is a free web server which we will use for this enablement.

Go to [https://www.mamp.info/en/](https://www.mamp.info/en/) and install MAMP (Free Edition).

MAMP comes in 2 versions: Free and Pro. For this enablement we'll be using the Free version.

**For Mac Users:** install MAMP with all default settings.

**For Windows Users:** during the installation of MAMP, you can also choose to install MAMP Pro. We will not be using MAMP Pro as part of this enablement so do not install MAMP Pro.

![MAMP Setup](./images/win_mamppro.png)

Configuration of MAMP will be done in the next exercise.

## Exercise 1.2 - Download Demo Site Package

Download the [AEP Demo-website zip package](../../assets/website/sytycd_demo_site.zip) to your computer, unzip it in a directory of your choice, f.i. on your Desktop:

![MAMP Setup](./images/mamp_app6.png)

## Exercise 1.3 - Setup Demo Site

**Mac:** Go to Launchpad and click on the grey MAMP-icon to start MAMP.

**Windows:** Go to your Windows Desktop and double-click on the grey MAMP-icon to start MAMP.

![MAMP Setup](./images/mamp.png)

MAMP will start and you'll see the below screen.

![MAMP Setup](./images/mamp1.png)

Click on Start Servers to start MAMP.

![MAMP Setup](./images/mamp2.png)

Servers are now running, and you can access the Start Page by clicking on ``Open WebStart page``.

![MAMP Setup](./images/mamp_localhost.png)

MAMP has a default website installed on a specific location on your computer. We need to replace the default website with our SYTYCD website.

**Mac:** On your MacBook, go to ``Applications`` and locate the ``MAMP`` folder in the Applications list.

**Windows:** On you Windows machine, go directly to ``C:\MAMP\htdocs``

![MAMP Setup](./images/mamp_app1.png)

**Only for Mac:** Double-click to go in the MAMP-folder.

![MAMP Setup](./images/mamp_app2.png)

**Only for Mac:** Open the folder ``htdocs``.

![MAMP Setup](./images/mamp_app3.png)

**Fot both Windows and Mac:** Delete all files in this folder.

![MAMP Setup](./images/mamp_app4.png)

Go to the folder where you unzipped the zip-package of the SYTYCD - website. Copy all files and paste them in the ``htdocs`` folder.

![MAMP Setup](./images/mamp_app6.png)
![MAMP Setup](./images/mamp_app7.png)

Go back to your web browser.

![MAMP Setup](./images/mamp_localhost.png)

Click on ``My Website`` to navigate to the AEP Demo-website.

You'll be redirected to the ``Admin`` - homepage.

![MAMP Setup](./images/mamp_boutique_admin1.png)

On the ``Admin`` - homepage, click on ``Select LDAP``. Select your LDAP and click ``Save``.

![MAMP Setup](./images/mamp_boutique_admin1a.png)

On the ``Admin`` - homepage, click on ``Select Brand``. On the ``Select Brand`` - page, select the brand ``Luma Retail`` from the dropdown-list. Click ``Save``.

![MAMP Setup](./images/mamp_boutique_admin3.png)

You'll then be redirected to the ``Admin``-homepage. Click the ``Luma``-logo to open the website.

![MAMP Setup](./images/mamp_boutique_admin3a.png)

You should now see this website:

![MAMP Setup](./images/mamp_boutique.png)

You can always Start and Stop MAMP by going back to the MAMP Application:

![MAMP Setup](./images/mamp2.png)

One you've started your web server, you can directly access the AEP Demo-website by going to [http://localhost:8888/index.html](http://localhost:8888/index.html).

If the AEP Demo-website is displayed and your demo brand is loaded successfully, then you've completed this exercise.

Congratulations!

Next Step: [Exercise 2 - Install the Mobile Application (iOS)](./ex2.md)

[Go Back to Module 0](README.md)

[Go Back to All Modules](../../README.md)
