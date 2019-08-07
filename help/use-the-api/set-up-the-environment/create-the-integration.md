# Create the integration in Adobe I/O

1. An integration can be subscribed to one or more services. In many cases, you will use the same client credentials to access multiple Adobe services. In addition to APIs, you may also subscribe your integration to I/O Events so that your applications can access content and services in real-time.

1. Create Certificate

   Open terminal and execute below command:

   ```shell
   openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout private.key -out certificate_pub.crt
   ```

   You will get a response similar to the following which prompts you to enter some information about yourself:

   ```
   Generating a 2048 bit RSA private key
   .................+++
   .......................................+++
   writing new private key to 'private.key'
   -----
   You are about to be asked to enter information that will be incorporated
   into your certificate request.
   What you are about to enter is what is called a Distinguished Name or a DN.
   There are quite a few fields but you can leave some blank
   For some fields there will be a default value,
   If you enter '.', the field will be left blank.
   -----
   Country Name (2 letter code) []:
   State or Province Name (full name) []:
   Locality Name (eg, city) []:
   Organization Name (eg, company) []:
   Organizational Unit Name (eg, section) []:
   Common Name (eg, fully qualified host name) []:
   Email Address []:
   ```

   After entering the information two files will be generated: `certificate_pub.crt` and `private.key`. These files can be found in the same directory that you ran the `openssl` command from.

   Note `certificate_pub.crt` will expire in 365 days. You can make the period longer by changing the value of days in the openssl command above but rotating credentials periodically is a good security practice.

   The `certificate_pub.crt` certificate will later be uploaded to the Adobe IO Console for when you create an API key for access to any Adobe I/O API.

   Your private key file named `private.key` will be used later to sign your JWT token.

   > Note: Don't close this terminal window as you will need it later.

1. Navigate to the [Adobe I/O Console](https://console.adobe.io/) and sign in with your Adobe ID.

1. From this page we want to create a New Integration.

   ![New integration](./images/new_integration.png)

1. You will then be prompted to Access an API or to Receive near-real-time events. We will be accessing APIs so select Access an API and then Continue.

   ![New integration 1](./images/new_integration1.png)

1. The drop-down menu on the top right of the screen is where you would switch your organization if your account is tied to multiple. We are selecting `Summit Platform Lab 03` and `Experience Platform API` under `Adobe Experience Platform`.

   ![New integration 2](./images/new_integration2.png)

1. Fill in your Integration Details. Afterwards, click on Select a File to upload your certificate_pub.crt file we generated in the previous section. Then click on `AEP Summit 2019` to select this product profile. Finally, click Create Integration to finish up the process

   ![New ingtegration 4](./images/new_integration4.png)

1. After creating your integration, you will be able to view the details of your integration. After clicking on Retrieve client Secret your screen should look similar to this.

   ![Access values](./images/access_values.png)

   Copy down the values for {API KEY}, {IMS ORG} which is the Organization ID, and {CLIENT SECRET} as these will be used in the next step.