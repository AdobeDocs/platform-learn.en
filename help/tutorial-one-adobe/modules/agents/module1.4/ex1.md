---
title: Getting started with Brand Concierge
description: Getting started with Brand Concierge
kt: 5342
doc-type: tutorial
exl-id: e05b60b1-62d7-4b70-834d-ef91782ac388
---
# 1.4.1 Getting started with Brand Concierge

## 1.4.1.1 Brand Concierge overview

While configuring Brand Concierge, the 2 main elements you'll be using are:

- **Agent Composer (Configuration Layer)**
  
  Purpose: The primary UI platform used to build and configure conversational AI experiences.

  Key Responsibilities:

  - Define and manage data sources and knowledge bases
  - Set brand expression (tone, style, guardrails)
  - Setup the meeting booking agent

- **Agent Orchestrator (Execution Engine)**

  Purpose: The reasoning and orchestration engine that interprets user requests and executes the appropriate agent actions.

  Key Responsibilities:

  - Interpret natural language user intents
  - Generate and execute multi-step reasoning plans
  - Select and invoke appropriate operators/tools
  - Enforce brand context, compliance, and guardrails
  - Coordinate multi-agent workflows
  - Aggregate and compose responses from multiple data sources

- **Brand Concierge Conversation Runtime (Service Layer)**

  Purpose: The customer-facing conversational service layer that manages chat sessions, context, and client interactions.

  Key Components:

  - Web Agent (Client): Browser or mobile chat UI integrated using the Web SDK
  - Conversation Service (Backend): Manages session state and acts as the orchestration gateway

  Key Responsibilities:

  - Manage user sessions and conversation transcripts
  - Handle user authentication and profiles
  - Route messages between the client and the Agent Orchestrator
  - Persist conversation context
  - Log behavioral and operational events to AEP for analytics
  - Apply surface-specific configurations

## 1.4.1.2 Brand Concierge instance configuration

To start creating your own Brand Concierge instance, follow the below steps.

