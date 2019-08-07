# [BONUS] Lesson 5 - Segmentation: Segment the Unified Profile

_NOTE: This section is bonus material and can be completed within this lab, if you have extra time._

## Objective

- Learn how to segment an audience of profiles using the API
- Learn how to post segment jobs and export them to a new dataset
- Define a segment via API in JSON
- Create a segment job and export it to a new dataset

## Lesson Context

Now that Luma has a system with Unified Profile populated from both batch customer data and streaming data, and demonstrated the ability to look up Unified Profile data, we can utilize Adobe Experience Platform to take further action on these profiles. Using the segmentation engine, we can specify filters to segment our database of Luma customers. These segments can then be delivered directly to other platforms either through Experience Platform's Segment Builder integrations with other Adobe solutions, or by creating new datasets of segmented customers to export to external solutions.

This will help utilize several aspects Luma's customer loyalty program, including targeted upgrade promotions, re-engagement or re-activation of customers, garnering insights from the loyalty program statistics, etc. Because all data for a customer including and beyond customer loyalty will be tied to one Unified Profile, we can bring in more information to further segment customers, or use segments for a broader scope of actions.

## Lesson Resources

- [Segment Definition in JSON](#linktofile)

## Exercise 5.1 - Segmentation via the API

1.  Now that we've ingested some data in [Lesson 2](#lesson-2---data-ingesting-data-via-batch-ingestion) into our Unified Profile Service, we're ready to begin segmenting the data in order to gain insights.
1.  Start by expanding the `Lesson 5` folder in postman under `L778`.
1.  Select the `Profile: Create A Segment Definition` action. Note that in the body section of the action we are creating a simple segment that will include all females who have interacted with the system in the past 90 days.

    ![](images/create_segment.png)

1. Then click `Send` to create the segment and view the results in the response section of Postman.

    ![](images/create_segment_result.png)

1. Now that we've been able to define a segment the next step is to start a job to run the segment query for us. So select `POST Segment Job` and hit `Send`.

    ![](images/create_segment_job.png)

1. A segment job may take a little while to run so let's check on it's status by selecting `GET Segment Job status` and hitting `Send`.

    ![](images/create_segment_job_status.png)

    If the `status` property says `PROCESSING` wait a little longer and `Send` the query again until you see `SUCCEEDED`.

1. Let's create a new dataset to hold the results of our segment job.

    ![](images/create_segment_dataset.png)

1. Now that the job has succeeded and we have a dataset to hold our segmentation data it's time to export the data. Select `POST Export Job` and hit `Send`.

    ![](images/create_segment_export.png)

1. We are getting close to being able to view our segment data. Select the `Get Export Job By Id` action and hit `Send`.

    ![](images/create_segment_export_success.png)

    If the `status` property says `PROCESSING` wait a little longer and `Send` the query again until you see `SUCCEEDED`.

1. Now the easiest way to view your segmented dataset is to log in to [https://platform.adobe.com](https://platform.adobe.com), click on the Data tab, then click on {{ldap}}\_ProfileSegmentDataset and finally the `Preview` button.

    ![](images/create_segment_final.png)

    As you can see all of the people in the dataset are `female`.

## Additional Resources

[Unified Profile, Identity, & Segmentation](https://www.adobe.io/apis/experienceplatform/home/profile-identity-segmentation.html)

# Next Steps

Now that we've been able to see how to use Adobe Experience Platform's APIs to empower Luma, the opportunities that to understand and utilize the real-time customer profile that Unified Profile offers are numerous. As an API-first built platform, Adobe Experience Platform allows developers to take full control of its features and integrate them into their own solutions as well.

We hope you enjoyed this workshop and that this workbook can serve as a useful reference for you going forward. Please don't hesitate to reach out to one of the Platform team members if you have any questions, and visit our booth at the pavillion to see the many other faces of Adobe Experience Platform!

## Additional Resources

[Adobe Experience Platfrom API Documentation](https://www.adobe.io/apis/experienceplatform/home.html)
