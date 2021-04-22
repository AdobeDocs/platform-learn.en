---
title: Foundation - Real-time Customer Profile - Visualize your own real-time customer profile - API
description: Foundation - Real-time Customer Profile - Visualize your own real-time customer profile - API
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
exl-id: 551b43b4-4930-406e-b38b-05827cac409b
---
# 3.3 - Visualize your own real-time customer profile - API

In this exercise, you'll use Postman and Adobe I/O to query Adobe Experience Platform's APIs to view your own real-time customer profile.
 
## Story

In the Real-time Customer Profile, all profile data is shown alongside event data, as well as existing segment memberships. The data shown can come from anywhere, from Adobe applications and external solutions. This is the most powerful view in Adobe Experience Platform&mdash;the experience system of record.

The Real-time Customer Profile can be consumed by all Adobe applications, but also by external solutions like Call Centers or in-store clienteling apps. The way to do this is to connect those external solutions to Adobe Experience Platform's APIs.

## 3.3.1 - Your Identifiers

On the X-ray panel on the website, you can find multiple identities. Every Identity is linked to a Namespace. 

![Customer Profile](./images/identities.png)

On the X-ray panel, we can see 4 different combinations of IDs and Namespaces:

| Identity     | Namespace       |
|:-------------:| :---------------:|
| Experience Cloud ID (ECID)          | 70064353701262275980354366981653865618 |
| Email ID          | woutervangeluwe+28052020-10@gmail.com|
| Mobile Number ID          | +32473622044+28052020-10|

Remember these identifiers for the next step.

With these IDs in mind, go to Postman.

## 3.3.2 - Setup your Adobe I/O Project

In this exercise you'll be using Adobe I/O quite intensively to query against Platform's APIs. Please follow the below steps to setup Adobe I/O.

