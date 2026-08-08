---
title: CX Enterprise Coworker and AEM
description: CX Enterprise Coworker and AEM
kt: 5342
doc-type: tutorial
---
# 1.2.6 CX Enterprise Coworker and AEM

>[!IMPORTANT]
>
>Your AEM CS sandbox may be hibernated. Given that dehibernating a sandbox takes 10-15 minutes, it would be a good idea to start the dehibernation process now so that you don't have to wait for it at a later time.

>[!IMPORTANT]
>
>Before you begin, read the below instructions!

## Instructions for in-person workshops

For this exercise, you need to use:

- **Instance**: **Adobe Tech Insiders**
- **Username**: adobetechinsiders-XXX@adobeeventlab.com
- **Password**: use the password that was shared with you
- **AEM Program**: Tech Insiders - AEM + ACCS XXX which you can access through [https://my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)
- **GitHub repository**: [https://github.com/woutervangeluwe/techinsidersXXX-citisignal-aem-accs](https://github.com/woutervangeluwe/techinsidersXXX-citisignal-aem-accs)

## 1.2.6.1 Finding assets

Go to [https://experience.adobe.com/#/coworker/chat](https://experience.adobe.com/#/coworker/chat). Sign in using your Adobe account. After logging in, click your user initials in the bottom left part of the screen and make sure you've selected the correct instance (**`--aepImsOrgName--`**) and sandbox (**`--aepSandboxName--`**) by selecting them as indicated below.

![AEM Agents](./images/aemagentscw1.png)

Enter the following prompt and click **Send**.

>[!IMPORTANT]
>
>Replace the X in the below prompt by the number that was assigned to you.

```
I want to work with AEM next, please use the AEM environment Tech Insiders - AEM + ACCS X going forward
```

![AEM Agents](./images/aemagentscw2.png)

You should then see this.

![AEM Agents](./images/aemagentscw3.png)

Enter the following prompt and click **Send**.

```javascript
find all images that contain a gorilla, a lion, a rabbit or a leopard
```

![AEM Agents](./images/aemagents32.png)

You should then see a similar answer.

![AEM Agents](./images/aemagents35.png)

## 1.2.6.2 Updating assets

### Content Update - Assets

The Content Update skill updates existing content — including content fragments, pages, forms and assets — with ease. The agent can perform actions such as updating, removing, replacing, or adding content elements to keep experiences accurate and current. Inputs can be natural language description, and when used with Jira PDFs and screenshots can provide input too.

Go back to CX Enterprise Coworker. Enter the following **prompt** and click **Send**.

```
For the first image, generate renditions for Instagram and LinkedIn posts
```

![AEM Agents](./images/aemagents40a.png)

After a couple of minutes, you should see a similar response.

![AEM Agents](./images/aemagents41.png)

Feel free to experiment with other prompts. Scroll up and select one of the other proposed prompts, or enter your own, and click **Send**.

```
For the first image, generate a mirrored image
```

![AEM Agents](./images/aemagents42a.png)

Review the image that was generated.

![AEM Agents](./images/aemagents42b.png)

### Content Update - Pages

Paste the following prompt and click **send**. Replace XXX in this prompt by the URL that you copied in the previous step.

```
On the page Fiber Max in the site CitiSignal, please make the following changes:

- change the word 'winter' to 'spring'
- change the word 'lion' to 'leopard'
- change the image in the hero block to use the image 'citisignal_leopard.png'
- change the text '99.9% network reliability' to '99.999% network reliability'
```

![AEM Agents](./images/aemagents72.png)

You should then see this. Click the link to open the changed page.

![AEM Agents](./images/aemagents74.png)

Here's your page.

![AEM Agents](./images/aemagents75.png)

Enter the following prompt and click **send**.

```
publish these changes
```

![AEM Agents](./images/aemagents76.png)

You should then see this.

![AEM Agents](./images/aemagents75a.png)

Enter the following prompt and click **send**.

```
Add a link to the Fiber Max page in the navigation of the website next to Entertainment, which is in the Header (nav) page
```

![AEM Agents](./images/aemagents77.png)

You should then see this.

![AEM Agents](./images/aemagents77a.png)

Visit your webpage, you should now see the updated navigation and the Fiber Max page.

![AEM Agents](./images/aemagents85.png)

### Content Update - Form Creation

Enter the following prompt. Click the **+** icon.

>[!IMPORTANT]
>
>Replace the X in the below prompt by the number that was assigned to you.

```
Create a new Edge Delivery Service Adaptive Form using the attached screenshot and https://github.com/woutervangeluwe/techinsidersX-citisignal-aem-accs github repository
```

![AEM Agents](./images/aemagentsforms1.png)

Select **Attach file**.

![AEM Agents](./images/aemagentsforms2.png)

Download the file [CitiSignal_Form.jpg](./assets/CitiSignal_Form.jpg) to your desktop.

![AEM Agents](./images/aemagentsforms2a.png)

Open the file. You'll see a handwritten form. You will now create a new form in AEM based on that handwritten file.

![AEM Agents](./assets/CitiSignal_Form.jpg)

Select the file **CitiSignal_Form.jpg** and click **Open**.

![AEM Agents](./images/aemagentsforms3.png)

You should then see this. Click **Send**.

![AEM Agents](./images/aemagentsforms4.png)

Provide permissions to Coworker when prompted.

![AEM Agents](./images/aemagentsforms5.png)

Your form is now created. Open the form in AEM.

![AEM Agents](./images/aemagentsforms6.png)

Your form now looks like this, which is identical to the handwritten drawing that was provided before.

![AEM Agents](./images/aemagentsforms7.png)

Enter the following prompt and click **Send**.

```
Configure the form submission to post to 'https://hook.fusion.adobe.com/towc5m6h2ggdxkrrp5i0d277732uaqv8'
```

![AEM Agents](./images/aemagentsforms8.png)

You should then see this.

![AEM Agents](./images/aemagentsforms9.png)

Enter the following prompt and click **Send**.

```
Create a new page in the website CitiSignal with the name `Fiber-Max-Interest-Form'. Make sure that the page doesn't have any other content. Embed the form in a new section on that page.
```

![AEM Agents](./images/aemagentsforms10.png)

View the page in Universal Editor:

![AEM Agents](./images/aemagentsforms11.png)

Enter the following prompt and click **Send**.

```
Publish the new page. Also, on the existing page Fiber Max, there's a text that says 'Fill out the form here to get started.'. Add a link to that line which takes people who click the link to the new page that has the form.
```

![AEM Agents](./images/aemagentsforms12.png)

You should then see this.

![AEM Agents](./images/aemagentsforms13.png)

Enter the following prompt and click **Send**.

```
Can you also publish the form?
```

![AEM Agents](./images/aemagentsforms14.png)

You should then see this.

![AEM Agents](./images/aemagentsforms15.png)

Go to your website, to the page **Fiber Max**. Click the link to fill out the form.

![AEM Agents](./images/aemagentsforms16.png)

Fill out the form and click **Submit**.

![AEM Agents](./images/aemagentsforms17.png)

You've now completed this lab.

## Next Steps

Go to [CX Enterprise Coworker and Workfront](./ex7.md){target="_blank"}

Go Back to [CX Enterprise Coworker](./coworker.md){target="_blank"}

[Go Back to All Modules](./../../../overview.md){target="_blank"}