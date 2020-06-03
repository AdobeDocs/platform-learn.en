# Exercise 15.1 - Introduction to Luma Insurance

In this exercise, you'll learn how to use the Luma Insurance Demo Brand and how to demo the Real-time ML Use-Case.

## Business Context

Luma Insurance is a typical Insurance Company with a big offline dealer-network and a website with lots of traffic.
Luma Insurance has been trying to personalize their digital communication for years, but it’s very hard to personalize anything if you don’t know who you’re speaking to. As most of the traffic on the website is from unknown, anonymous users who only visit the website once or twice, it’s difficult for Luma Insurance to build out a deep customer profile.

Most of these unknown, anonymous visitors only come to the website with one goal: get a quick indication of the cost of an insurance, by filling out a form which then gives them an idea of the insurance cost.

Because of this limited amount of information, Luma Insurance has a hard time optimizing any kind of digital campaign which leads to prospects being bombarded with irrelevant and inconsistent messaging.

As a consequence, Luma Insurance can’t understand which customer are interesting targets and which customers aren’t, they’re unable to optimize their ad spend and they’re unable to understand which channels are best used to interact with any given customer.

Let's have a look at the demo scenario.

## Demo Scenario

Open your AEP Demo-website.

You'll be redirected to the Admin Homepage.

![LumaBank](./images/1.png)

You first need to select your LDAP.

Go to ``Select LDAP``.

![LumaBank](./images/2a.png)

From the list, search and select your LDAP and click ``Save``. Wait 3 seconds until you're back on the Admin Homepage.

Next, go to ``Select Brand``.

![LumaBank](./images/2.png)

From the list, select ``Luma Insurance`` and click ``Save``.

After 10 seconds, Luma Insurance will be loaded and you'll be redirected to the Admin Homepage.

![LumaBank](./images/4.png)

From the Admin Homepage, click the ``Luma``-logo to go to the demo website.

![LumaBank](./images/4a.png)

From the Luma Insurance homepage, scroll down to see the Luma Insurance ``product`` that allows you to report a claim.

![LumaBank](./images/5.png)

The ``Luma Insurance`` - demo brand also allows you to visit pages like ``Car Insurance``, ``Travel Insurance`` and ``Household Insurance``.

Go to the ``Car Insurance``-page.

![LumaBank](./images/6.png)

Go back to the Luma Insurance homepage and open the Xray-panel, go to Experience Events.

![LumaBank](./images/6a.png)

``Luma Insurance``offers a standard template for the Insurance-industry, which includes a Car Insurance Simulator and also, Sensei Services with Real-time Machine Learning (RTML).

Let's have a look at that template. Click on the ``Get A Car Insurance Quote`` - menu option.

![LumaBank](./images/7a.png)

You'll then be redirected to the ``Get A Car Insurance Quote`` - page and you'll be able to start the Car Insurance process.

![LumaBank](./images/7b.png)

Just like in reality, at this moment, you're an unknown, anonymous customer to ``Luma Insurance``. Unknown customers do Car Insurance simulations every day and it's important for any insurance company to react in an intelligent way to this specific customer behavior.

To react in an intelligent way, ``Luma Insurance`` has implemented Adobe Experience Platform Data Science Workspace and has a real-time Sales Prediction model running. The Sales Prediction model will look at all available information, like all of the form fields a customer has filled out and will combine this with any other temporal, behavioral or device data. Obviously, if Luma Insurance has seen this customer on their website before, they'll have more information available for this customer which will make any ML model even better.

This unknown, anonymous customer decides to fill out the fields on this form (you can use the default values which are prepopulated on the form) and clicks ``Get Quote``.

![LumaBank](./images/7c.png)

By clicking ``Get Quote``, the customer is presented with the different Insurance types and their price.
Also, by clicking ``Get Quote``, an Experience Event for this Car Insurance Qet Quote-action is sent to Adobe Experience Platform and will be taken into account by the Sales Prediction model in real-time.

If you wish, you may decide to simulate a Car Insurance Purchase by pushing the ``Purchase`` - button.

![LumaBank](./images/7cp.png)

Go back to the Luma Insurance homepage, open the X-ray panel and go to Sensei Services.
As you can see, Sensei has calculated a Car Insurance Sales Prediction score based on the information you provided on the ``Get Quote``-form. In this example, the propensity score is ``76``.

![LumaBank](./images/7d.png)

Every change in the information you provide on the form will influence the score in real-time, so if you wish, please go back to the ``Get Quote``-form and fill out different information, followed by clicking the ``Get Quote``-button.

Additionally, you'll also find your Car Insurance Experience Events in the Experience Events - section of X-ray.

![LumaBank](./images/9.png)

And finally, based on the calculated propensity score, you'll also see specific segments qualify. In this example, this anonymous customer now qualifies for the segment ``- Car Insurance Sales Propensity 60-80``.

![LumaBank](./images/8.png)

This segment qualification can then be shared through the Bi-Directional Segment Sharing connector between AEP and AEC, which means that solutions like Adobe Audience Manager and Adobe Target are now able to use that segment qualification and deliver an alternative, more personal experience to the customer.

Next Step: [Exercise 15.2 - Interact with data in Adobe Experience Platform from a local JupyterLab environment](./ex2.md)

[Go Back to Module 15](./README.md)

[Go Back to All Modules](../../README.md)
