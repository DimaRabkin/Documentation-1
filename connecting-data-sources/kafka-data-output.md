---
description: >-
  This article provides an introduction to using Apache Kafka with Upsolver
  along with a guide on how to create a Kafka Data source in Upsolver.
---

# Kafka data source

## How Upsolver works with Apache Kafka

### Reading from a topic

Upsolver reads events from the specified Kafka topic in your Kafka cluster.

While setting up the data source, Upsolver scans the **last 30 minutes** of data in the topic in order find **100 records** \(to preview\) and auto detect the content format. 

{% hint style="warning" %}
If there is no data in the last 30 minutes, you will need to select a content format.
{% endhint %}

When a data source is created, it is populated with the **sample 100 records** from the preview. Once data is captured from the topic, this preview data is replaced with actual data. 

This means that if you do not select to read from the start, the data source will initially appear with 100 historical records from the past 30 minutes, and these will be replaced when data is ingested from the topic.

 If you create an output based on this data source, the preview data is not included.

### Data retention

By default the data in a data source is kept in Upsolver forever. If you specify a retention period in Upsolver \(e.g. 30 days\), this only applies to the data source. 

If you create an output based on this data source, it will have its own retention, and these do not need to match \(e.g. the output may be configured to retain the data for a year\).

## Create a Kafka data source

{% hint style="info" %}
If you wish to customize the data source by selecting:

* a specific compute cluster
* a target storage option
* retention options

**See:** [Advanced](kafka-data-output.md#creating-a-kafka-data-source-advanced-options)
{% endhint %}

1. From the **Data Sources** page, click **New**.

2. Select **Kafka**.

3. Enter in the **host:port** for your **Kafka cluster**.

{% hint style="info" %}
If there are multiple hosts, the format should be `host1:port1, host2:port2, ...`
{% endhint %}

4. Select the **Kafka** **topic** to read from.

5. **Name** this data source.

6. Click **Continue**. The S3 Bucket Integration window will appear.

7. Click **Launch Integration** to launch the AWS CloudFormation page in a new tab.

8. Check the **I acknowledge** statement and click **Create Stack**.

{% hint style="success" %}
Once the stack is created with the required resources, the message in Upsolver disappears automatically.

You can now use your Kafka topic data source.
{% endhint %}

## Create a Kafka data source \(Advanced\)

1. From the **Data Sources** page, click **New**.

2. Select **Kafka** and then click **Advanced**.

3. **Name** this data source.

4. Select your **Kafka version**.

5. Enter in the **`host:port`** for your **Kafka cluster**.

{% hint style="info" %}
If there are multiple hosts, the format should be `host1:port1, host2:port2, ...`
{% endhint %}

6. Select the **Kafka** **topic** to read from.

{% hint style="info" %}
Click **Show Advanced Options** to configure:

* Kafka Consumer Properties
* Shards
* Execution Parallelism
* Real Time Statistics
* Use SSL
* End Read At
* Store Raw Data
* Compression

Otherwise, skip to step 15.
{% endhint %}

7. \(Optional\) Add any additional **properties** necessary for the **Kafka consumer**.  
The format should look as follows:

```bash
bootstrap.servers = HOST:PORT
security.protocol = SASL_SSL
sasl.jaas.config = org.apache.kafka.common.security.plain.PlainLoginModule   required username = "API_KEY"   password = "SECRET";
ssl.endpoint.identification.algorithm = https
sasl.mechanism = PLAIN
```

where:

* `HOST:PORT` = the same Kafka host\(s\) entered in step 5
* `API_KEY` = an API key for your Kafka cluster
* `SECRET` = the corresponding secret for your API key

8. Specify the number of **shards** or parallel readers from Kafka \(the more shards, the quicker the data processing\). 

{% hint style="warning" %}
Each shard in Upsolver can read from one or more partitions in Kafka. 

The number of shards in Upsolver must be **less than or equal to** the number of partitions in Kafka.

Contact Upsolver Professional Services if you want to configure this option. Typically you need one Upsolver shard per 10-20 MBps of data.
{% endhint %}

9. Contact Upsolver Professional Services if you wish to configure the **execution parallelism**. This determines how many files will be created in the data source per minute and must be set to a value that is **less than** the number of shards.

10. Check **Real Time Statistics** to calculate the data source statistics in real time directly from the input topic.

{% hint style="info" %}
This is relevant to lookup tables, when answers are required very fast and in real time.
{% endhint %}

11. Check **Use SSL** if your connection requires SSL. 

{% hint style="info" %}
Contact Upsolver Support to ensure that your SSL certificate is supported.
{% endhint %}

12. \(Optional\) Under **End Read At**, select a time to stop reading from the topic. This is useful if you wish to stop processing a topic.

13. Check **Store Raw Data** to store an additional copy of the data in its original format without any transformations.

14. Select the **compression** in the topic from the dropdown options. 

{% hint style="info" %}
If you set the compression to **Auto Detect**, the data that is ingested can be in multiple formats.
{% endhint %}

15. Decide whether or not to **read the topic** **from the start**.  
This could be a day or a week, depending on the Kafka setup. 

{% hint style="warning" %}
If you do not select **Read From Start**, the topic will be read from the current time onwards and there will be no historical data in the data source.
{% endhint %}

16. Select the **content format**. This is typically auto-detected, but you can manually select a format. 

{% hint style="info" %}
If necessary, configure the content format options.   
**See:** [Data formats](../getting-started/glossary/data-formats.md)
{% endhint %}

Optional: Connect to schema registry by choosing the `Avro w/ Schema Registry` option from from  `CONTENT FORMAT` Use the URL to retrieve schema from the schema registry in the URL box  `https://my.schema.registry.upsolver.com/schema/{id}`

17. From the dropdown, select a **compute cluster** \(or [create a new one](../administration/managing-clusters/cluster-types/adding-a-compute-cluster.md)\) to run the calculation on. 

{% hint style="warning" %}
A ![](../.gitbook/assets/screen-shot-2020-08-13-at-5.48.22-pm.png) may appear. This warning can be ignored for POCs \(proof of concept\). 

For production environments, this indicates that if you run your task retroactively \(**Start Ingestion From**\), your compute cluster will process a burst of additional tasks, possibly causing delays in outputs and lookup tables running on this cluster. 

To prevent this, go to the **Clusters** page to edit your cluster and set the **Additional Processing Units For Replay** to a number greater than 0.
{% endhint %}

18. Select a **target storage connection** \(or [create a new one](../administration/connections/)\) to store the data read from the topic \(output storage\).

19. If you choose to check **Enabled**, specify a **retention period** in Upsolver for the data in minutes, hours, or days. 

{% hint style="warning" %}
The data will be deleted permanently after this period elapses.   
By default, the data is kept forever.
{% endhint %}

20. Click **Continue**. A preview of the data will appear.

21. For CSV, select a **Header**.

22. Click **Continue** again. 

{% hint style="info" %}
Parsed data samples will appear and you can review the **Sample Size**, **Parsed Successfully**, and **\# of Errors**.
{% endhint %}

23. \(Optional\) If there are any errors, click **Back** to change the settings as required.

24. Click **Create**.

{% hint style="success" %}
You can now use your Kafka data source.
{% endhint %}

