---
title: Voice Assistant - Amazon Alexa - Define your Alexa skill
description: Voice Assistant - Amazon Alexa - Define your Alexa skill
kt: 5342
audience: Application Developer
doc-type: tutorial
activity: develop
exl-id: fb402408-5d66-4dff-842f-72b3bfe65aac
---
# 4.2: Define your Alexa skill

## Introduction

This exercise will guide you through all the necessary steps to define and configure a new Amazon Alexa skill.

## Prerequisites

Before you can create and configure an Amazon Alexa skill, you must:

1. Have an Amazon developer account and be signed in
1. Have an AWS account and be signed in
 
See [Exercise 4.1](./ex1.md) for more details.

## 4.2.1: Create an Alexa skill

To create a new skill, follow these steps:

At the **Amazon Developer Dashboard** screen ([https://developer.amazon.com/dashboard](https://developer.amazon.com/dashboard)), select **Alexa Skills Kit** from the **Alexa** menu.

![Select Alexa Skill](images/selectalexaskill.png)

In the **alexa developer console**, click the **Create Skill** button.

![Alexa Developer Console](./images/defineskill.png)

In the **Create a new skill** screen:

1. Specify **AEP** as the **Skill name**.
2. Select **English (UK)** or **English (US)** as the **Default Language**.
3. Select **Custom** as the model to use in the **Choose a model to add to your skill** section.
   ![Create Skill](images/creatskill1.png)
4. Select **Provision your own** as the method to use in the **Choose a method to host your skill's backend resources** section.
   
   ![Create Skill 2](images/createskill2.png)
   
   Your screen might look a bit different dependent on the **Default language** you have selected.

5. Click **Create skill**.
   
In the **Choose a template** screen:

1. Select **Start from scratch** as the template to use in the **Choose a template** section.
![Choose a template](images/chooseatemplate.png)
2. Click the **Choose** button.
   
You will end up in your **AEP** skill main screen, which should look like this:

![Platform Skill Main Screen](images/aepskillmainscreen.png)

## 4.2.2: Define invocation name

For your skill to be invoked, it needs an invocation name. To define this:

1. Click on **Invocation** in the left rail, or on the **1. Invocation name >** button in the **Skill builder checklist** of the **AEP** skill main screen.

2. In the **Invocation** panel, replace **AEP** with **adobe experience platform** as the **Skill Invocation Name**.

   ![Invocation Name](images/invocationname.png)

Click on **Save Model**.

This will update the invocation of your Alexa skill so you can say **Alexa, open adobe experience platform**.

## 4.2.3: Define Intents, Samples and Slots

The next step is to configure the interaction with our skill. Interaction with an Alexa skill happens through so called intents, of which Amazon provides 5 built-in intents (e.g. **AMAZON.HelpIntent**, to ask for help). Each intent defines sample utterances; phrases you use to invoke the intent. And each intent can have one or more slot values; values you provide as input to the intent.

Rather than let you define step by step the various intents, utterances and slot values we do require for our skill, we will use a JSON file to set this all up in one go. To do so:

Click on **JSON Editor** in the left rail.

![JSON Editor](images/jsoneditor.png)

Open the file **aepskillinteractionmodel.json** from your **Environment Variables GitHub repository**. Click on **Raw**.

![Raw](images/raw.png)
   
Select everything and then, copy everything.

![Raw](images/rawcopy.png)
   
In the **JSON Editor** panel on the right, select everything and paste the code that you copied in the previous step, by overwriting the text that was there already. 

![Drag and drop JSON file](images/dragdropjson.png)

This will load the interaction model.

Click **Save Model** to save the model.

![Save Model](images/savenewmodel.png)

You will now see the various specific intents for our skill on the left rail, e.g. **LdapIntent**, **GetProductIntent**, .... **UseEmailAddressIntent**. Some of these intents do have a slot, e.g. like **productId** for **GetProductIntent**.

## 4.2.3: Define the interfaces

We will now define the interface for the skill. Interfaces define how you interact with your skill: only through voice or will the skill also support display and touch? If we want our skill to use the display and touch events, we need to enable that interface. Also our skill's implementation will use the Amazon Presentation Language (BETA). To properly configure this:

Click on **Intents** to collapse all intents. Then click on **Interfaces** in the left rail.

![Interfaces](./images/interfaces.png)

In the **Interfaces** panel, enable **Display Interface** and **Alexa Presentation Language BETA**.

![Enable Interfaces](images/enableinterfaces.png)

Click on **Save Interfaces**.

## Exercise 4.2.4: Setup the implementation

Our skill's logic is implemented using the [NodeJS Alexa SDK v2](https://developer.amazon.com/docs/alexa-skills-kit-sdk-for-nodejs/overview.html).

We need our functionality deployed in AWS Lambda so that we can invoke it from the skill. And then we also need to tell our skill where to find that serverless functionality so that it can invoke it when so required.

Let's first set up our server-less functionality for the skill. To do so:

Ensure you are logged in to your **AWS Management Console** ([https://us-east-2.console.aws.amazon.com/console/home](https://us-east-2.console.aws.amazon.com/console/home)).

Pick a datacenter you prefer from the dropdown listbox at the top right menu. E.g. **US East (Ohio)** or **EU (Ireland)**.

![Data Center](images/datacenter.png)

In **Find Services** type **lambda** and press Enter.

![Lambda](images/lambda.png)

You will end up at the **AWS Lambda** home screen.

![Lambda function main screen](images/functionmainscreen.png)

Click on **Create a function**.

In the **Create function** screen:

1. Select **Author from scratch**.

   ![Author From Scratch](images/authorfromscratch.png)

1. Give your skill function a **Function name**, e.g. **AEP**.

   ![Function Name](images/functionname.png)

1. Select **Node.js 12.x** from the **Runtime** dropdown list.

   ![Runtime](images/runtime.png)

1. Click on **Choose or create an execution role** below **Permissions**. Then select **Create a new role with basic Lambda permissions**from the **Execution role** dropdown list. Your screen should look like

   ![Permissions](images/permissions.png)

1. Click on **Create function**. It will take a while to finish that creation.
1. You will end up in your **AEP** function definition screen, with the **Configuration** tab active.

   ![Platform Function Definition](images/aepfunctiondefinition.png)

1. In the list of triggers listed below **Add triggers**, select **Alexa Skills Kit**. You will see that the skill is added to the definition screen, with the remark **Configuration required**.

   ![Configuration Required](images/configurationrequired.png)
   
>[!NOTE]
>
>If **Alexa Skills Kit** is not available in the **Add triggers** list, the data center you selected does not support it. Select another datacenter (e.g. **EU (Ireland)**) that provides the **Alexa Skills Kit** trigger.

Move over to your **Alexa developer console** ([https://developer.amazon.com/alexa/console/ask](https://developer.amazon.com/alexa/console/ask)).

Click on **Endpoint**. Then select **AWS Lambda ARN**. This will show your skill id.
  
![Endpoint](images/endpoint.png)

Click on **Copy to Clipboard** to copy the skill.

Move back to your **AEP** function definition screen in the **AWS Lambda** home screen.

1. Paste the skill id in the **Skill ID** field below the **Skill ID Verification**. Ensure **Enable** is selected, which is the default and recommended setting.

   ![Configure Skill ID](images/pasteskillid.png)

1. Click on **Add** in the **Configure Triggers** panel.
1. Then click on **Save**.

Continue, in the **AEP** definition screen.

1. Click on **AEP** box in the **Designer** panel.

   ![Select Platform](images/selectaep.png)

1. In the **Function code** panel, from the **Code entry type** dropdown list, select **Upload a .zip file**.

   ![Function Code](images/functioncode.png)

1. Download **aepskill.zip** from your **Environment Variables GitHub repository** and save the file somewhere on your computer as **aepskill.zip**.
1. Click on the **Upload** button. Pick the **aepskill.zip** you saved on your computer from the file browser dialog.

   ![Platform Skill ZIP](images/selectaepskillzip.png)

1. Click **Save**.
   
Continue in the **AEP** definition screen

1. Scroll down until you see the **Environment Variables** panel.

   ![Environment Variables](images/envvariables.png)

1. Add the key value pairs from the table below, so your **Environment variables** panel will look like below.

   ![Environment Variables](images/environmentvariables.png)

### Environment variables

| Key                 | Value                 |
| ------------------- | --------------------- |
| **alexaBrandName**  | **luma retail**       |
| **emailAddress**    | **rmaur@adobe.com**   |
| **ldap**            | `--demoProfileLdap--` |
| **configurationId** | `--configurationID--` |
    
Ensure you replace **alexaBrandName**, **ldap** and **emailAddress** with your specific configuration details.

>[!IMPORTANT]
>
> - Define your **alexaBrandName** as the lowercase version of your brand name (e.g. Luma Retail as **luma retail**),
> - If your brand name contains an **&** replace it with **and**. So as an example, H&M becomes **h and m**.

Click **Save**.

As a final step, we need to copy the Amazon Resource Name that represents this functionality to our skill. 

To do so,

- In the **AEP** function definition screen, click on the copy icon right from the **ARN - arm:aws.lambda:.....** text at the top right of the screen.

   ![ARN](images/arn.png)

- A **copied** will indicate the value has been copied.
 
Move over to your **alexa developer console**.

- In the **Endpoint** config screen.
- Paste the copied ARN from the previous step in the **Default Region (Required)** field.
  
   ![Endpoint](images/defaultregion.png)
  
- Click on **Save Endpoints**.

## Exercise 4.2.5: Finalizing the skill

After we have setup invocation, intents, interfaces and endpoint, our final step is to build the final version of our skill.

The final step for the skill is to build the model. To do so:

1. Select **Invocation** from the left rail.
2. Click on **Build Model**. This will build the skill's model. This might take a while.
    
![Build Started](images/buildstarted.png)
  
Verify that on your skill's main screen all the items on the **Skill builder checklist** (except for the optional **In-skill products**) are checked. To do so:

- Click on **Build**.
   
   ![Finished](images/finished.png)
  
- Your **alexa developer console** should display green checkmarks for the first four items in the **Skill builder checklist**.
  
- Your skill and its implementation are now ready to be used.

You have finished this exercise. 

Next Step: [4.3 Use your Alexa skill](./ex3.md)

[Go Back to Module 4](./data-ingestion-amazon-alexa.md)

[Go Back to All Modules](./../../overview.md)
