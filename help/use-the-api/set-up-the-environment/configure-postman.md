# Configure Postman

In this lesson, you will configure a Postman environment with environment variables from your new integration and a collection of requests provided by Adobe. Postman is a widely used tool for interacting with APIs and was chosen for this tutorial as a "common denominator" environment for learning the API. Once you are comfortable with the API, can then incorporate them as needed into your own custom environment. If you are new to Postman, we're confident you will quickly get up-to-speed. 

## Prerequisites

In order to complete this lesson, you need to have Developer-level access to Platform

## Learning Objectives

* Get comfortable using Postman
* Explain the environment variables
* Explain the calls in the collection
* Explain the Platform endpoints

## Download and Install Postman

If you don't already have it, [download and install Postman](https://www.getpostman.com/) on your machine.

## Authenticate via Postman

<!--Establishing your own best practices

Quotes from customers about how they like to work

Maybe organize by the UI labels:

1. Data Management
   1. Schemas
   1. Datasets
   1. Connections
   1. Queries
   1. Monitoring
1. Unified Profile
   1. Profiles
   1. Segments
   1. Identities
1. Data Science
   1. Models
   1. Services
-->
1. Start Postman
   ![Start Postman](../assets/postman.png)

1. Click the `Import` button on the top left.
   ![Click Import](../assets/postman_import.png)

   Select the [Check_Streaming_to_Profile.json](https://github.com/adobe/experience-platform-postman-samples/blob/master/Postman%20Collections/Check_Streaming_to_Profile.json) collection file from this repository.

1. Next we need to import our environment. Click on the settings icon ![settings icon](../assets/postman_settings.png) to open the **Manage Environments** dialog.

   ![Click on the settings icon to open the Manage Environments dialog.](../assets/postman_manage_env.png)

1. Then click on `Import`

   ![Click on "Import"](../assets/postman_import_env.png)

1. Select the [L778.postman_environment.json](../assets//L778.postman_environment.json) file to import the environment.

   ![](../assets/postman_after_env_import.png)

1. Now click on the newly imported `Check Streaming to Profile` environment.

   ![Click on the new environment](../assets/postman_set_env.png)

1. Using the values from the Adobe I/O integration you created in the last lesson, complete the values for the following, putting them **in both the "Initial Values" and the "Current Values" fields.**:

   * clientID
   * clientSecret
   * OrgID
   * TechAcctID

1. Complete the `ldap` field using your Adobe Id. This field will be used to to uniquely identify the datasets you create. <!--is this all the ldap field is used for? perhaps it should have a friendlier name in the collection-->

1. Copy the contents of the `private.key` and use it as the value for `secret`.  To copy the contents, from the same terminal you ran `openssl`, execute the following command:

   ```shell
   pbcopy < private.key
   ```

   Paste the contents of the clipboard into the `secret` field, include the `-----BEGIN PRIVATE KEY-----` and `-----END PRIVATE KEY-----` lines up to the last `-`. When you paste the contents of the clipboard into Postman you may end up with an extra new line character. Delete this newline character or it will prevent you from making API calls later on.

   ![Private key pasted into Postman](../assets/private_key_good.png)

1. Click `Update` and close the `Manage Environments` dialog.

1. Now make sure you select the `Check Streaming to Profile` from the environments drop down at the top right of Postman.

   ![Select the environment](../assets/postman_experience_platform_env.png)

1. From our newly imported collection, open `Auth Setup` and click on `INIT: Load Crypto Library for RS256`.<!--need to provide context on what this does. check with Thomas-->
1. Now you are ready to generate an JWT and bearer token to interact with Adobe I/O. In order to make this process easier we'll be using an Adobe I/O Runtime action. Click on `IMS: JWT Generate + Auth via User Token`. Then click on the body tab:<!--need to provide more context around the JWT token, how long it lasts, etc.-->

   ![Body tab of the JWT generation request](../assets/postman_auth_body.png)

   All of that work you did to setup the environment has been put to good use. Each Postman call will take advantage of these values.

1. Now click `Send` and scroll down to the response section:

   ![](../assets/postman_auth_response.png)

   That JSON response includes an `access_token` which is the Bearer token used to authenticate with Adobe I/O. The Postman call will save this value in an environment variable for future use.

Whew! We are finally ready to start calling the Adobe Experience Platform API's for real. We've run through creating an integration and getting authenticated.

## Lesson 0 - Additional Resources

* [Authentication Documentation on Adobe I/O](https://www.adobe.io/authentication.html)
* [Using Postman for JWT authentication on Adobe I/O - Adobe Tech Blog](https://medium.com/adobetech/using-postman-for-jwt-authentication-on-adobe-i-o-7573428ffe7f)