Go to [https://console.adobe.io/projects](https://console.adobe.io/projects)

![Adobe I/O New Integration](./images/iohome.png)

Make sure to select the correct Adobe Experience Platform instance in the top right corner of your screen. 

![Adobe I/O New Integration](./images/iocomp.png)

Click **Create new project**.

![Adobe I/O New Integration](./images/adobe_io_new_integration.png) or 
![Adobe I/O New Integration](./images/adobe_io_new_integration1.png)

Select **+ Add to Project** and select **API**.

![Adobe I/O New Integration](./images/adobe_io_access_api.png)

You'll then see this:

![Adobe I/O New Integration](./images/api1.png)

Click the **Adobe Experience Platform** icon.

![Adobe I/O New Integration](./images/api2.png)

Click **Experience Platform API**.

![Adobe I/O New Integration](./images/api3.png)

Click **Next**.

![Adobe I/O New Integration](./images/next.png)

You can now choose to either have Adobe I/O generate your security key pair, or upload an existing one. 

Choose **Option 1 - Generate a key pair**.

![Adobe I/O New Integration](./images/api4.png)

Click **Generate keypair**.

![Adobe I/O New Integration](./images/generate.png)

You'll see a spinner for about 30 seconds.

![Adobe I/O New Integration](./images/spin.png)

You'll then see this, and your generated keypair will be downloaded as a zip file: **config.zip**.

Unzip the file **config.zip** on your desktop, you'll see it contains 2 files:

![Adobe I/O New Integration](./images/zip.png)

* **certificate_pub.crt** is your Public key certificate. From a security perspective, this is the certificate that is freely used to setup integrations with online applications.
* **private.key** is your Private key. This should never, ever be shared with anyone. The Private Key is what you use to authenticate to your API implementation and is supposed to be a secret. If you share your Private Key with anyone, they can access your implementation and abuse the API to ingest malicious data into Platform and extract all the data that sits in Platform.

![Adobe I/O New Integration](./images/config.png)

Make sure to save the **config.zip** file in a safe location, as you'll need this for the next steps and for future access to Adobe I/O and Adobe Experience Platform APIs.

Click **Next**.

![Adobe I/O New Integration](./images/next.png)

You now have to select the **Product Profile(s)** for your integration. 

Select the required Product Profiles. 

**FYI**: in your Adobe Experience Platform instance, the Product Profiles will have a different naming. You need to select at least one product profile with the proper access rights, which are set up in the Adobe Admin Console.

![Adobe I/O New Integration](./images/api9.png)

Click **Save Configured API**.

![Adobe I/O New Integration](./images/saveconfig.png)

You'll see a spinner for a couple of seconds.

![Adobe I/O New Integration](./images/api10.png)

And next, you'll see your integration.

![Adobe I/O New Integration](./images/api11.png)

Click the **Download for Postman** button to download a Postman environment (wait until the environment is downloaded, this can take a couple of seconds).

![Adobe I/O New Integration](./images/iopm.png)

Scroll down until you see **Service Account (JWT)**, which is where you can find all your integration details that are used to configure the integration with Adobe Experience Platform.

![Adobe I/O New Integration](./images/api12.png)

Your IO Project currently has a generic name. You need to give a friendly name to your integration. Click on **Project 1** (or similar name) as indicated

![Adobe I/O New Integration](./images/api13.png)

Click **Edit Project**.

![Adobe I/O New Integration](./images/api14.png)

Enter a Name and Description for your integration. As a naming convention, we'll use **AEP API ldap**. Replace ldap with your ldap.
For instance, if your ldap is vangeluw, the name and description of your integration becomes Platform API vangeluw.

Enter **AEP API ldap** as the **Project Title**. Click **Save**.

![Adobe I/O New Integration](./images/api15.png)

Your Adobe I/O integration is now finished.

![Adobe I/O New Integration](./images/api16.png)

## Exercise 3.3.3 - Postman authentication to Adobe I/O

Go to [https://www.getpostman.com/](https://www.getpostman.com/). 

Click on **Get Started**.

![Adobe I/O New Integration](./images/getstarted.png)

Next, download and install Postman.

![Adobe I/O New Integration](./images/downloadpostman.png)

After installation of Postman, start the application.

In Postman, there are 2 concepts: Environments and Collections.

* The Environment contains all of your environmental variables which are more or less consistent. In the Environment, you'll find things like the IMSOrg of our Platform environment, alongside security credentials like your Private Key and others. The environment file is the one you downloaded during the Adobe I/O setup in the previous exercise, it's name like this: **service.postman_environment.json**.
  
* The Collection contains a number of API requests that you can use. We will use 2 collections
  * 1 Collection for Authentication to Adobe I/0
  * 1 Collection for our Exercises

Please download **postman.zip** from your **Environment Variables GitHub repository** to your local desktop. 

In this **postman.zip** file, you'll find the following files:

* _Adobe I-O - Token.postman_collection.json
* _Adobe Experience Platform Enablement.postman_collection.json
  
Unzip the **postman.zip** file and store these 2 files in a folder on your desktop, together with the downloaded Postman environment from Adobe I/O. You need to have these 3 files in that folder:

![Adobe I/O New Integration](./images/pmfolder.png)

Go back to the Postman UI.

![Adobe I/O New Integration](./images/postmanui.png)

In Postman, click on **Import**.

![Adobe I/O New Integration](./images/import.png)

Click on **Choose files**.

![Adobe I/O New Integration](./images/choosefiles.png)

Navigate to the folder on your desktop in which you extracted the 3 downloaded files. Select these 3 files at the same time and click **Open**.

![Adobe I/O New Integration](./images/selectfiles.png)

After having clicked **Open**, Postman will show you an overview of the Environment and Collections you're about to import. Click **Import**.

![Adobe I/O New Integration](./images/impconfirm.png)

You now have everything you need in Postman to start interacting with Adobe Experience Platform through the APIs.

The first thing to do, is to make sure you're properly authenticated. To be authenticated, you need to request an access token.

Make sure that you've got the right Environment selected before executing any request. You can check the currently selected Environment by verifying the Environment-dropdown list in the top right corner. 

The selected Environment should have a name similar to this one:

![Postman](./images/envselemea.png)

Click the **gear** icon to update the Private Key in the environment file.

![Postman](./images/gear.png)

Click the environment in the list:

![Postman](./images/pk1.png) 

You'll then see this. All fields are pre-populated, except for the field **PRIVATE_KEY**.

![Postman](./images/pk2.png)

The private key has been generated when you created your Adobe I/O Project. It was downloaded as a zip file, named **config.zip**. Extract that zip file to your desktop.

![Postman](./images/pk3.png)

Open the folder **config** and open the file **private.key** with your text editor of choice.

![Postman](./images/pk4.png)

You'll then see something resembling this, copy all the text to your clipboard.

![Postman](./images/pk5.png)

Go back to Postman and paste the private key in the fields next to the variable **PRIVATE_KEY**. Finally, click **Update**.

![Postman](./images/pk6.png)

Your Postman environment and collections are now configured and working. You can now authenticate from Postman to Adobe I/O.

To do that, you need to load an external library that will take care of the encryption and decryption of communication. To load this library, you have to execute the request with the name **INIT: Load Crypto Library for RS256**. Select this request in the **_Adobe I/O - Token collection** and you'll see it displayed in the middle of your screen.

![Postman](./images/iocoll.png)

![Postman](./images/cryptolib.png)

Click the blue **Send** button. After a couple of seconds, you should see a response displayed in the **Body** section of Postman:

![Postman](./images/cryptoresponse.png)

With the crypto library now loaded, we can authenticate to Adobe I/O.

In the **\_Adobe I/O - Token collection**, select the request with the name **IMS: JWT Generate + Auth**. Again, you'll see the request details displayed in the middle of the screen.

![Postman](./images/ioauth.png)

Click the blue **Send** button. After a couple of seconds, you should see a response displayed in the **Body** section of Postman:

![Postman](./images/ioauthresp.png)

If your configuration was successful, you should see a similar response that contains the following information:

| Key     | Value     | 
|:-------------:| :---------------:| 
| token_type          | **bearer** |
| access_token    | **eyJ4NXUiOiJpbXNfbmEx...QT7mqZkumN1tdsPEioOEl4087Dg** | 
| expires_in          | **86399973** |

Adobe I/O has given you a **bearer**-token, with a specific value (this very long access_token) and an expiration window.

The token that we've received is now valid for 24 hours. This means that after 24 hours, if you want to use Postman to authenticate to Adobe I/O, you will have to generate a new token by running this request again.

## Exercise 3.3 - Real-time Customer Profile API, Schema: Profile

Now you can go ahead and send your first request to Platform's Real-time Customer Profile APIs.

In Postman, locate the collection **_Adobe Experience Platform Enablement**.

![Postman](./images/coll_enablement.png)

In **1. Unified Profile Service**, select the first request with the name **UPS - GET Profile by Entity ID & NS**.

![Postman](./images/upscall.png)

For this request, there are three required variables:

| Key     | Value     | Definition |
|:-------------:| :---------------:| :---------------:| 
| entityId          | **id** | the specific customer ID |
| entityIdNS    | **namespace** | the specific namespace that is applicable to the ID |
| schema.name          | **_xdm.context.profile** | the specific schema for which you want to receive information |

So, if you want to ask Platform's APIs to give you back all Profile information for your own ECID, you will need to configure the request as follows:

| Key     | Value     | 
|:-------------:| :---------------:| 
| entityId          | **yourECID** |
| entityIdNS    | **ecid** | 
| schema.name          | **_xdm.context.profile** |

![Postman](./images/callecid.png)

You should also verify the **Header** - fields of your request. Go to **Headers**. You'll then see this:

![Postman](./images/callecidheaders.png)

>[!NOTE]
>
>You need to specify the name of the Adobe Experience Platform sandbox you're using. If you're using the **Production** sandbox, the value for the key **x-sandbox-name** should be set to **prod**. If you're using another sandbox, please verify what the sandbox name by viewing the details of your Configuration ID.

Click **Send** to send your request to Platform.

You should get an immediate response from Platform, showing you something like this:

![Postman](./images/callecidresponse.png)

This is the full response from Platform:

```javascript
{
    "A2-OOBvy2Ns7YZIkm23k9uoE": {
        "entityId": "A2-OOBvy2Ns7YZIkm23k9uoE",
        "mergePolicy": {
            "id": "2eb6e85d-12c3-45f4-b421-624ce6ac5ef8"
        },
        "sources": [
            "profile-streaming-segment",
            "5eb31a637ca9d318a829f499",
            "5ea04d5b005a6e18a8bc88af",
            "5ea04d5b005a6e18a8bc88ae"
        ],
        "tags": [
            "",
            "1590666414478:0586:29",
            "1590667621104:8198:227",
            "1590665951756:0837:55",
            "1590667621126:5817:55"
        ],
        "identityGraph": [
            "GaBRQX2_A_h_3Tmjyt4ZNAf1UmIZZL8ceANGOHNsX_Z3d7hHQ2mv",
            "BVnqB2rJNot-AvailableA",
            "A2-gvnReLZPTUFyy99pj_O51",
            "A2-OOBvy2Ns7YZIkm23k9uoE",
            "CkF9rwWwrwL_y97ayo791IyW22qvqCfSZZLh3a3hDdEbhXa4HA",
            "GesCQXBHQTEuMi6DAYVkXy6DIaLPXg",
            "GquYmEFvK4QcJpSPByuDNAqsAS0xMA",
            "BUF9zMKLrXq72p4HpbsHv1SDNAqsAS0xMEBnbWFpbC5jb20"
        ],
        "entity": {
            "_apac_sc": {
                "faceDetection": {
                    "estimatedAge": "",
                    "estimatedGender": "unknown",
                    "estimatedEyeMakeup": "",
                    "estimatedLipMakeup": "",
                    "estimatedEmotion": "",
                    "estimatedGlasses": ""
                },
                "allergies": {
                    "soy": "N",
                    "dairy": "",
                    "gluten": "N",
                    "nuts": "N",
                    "shellfish": "N"
                },
                "identification": {
                    "emailId": "woutervangeluwe+28052020-10@gmail.com",
                    "mobilenr": "+32473622044+28052020-10",
                    "gaid": "GA1.2.1600423169.1590665761",
                    "emailIdSha256": "05b0af02ffcbdedaca8efdd48c96db6aa827d26592e1ddade10dd11b8576b81c",
                    "ecid": "70064353701262275980354366981653865618"
                },
                "loyalty": {
                    "loyaltyStatus": "Bronze",
                    "loyaltyPoints": 0
                },
                "brand": {
                    "brandName": "Luma Retail",
                    "ldap": "vangeluw",
                    "tms": "Launch"
                },
                "retailSizes": {
                    "shirtSize": "L",
                    "shoeSize": "43",
                    "preferredColor": "black"
                },
                "churnInformation": {
                    "churnScore": "0.00"
                }
            },
            "personalEmail": {
                "address": "woutervangeluwe+28052020-10@gmail.com"
            },
            "_id": "9y7iwfcil1590667621107",
            "_repo": {
                "createDate": "2020-05-28T12:07:01Z"
            },
            "homeAddress": {
                "postalCode": "8790",
                "city": "Waregem",
                "country": "Belgium",
                "street1": "Bosstraat"
            },
            "mobilePhone": {
                "number": "+32473622044+28052020-10"
            },
            "optInOut": {
                "_channels": {
                    "directMail": "out",
                    "sms": "in",
                    "email": "in",
                    "phone": "in"
                }
            },
            "segmentMembership": {
                "ups": {
                    "ac6dc704-1484-48f7-a1e6-1245dfd1107d": {
                        "lastQualificationTime": "2020-05-28T12:08:11Z",
                        "status": "existing"
                    },
                    "28578f46-f360-4398-9a5a-00463e2fb8d0": {
                        "lastQualificationTime": "2020-05-28T12:08:11Z",
                        "status": "existing"
                    }
                }
            },
            "person": {
                "name": {
                    "lastName": "Van Geluwe",
                    "firstName": "Wouter"
                },
                "gender": "male",
                "birthDate": "1982-01-01"
            },
            "userActivityRegions": {
                "NLD2": {
                    "captureTimestamp": "2020-05-28T12:07:01Z"
                }
            },
            "profilePictureLink": "https://s7e4a.scene7.com/is/image/OmniPS/adobelogo?$fmt=alpha-png",
            "identityMap": {
                "mobilenr": [
                    {
                        "id": "+32473622044+28052020-10"
                    }
                ],
                "email": [
                    {
                        "id": "woutervangeluwe+28052020-10@gmail.com"
                    },
                    {
                        "id": "Not Available"
                    }
                ],
                "google": [
                    {
                        "id": "GA1.2.1600423169.1590665761"
                    }
                ],
                "apns": [
                    {
                        "id": "03F87FDD39A3CADE193407F5526219641C78034638736C5FF67777B8474369AF"
                    }
                ],
                "ecid": [
                    {
                        "id": "70064353701262275980354366981653865618"
                    },
                    {
                        "id": "58241605661877039688498007052700332636"
                    }
                ],
                "email_lc_sha256": [
                    {
                        "id": "05b0af02ffcbdedaca8efdd48c96db6aa827d26592e1ddade10dd11b8576b81c"
                    }
                ]
            }
        },
        "lastModifiedAt": "2020-05-28T12:08:11Z"
    }
}
```

This is currently all of the available Profile data in Platform for this ECID.

You're not required to use the ECID to request Profile data from Platform's Real-time Customer Profile, you can use any ID in any namespace to request this data. 

Let's go back to Postman and pretend we're the call center, and send a request to Platform specifying the namespace of **Phone** and your mobile number.

So, if you want to ask Platform's APIs to give you back all Profile information for a specific Phone, you will need to configure the request as follows:

| Key     | Value     | 
|:-------------:| :---------------:| 
| entityId          | **your phone number** |
| entityIdNS    | **mobilenr** (replace ecid by mobilenr) | 
| schema.name          | **_xdm.context.profile** |

If your phone number contains special symbols like **+**, you have to select your full phone number, do a right-click and click **EncodeURIComponent**.

![Postman](./images/encodephone.png)

You'll then have this:

![Postman](./images/callmobilenr.png)

You should also verify the **Header** - fields of your request. Go to **Headers**. You'll then see this:

![Postman](./images/callecidheaders.png)

>[!NOTE]
>
>You need to specify the name of the Adobe Experience Platform sandbox you're using. If you're using the **Production** sandbox, the value for the key **x-sandbox-name** should be set to **prod**. If you're using another sandbox, please verify what the sandbox name by viewing the details of your Configuration ID.

Click the blue **Send** button and verify the response.

![Postman](./images/callmobilenrresponse.png)

Let's do the same thing for your email address by specifying the namespace of **email** and your email address.

So, if you want to ask Platform's APIs to give you back all Profile information for a specific email address, you will need to configure the request as follows:

| Key     | Value     | 
|:-------------:| :---------------:| 
| entityId          | **youremail** |
| entityIdNS    | **email** (replace Phone with email) | 
| schema.name          | **_xdm.context.profile** |

If your email address contains special symbols like **+**, you have to select your full email address, do a right-click and click **EncodeURIComponent**.

![Postman](./images/encodeemail.png)

You'll then have this:

![Postman](./images/callemail.png)

You should also verify the **Header** - fields of your request. Go to **Headers**. You'll then see this:

![Postman](./images/callecidheaders.png)

>[!NOTE]
>
>You need to specify the name of the Adobe Experience Platform sandbox you're using. If you're using the **Production** sandbox, the value for the key **x-sandbox-name** should be set to **prod**. If you're using another sandbox, please verify what the sandbox name by viewing the details of your Configuration ID.

Click the blue **Send** button and verify the response.

![Postman](./images/callemailresponse.png)

This is a very important kind of flexibility that is offered to brands. This means that any environment can send a request to Platform, using their own ID and namespace, without having to understand the complexity of multiple namespaces and IDs.

As an example:

* the Call Center will request data from Platform using the namespace **mobilenr**
* the Loyalty System will request data from Platform using the namespace **email**
* online applications might use the namespace **ecid**

The Call Center doesn't necessarily know what kind of identifier is used in the Loyalty System and the Loyalty System doesn't necessarily know what kind of identifier is used by online applications. Each individual system can use the information that they have and understand to get the information they need, when they need it.

## Exercise 3.3.4 - Real-time Customer Profile API, Schema: Profile and ExperienceEvent

After having queried Platform's APIs successfully for Profile data, let's now do the same with ExperienceEvent data.

In Postman, locate the collection **_Adobe Experience Platform Enablement**.

![Postman](./images/coll_enablement.png)

In **1. Unified Profile Service**, select the second request with the name **UPS - GET Profile & EE by Entity ID & NS**.

![Postman](./images/upseecall.png)

For this request, there are four required variables:

| Key     | Value     | Definition | 
|:-------------:| :---------------:|  :---------------:| 
| schema.name          | **_xdm.context.experienceevent** | the specific schema for which you want to receive information. In this case, we're looking for data that is mapped against the ExperienceEvent schema. | 
| relatedSchema.name          | **_xdm.context.profile** | While we're looking for data that is mapped against the ExperienceEvent schema, we need to specify an identity for which we want to receive that data. The schema that has access to identity is the Profile-schema, so the relatedSchema here is the Profile-schema. |
| relatedEntityId          | **id** | the specific customer I D|
| relatedEntityIdNS    | **namespace** | the specific namespace that is applicable to the ID | 

So, if you want to ask Platform's APIs to give you back all Profile information for your own ecid, you will need to configure the request as follows:

| Key     | Value     | 
|:-------------:| :---------------:| 
| schema.name          | **_xdm.context.experienceevent** |
| relatedSchema.name          | **_xdm.context.profile** |
| relatedEntityId          | **yourECID** |
| relatedEntityIdNS    | **ecid** | 

![Postman](./images/eecallecid.png)

You should also verify the **Header** - fields of your request. Go to **Headers**. You'll then see this:

![Postman](./images/eecallecidheaders.png)

>[!NOTE]
>
>You need to specify the name of the Adobe Experience Platform sandbox you're using. If you're using the **Production** sandbox, the value for the key **x-sandbox-name** should be set to **prod**. If you're using another sandbox, please verify what the sandbox name by viewing the details of your Configuration ID.

Click **Send** to send your request to Platform.

You should get an immediate response from Platform, showing you something like this:

![Postman](./images/eecallecidresponse.png)

Below is the full response from Platform. In this example, there are eight ExperienceEvents linked to this customer's ECID. Have a look at the below to see the different variables on the request, as what you see below is the direct consequence of your configuration in Launch in previous exercises.

Also, when the X-ray panel shows ExperienceEvent information, it is using the below payload to parse and retrieve the information like Product Name (search for productName in the below payload) and Product Image URL (search for productImageUrl in the below payload).

```javascript
{
    "_page": {
        "orderby": "timestamp",
        "start": "8594734639914.326",
        "count": 16,
        "next": ""
    },
    "children": [
        {
            "relatedEntityId": "GesCQXBHQTEuMi6DAYVkXy6DIaLPXg",
            "entityId": "8594734639914.326",
            "timestamp": 1590665857000,
            "entity": {
                "environment": {
                    "browserDetails": {
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.61 Safari/537.36",
                        "acceptLanguage": "en"
                    }
                },
                "web": {
                    "webPageDetails": {
                        "name": "Nadia Elements Shell"
                    }
                },
                "identityMap": {
                    "GOOGLE": [
                        {
                            "id": "GA1.2.1600423169.1590665761"
                        }
                    ]
                },
                "_id": "8594734639914.326",
                "commerce": {
                    "productViews": {
                        "value": 1
                    }
                },
                "productListItems": [
                    {
                        "name": "Nadia Elements Shell",
                        "product": "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/2d46bee7e82aa3583a103ac6405fb3b4_1.jpg",
                        "quantity": 1,
                        "productAddMethod": "Desktop",
                        "SKU": "Nadia Elements Shell",
                        "priceTotal": 69
                    }
                ],
                "timestamp": "2020-05-28T11:37:37Z",
                "_apac_sc": {
                    "productData": {
                        "productUrl": "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/2d46bee7e82aa3583a103ac6405fb3b4_1.jpg",
                        "productName": "Nadia Elements Shell",
                        "productInteraction": "productView"
                    },
                    "brand": {
                        "brandName": "Luma Retail",
                        "tms": "GTM"
                    },
                    "identification": {
                        "gaid": "GA1.2.1600423169.1590665761"
                    }
                }
            },
            "lastModifiedAt": "2020-05-28T11:37:38Z"
        },
        {
            "relatedEntityId": "A2-OOBvy2Ns7YZIkm23k9uoE",
            "entityId": "8962969537248.941",
            "timestamp": 1590665858000,
            "entity": {
                "environment": {
                    "browserDetails": {
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.61 Safari/537.36",
                        "acceptLanguage": "en"
                    }
                },
                "web": {
                    "webPageDetails": {
                        "name": "Nadia Elements Shell",
                        "URL": "https://aepdemo.net/p1.html"
                    }
                },
                "_id": "8962969537248.941",
                "commerce": {
                    "productViews": {
                        "value": 1
                    }
                },
                "productListItems": [
                    {
                        "name": "Nadia Elements Shell",
                        "product": "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/2d46bee7e82aa3583a103ac6405fb3b4_1.jpg",
                        "quantity": 1,
                        "productAddMethod": "Desktop",
                        "SKU": "LLWJ10.1-XS",
                        "priceTotal": 69
                    }
                ],
                "_apac_sc": {
                    "campaign": {
                        "campaignId": ""
                    },
                    "productData": {
                        "productUrl": "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/2d46bee7e82aa3583a103ac6405fb3b4_1.jpg",
                        "productName": "Nadia Elements Shell",
                        "productInteraction": "productView"
                    },
                    "identification": {
                        "ecid": "70064353701262275980354366981653865618"
                    },
                    "brand": {
                        "ldap": "vangeluw",
                        "brandName": "Luma Retail",
                        "tms": "Launch"
                    }
                },
                "timestamp": "2020-05-28T11:37:38Z"
            },
            "lastModifiedAt": "2020-05-28T11:37:39Z"
        },
        {
            "relatedEntityId": "A2-OOBvy2Ns7YZIkm23k9uoE",
            "entityId": "3261289222635.432",
            "timestamp": 1590665951000,
            "entity": {
                "environment": {
                    "browserDetails": {
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.61 Safari/537.36",
                        "acceptLanguage": "en"
                    }
                },
                "_id": "3261289222635.432",
                "web": {
                    "webPageDetails": {
                        "pageViews": {
                            "value": 1
                        },
                        "name": "Luma Retail Home",
                        "URL": "https://aepdemo.net/index.html"
                    }
                },
                "_apac_sc": {
                    "campaign": {
                        "campaignId": ""
                    },
                    "brand": {
                        "ldap": "vangeluw",
                        "brandName": "Luma Retail",
                        "tms": "Launch"
                    },
                    "identification": {
                        "ecid": "70064353701262275980354366981653865618"
                    }
                },
                "timestamp": "2020-05-28T11:39:11Z"
            },
            "lastModifiedAt": "2020-05-28T11:39:13Z"
        },
        {
            "relatedEntityId": "GesCQXBHQTEuMi6DAYVkXy6DIaLPXg",
            "entityId": "6905931257525.983",
            "timestamp": 1590666079000,
            "entity": {
                "environment": {
                    "browserDetails": {
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.61 Safari/537.36",
                        "acceptLanguage": "en"
                    }
                },
                "web": {
                    "webPageDetails": {
                        "name": "Radiant Tee - (Orange)"
                    }
                },
                "identityMap": {
                    "GOOGLE": [
                        {
                            "id": "GA1.2.1600423169.1590665761"
                        }
                    ]
                },
                "_id": "6905931257525.983",
                "commerce": {
                    "productViews": {
                        "value": 1
                    }
                },
                "productListItems": [
                    {
                        "name": "Radiant Tee - (Orange)",
                        "product": "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/58ae7e91a9bac17cdf92a178d6e25186_1.jpg",
                        "quantity": 1,
                        "productAddMethod": "Desktop",
                        "SKU": "Radiant Tee - (Orange)",
                        "priceTotal": 22
                    }
                ],
                "timestamp": "2020-05-28T11:41:19Z",
                "_apac_sc": {
                    "productData": {
                        "productUrl": "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/58ae7e91a9bac17cdf92a178d6e25186_1.jpg",
                        "productName": "Radiant Tee - (Orange)",
                        "productInteraction": "productView"
                    },
                    "brand": {
                        "brandName": "Luma Retail",
                        "tms": "GTM"
                    },
                    "identification": {
                        "gaid": "GA1.2.1600423169.1590665761"
                    }
                }
            },
            "lastModifiedAt": "2020-05-28T11:41:21Z"
        },
        {
            "relatedEntityId": "A2-OOBvy2Ns7YZIkm23k9uoE",
            "entityId": "2718359654069.1577",
            "timestamp": 1590666080000,
            "entity": {
                "environment": {
                    "browserDetails": {
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.61 Safari/537.36",
                        "acceptLanguage": "en"
                    }
                },
                "web": {
                    "webPageDetails": {
                        "name": "Radiant Tee - (Orange)",
                        "URL": "https://aepdemo.net/p4.html"
                    }
                },
                "_id": "2718359654069.1577",
                "commerce": {
                    "productViews": {
                        "value": 1
                    }
                },
                "productListItems": [
                    {
                        "name": "Radiant Tee - (Orange)",
                        "product": "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/58ae7e91a9bac17cdf92a178d6e25186_1.jpg",
                        "quantity": 1,
                        "productAddMethod": "Desktop",
                        "SKU": "LUMA-24-CXV14",
                        "priceTotal": 22
                    }
                ],
                "_apac_sc": {
                    "campaign": {
                        "campaignId": ""
                    },
                    "productData": {
                        "productUrl": "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/58ae7e91a9bac17cdf92a178d6e25186_1.jpg",
                        "productName": "Radiant Tee - (Orange)",
                        "productInteraction": "productView"
                    },
                    "identification": {
                        "ecid": "70064353701262275980354366981653865618"
                    },
                    "brand": {
                        "ldap": "vangeluw",
                        "brandName": "Luma Retail",
                        "tms": "Launch"
                    }
                },
                "timestamp": "2020-05-28T11:41:20Z"
            },
            "lastModifiedAt": "2020-05-28T11:41:21Z"
        },
        {
            "relatedEntityId": "A2-OOBvy2Ns7YZIkm23k9uoE",
            "entityId": "7648937446618.019",
            "timestamp": 1590666107000,
            "entity": {
                "environment": {
                    "browserDetails": {
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.61 Safari/537.36",
                        "acceptLanguage": "en"
                    }
                },
                "_id": "7648937446618.019",
                "web": {
                    "webPageDetails": {
                        "pageViews": {
                            "value": 1
                        },
                        "name": "Luma Retail Home",
                        "URL": "https://aepdemo.net/index.html"
                    }
                },
                "_apac_sc": {
                    "campaign": {
                        "campaignId": ""
                    },
                    "brand": {
                        "ldap": "vangeluw",
                        "brandName": "Luma Retail",
                        "tms": "Launch"
                    },
                    "identification": {
                        "ecid": "70064353701262275980354366981653865618"
                    }
                },
                "timestamp": "2020-05-28T11:41:47Z"
            },
            "lastModifiedAt": "2020-05-28T11:41:48Z"
        },
        {
            "relatedEntityId": "A2-OOBvy2Ns7YZIkm23k9uoE",
            "entityId": "3574385856064.7007",
            "timestamp": 1590666194000,
            "entity": {
                "environment": {
                    "browserDetails": {
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.61 Safari/537.36",
                        "acceptLanguage": "en"
                    }
                },
                "_id": "3574385856064.7007",
                "web": {
                    "webPageDetails": {
                        "pageViews": {
                            "value": 1
                        },
                        "name": "Register",
                        "URL": "https://aepdemo.net/login-register.html"
                    }
                },
                "_apac_sc": {
                    "campaign": {
                        "campaignId": ""
                    },
                    "brand": {
                        "ldap": "vangeluw",
                        "brandName": "Luma Retail",
                        "tms": "Launch"
                    },
                    "identification": {
                        "ecid": "70064353701262275980354366981653865618"
                    }
                },
                "timestamp": "2020-05-28T11:43:14Z"
            },
            "lastModifiedAt": "2020-05-28T11:43:15Z"
        },
        {
            "relatedEntityId": "A2-OOBvy2Ns7YZIkm23k9uoE",
            "entityId": "7430305893729.134",
            "timestamp": 1590666382000,
            "entity": {
                "environment": {
                    "browserDetails": {
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.61 Safari/537.36",
                        "acceptLanguage": "en"
                    }
                },
                "_id": "7430305893729.134",
                "web": {
                    "webPageDetails": {
                        "pageViews": {
                            "value": 1
                        },
                        "name": "Luma Retail Home",
                        "URL": "https://aepdemo.net/index.html"
                    }
                },
                "_apac_sc": {
                    "campaign": {
                        "campaignId": ""
                    },
                    "brand": {
                        "ldap": "vangeluw",
                        "brandName": "Luma Retail",
                        "tms": "Launch"
                    },
                    "identification": {
                        "ecid": "70064353701262275980354366981653865618"
                    }
                },
                "timestamp": "2020-05-28T11:46:22Z"
            },
            "lastModifiedAt": "2020-05-28T11:46:25Z"
        },
        {
            "relatedEntityId": "A2-OOBvy2Ns7YZIkm23k9uoE",
            "entityId": "9703616156885.674",
            "timestamp": 1590666414000,
            "entity": {
                "environment": {
                    "browserDetails": {
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.61 Safari/537.36",
                        "acceptLanguage": "en"
                    }
                },
                "_id": "9703616156885.674",
                "web": {
                    "webPageDetails": {
                        "pageViews": {
                            "value": 1
                        },
                        "name": "Luma Retail Home",
                        "URL": "https://aepdemo.net/index.html#"
                    }
                },
                "_apac_sc": {
                    "campaign": {
                        "campaignId": ""
                    },
                    "brand": {
                        "ldap": "vangeluw",
                        "brandName": "Luma Retail",
                        "tms": "Launch"
                    },
                    "identification": {
                        "ecid": "70064353701262275980354366981653865618"
                    }
                },
                "timestamp": "2020-05-28T11:46:54Z"
            },
            "lastModifiedAt": "2020-05-28T11:46:55Z"
        },
        {
            "relatedEntityId": "A2-gvnReLZPTUFyy99pj_O51",
            "entityId": "1590667564.980942",
            "timestamp": 1590667560000,
            "entity": {
                "_id": "1590667564.980942",
                "eventType": "storeEntry",
                "web": {
                    "webPageDetails": {
                        "pageViews": {
                            "value": 1
                        },
                        "name": "Beacon Entry - Luma Retail - Waregem"
                    }
                },
                "_experience": {
                    "campaign": {
                        "orchestration": {
                            "eventID": "b7c500a6a32a14216374a39394023d9c1e662544fb9e07714e754f2294d63b12"
                        }
                    }
                },
                "timestamp": "2020-05-28T12:06:00Z",
                "_apac_sc": {
                    "storeEntry": {
                        "brandName": "Luma Retail",
                        "storeName": "Waregem",
                        "location": "vangeluw",
                        "state": "Entry"
                    },
                    "identification": {
                        "pushToken": "03F87FDD39A3CADE193407F5526219641C78034638736C5FF67777B8474369AF",
                        "ecid": "58241605661877039688498007052700332636"
                    }
                }
            },
            "lastModifiedAt": "2020-05-28T12:06:06Z"
        },
        {
            "relatedEntityId": "A2-gvnReLZPTUFyy99pj_O51",
            "entityId": "1590667582.154284",
            "timestamp": 1590667560000,
            "entity": {
                "_id": "1590667582.154284",
                "timestamp": "2020-05-28T12:06:00Z",
                "_apac_sc": {
                    "identification": {
                        "ecid": "58241605661877039688498007052700332636",
                        "emailId": "woutervangeluwe+28052020-10@gmail.com"
                    }
                }
            },
            "lastModifiedAt": "2020-05-28T12:06:23Z"
        },
        {
            "relatedEntityId": "A2-gvnReLZPTUFyy99pj_O51",
            "entityId": "1590667588.3219628",
            "timestamp": 1590667560000,
            "entity": {
                "_id": "1590667588.3219628",
                "eventType": "storeExit",
                "web": {
                    "webPageDetails": {
                        "pageViews": {
                            "value": 1
                        },
                        "name": "Beacon Exit - Luma Retail - Waregem"
                    }
                },
                "timestamp": "2020-05-28T12:06:00Z",
                "_apac_sc": {
                    "storeEntry": {
                        "brandName": "Luma Retail",
                        "storeName": "Waregem",
                        "location": "vangeluw",
                        "state": "Entry"
                    },
                    "identification": {
                        "ecid": "58241605661877039688498007052700332636"
                    }
                }
            },
            "lastModifiedAt": "2020-05-28T12:06:29Z"
        },
        {
            "relatedEntityId": "A2-gvnReLZPTUFyy99pj_O51",
            "entityId": "1590667603.070987",
            "timestamp": 1590667560000,
            "entity": {
                "_id": "1590667603.070987",
                "commerce": {
                    "productViews": {
                        "value": 1
                    }
                },
                "web": {
                    "webPageDetails": {
                        "name": "Cora Parachute Pant"
                    }
                },
                "productListItems": [
                    {
                        "name": "Cora Parachute Pant",
                        "product": "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/20ac59cb5aad041e634a43cebb87706d_1.jpg",
                        "quantity": 1,
                        "productAddMethod": "Mobile App",
                        "SKU": "LUMA-24-WB4785"
                    }
                ],
                "timestamp": "2020-05-28T12:06:00Z",
                "_apac_sc": {
                    "productData": {
                        "productUrl": "https://parsefiles.back4app.com/hgJBdVOS2eff03JCn6qXXOxT5jJFzialLAHJixD9/20ac59cb5aad041e634a43cebb87706d_1.jpg",
                        "productName": "Cora Parachute Pant",
                        "productInteraction": "productView"
                    },
                    "brand": {
                        "tms": "Launch"
                    },
                    "identification": {
                        "ecid": "58241605661877039688498007052700332636"
                    }
                }
            },
            "lastModifiedAt": "2020-05-28T12:06:45Z"
        },
        {
            "relatedEntityId": "A2-OOBvy2Ns7YZIkm23k9uoE",
            "entityId": "3334663289694.599",
            "timestamp": 1590667621000,
            "entity": {
                "environment": {
                    "browserDetails": {
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.61 Safari/537.36",
                        "acceptLanguage": "en"
                    }
                },
                "_id": "3334663289694.599",
                "web": {
                    "webPageDetails": {
                        "pageViews": {
                            "value": 1
                        },
                        "name": "Luma Retail Home",
                        "URL": "https://aepdemo.net/index.html"
                    }
                },
                "_apac_sc": {
                    "campaign": {
                        "campaignId": ""
                    },
                    "brand": {
                        "ldap": "vangeluw",
                        "brandName": "Luma Retail",
                        "tms": "Launch"
                    },
                    "identification": {
                        "ecid": "70064353701262275980354366981653865618"
                    }
                },
                "timestamp": "2020-05-28T12:07:01Z"
            },
            "lastModifiedAt": "2020-05-28T12:07:02Z"
        },
        {
            "relatedEntityId": "A2-gvnReLZPTUFyy99pj_O51",
            "entityId": "1590672952.355521",
            "timestamp": 1590672900000,
            "entity": {
                "_id": "1590672952.355521",
                "eventType": "storeEntry",
                "web": {
                    "webPageDetails": {
                        "pageViews": {
                            "value": 1
                        },
                        "name": "Beacon Entry - Luma Retail - Waregem"
                    }
                },
                "_experience": {
                    "campaign": {
                        "orchestration": {
                            "eventID": "b7c500a6a32a14216374a39394023d9c1e662544fb9e07714e754f2294d63b12"
                        }
                    }
                },
                "timestamp": "2020-05-28T13:35:00Z",
                "_apac_sc": {
                    "storeEntry": {
                        "brandName": "Luma Retail",
                        "storeName": "Waregem",
                        "location": "vangeluw",
                        "state": "Entry"
                    },
                    "identification": {
                        "pushToken": "03F87FDD39A3CADE193407F5526219641C78034638736C5FF67777B8474369AF",
                        "ecid": "58241605661877039688498007052700332636"
                    }
                }
            },
            "lastModifiedAt": "2020-05-28T13:35:54Z"
        },
        {
            "relatedEntityId": "A2-gvnReLZPTUFyy99pj_O51",
            "entityId": "1590672985.06268",
            "timestamp": 1590672960000,
            "entity": {
                "_id": "1590672985.06268",
                "eventType": "storeExit",
                "web": {
                    "webPageDetails": {
                        "pageViews": {
                            "value": 1
                        },
                        "name": "Beacon Exit - Luma Retail - Waregem"
                    }
                },
                "timestamp": "2020-05-28T13:36:00Z",
                "_apac_sc": {
                    "storeEntry": {
                        "brandName": "Luma Retail",
                        "storeName": "Waregem",
                        "location": "vangeluw",
                        "state": "Entry"
                    },
                    "identification": {
                        "ecid": "58241605661877039688498007052700332636"
                    }
                }
            },
            "lastModifiedAt": "2020-05-28T13:36:26Z"
        }
    ],
    "_links": {
        "next": {
            "href": ""
        }
    }
}
```

This is currently all of the available ExperienceEvent data in Platform for this ECID.

You're not required to use the ECID to request ExperienceEvent data from Adobe Experience Platform's Real-time Profile, you can use any ID in any namespace to request this data. 

Next Step: [3.4 Create a segment - UI](./ex4.md)

[Go Back to Module 3](./real-time-customer-profile.md)

[Go Back to All Modules](../../overview.md)
