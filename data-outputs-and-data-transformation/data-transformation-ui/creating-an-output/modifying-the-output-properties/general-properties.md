---
description: >-
  This page provides a list of the properties that can be found under the
  general section of output properties.
---

# General output properties

Properties have been sorted as:

* [General](general-properties.md#general) 
  * properties most outputs have
* [Storage](general-properties.md#storage)
  * e.g. Amazon S3, Google Storage, etc.
* [Hive Metastores](general-properties.md#hive-metastores)
  * e.g. Amazon Athena, Qubole, etc.
* [Databases](general-properties.md#databases)
  * e.g. Snowflake, MySQL, etc.
* [Lookup Tables](general-properties.md#lookup-tables)
* [Kinesis](general-properties.md#kinesis)
* [Elasticsearch](general-properties.md#elasticsearch)
* [Kafka](general-properties.md#kafka)

{% hint style="warning" %}
**Note:** Properties listed below may not apply to all outputs.
{% endhint %}

## General

<table>
  <thead>
    <tr>
      <th style="text-align:left">Property</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>Data Sources</b>
      </td>
      <td style="text-align:left">The required data sources to base the output on.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Override Window Size</b>
      </td>
      <td style="text-align:left">
        <p>If enabled, this feature can be set to minutes, hours, or days, or <b>Infinite Override Size</b>.</p>
        <p>For example, if you wish to create an <b>hourly output</b> that will <b>aggregate data</b>  <b>for the last day</b>,
          then the<b> output interval</b> should be <b>1 hour</b>, but <b>override window size</b> should
          be <b>1 day</b>.</p>
        <p>This option is useful when used in combination with upserts.
          <br />For example, if you want the latest total count of events per user, set
          the <b>Override Window</b> to <b>infinite</b>; in this case, every time an
          event arises for a user, the updated total count for the user is upserted,
          and the old record is deleted.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Reporting Tags</b>
      </td>
      <td style="text-align:left">Tags that can be sent to external monitoring systems.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Path</b>
      </td>
      <td style="text-align:left">
        <p>The desired path for data to be exported to.</p>
        <p>If left empty, a system generated unique path will be used.</p>
      </td>
    </tr>
  </tbody>
</table>

## Storage

| Property | Description |
| :--- | :--- |
| **Date Format** | How output will be partitioned by time \(e.g. yyyy/MM/dd\). |
| **Output Format** | File format for output. |
| **&lt;Storage&gt; Connection** | Connection string for storage location. |
| **Tabular** | Whether or not the output is tabular. |

## Hive Metastores

| Property | Description |
| :--- | :--- |
| **Partition Size** | The output partition size \(Hourly, Daily, Weekly, or Yearly\). |
| **Compression** | The compression applied to the output \(None, GZip, or Snappy\). |
| **Run Compactions** | Whether to run compactions on the output. |
| **Excluded Partitions** | The partitions to exclude. You can import, export, or edit the list. |
| **S3 Storage** | S3 storage location where Upsolver stores the intermediate bulk files before uploading. |

## Databases

| Property | Description |
| :--- | :--- |
| **Skip Failed Files** | If enabled, when a load fails the manifest of that load will be skipped. The skipped manifest will be saved aside for manual re-processing once the copy error has been fixed. |
| **Fail on Write Error** | If enabled, any error while copying to the target will cause the load to fail. If disabled the same behavior will occur after 100K errors \(The max allowed by Redshift\) |
| **&lt;Database&gt; Connection** | Connection string of database connected to this output. |
| **Schema** | Schema of this output. |
| **Table Name** | Name of output table. |
| **Intermediate Storage Location** | Where Upsolver stores the intermediate bulk files before uploading. |

## Lookup Tables

| Property | Description |
| :--- | :--- |
| **Window** | Window of time to keep in lookup table. |
| **Omit Key Columns** | Whether or not to store the key columns in the lookup table. This saves space if enabled, but prevents iteration from returning the key columns. |
| **Real Time** | Load data into this lookup table directly from the input stream using a real time cluster if one is deployed. |

## Kinesis

| Property | Description |
| :--- | :--- |
| **Kinesis Connection** | Connection string for Kinesis stream. |
| **Stream Name** | Name of stream output is written to. |
| **Intermediate Storage** | Location where Upsolver stores the intermediate bulk files before uploading. |
| **Tabular** | Whether or not the output is tabular. |

## Elasticsearch

| Property | Description |
| :--- | :--- |
| **Delete Indices** | Delete indices from ElasticSearch based on retention period. |
| **Connection** | Elasticsearch connection string. |
| **Index Name** | Name of index output is written to. |
| **Index Partition Size** | Size of index partition. |
| **S3 Connection** | S3 storage location where Upsolver stores the intermediate bulk files before uploading. |

## Kafka

| Property | Description |
| :--- | :--- |
| **Kafka Hosts** | Comma-separated list of `host:port` pairs required to connect to Kafka cluster. |
| **Topic Name** | Name of topic this output is written to. |
| **Additional Kafka Properties** | Tags that can be sent to external monitoring systems. |
| **Intermediate Storage** | Location where Upsolver stores the intermediate bulk files before uploading. |
| **Tabular** | Whether or not the output is tabular. |

