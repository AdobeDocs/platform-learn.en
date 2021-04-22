---
title: Real-time CDP - Build a segment and take action - Send your segment to an S3-destination
description: Real-time CDP - Build a segment and take action - Send your segment to an S3-destination
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 9fc940fd-da61-428e-b091-41a91e4fb7e8
---
# 11.5 Take Action: send your segment to an S3-destination

Adobe Experience Platform also has the ability to share Audiences to Email Marketing Destinations such as Salesforce Marketing Cloud, Oracle Eloqua, Oracle Responsys and Adobe Campaign.

You can use FTP or SFTP as part of the dedicated destinations for each of these Email Marketing Destinations, or you can use AWS S3 to exchange lists of customers between Adobe Experience Platform and these Email Marketing Destinations.

In this module, you'll configure such a destination by making use of an AWS S3 bucket.

## Create your S3 bucket

Go to [https://console.aws.amazon.com](https://console.aws.amazon.com) and sign in with the Amazon-account you created in Module 4.

![ETL](./images/awshome.png) 

After logging in, you'll be redirected to the **AWS Management Console**.

![ETL](./images/awsconsole.png)

In the **Find Services** menu, search for **s3**.

![ETL](./images/awsconsoles3.png)

Click the first search result: **S3 - Scalable Storage in the Cloud**.

You'll then see the **Amazon S3** homepage.

![ETL](./images/s3home.png)

Click the **Create Bucket** button.

![ETL](./images/createbucket.png)

In the **Create Bucket** screen, you need to configure two things:
  
- Name: use the name **aepmodule11LDAP** and replace LDAP by your LDAP. As an example, in this exercise the bucket name is **aepmodule11vangeluw**
- Region: use the region **EU (Frankfurt) eu-central-1**

![ETL](./images/bucketname.png) 

Click the **Create** button.

![ETL](./images/createbucket.png)

You'll then see your bucket being created and will be redirected to the Amazon S3 homepage.

![ETL](./images/S3homeb.png)

### Set permissions to access your S3 bucket

The next step is to setup access to your S3 bucket.

To do that, go to [https://console.aws.amazon.com/iam/home](https://console.aws.amazon.com/iam/home).

Access to AWS resources is controlled by Amazon Identity and Access Management (IAM).

You'll now see this page.

![ETL](./images/iam.png)

In the left menu, click **Users**.

![ETL](./images/iammenu.png)

You'll then see the **Users** screen.

![ETL](./images/users.png)

Click **Add User**.

![ETL](./images/adduser.png)

Next, configure your user:

- User Name: use **s3_ldap_module11** as a name, so in this example the name is **s3_vangeluw_module11**.
- AWS access type: select **Programmatic access**.

![ETL](./images/configuser.png)

Click **Next: Permissions**.

![ETL](./images/nextperm.png)

You'll then see this permissions screen. Click **Attach existing policies directly**.

![ETL](./images/perm1.png) 

Enter the search term **s3** to see all related S3 policies. Select the policy **AmazonS3FullAccess**.

![ETL](./images/perm2.png)

Click **Next: Tags**.

![ETL](./images/nexttags.png) 

On the **Tags** screen, there's no need to configure anything.

![ETL](./images/perm3.png)

Click **Next: Review**.

Review your configuration.

![ETL](./images/review.png)

Click **Create User**.

Your user is now created and you're seeing your Credentials to access your S3 environment. This is the only time you'll see your credentials so please write them down.

![ETL](./images/cred.png)

Click **Show** to see your Secret access key:

![ETL](./images/cred1.png)

>[!IMPORTANT]
>
>Store your credentials in a text-file in your computer.
>
> - Access key ID: ...
> - Secret access key: ...
>
> Once you click **Close** you'll never see your credentials again!

Click **Close**. 

![ETL](./images/close.png)

You've now successfully created an AWS S3 bucket and you've created a user with permissions to access this bucket.

### Configure Destination in Adobe Experience Platform

Log in to Adobe Experience Platform by going to this URL: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./images/home.png)

Before you continue, make sure you are in the `Production Prod`-environment in the blue line on top of your screen.

In the left menu, go to **Destinations**.

![RTCDP](./images/rtcdpmenudest.png)

You'll then see the **Destinations** homepage.

![RTCDP](./images/rtcdp.png)

Select the type **Connections**.

![RTCDP](./images/rtcdp2.png)

Click on **Amazon S3** and then click on **+ Connect Destination**.

![RTCDP](./images/rtcdpsf.png)

Select **New Account** as Account Type. Please use the S3 credentials that were given to you in the previous step:

| Access Key ID             | Secret Access Key             |
|:-----------------------:| :-----------------------:|
| AKIA..... |Cm5Ln.....|

![RTCDP](./images/rtcdpsfs3.png)

Click **Connect to destination**.

![RTCDP](./images/rtcdpsfs3connect.png)

You'll then see a visual confirmation that this destination is now connected.

![RTCDP](./images/rtcdpsfs3connected.png)

Click **Next**.

![RTCDP](./images/next.png)

On the next screen, you have to provide a name and folder so that Adobe Experience Platform can connect to the S3 bucket.

![RTCDP](./images/rtcdpsfs3connect1.png)

As a naming convention, please use the following:

| Access Key ID             | Secret Access Key             |
|:-----------------------:| :-----------------------:|
| Name |AWS - S3 - ldap, replace **ldap** with your ldap.|
| Description |AWS - S3 - ldap, replace **ldap** with your ldap.|
| Bucket Name |aepmodule11vangeluw|
| Folder Path |/|

![RTCDP](./images/rtcdpsfs3connect2.png)

Click **Create Destination** to create your connection.

![RTCDP](./images/rtcdpsfs3connect2create.png)

You'll see a confirmation that the destination has been created.

![RTCDP](./images/rtcdpsfs3connect2created.png)

Click **Next**.

![RTCDP](./images/next.png)

After creating the destination, you can select segments to send to your AWS S3 destination.

![RTCDP](./images/rtcdpsfs3connect2created1.png)

In the list of segments, search for the segment you created in exercise 1 and select it.

![RTCDP](./images/s3a.png)

Click **Next**.

![RTCDP](./images/s3b.png)

You can now select attributes for the export towards AWS S3. Click **+ Add New Field**.

![RTCDP](./images/s3c.png)

Click the icon as indicated in the screenshot to open the Union Schema with all available fields.

![RTCDP](./images/s3d.png)

In the popup, you'll see the Union Schema and you can select any field from the Union Schema to include it in the export. In this example, the field **personalEmail.address** is selected to be part of the export.

Click **Select** to add the field.

![RTCDP](./images/s3e.png)

You can add as many fields as required.

Once you've added all fields, click **Next**.

![RTCDP](./images/s3b.png)

The export to AWS S3 will run once every 24 hours.

![RTCDP](./images/s3f.png)

Click **Next**.

![RTCDP](./images/s3b.png)

Review your configuration.

![RTCDP](./images/s3g.png)

Click **Finish** to finish your configuration.

![RTCDP](./images/s3i.png)

You'll then be back at the Destination Activation screen and you'll see your segment added to this destination.

![RTCDP](./images/s3j.png)

if you'd like to add more segment exports, you can click **Edit Activation** to restart the process and add more segments.

![RTCDP](./images/s3k.png)

Next Step: [11.6 Take Action: send your segment to Adobe Target](./ex6.md)

[Go Back to Module 11](./real-time-cdp-build-a-segment-take-action.md)

[Go Back to All Modules](../../overview.md)
