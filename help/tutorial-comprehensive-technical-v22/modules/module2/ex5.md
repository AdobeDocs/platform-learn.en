---
title: Foundation - Data Ingestion - Data Ingestion from Offline Sources
description: Foundation - Data Ingestion - Data Ingestion from Offline Sources
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 75602640-7738-4d73-aa27-767fcaa54fbc
---
# 2.5 Data Landing Zone

In this exercise, the goal is to setup your Data Landing Zone Source connector with Azure Blob storage.

Data Landing Zone is an Azure Blob storage interface provisioned by Adobe Experience Platform, granting you to access a secure, cloud-based file storage facility to bring files into Platform. Data Landing Zone supports SAS-based authentication and its data is protected with standard Azure Blob storage security mechanisms at rest and in transit. SAS-based authentication allows you to securely access your Data Landing Zone container through a public internet connection.

! Platform **enforces a strict seven-day time-to-live (TTL)** on all files uploaded to a Data Landing Zone container. All files are deleted after seven days.


## 2.5.1 Prerequisites

To copy blobs or files to your AEP Data Landing Zone we will use AzCopy, a command-line utility. You can download a version for your operating system via  https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10

![dlz-install-az-copy.png](./images/dlz-install-az-copy.png)

* Unzip the downloade file

* Download a sample data file [journey-citys-global-context-websiteinteractions.csv](../../assets/csv/data-ingestion/journey-citys-global-context-websiteinteractions.csv), which contains City Signal's website interactions and save it to the unzip location of azcopy.

* Open a terminal window and navigate to your "unzip" folder, you should see the following content (azcopy and citys-pages-s2-app.csv), for example on OSX:

![dlz-unzip-azcopy.png](./images/dlz-unzip-azcopy.png)

## 2.5.2 Connect Data Landing Zone to Adobe Experience Platform

Open Adobe Experience Platorm UI and navigate to "Sources" (1), in the "sources" catalog (2) search for "data landing" (3). On de "Data Landing Zone"-card, click the "..." and select "View Credentials" (4)

![dlz-view-credentials.png](./images/dlz-view-credentials.png)

Copy the "SASUri"-key

![dlz-copy-sas-uri.png](./images/dlz-copy-sas-uri.png)

## 2.5.3 Copy your csv-file to your AEP data landing zone

Copy data in AEP using Azure command line tools using AZCopy

Open a terminal at the location of you azcopy install location and execute the following command to copy a file into AEP's data landing zone:

./azcopy copy &lt;your-local-file&gt; &lt;your SASUri&gt;
  
Make sure to surround your SASUri with double quotes.

```command
./azcopy copy journey-citys-global-context-websiteinteractions.csv "https://sndbxdtlndemxdz3v9p7mlfm.blob.core.windows.net/dlz-user-container?sv=2020-04-08&si=dlz-eaf19e1f-06c2-4ce1-9abc-0141ef5d137c&sr=c&sp=racwdlm&sig=TZ9Tq3GD8wo3BiAETwpWj9xxxxxxxxxxxxxxxxxxxxxxxx"
```

After executing the above command in your terminal, you will see copy result:

![dlz-exec-copy-command.png](./images/dlz-exec-copy-command.png)

## 2.5.4 Lookup your file in your AEP data landing zone

Let's navigate to AEP's data landing zone:

Select "Sources" (1), search for "data lan" (2) and click the "Setup" (3) button.

![dlz-inspect-datalanding-zone.png](./images/dlz-inspect-datalanding-zone.png)

This will open the AEP's data landing zone, your file should be listed in teh data landing zone's "select data"-panel:

![dlz-datalanding-zone-open.png](./images/dlz-datalanding-zone-open.png)

## 2.5.6 Process your file

Select your file (1) and select "Delimited" (2) as its data format, as a result you will see a data preview (3):

![dlz-datalanding-select-file.png](./images/dlz-datalanding-select-file.png)

To continue click "Next" (4) to start mapping the uploaded data onto the XDM of the selected dataset.

Pick "existing dataset" (1) and click the icon (2) to select a dataset:

![dlz-target-dataset.png](./images/dlz-target-dataset.png)

Our csv data has to be uploaded into the "Demo System - Event Dataset for Website (Global v1.1)" dataset. Enter "website" in the search field (1) and pick "Demo System - Event Dataset for Website (Global v1.1)" from the search results (2), click "Confirm" (3).

![dlz-select-dataset.png](./images/dlz-select-dataset.png)

Now you are ready map the "source" fields from your csv file onto the "target" fields from the dataset's XDM. This mapping process is described in 

![dlz-start-mapping.png](./images/dlz-start-mapping.png)

## 2.5.7 Map fields

Although screen indicates a succesful premapping we clear all mappings (1). Next select "Add new mapping" (2) and click the "source" field icon (3):

![dlz-clear-mappings.png](./images/dlz-clear-mappings.png)

In the source field browser you would expect a flat structure (we are importing a CSV file), but instead it is presented as an hierachical structure. This is because the column names (derived from the first line in the CSV) have a "dot"-notation (e.g. **identities.ecid** or **resource.info.pagename**). 

To map the "ecid" source field, click to open "identities" (1) and select the "ecid" field (2) and hit the "Select" button (3).

![dlz-map-identity.png](./images/dlz-map-identity.png)

With the "ecid" source field selected, click the target field icon (1):

![dlz-map-select-target-field.png](./images/dlz-map-select-target-field.png)

Select the "ecid" target field in the XDM model associtated to our "Demo System - Event Dataset for Website (Global v1.1)" dataset, click (1)(2)(3) to navigate to the "ecid" field, select it (4) and click the "Select" button (5):

![dlz-map-target-field.png](./images/dlz-map-target-field.png)

We need to map a couple of other fields, hit the "Add new mapping" button again;

![dlz-add-other-mapping.png](./images/dlz-add-other-mapping.png)

Repeat "Add new mapping" for the following fields:

| source  | target  |
|---|---|
| resource.info.pagename |  web.webPageDetails.name |
| timestamp  |  timestamp |
| timestamp |  _id |

When finished your screen should look like, the screen below. When correct, hit the "Next" button (1):

![dlz-mapping-result.png](./images/dlz-mapping-result.png)

Accept the default scheduling and click next "Next" button:

![dlz-default-scheduling.png](./images/dlz-default-scheduling.png)

In the dataflow detail screen, make sur to add a description (1) (due to a bug, dataloading might otherwise fail) and hit "Next" (2):

![dlz-dataflow.png](./images/dlz-dataflow.png)

Click "Finish" (1) in the "Add data - review" screen:

![dlz-import-finish.png](./images/dlz-import-finish.png)

## 2.5.8 Monitor dataflow 

To monitor you dataflow, select "sources" (1) and click on your dataflow (2):

![dlz-monitor-dataflow.png](./images/dlz-monitor-dataflow.png)

As long as the data is being loaded you will see "Processing" as its status. Loading the data can take a couple of minutes, when succesful, "Status" will indicate "success":

![dlz-monitor-dataflow-result.png](./images/dlz-monitor-dataflow-result.png)

Next Step: [Summary and benefits](./summary.md)

[Go Back to Module 2](./data-ingestion.md)

[Go Back to All Modules](../../overview.md)
