---
description: >-
  This article provides a guide on how to create an Amazon S3 over SQS data
  source in Upsolver.
---

# Amazon S3 over SQS data source

## Create an S3 over SQS data source

1. From the **Data Source** page, click **New**.

2. Select **S3 Over SQS**.

{% hint style="info" %}
As you fill in the fields, the top matching files with their dates appear in the **Preview** pane on the right.
{% endhint %}

3. **Name** this data source.

4. From the **Source Storage** dropdown, select the **Amazon S3 over SQS connection** to read from \(or [create a new one](../../administration/connections/amazon-s3-over-sqs.md)\).

5. \(Optional\) Enter in the **prefix** that is used to determine whether to create a notification on the event that was published to the S3 bucket. 

{% hint style="info" %}
Amazon S3 allows notifications on buckets using a **prefix** and **suffix**. 

Any new file in the S3 bucket should only trigger **one** notification. 

The prefix/suffix combination must **uniquely** identify files. 

You cannot specify a prefix/suffix combination in a different data source that would conflict \(e.g. given the same suffix, if you specify **abc** as a prefix in this data source, you cannot specify **abc2** in a different data source as this would not be unique\).
{% endhint %}

6. \(Optional\) Enter in the **suffix** that is used to determine whether or not to create a notification on the event that was published to the S3 bucket.

7. Select the **content format**. This is typically auto-detected, but you can manually select a format. 

{% hint style="info" %}
If necessary, configure the content format options.   
**See:** [Data formats](../../getting-started/glossary/data-formats.md)
{% endhint %}

8. From the dropdown, select a **compute cluster** \(or [create a new one](../../administration/managing-clusters/cluster-types/adding-a-compute-cluster.md)\) to run the calculation on. 

{% hint style="warning" %}
A ![](../../.gitbook/assets/screen-shot-2020-08-13-at-5.48.22-pm.png) may appear. This warning can be ignored for POCs \(proof of concept\). 

For production environments, this indicates that if you run your task retroactively \(**Start Ingestion From**\), your compute cluster will process a burst of additional tasks, possibly causing delays in outputs and lookup tables running on this cluster. 

To prevent this, go to the **Clusters** page to edit your cluster and set the **Additional Processing Units For Replay** to a number greater than 0.
{% endhint %}

9. Select a **target storage connection** \(or [create a new one](../../administration/connections/)\) where the data read will be stored \(output storage\).

10. \(Optional\) Under **Start Ingestion From**, select the time from which to start ingesting the files.   
It is important to set this option so that the data is spread out properly over the date range.

{% hint style="info" %}
Click **Show Advanced Options** to configure:

* End Read At
* KMS Key

Otherwise, skip to step 13.
{% endhint %}

11. \(Optional\) Under **End Read At**, select the time to stop reading the data.   
This is useful if you want to stop processing a data stream.

12. \(Optional\) Enter in a [**KWS key**](https://aws.amazon.com/kms/).

13. If enabled, specify a **retention period** in Upsolver for the data. 

{% hint style="warning" %}
After this time period elapses, the data will be deleted forever.
{% endhint %}

14. Click **Continue**. A preview of the data will appear.

15. For CSV, select a **Header**.

16. Click **Continue** again. 

{% hint style="info" %}
Parsed data samples will appear and you can review the **Sample Size**, **Parsed Successfully**, and **\# of Errors**.
{% endhint %}

17. \(Optional\) If there are any errors, click **Back** to change the settings as required.

18. Click **Create**.

{% hint style="success" %}
You can now use your S3 Over SQS data source.
{% endhint %}

