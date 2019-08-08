# Lesson 2 - Data: Ingesting Data via Batch Ingestion

## Objective

- Learn how to ingest XDM-formatted data files
- Learn the API interface for data ingestion

## Lesson Resources

- Sample data .parquet file in Profile XDM format (required download): [Profile_CRM_Data_Sample.parquet](/resources/Profile_CRM_Data_Sample.parquet)

## Lesson Context

Luma's engineers and developers are likely to also utilize the Adobe Experience Platform APIs to ingest data. This includes not just batch data of files, but also point-to-point connectors that could be transferring or streaming data from user registration forms on Luma's site, sign-in details and CRM data, as well as behavioral transactions from logged-in users using the Luma site. We will implement these different data ingestion and lookup functions using the API, and demonstrate the tools available for integration of Experience Platform, starting with batch ingestion.

For Lesson 2, we will first start with basic dataset creation, and the requirements that go into that - selecting a schema to use, creating a dataset, enabling it for Unified Profile, and bringing in batch data via files.

## Exercise 2.1 - Dataset Lookup

1. Start by expanding the `Lesson 2` & `List Datasets` folder in postman under `Adobe Experience Platform`.
1. Skip over `Catalog: Get Datasets` and instead select the `Catalog: Get Datasets Limit 5` action and click `Send`.

    ![](assets/get_datasets.png)

    In the response pane you can scroll down and see the top five datasets. We are limiting the number of datasets returned to five in order have the query return quickly and not process too much data.

1. Next let's run the `Catalog: Get Batches` action by selecting it and clicking `Send`.

    ![](assets/get_batches_in_dataset.png)

    Datasets can consist of multiple batches.

1. Finally let's run the `Catalog: Get Dataset Files` action by selecting it and clicking `Send`.

    ![](assets/get_files_in_dataset.png)

    In this case we'll get a list of files in the dataset and the metadata will include which batch it is from. Now that we've learned how to query datasets let's get busy creating one.

## Exercise 2.2 - Dataset Creation

1.  Expand the `Create Dataset` folder in postman under `Lesson 2`, select the `Catalog: Create CRM Dataset` action and click `Send`.

    ![](assets/create_dataset.png)

    The call will create a new dataset named `L778+[AccountID]_CRM_Dataset` and return a ID we can use in future calls. The `"unifiedProfile": ["enabled:true"]` flag within the body ensures that this dataset is automatically included in the Unified Profile Service.

    Remember that the Dataset is based on the schema you select, which is based on a schema class like Profile.

    ![](assets/overview-2.png)

    Once created it will conceptually look like this:

    ![](assets/overview-3.png)


1. Next we'll call `Catalog: Get CRM Dataset` to inspect the dataset:

    ![](assets/create_dataset_verify.png)

    In the response area of the postman call you view the datasets metadata. In our next exercise we'll populate this dataset.

## Exercise 2.3 - Batch Data Ingestion

1. Now that we've successfully created a dataset we'll create a batch so we can start ingesting files.

    ![](assets/overview-4.png)

    Expand the `Create Batch` folder, select `Ingest: Create Batch` and click `Send`:

    ![](assets/create_batch.png)

1. Next we'll upload a file to the batch.

    ![](assets/overview-5.png)

    Select `Ingest: Upload File` then click on the `Body` tab.

    ![](assets/upload_file_body.png)

1.  From there you'll need to select a file to upload by clicking on `Choose Files` and selecting [Profile_CRM_Data_Sample.parquet](data/Profile_CRM_Data_Sample.parquet).

    ![](assets/upload_file_selected.png)

    Then click `Send` to upload the file. If the upload succeeds you won't see anything in the response section other than a 200 OK.

1. Since batches may contain multiple files we have to make an additional call to close off the batch to indicate that the batch is now ready for processing.

    ![](assets/overview-6.png)

    So select the `Ingest: Close Batch` action and click `Send`.

    Once again you won't see anything in the response section of postman other than a 200 OK.

1. If we've done everything right up until this point the file and batch should be successfully ingested. In order to check on that we'll open the `Batch Status` folder, select the `Batch by ID` action and click `Send`.

    ![](assets/get_batch_status.png)

    In the response section pay close attention to the value of `status`. We want it to say `success` but if it says `processing` it just means we have to wait a bit and make this postman request again.

    In the meantime, this is what the response would look like _if_ the ingested file brings up a `failed` status - likely due to not being in the correct format for that dataset:

    ![](assets/get_batch_status_failed.png)

1. Once we've seen the file in the batch has been successfully ingested we can check to see how many files are in the batch. Select the `Files in Batch` action and click `Send`.

    ![](assets/get_batch_files.png)

    The response pane will show you how many files are in this batch. In our case there should only be one file.

1.  Let's walk back up the containers and check on the status of our dataset. Expand the `Dataset Status` folder, select the `Catalog: Get Dataset` action and click `Send`.

    ![](assets/dataset_status.png)

    Scroll down in the response pane until you find `lastBatchStatus` property which should read as `success`.

## Exercise 2.4 - Dataset Inspection and Preview

1. Things are looking good for our dataset but what if we want to get more information about the files stored in the dataset? Then we open the `Data Access` folder, select `Data Export: Get File Details` action and hit `Send`.

    ![](assets/get_file_details.png)

    This response contains important metadata like the file name and file size.

1. Next, let's take a look at the file stored in Experience Platform.

    ![](assets/overview-7.png)

    Select the `Data Export: Get File` action and hitting `Send`.

    ![](assets/get_file_contents.png)

    In this case the response is not that useful to us as .parquet files are binary in format so they are difficult to read. However, it should make customers happy to know whatever data they import into Adobe Experience Platform can be exported as well.

1. Finally, let's use the preview API to get a human readable version of the dataset we've just created. Select the `Data Export: Get Dataset Preview` action and hitting `Send`.

    ![](assets/get_dataset_preview.png)

    This response returns JSON data which is at least textual format which can be read without any additional programs to do the formatting. Note: preview will only show you the results of the latest batch to be ingested into that dataset.

## Lesson 2 - Wrap

Well that was a lot of work to ingest the data! Let's move on to the next step, which is collecting real time data from user interactions in the format of Experience Events.

## Lesson 2 - Additional Resources

[Catalog Service RESTful API Resource](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/catalog.yaml)