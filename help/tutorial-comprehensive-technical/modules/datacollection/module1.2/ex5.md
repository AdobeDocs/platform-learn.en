---
title: Foundation - Data Ingestion - Data Ingestion from Offline Sources
description: Foundation - Data Ingestion - Data Ingestion from Offline Sources
kt: 5342
doc-type: tutorial
exl-id: 21b84a77-4115-4ba7-b847-b236aa14bbdd
---
# 1.2.5 Data Landing Zone

In this exercise, the goal is to setup your Data Landing Zone Source connector with Azure Blob storage.

Data Landing Zone is an Azure Blob storage interface provisioned by Adobe Experience Platform, granting you to access a secure, cloud-based file storage facility to bring files into Platform. Data Landing Zone supports SAS-based authentication and its data is protected with standard Azure Blob storage security mechanisms at rest and in transit. SAS-based authentication allows you to securely access your Data Landing Zone container through a public internet connection.

>[!NOTE]
>
> Adobe Experience Platform **enforces a strict seven-day time-to-live (TTL)** on all files uploaded to a Data Landing Zone container. All files are deleted after seven days.


## Prerequisites

To copy blobs or files to your Adobe Experience Platform Data Landing Zone you'll use AzCopy, a command-line utility. You can download a version for your operating system via [https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10), scroll down on that page to **Download the AzCopy portable binary** and select the approproate version for your OS.

![dlz-install-az-copy.png](./images/dlzinstallazcopy.png)

- Unzip the downloaded file

![dlz-install-az-copy.png](./images/dlz1.png)

- Download the sample data file [global-context-websiteinteractions.csv](./../../../assets/csv/data-ingestion/global-context-websiteinteractions.csv), which contains sample website interactions and save it into the folder in which you unzipped **azcopy**.

![dlz-install-az-copy.png](./images/dlz2.png)

- Open a terminal window and navigate to the folder on your desktop, you should see the following content (azcopy and global-context-websiteinteractions.csv), for example on OSX:

![dlz-unzip-azcopy.png](./images/dlzunzipazcopy.png)

## 1.2.5.2 Connect Data Landing Zone to Adobe Experience Platform

Log in to Adobe Experience Platform by going to this URL: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](./images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxName--``.  After selecting the appropriate sandbox, you'll see the screen change and now you're in your dedicated sandbox.

![Data Ingestion](./images/sb1.png)

In the left menu, go to **Sources**. In the Sources catalog, search for **data landing**. 

![Data Ingestion](./images/sourcesdlz.png)

Click the **Data Landing Zone** card, you'll see the credentials on the right tab.

![dlz-view-credentials.png](./images/dlzviewcredentials.png)

Click the icon as indicated to copy the **SASUri**.

![dlz-copy-sas-uri.png](./images/dlzcopysasuri.png)

## Copy your csv-file to your AEP data landing zone

You'll now ingest data into Adobe Experience Platform using Azure command line tools using AZCopy.

Open a terminal at the location of you azcopy install location and execute the following command to copy a file into AEP's data landing zone:

``./azcopy copy <your-local-file> <your SASUri>``
  
Make sure to surround your SASUri with double quotes. Replace `<your-local-file>` by the path to your local copy of the file **global-context-websiteinteractions.csv** in the azcopy directory, and replace `<your SASUri>` by the **SASUri** value which you copied from the Adobe Experience Platform UI. Your command should look like this:

```command
./azcopy copy global-context-websiteinteractions.csv "https://sndbxdtlnd2bimpjpzo14hp6.blob.core.windows.net/dlz-user-container?sv=2020-04-08&si=dlz-xxxxxxx-9843-4973-ae52-xxxxxxxx&sr=c&sp=racwdlm&sig=DN3kdhKzard%2BQwKASKg67Zxxxxxxxxxxxxxxxx"
```

After executing the above command in your terminal, you'll see this:

![dlz-exec-copy-command.png](./images/dlzexeccopycommand.png)

## Lookup your file in your Data Landing Zone

Go to your Data Landing Zone in Adobe Experience Platform.

Select **Sources**, search for **data landing** and click the **Setup** button.

![dlz-inspect-datalanding-zone.png](./images/dlzinspectdatalandingzone.png)

This will open the Data Landing Zone. You'll see the file that you just uploaded in the data landing zone's **select data** panel.

![dlz-datalanding-zone-open.png](./images/dlzdatalandingzoneopen.png)

## Process your file

Select your file and select **Delimited** as data format. You'll then see a preview of your data. Click **Next**.

![dlz-datalanding-select-file.png](./images/dlzdatalandingselectfile.png)

You can now start mapping the uploaded data to match the XDM schema of your dataset.

Select **Existing dataset** and select the dataset **Demo System - Event Dataset for Website (Global v1.1)**. Click **Next**.

![dlz-target-dataset.png](./images/dlztargetdataset.png)

Now you are ready map the incoming source data from your csv file to the target fields from the dataset's XDM schema.

![dlz-start-mapping.png](./images/dlzstartmapping.png)

>[!NOTE]
>
> Don't mind the potential errors with the mapping. You'll correct the mapping in the next step.

## Map fields

First of all, click the **Clear all mappings** button. You can then start with a clean mapping.

![dlz-clear-mappings.png](./images/mappings1.png)

Next, click **New field type** and then select **Add new field**.

![dlz-clear-mappings.png](./images/dlzclearmappings.png)

To map the **ecid** source field, select the field **identities.ecid** and click **Select**.

![dlz-map-identity.png](./images/dlzmapidentity.png)

Next, click **Map target field**.

![dlz-map-select-target-field.png](./images/dlzmapselecttargetfield.png)

Select the field ``--aepTenantId--``.identification.core.ecid in the schema structure.

![dlz-map-target-field.png](./images/dlzmaptargetfield.png)

You need to map a couple of other fields, click **+ New field type** followed by **Add new field** and add fields for this mapping

| source  | target  |
|---|---|
| resource.info.pagename |  web.webPageDetails.name |
| timestamp  |  timestamp |
| timestamp |  _id |

![dlz-add-other-mapping.png](./images/dlzaddothermapping.png)

When finished your screen should look like, the screen below. Click **Next**.

![dlz-mapping-result.png](./images/dlzmappingresult.png)

Click **Next**.

![dlz-default-scheduling.png](./images/dlzdefaultscheduling.png)

Click **Finish**.

![dlz-import-finish.png](./images/dlzimportfinish.png)

## Monitor dataflow 

To monitor you dataflow, go to **Sources**, **Dataflows** and click on your dataflow:

![dlz-monitor-dataflow.png](./images/dlzmonitordataflow.png)

Loading the data can take a couple of minutes, when succesful, you'll see a status of **Success**:

![dlz-monitor-dataflow-result.png](./images/dlzmonitordataflowresult.png)

Next Step: [Summary and benefits](./summary.md)

[Go Back to Module 1.2](./data-ingestion.md)

[Go Back to All Modules](../../../overview.md)
