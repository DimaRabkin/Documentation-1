---
description: >-
  This article provides a list of data source properties and their corresponding
  descriptions.
---

# Data source properties

{% hint style="warning" %}
**Note:** Properties listed below may not apply to all data sources.
{% endhint %}

You can modify certain properties by clicking on the pencil icon![](https://gblobscdn.gitbook.com/assets%2F-MAbbZ6XL3iXMHb3pjqP%2F-MF710zjyG0lukV90o0R%2F-MF72tpoG-yBWH_AWsf4%2Fimage.png?alt=media&token=08a91822-caad-46f1-9790-2c8fe201ae8e).

* [General](data-source-properties.md#general)
* [Content Type](data-source-properties.md#content-type)
* [Advanced](data-source-properties.md#advanced)
* [Initial Load Configuration](data-source-properties.md#initial-load-configuration)
* [File Match Pattern](data-source-properties.md#file-match-pattern)
* [Display Data](data-source-properties.md#display-data)
* [Sidebar](data-source-properties.md#sidebar)

## General

| Property | Description |
| :--- | :--- |
| **Content Format** | Content format of ingested data source \(**Avro, Parquet, ORC, JSON, CSV, TSV, x-www-form-urlencoded, Protobuf, Avro-record, Avro with Schema Registry,** or **XML**\). |
| **Compute Cluster** | Compute cluster this data source is running on. |
| **Target Storage** | Where to store the data read \(the output storage\). |
| **Retention** | The retention policy in Upsolver in minutes, hours, or days. The data is deleted permanently after this period elapses \(unless **Soft Retention** is set to **Yes**\). By default, the data is kept forever. |
| **Soft Retention** | A setting that prevents data deletion when the retention policy in Upsolver activates. When enabled, the metadata is purged but the underlying data \(e.g. S3 object\) is not deleted. |
| **&lt;Type&gt; Connection** | The connection string that represents a resource and its credentials. |
| **Kafka Version** | The Kafka version. |
| **Kafka Topic** | The Kafka topic. |
| **Stream Name** | The Kinesis stream name. |
| **Read From Start** | Whether the stream was read from the start. |
| **Folder** | The data folder \(e.g. billing data\). If this is not specified, the data is assumed to be in the top-level of the hierarchy. |
| **Date Pattern** | The date pattern of the files ingested. |
| **Start Ingestion From** | When ingestion started. |

## Content Type

### CSV

| Property | Description |
| :--- | :--- |
| **Infer Types** | Whether or not to infer types. |
| **Header** | If applicable, the header of the file. |
| **Delimiter** | The delimiter between columns of data. |
| **Null Value** | If applicable, the default null value in the data. |

### JSON

| Property | Description |
| :--- | :--- |
| **Split Root Array** | If the content is an array of JSON records, select to split the array content into separate records. |
| **Store JSON as String** | Whether to store the JSON in native format in a separate field. |

## Advanced

| Property | Description |
| :--- | :--- |
| **Real Time Statistics** | Whether the data source statistics are calculated in real-time directly from the input stream. This is relevant to lookup tables, when answers are required very fast and in real-time. |
| **Shards** | The number of shards, and the more shards the quicker the data processing. |
| **Execution Parallelism** | The number of independent shards to parse data, to increase parallelism and reduce latency. This should remain 1 in most cases. |
| **End Read At** | When to stop reading the stream. |
| **Use SSL** | Whether or not to use SSL. |
| **Compression** | The compression in the data \(Zip, GZip, Snappy, SnappyUnframed, Tar, or None\). |
| **Store Raw Data** | Whether to store an additional copy of the data in its original format. |
| **Data Dump Date** | The date that the data starts. |
| **Max Delay** | The maximum delay to consider the data, that is, any data that arrives delayed by more than the max delay is filtered out. |
| **Interval** | The sliding interval to wait for data. |

## Initial Load Configuration

| Property | Description |
| :--- | :--- |
| **Prefix** | The file prefix. |
| **Pattern** | The file pattern. |

## File Match Pattern

| Property | Description |
| :--- | :--- |
| **File Name Pattern** | The file name pattern. |

## Display Data

| Property | Description |
| :--- | :--- |
| **Name** | Data source name in Upsolver. |
| **Description** | Description of data source. |
| **Creation Time** | Time this data source was created. |
| **Created By** | Which user this data source was created by. |
| **Modified Time** | If applicable, time this data source was last modified. |
| **Modified By** | Which user last modified this data source. |

## Sidebar

| Property | Description |
| :--- | :--- |
| **Show Sparse Fields** | Select to show fields with density under 0.01%. |
| **Attached Workspaces** | The workspaces attached to the data source. |

