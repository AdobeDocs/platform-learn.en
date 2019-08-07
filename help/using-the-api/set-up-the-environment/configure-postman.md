## Exercise 0.2 - Authenticate via POSTMan

* Explain all of the environment variables
* Explain all of the calls in the collection
* Explain endpoints
* seems to be some segments stuff in l778 that isn't in git postman

Establishing your own best practices

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

1. Start POSTMan

   ![](images/postman.png)

1. Click the `Import` button on the top left.

   ![](images/postman_import.png)

   Select the [L778.postman_collection.json](/resources/L778.postman_collection.json) collection file from this repository.

1. Next we need to import our environment. Click on the settings logo

   ![](images/postman_settings.png)

   To bring up the **Manage Environments** dialog.

   ![](images/postman_manage_env.png)

1. Then click on `Import`

   ![](images/postman_import_env.png)

1. Select the [L778.postman_environment.json](/resources/L778.postman_environment.json) file to import the environment.

   ![](images/postman_after_env_import.png)

1. Now click on the newly imported `L778 - Environment`.

   ![](images/postman_set_env.png)

1. Fill out the values for:

   - clientID
   - clientSecret
   - OrgID
   - TechAcctID

   that you generated when you created your **new integration**.

   **Fill these out in both the "Initial Values" and the "Current Values" field.**

   **Your AccountID is assigned to you by your computer's label and should appear as L778+###.** Fill out the `ldap` field in Postman with your Account ID (L778+###) so you'll be able to uniquely identify the datasets you create.

1. Copy the contents of the `private.key` and use it as the value for `secret`.

   From the same terminal you ran `openssl`, execute the following command:

   ```shell
   pbcopy < private.key
   ```

   Paste the contents of the clipboard into the `secret`, include the `-----BEGIN PRIVATE KEY-----` and `-----END PRIVATE KEY-----` lines up to the last `-`. When you paste the contents of the clipboard into POSTman you may end up with an extra new line character.

   ![](images/private_key_bad.png)

   Make sure you delete this character as it is not required and will cause problems with authentication.

   ![](images/private_key_good.png)

1. Click `Update` and close the `Manage Environments` dialog.

1. Now make sure you select the `L778 - Environment` from the environments drop down at the top right of POSTMan.

   ![](images/postman_experience_platform_env.png)

1. After all this setup you are now ready to generate an JWT and bearer token to interact with Adobe I/O. In order to make this process easier we'll be using an Adobe I/O Runtime action.

   From our newly imported `L778` collection, open `Lesson 0` and click on `Adobe I/O Runtime: Generate Auth`. Then click on the body tab:

   ![](images/postman_auth_body.png)

   All of that work you did to setup the environment has been put to good use. Each POSTMan call will take advantage of these values.

1. Now click `Send` and scroll down to the response section:

   ![](images/postman_auth_response.png)

   That JSON response includes an `access_token` which is the Bearer token used to authenticate with Adobe I/O. The POSTMan call will save this value in an environment variable for future use.

## Exercise 0.3 - Setup Fenix Web Server

1.  Download the [Luma website](/resources/Luma-local.zip).
1.  Unzip the `Luma-local.zip` file and make note of which directory you extract the content to.
1.  Start the Fenix web server.

    ![](images/start-fenix.png)

1.  Select the `Web Servers` menu and click `New`

    ![](images/new-server.png)

1.  Use `Luma` as descriptive name.

    ![](images/luma.png)

1.  Click on the folder in the `Directory` input field. Then navigate the file dialog to the directory you unzipped the `Luma-local` folder, for the lab machines it should be `Desktop/resources/Luma-local`, highlight it and click `Select`.

    ![](images/select-folder.png)

1.  Click `Create`.

    ![](images/create.png)

1.  Click on the `Play` button to start the server.

    ![](images/click-start.png)

1.  Now your Luma site should be ready to be browsed.

    ![](images/server-started.png)

1)  Navigate to [http://luma.com](http://luma.com) to test the web server. You should see the following:

    ![](images/not-localhost.png)

## Lesson 0 - Wrap

Whew! We are finally ready to start calling the Adobe Experience Platform API's for real. We've run through creating an integration and getting authenticated.

## Lesson 0 - Additional Resources

- [Authentication Documentation on Adobe I/O](https://www.adobe.io/authentication.html)
- [Using POSTMan for JWT authentication on Adobe I/O - Adobe Tech Blog](https://medium.com/adobetech/using-postman-for-jwt-authentication-on-adobe-i-o-7573428ffe7f)