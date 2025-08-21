---
title: GenStudio for Performance Marketing Create your Amazon AWS S3 bucket
description: GenStudio for Performance Marketing Create your Amazon AWS S3 bucket
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
---
# 1.6.2 Create your AWS S3 bucket

## 1.6.2.1 Create your S3 bucket

Go to [https://console.aws.amazon.com](https://console.aws.amazon.com) and sign in.

>[!NOTE]
>
>If you don't have an AWS account yet, please create a new AWS account using your personal email address.

![ETL](./images/awshome.png)

After logging in, you'll be redirected to the **AWS Management Console**.

![ETL](./images/awsconsole.png)

In the search bar, search for **s3**. Click the first search result: **S3 - Scalable Storage in the Cloud**.

![ETL](./images/awsconsoles3.png)

You'll then see the **Amazon S3** homepage. Click **Create Bucket**.

![ETL](./images/s3home.png)

In the **Create Bucket** screen, use the name `--aepUserLdap---gspem-dam`.

![ETL](./images/bucketname.png)

Leave all the other default settings as they are. Scroll down and click **Create bucket**.

![ETL](./images/createbucket.png)

You'll then see your bucket being created and will be redirected to the Amazon S3 homepage.

![ETL](./images/S3homeb.png)

## Set permissions to access your S3 bucket

The next step is to setup access to your S3 bucket.

To do that, go to [https://console.aws.amazon.com/iam/home](https://console.aws.amazon.com/iam/home).

Access to AWS resources is controlled by Amazon Identity and Access Management (IAM).

You'll now see this page.

![ETL](./images/iam.png)

In the left menu, click **Users**. You'll then see the **Users** screen. Click **Create user**.

![ETL](./images/iammenu.png)

Next, configure your user:

- User Name: use `s3_--aepUserLdap--_gspem_dam`

Click **Next**.

![ETL](./images/configuser.png)

You'll then see this permissions screen. Click **Attach policies directly**.

![ETL](./images/perm1.png)

Enter the search term **s3** to see all related S3 policies. Select the policy **AmazonS3FullAccess**. Scroll down and click **Next**.

![ETL](./images/perm2.png)

Review your configuration. Click **Create User**.

![ETL](./images/review.png)

You'll then see this. Click **View User**.

![ETL](./images/review1.png)

Click **Security credentials** and then click **Create access key**.

![ETL](./images/cred.png)

Select **Application running outside AWS**. Scroll down and click **Next**.

![ETL](./images/creda.png)

Click **Create access key**

![ETL](./images/credb.png)

You'll then see this. Click **Show** to see your Secret access key:

![ETL](./images/cred1.png)

Your **Secret access key** is now being shown.

>[!IMPORTANT]
>
>Store your credentials in a text-file in your computer.
>
> - Access key ID: ...
> - Secret access key: ...
>
> Once you click **Done** you'll never see your credentials again!

Click **Done**. 

![ETL](./images/cred2.png)

You've now successfully created an AWS S3 bucket and you've created a user with permissions to access this bucket.

## 1.6.2.2 Upload Assets to your S3 bucket

In the search bar, search for **s3**. Click the first search result: **S3 - Scalable Storage in the Cloud**.

![ETL](./images/bucket1.png)

Click to open your newly creatd S3 bucket, which should be named `--aepUserLdap---gspem-dam`.

![ETL](./images/bucket2.png)

Click **Upload**.

![ETL](./images/bucket3.png)

You should then see this. 

![ETL](./images/bucket4.png)

You can download CitiSignal image files [here](./images/package.zip){target="_blank"}.

Export the files onto your desktop.

![ETL](./images/bucket5.png)

Click **Add Folder**.

![ETL](./images/bucket6.png)

Select the folder **assets** from the download folder **package**. Click **Upload**.

![ETL](./images/bucket7.png)

You should then see this. Click **Add Folder** again.

![ETL](./images/bucket8.png)

Select the folder **thumbnails** from the download folder **package**. Click **Upload**.

![ETL](./images/bucket9.png)

You should then see this. Click **Upload**.

![ETL](./images/bucket10.png)

Your upload is now done. Click **Close**.

![ETL](./images/bucket11.png)

You should now have this folder structure in your S3 bucket.

![ETL](./images/bucket12.png)

## Next Steps

Go to [Create your external DAM app](./ex3.md){target="_blank"}

Go back to [GenStudio for Performance Marketing - Extensibility](./genstudioext.md){target="_blank"}

Go back to [All Modules](./../../../overview.md){target="_blank"}
