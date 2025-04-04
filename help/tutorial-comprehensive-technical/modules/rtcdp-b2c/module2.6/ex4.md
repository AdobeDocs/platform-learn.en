---
title: Install and configure Kafka Connect and the Adobe Experience Platform Sink Connector
description: Install and configure Kafka Connect and the Adobe Experience Platform Sink Connector
kt: 5342
doc-type: tutorial
exl-id: 93ded4f9-0179-4186-9601-52f479350075
---
# 2.6.4 Install and configure Kafka Connect and the Adobe Experience Platform Sink Connector

## Download the Adobe Experience Platform Sink Connector

Go to [https://github.com/adobe/experience-platform-streaming-connect/releases](https://github.com/adobe/experience-platform-streaming-connect/releases) and download the latest official release of the Adobe Experience Platform Sink Connector.

![Kafka](./images/kc1.png)

Download the file **streaming-connect-sink-0.0.27-java-11.jar**.

![Kafka](./images/kc1a.png)

Place the download file, **streaming-connect-sink-0.0.27-java-11.jar**, onto your desktop.

![Kafka](./images/kc2.png)

## Configure Kafka Connect

Go to the folder on your desktop named **Kafka_AEP** and navigate to the folder `kafka_2.13-3.9.0/config`.
In that folder, open the file **connect-distributed.properties** using any Text Editor.

![Kafka](./images/kc3a.png)

In your Text Editor, go to line 34 and 35 and make sure to set the fields `key.converter.schemas.enable` and `value.converter.schemas.enable` to `false`

```json
key.converter.schemas.enable=false
value.converter.schemas.enable=false
```

Save your changes to this file.

![Kafka](./images/kc3.png)

Next, go back to the folder `kafka_2.13-3.1.0` and manually create a new folder, and name it `connectors`.

![Kafka](./images/kc4.png)

Right-click the new folder and click **New terminal at Folder**.

![Kafka](./images/kc5.png)

You'll then see this. Enter the command `pwd` to retrieve the full path for that folder. Select the full path and copy it to your clipboard.

![Kafka](./images/kc6.png)

Go back to your Text Editor, to the file **connect-distributed.properties** and scroll down to the last line (line 89 in the screenshot). You should uncomment the line (remove `#`) that starts with `# plugin.path=` and you should paste the full path to the folder named `connectors`. The result should look similar to this:

`plugin.path=/Users/woutervangeluwe/Desktop/Kafka_AEP/kafka_2.13-3.9.0/connectors` 

Save your changes to the file **connect-distributed.properties** and close your Text Editor.

![Kafka](./images/kc7.png)

Next, copy the latest official release of the Adobe Experience Platform Sink Connector that you downloaded into the folder named `connectors`. The file that you downloaded before is named **streaming-connect-sink-0.0.27-java-11.jar**, you can simply move it into the `connectors` folder.

![Kafka](./images/kc8.png)

Next, open a new Terminal window at the level of the **kafka_2.13-3.9.0** folder. Right-click that folder and click **New Terminal at Folder**.

In the Terminal window, paste this command: `bin/connect-distributed.sh config/connect-distributed.properties` and click **Enter**. This command will start Kafka Connect and will load the library of the Adobe Experience Platform Sink Connector.

![Kafka](./images/kc9.png)

After a couple of seconds, you'll see something like this:

![Kafka](./images/kc10.png)

## Create your Adobe Experience Platform Sink Connector using Postman

You can now interact with Kafka Connect using Postman. To do so, download [this Postman Collection](./../../../assets/postman/postman_kafka.zip) and uncompress it to your local computer on the desktop. You'll then have a file that is called `Kafka_AEP.postman_collection.json`.

![Kafka](./images/kc11a.png)

You need to import this file in Postman. To do so, open Postman, click **Import**, drag and drop the file `Kafka_AEP.postman_collection.json` into the popup and click **Import**.

![Kafka](./images/kc11b.png)

You'll then find this collection in the left menu of Postman. Click the first request, **GET Available Kafka Connect connectors** to open it.

![Kafka](./images/kc11c.png)

You'll then see this. Click the blue **Send** button, after which you should see an empty response `[]`. The empty response is due to the fact that no Kafka Connect connectors are currently defined.

![Kafka](./images/kc11.png)

To create a connector, click to open the second request in the Kafka collection, **POST Create AEP Sink Connector** and go to **Body**. You'll then see this. On line 11, where it says **"aep.endpoint": ""**, you need to paste in the HTTP API Streaming endpoint URL that you received at the end of one of the previous exercises. The HTTP API Streaming endpoint URL looks like this: `https://dcs.adobedc.net/collection/63751d0f299eeb7aa48a2f22acb284ed64de575f8640986d8e5a935741be9067`.

![Kafka](./images/kc12a.png)

After pasting it, the body of your request should look like this. Click the blue **Send** button to create your connector. You'll get an immediate response of the creation of your connector.

![Kafka](./images/kc12.png)

Click the first request, **GET Available Kafka Connect connectors** to open it again and click the blue **Send** button again. you'll now see that a Kafka Connect connector exists.

![Kafka](./images/kc13.png)

Next, open the third request in the Kafka collection, **GET Check Kafka Connect Connector Status**. Click the blue **Send** button, you'll then get a response like the one below, stating that the connector is running.

![Kafka](./images/kc14.png)

## Produce an experience event

Open a new **Terminal** window by right-clicking your folder **kafka_2.13-3.9.0** and clicking **New Terminal at Folder**.

![Kafka](./images/kafka11.png)

Enter the following command:

`bin/kafka-console-producer.sh --broker-list 127.0.0.1:9092 --topic aep`

You'll then see this. Every new line followed by pushing the Enter button will result in a new message being sent into the topic **aep**.

![Kafka](./images/kc16.png)

You can now send a message, which will result in being consumed by the Adobe Experience Platform Sink Connector, and which will be ingested into Adobe Experience Platform in real-time.

Take the below sample experience event payload and copy it into a Text Editor.

```json
{
  "header": {
    "datasetId": "61fe23fd242870194a6d779c",
    "imsOrgId": "--aepImsOrgID--",
    "source": {
      "name": "Launch"
    },
    "schemaRef": {
      "id": "https://ns.adobe.com/experienceplatform/schemas/b0190276c6e1e1e99cf56c99f4c07a6e517bf02091dcec90",
      "contentType": "application/vnd.adobe.xed-full+json;version=1"
    }
  },
  "body": {
    "xdmMeta": {
      "schemaRef": {
        "id": "https://ns.adobe.com/experienceplatform/schemas/b0190276c6e1e1e99cf56c99f4c07a6e517bf02091dcec90",
        "contentType": "application/vnd.adobe.xed-full+json;version=1"
      }
    },
    "xdmEntity": {
      "eventType": "callCenterInteractionKafka",
      "_id": "",
      "timestamp": "2024-11-25T09:54:12.232Z",
      "_experienceplatform": {
        "identification": {
          "core": {
            "phoneNumber": ""
          }
        },
        "interactionDetails": {
          "core": {
            "callCenterAgent": {
              "callID": "Support Contact - 3767767",
              "callTopic": "contract",
              "callFeeling": "negative"
            }
          }
        }
      }
    }
  }
}
```

You'll then see this. You need to manually update 2 fields:

- **_id**: please set it to a random id, something like `--aepUserLdap--1234`
- **timestamp**: update the timestamp to the current date and time
- **phoneNumber**: enter the phoneNumber of the account that was created earlier on the demo website. You can find it on the Profile Viewer panel under **Identities**.

You also need to check and maybe update these fields:

- **datasetId**: you need to copy the Dataset ID for the dataset Demo System - Event Dataset for Call Center (Global v1.1)

![Kafka](./images/kc20ds.png)

- **imsOrgID**: your IMS Org ID is `--aepImsOrgId--`

>[!NOTE]
>
>The field **_id** needs to be unique for every data ingestion. If you produce multiple events, please make sure that you update the field **_id** every time to a new, unique value.

You should then have something like this:

![Kafka](./images/kc21.png)

Next, copy your full experience event to your clipboard. The whitespace of your JSON payload needs to be stripped and we'll use an online tool to do that. Go to [http://jsonviewer.stack.hu/](http://jsonviewer.stack.hu/) to do that.

Paste your experience event into the editor and click **Remove white space**.

![Kafka](./images/kc22a.png)

Next, select all of the output text and copy it to your clipboard.

![Kafka](./images/kc23.png)

Go back to your Terminal window.

![Kafka](./images/kc16.png)

Paste the new payload without whitespaces into the Terminal window and click **Enter**.

![Kafka](./images/kc23a.png)

Next, go back to your demo website and refresh the page. You should now see an experience event on your profile, under **Experience Events**, just like the one below:

![Kafka](./images/kc24.png)

>[!NOTE]
>
>If you want your call center interactions to appear on the Profile Viewer panel, you need to add the below label and filter in your project on [https://dsn.adobe.com](https://dsn.adobe.com), by going to the tab **Profile Viewer** and adding a new line under **Events**, with these variables:
>- **Event Type Label**: Call Center Interactions
>- **Event Type Filter**: callCenterInteractionKafka
>- **Title**: `--aepTenantId--.interactionDetails.core.callCenterAgent.callID`

![Kafka](./images/kc25.png)

You have finished this exercise.

Next Step: [Summary and benefits](./summary.md)

[Go Back to Module 2.6](./aep-apache-kafka.md)

[Go Back to All Modules](../../../overview.md)
