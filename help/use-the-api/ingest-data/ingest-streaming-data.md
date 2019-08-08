# Lesson 3 - Streaming: Stream in Data using Launch

## Objective

- Learn how to integrate Adobe Experience Platform Launch onto a webpage
- Create Launch rules to stream data to Experience Platform

## Lesson Context

Once Luma has its customer data system set up on Experience Platform by defining schema to use, datasets to ingest data, and ingesting existing customer data, we now want to make sure that new Profile data (from sign-ups, updates, etc) and behavioral ExperienceEvent data (browsing habits, actionable triggers, etc) are recorded and updated in near real-time. We can do this by utilizing Adobe Experience Platform Launch on our website. For this exercise, we will see how we can bring in behavioral and profile data from website interactions into Adobe Experience Platform. We can flex our experience in creating new schema and new datasets from Lessons 1 & 2, and apply it to creating streaming datasets to use with Experience Platform Launch.

## Lesson Resources

- Launch URL: [https://launch-demo.adobe.com](https://launch-demo.adobe.com)

## Launch and Luma

Some elements of Launch are pre-packaged for sake of time. Rules, Data Elements and Extensions are already populated with a few settings that we will add or update during this lab to demonstrate how Launch works.

Make sure that Fenix webserver is running with luma.com. Navigate to [http://luma.com](http://luma.com) to make sure that you have Luma running properly.

## Exercise 3.1 - Creating Behavioral Schema, and Datasets for Streaming

1. Since we will be streaming in data for this lab, we will need to create new datasets that are streaming-enabled, as well as a new schema for behavioral events with the `ExperienceEvent` class, which we'll name `L778+[AccountID]_WebBehavior_Schema`. Since we covered schema creation in Lesson 1 and dataset creation in detail in Lesson 2, we've put the correct POST calls into the Postman collection for you to run. First, open the `Create Streaming Datasets` folder in `Lesson 3`, and send the `Create Web Behavior Schema` POST call. You should receive a response showing the structure of the ExperienceEvent, including a few mixins we've defined. This schema has also been enabled for Unified Profile as well.

   ![](../assets/create-ee-dataset-1a.png)

1. Next, we need to define the schema identity decriptor in order to tell Experience Platform what the main identifying field for data is in this schema, which here will be the ECID, or Experience Cloud ID that a user is auto-assigned within their browser session. Click `Define Identity Descriptor` and send the POST call.

   ![](/images/create-ee-dataset-1b.png)

1. Send the POST call for `Create Web Behavior Event Dataset`, which includes the tag `"streamingIngestionEnabled": "true"` within it to enable data streaming. You should then get a Dataset ID in response:

   ![](../assets/create-ee-dataset-2.png)

   ![](/images/create-ee-dataset-2a-streaming.png)

1. Do the same with the next call, `Create User Signups Dataset`, to create a new Profile-based dataset with `"streamingIngestionEnabled": "true"` in it as well.

1. Then send a GET call to get the ExperienceEvent dataset details. Now you will have your `WebBehavior Dataset` ExperienceEvent dataset created:

   ![](../assets/create-ee-dataset-3.png)

1. You can also GET the details of the `User Signups Dataset` Profile-based dataset that you just crated for Profile data streaming:

   ![](../assets/create-ee-dataset-4.png)

1. Examples of the two datasets after creation in the Experience Platform UI is below:

   ![](../assets/launch-setup-4.png)

## Exercise 3.2 - Setting up a Launch Property

1. Open Adobe Experience Platform Launch at https://launch-demo.adobe.com
1. Login with your Adobe ID, and ensure in the top right Organization selector that you are in `Summit 2019 Platform Lab 03`

1. Find the property associated with your user number (`L778+### Property`) and open it. This property points to the URL "luma.com", which should be set up on your local machine prior to this lab. The property will open up and take you to the Launch property home screen.

   ![](../assets/launch-setup-5.png)

   ![](../assets/launch-setup-6.png)

1. First, we need to set up a Launch library in the development environment. Go to the `Publishing` tab and click `Add New Library`.

   ![](../assets/launch-setup-publish-1.png)

1. Next, name your library `web publish` and select `Development` as the environment.

   ![](../assets/launch-setup-publish-2.png)

   ![](../assets/launch-setup-publish-3.png)

1. Launch requires us to select which elements in our Property that it should publish. This property already has several Data Elements and Rules set (we'll learn about this in a bit), so we need to click `Add All Changed Resources` at the bottom of the page to add every existing element to this library. Then, click `Save & Build for Development`.

   ![](../assets/launch-setup-publish-4.png)

   ![](../assets/launch-setup-publish-5.png)

1. The last step is to select our new library as the working environment. In the top right drop down for `Working Library`, select our new `web publish` library. This will now update the library whenever we make any changes in the next steps.

## Exercise 3.3 - Putting Launch into a website

1. Now, we need to take a snippet of HTML to insert in your Luma site. This snippet will be how Launch sends data to the Experience Platform. Click the `Environments` tab from the home screen, and then click the small box icon to the right of the `Development` row.

   ![](../assets/launch-setup-7.png)

1. Click the "copy" square button to the right of the script textbox to copy this snippet to the clipboard.

   ![](../assets/launch-setup-8.png)

1. Open up the `index.html` and `signup.html` pages of your Luma site in your text/code editor, and paste this code into the `<head>` tags of each file. This will enable Launch to run its rules on these two pages. _Remember to paste this snippet in BOTH files._

   ![](../assets/launch-luma-snippet1.png)

   ![](../assets/launch-luma-snippet2.png)

## Exercise 3.4 - Setting up Launch Rules and Elements

1. Go to the `Data Elements` tab. This is where we will define elements from our Luma site to pull in values - names, emails, IDs, descriptors, etc. There are already a few populated in here that we will be using when we send data to Experience Platform.

   ![](../assets/launch-setup-11.png)

1. Let's take a look at the extensions we will need for our Luma site. Click the `Extensions` tab. You'll see that the Core extension is there by default, and that we've already had the following extensions installed:

   1. Adobe Experience Platform - _This is the extension needed to send data specifically to our Experience Platform instance_
   1. Experience Cloud ID Service - _This is the extension that allows us to identify the unique Experience Cloud ID attribute across all Adobe products_

   ![](../assets/launch-setup-12.png)

1. We're going to need to configure the Adobe Experience Platform extension, so click `Config` on that box. Click on `Create a streaming endpoint`, and name it `Launch Streaming Endpoint [AccountID]`, with `Source ID` = `Launch_[AccountID]`, and then click `Save`.

   ![](../assets/launch-setup-13.png)

1. Select your streaming endpoint - in the text box, type your [AccountID] and your endpoint should pop up. Select it and click `Save to Library and Build`.

## Exercise 3.5 - Sending ExperienceEvent Data (behavioral data)

1. Now, we have our streaming endpoint from our Luma site into Experience Platform defined and ready to go. The next step is to create triggers that will make actions happen on our Luma site. Go to the `Rules` tab. Take alook at the existing rules - we have two defined here. Look into `Page Visit`.

   ![](../assets/launch-setup-14.png)

1. You can see that the Event, `Core - Page Bottom` is triggered when the browser hits the bottom of the page. This stands in as a de-facto "page view" as the bottom of the page is automatically hit when the page renders. At the bottom, the Action flow shows two actions - one for Experience Cloud ID Service, and then one for Adobe Experience Platform.

   ![](../assets/launch-setup-15.png)

1. Click on the Experience Cloud ID Service action. You can see that it is setting the ECID to share across Adobe solutions with the ECID being sent to it from our "ECID" Data Element. Click `Cancel` and `Discard changes` (don't worry, no changes were made) to go back to the Rule editor.

   ![](../assets/launch-setup-16.png)

1. Now let's define data that we send to Experience Platform. Click on `Adobe Experience Platform - Send Beacon`. This action is sending an ExperienceEvent. You'll see that some of the variables and data elements populating those variables are already set - sending the ECID as an identity for the event, the name of the webpage currently viewed, and a timestamp of that action.

   ![](../assets/launch-setup-17.png)

1. There are two things here that we need to change. First, the dataset selected that we're sending data to needs to but changed. Click the dropdown and find your corresponding `L778+[AccountID]_WebBehavior_Dataset` dataset from earlier. You will get a warning to make sure the fields match, which you should assume is true here.

   ![](../assets/launch-setup-20.png)

1. Now let's add another variable to send in our beacon - the Language data element. Click on `Add Another` and create the following:

   1. variable: use the "target" icon to select the `Environment - browserDetails - acceptLanguage` schema field
   1. value: `%Language%` - _(Select this from the list of data elements by clicking the round stack icon next to the value field. It can also be typed in directly)_

   ![](../assets/launch-setup-19a.png)

   ![](../assets/launch-setup-18.png)

   ![](../assets/launch-setup-19b.png)

1. Let's save our changes. Click on `Keep Changes` to save our Action, and then `Save to Library and Build`. Now the rule for "Page View" has been set.

## Exercise 3.6 - Sending Profile Data (attribute data)

1. We just set up our first rule to send an ExperienceEvent to Adobe Experience Platform! Now let's do the same thing for same with Profile data, by taking a look at the `Sign Up` rule. Clicking on `Core - Click` you can see the composition of the event that we're looking for - a click on the `Submit` button during sign-up, with a specific CSS selector for that button.

   ![](../assets/launch-setup-21a.png)

   ![](../assets/launch-setup-21b.png)

1. Under the `Conditions` field, you can see there as a requirement that we be on the `signup.html` page for this rule to fire.

   ![](../assets/launch-setup-21c.png)

1. Just like we did with the ExperienceEvent dataset, we need to select the correct dataset. Since this is a Profile-updating action, we want to send our data beacon to our `L778+[AccountID]_Signups_Dataset` dataset, so select that from the dropdown.

   ![](../assets/launch-setup-21.png)

1. Explore the actions for this rule, as there are several already pre-populated. You'll notice that we are sending the many variables, including identityMap which defines who to attribute this beacon data to, sending the ECID and the user's email (which is marked as our primary identifier):

   1. %ECID% => ECID
   1. %Email Address% => Email, Primary

1. You'll also see that the `personalEmail.address` value is `DELETE` and needs to be corrected. This value sets one of the identities that Unified Profile uses to match XDM data to each other. Clear this text box and then select the `Email Address` data element using the round stack icon next to the text box.

   ![](../assets/launch-setup-22.png)

   ![](../assets/launch-setup-23.png)

1. Click `Keep Changes` on the action, and thten `Save to Library and Build` on the rule. Click on the `Publishing` tab to watch the status of our build and see it succeed.

   ![](../assets/launch-setup-24.png)

## Exercise 3.7 - Streaming a Launch data beacon into Adobe Experience Platform from Luma

Now we've got a Launch property set up, and a Luma instance running with the Launch streaming endpoint included. Let's watch it stream data into Experience Platform.

1. Go to http://www.luma.com. This should be pointing to your Fenix webserver instance of Luma. Right click and open up `Inspect` to see the page inspector.

   ![](../assets/launch-luma-homepage.png)

1. Go to the `Network` tab, and type `dcs` into the filter box. This will filter our network commands being sent to the Launch streaming URL. Refresh the page.

1. Select the endpoint under `Name"\` and scroll dwon on the right pane to `Request Payload`. You should see an expandable JSON payload starting with `{header:`. Expand all these fields and you will be able to see the XDM data that we defined in our Launch rule for "Page View" being sent from the page to Launch.

   ![](../assets/launch-luma-eebeacon-homepage.png)

1. Go back to your Luma screen. Now let's see our Sign-Up rule in action by going to `Sign Up` in the top right of the page. Scroll down to the sign-up form and fill in some dummy details with your name and email. These do not have to be real or accurate.

   ![](../assets/launch-luma-signup.png)

1. Click `Sign Up`. Nothing will happen visually; our instance of Luma is stripped-down and does not contain any functionality past this page. Go back to your inspector and you can now observe two Launch beacons being sent!

1. One beacon data contains the Profile XDM data we filled into the form. You can see all the fields we defined in the "Sign Up" rule on Launch here.

   ![](../assets/launch-luma-profilebeacon.png)

1. The other beacon is an ExperienceEvent XDM fired by the "Page View" rule, the same as when we were at the Luma Homepage. You'll notice the data for this page is basically identical, except for the `webPageDetails` and `timestamp` fields.

   ![](../assets/launch-luma-eebeacon-signup.png)

1. We can also look at all of our ExperienceEvent data within Experience Platform using an API call through Postman. Within the beacon data, find the `ecid: {id: "##"` field and select your ECID. This ID is specific to your browser session and can be used to look up ExperienceEvent and Unified Profile data. Copy this field and we'll use it in the first step of Lesson 4.

   ![](../assets/launch-luma-ecid.png)

## Lesson 3 Wrap

Congratulations! You've got all the basics you need for your Adobe Experience Platform setup to build out not just a basis for customer loyalty programs, but also for data collection, storage, and analysis of your incoming customer data from batch ingestion and streaming data.

The streaming capabilities of data into Experience Platform are not limited to websites - mobile apps, POS devices, and other points of data capture can all stream behavioral and other types of data into Experience Platform using methods like Launch.

## Lesson 3 - Additional Resources

[Getting Started with Adobe Launch](https://docs.adobelaunch.com/getting-started)