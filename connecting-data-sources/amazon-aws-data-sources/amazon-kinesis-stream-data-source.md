---
description: >-
  This article provides an introduction on how Upsolver works with Amazon
  Kinesis along with a guide on how to create an Amazon Kinesis Stream data
  source in Upsolver.
---

# Amazon Kinesis Stream data source

## How Upsolver works with Amazon Kinesis

### Reading from a stream

Upsolver can read events from your Amazon Kinesis, from the specified stream.

While setting up the data source, Upsolver scans the **last 30 minutes** of data in the stream in order find **100 records** \(to preview\) and auto detect the content format. 

{% hint style="warning" %}
If there is no data from the last 30 minutes, you will need to select a content format.
{% endhint %}

When a data source is created it is populated with the **sample 100 records** from the preview. Once data is captured from the data stream, this preview data will be replaced with the actual data. 

This means that if you do not select to read from the start, the data source will initially appear with 100 historical records from the past 30 minutes, and these will be replaced when data is ingested from the stream. 

If you create an output based on this data source, the preview data is not included.

### Data retention

By default the data in a data source is kept forever. If you specify a retention period \(e.g. 30 days\), this only applies to the data source. I

f you create an output based on this data source, it will have its own retention, and these do not need to match \(e.g. output may be configured to retain the data for a year\).

## Create an Amazon Kinesis data source

{% hint style="info" %}
If you wish to customize the data source by selecting:

* a specific compute cluster
* a target storage option
* retention options

**See:** [Advanced](amazon-kinesis-stream-data-source.md#create-an-amazon-kinesis-data-source-advanced)
{% endhint %}

1. From the **Data Sources** page, click **New**.

2. Select **Amazon Kinesis Stream**.

3. Select your **AWS** **region**.

4. Select the **Kinesis** **stream** to read from.

5. **Name** this data source.

6. Click **Continue**. The S3 Bucket Integration window will appear.

{% hint style="info" %}
If the content type is not automatically identified, you will be prompted to select the **Content Format** and configure any related options.   
**See:** [Data formats](https://docs.upsolver.com/Content/Upsolver%20Software%20User%20Guide/Supported%20Data%20Formats.htm)
{% endhint %}

{% hint style="success" %}
If you have connected to this stream previously, and therefore have the required permissions, you can now use your Amazon Kinesis Stream data source.
{% endhint %}

7. If you have not connected to this stream previously, click **Launch Integration** to launch the AWS CloudFormation page in a new tab. 

8. Check the **I acknowledge** statement and click **Create Stack**. 

{% hint style="success" %}
Once the stack is created with the required resources, the message in Upsolver disappears automatically. 

You can now use your Amazon Kinesis Stream data source.
{% endhint %}

## Create an Amazon Kinesis data source \(Advanced\)

1. From the **Data Sources** page, click **New**.

2. Select **Amazon Kinesis Stream** and then click **Advanced**.

3. **Name** this data source.

4. Select the **content format**. This is typically auto-detected, but you can manually select a format. 

{% hint style="info" %}
If necessary, configure the content format options.   
**See:** [Data formats](../../getting-started/glossary/data-formats.md)
{% endhint %}

5. Select the desired **Kinesis connection** \(or [create a new one](../../administration/connections/amazon-kinesis.md)\).

6. Select the **name** of the **Kinesis stream** to read from.

7. Decide whether or not to **read the stream** **from the start**.  
This could be a day or a week, depending on the Amazon Kinesis setup. 

{% hint style="warning" %}
If you do not select **Read From Start**, the stream will be read from the current time onwards and there will be no historical data in the data source.
{% endhint %}

8. From the dropdown, select a **compute cluster** \(or [create a new one](../../administration/managing-clusters/cluster-types/adding-a-compute-cluster.md)\) to run the calculation on. 

9. Select a **target storage connection** \(or [create a new one](../../administration/connections/)\) to store the data read from the stream \(output storage\).

10. If you choose to check **Enabled**, specify a **retention period** in Upsolver for the data in minutes, hours, or days. 

{% hint style="warning" %}
The data will be deleted permanently after this period elapses.   
By default, the data is kept forever.
{% endhint %}

{% hint style="info" %}
Click **Show Advanced Options** to configure:

* Real Time Statistics
* Shards
* Execution Parallelism
* End Read At
* Compression
* Store Raw Data

Otherwise, skip to step 17.
{% endhint %}

11. Check **Real Time Statistics** to calculate the data source statistics in real time directly from the input stream.

{% hint style="info" %}
This is relevant to lookup tables, when answers are required very fast and in real time.
{% endhint %}

12. Specify the number of **shards** or parallel readers from Amazon Kinesis \(the more shards, the quicker the data processing\). 

{% hint style="warning" %}
Each shard in Upsolver can read from one or more shards in Amazon Kinesis. 

The number of shards in Upsolver must be **less than or equal to** the number of shards in Amazon Kinesis.

Contact Upsolver Professional Services if you want to configure this option. Typically you need one Upsolver shard per 10-20 MBps of data.
{% endhint %}

13. Contact Upsolver Professional Services if you wish to configure the **execution parallelism**. This determines how many files will be created in the data source per minute and must be set to a value that is **less than** the number of shards.

14. \(Optional\) Under **End Read At**, select a time to stop reading from the stream. This is useful if you wish to stop processing a stream.

15. Select the **compression** in the stream from the dropdown options. 

{% hint style="info" %}
If you set the compression to **Auto Detect**, the data that is ingested can be in multiple formats.
{% endhint %}

16. Check **Store Raw Data** to store an additional copy of the data in its original format without any transformations.

17. Click **Continue**. A preview of the data will appear.

18. For CSV, select a **Header**.

19. Click **Continue** again. 

{% hint style="info" %}
Parsed data samples will appear and you can review the **Sample Size**, **Parsed Successfully**, and **\# of Errors**.
{% endhint %}

18. \(Optional\) If there are any errors, click **Back** to change the settings as required.

19. Click **Create**.

{% hint style="success" %}
You can now use your Amazon Kinesis Stream data source.
{% endhint %}