Go to [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Open **Brand Concierge**.

![Brand Concierge](./images/bc1.png)

You should then see this. Click the **sandbox selection** menu.

![Brand Concierge](./images/bc2.png)

Choose the sandbox that has been assigned to you. That sandbox should be named `--aepUserLdap-- - bc`.

![Brand Concierge](./images/bc3.png)

Click **Get Started**.

![Brand Concierge](./images/bc4.png)

For the name of your Brand Concierge instance, use: `--aepUserLdap-- - CitiSignal Brand Concierge`.

Enter the following text under **What would you like the concierge to do?**.

```javascript
Brand Concierge should help customers find their best device, plan or entertainment deal. Brand Concierge should help users discover internet plans, entertainment deals,  and help find the best available packages. Brand Concierge should also answer questions about devices such as phones and watches.
```

Click **Create**.

![Brand Concierge](./images/bc5.png)

You should then see this. Click **Get Started** to add a knowledge source.

![Brand Concierge](./images/bc6.png)

Select **Website Links** and click **Continue**.

![Brand Concierge](./images/bc7.png)

You should then see this. Enter `CitiSignal website` as name for your knowledge source. 

You now need to upload a csv file that contains the links of your website. Download [CitiSignal website links CSV file](./assets/citisignal-website-links.csv) to your desktop.

Click **Browse Files**.

![Brand Concierge](./images/bc8.png)

Open the file **citisignal-website-links.csv** and update the links to point to your own CitiSignal website.

![Brand Concierge](./images/bc8a.png)

Select the file **citisignal-website-links.csv** that you just downloaded and edited. Click **Open**.

![Brand Concierge](./images/bc9.png)

Your file is now added to this knowledge source. Click **Add**.

![Brand Concierge](./images/bc10.png)

You should then see this. Click **Take me home**.

![Brand Concierge](./images/bc11.png)

You should then see this. Click **Get Started** on the **Product advisory for consumers** card.

![Brand Concierge](./images/bc12.png)

You should then see this. Fill out the following fields using the below text.

**What should the concierge know about the product or audience before making recommendations?**

```
CitiSignal is a telecommunications company that sells devices such as phones and watches and that sells internet services such as their lead product CitiSignal Fiber Max. On top of that, CitiSignal sells entertainment services that offer premium streaming services at a discounted price. CitiSignal is targeting these 3 personas primarily: Smart Home Families, Online Gamers and Remote Professionals.
```

**Are there any business rules or limitations the concierge should follow when making recommendations?**

```
Prioritize positioning the CitiSignal Fiber Max offering.
```

**Are there any specific keywords or phrases the concierge should follow or avoid?**

```
Competitor pricing, competitor products
```

Your updates are automatically saved. Click the **arrow** to go back to the previous screen.

![Brand Concierge](./images/bc13.png)

You should then see this. Click **Get Started** to customize your brand expression.

![Brand Concierge](./images/bc14.png)

You can make your own choices on the **Brand expression** page, ensure that an option is selected for each question.

![Brand Concierge](./images/bc15.png)

Scroll down and select any setting for the field **Response length**.

Your updates are automatically saved. 

![Brand Concierge](./images/bc16.png)

Scroll up and click the **arrow** to go back to the previous screen.

![Brand Concierge](./images/bc17.png)

You'll then be back here. Click **Knowledge Sources**.

![Brand Concierge](./images/bc18.png)

Click **Build your knowledge sources**.

![Brand Concierge](./images/bc19.png)

Select **Product catalog** and click **Continue**.

![Brand Concierge](./images/bc20.png)

You should then see this. Enter `CitiSignal Products` as name for your knowledge source. 

![Brand Concierge](./images/bc21.png)

You now need to upload a csv file that contains the links of your website. Download [CitiSignal product catalog](./assets/CitiSignal-catalog.json.zip) to your desktop and unzip it.

![Brand Concierge](./images/bc26.png)

Click **Browse Files** and then select **Browse from your device**.

![Brand Concierge](./images/bc22.png)

Select the file **CitiSignal-catalog.json** and click **Open**.

![Brand Concierge](./images/bc23.png)

You should then see this. Click **Add**.

![Brand Concierge](./images/bc24.png)

You'll then be back here.

![Brand Concierge](./images/bc25.png)

After 10-20 minutes, the **Status** of both knowledge sources should be **Completed**. Click **Home**.

![Brand Concierge](./images/bc27.png)

You should then see this. Click **+ Connect** on the **Website links** card.

![Brand Concierge](./images/bc28.png)

Select the knowledge source **CitiSignal Website** and click **Save**.

![Brand Concierge](./images/bc29.png)

You should then see this. Click **+ Connect** on the **Product catalog** card.

![Brand Concierge](./images/bc30.png)

Select the knowledge source **CitiSignal Products** and click **Save**.

![Brand Concierge](./images/bc31.png)

You should then see this. Click **Preview** to start interacting with your Brand Concierge.

![Brand Concierge](./images/bc32.png)

You can now start asking questions related to the provided knowledge sources.

![Brand Concierge](./images/bc33.png)

## 1.4.1.3 AEP onboarding steps

Brand Concierge uses Adobe Experience Platform to store interaction data from conversations. The connection between Brand Concierge and Experience Platform requires a datastream to be configured and used by Brand Concierge.

### Datastream

Go to [https://experience.adobe.com/](https://experience.adobe.com/){target="_blank"}. Open **Experience Platform**.

![Brand Concierge](./images/aep1.png)

Ensure that you've selected the right sandbox, which should be named `--aepUserLdap-- - bc`. In the left menu, scroll down and select **Datastreams**.

![Brand Concierge](./images/aep2.png)

Click **New Datastream**.

![Brand Concierge](./images/aep3.png)

Enter the **Datastream Name** `--aepUserLdap-- - Brand Concierge` and then select the **Mapping Schema** `cja-brand-concierge-sb-XXX`. 

Click **Save**.

![Brand Concierge](./images/aep4.png)

Your datastream is now configured. Copy the datastream name and the datastream id and write them down in a text file on your computer.

![Brand Concierge](./images/aep5.png)

### Datastream Config Management

The next step is to enable the Brand Concierge Configuration Management API to configure the datastream that you just created. This is required to resolve things like IMS Org ID and sandbox details during request processing.

Go to **Admin controls**.

![Brand Concierge](./images/admincontrols1.png)

Go to **Datastream Config Management** and then click **Add Config**.

![Brand Concierge](./images/admincontrols2.png)

Paste the **Datastream ID** of the datastream that you created earlier. Click **Save**.

![Brand Concierge](./images/admincontrols3.png)

You should then see something like this.

![Brand Concierge](./images/admincontrols4.png)

## 1.4.1.4 Styling Config Management

Go to **Styling Config Management**. Click **Initialize style config**.

![Brand Concierge](./images/admincontrols7.png)

Enter the **Brand Name** `CitiSignal` and then click **Initialize style config**.

![Brand Concierge](./images/admincontrols8.png)

You should then see this.

![Brand Concierge](./images/admincontrols9.png)

## 1.4.1.5 Agent Orchestrator Manifest

Go to **Update Manifest**. You should then see this.

![Brand Concierge](./images/admincontrols5.png)

You now need to update the fields in the manifest. Use the below input for that.

**Agent Name**: 

```
CitiSignal Sales Assistant
```

**Introduction**: 

```
Welcome to CitiSignal! I'm here to help you discover the best connectivity and entertainment solutions for your home or business.
```

**Roles and Responsibilities**:

```
You are CitiSignal's AI Sales Assistant focused on:
1. **Primary Goal**: Selling connectivity products from the knowledge base
2. **Upselling Strategy**: Proactively recommending entertainment packages from the knowledge base to complement connectivity subscriptions
3. **Device Sales**: Assisting with device purchases from the knowledge base when relevant
4. **Customer Support**: Answering questions about plans, pricing, installation, and features based on knowledge base content

- ALWAYS call brand_concierge_product_knowledge_agent to obtain a response to a user query and provide it directly to the user without modification.
- All product information (names, descriptions, features, ratings) comes from the knowledge base <Documents>.
- When users show interest in internet services, identify and lead with connectivity products from the knowledge base.
- After establishing connectivity interest, naturally suggest entertainment add-ons from the knowledge base.
- Use consultative selling: understand user needs, then recommend appropriate products and bundles from the knowledge base.
```

**Scope**:

```
You are CitiSignal's AI Sales Assistant, specializing in connectivity sales and entertainment bundle upselling.

# Your Primary Objectives:
1. **Sell Connectivity Products**: When users ask about internet or connectivity, recommend the appropriate connectivity product from <Documents>. Highlight key benefits mentioned in the product description.
2. **Upsell Entertainment Packages**: After discussing connectivity, proactively recommend entertainment products from <Documents> that complement the user's needs. Match recommendations to user context (families, movie enthusiasts, music lovers, etc.).
3. **Device Sales**: When relevant, recommend device products from <Documents> as complementary offerings.

# Sales Strategy:
- When a user inquires about internet, streaming, or connectivity, identify and recommend the relevant connectivity product from <Documents>.
- After establishing interest in connectivity, naturally transition to entertainment packages by highlighting how fast internet enhances streaming quality.
- Use natural transition phrases to introduce entertainment upsells.
- Emphasize bundle value and the seamless experience of having connectivity + entertainment from one provider.
- Use product ratings from <Documents> (productRating field) to prioritize higher-rated products when multiple options exist.

# Product Information Source:
- ALL product names, descriptions, features, and details MUST come from <Documents>.
- Use the exact productName from <Documents> - do not abbreviate or modify product names.
- Reference productDescription from <Documents> for accurate feature information.
- Use productRating from <Documents> to inform recommendations (higher ratings = stronger recommendations).
```

Click **Update Manifest**.

![Brand Concierge](./images/admincontrols6.png)

Click **Home**.

![Brand Concierge](./images/admincontrols10.png)

You should then see this. Click **Preview** to start interacting with your Brand Concierge.

![Brand Concierge](./images/bc101.png)

You can now start asking questions related to the provided knowledge sources. Enter the question `what products do you sell?` and click **Send**.

![Brand Concierge](./images/bc102.png)

You should then get a similar response back.

![Brand Concierge](./images/bc103.png)

Your Brand Concierge instance is now ready to be implemented on your website.

Next Step: [Implement Brand Concierge on your website](./ex2.md){target="_blank"}

Go Back to [Brand Concierge](./brandconcierge.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}
