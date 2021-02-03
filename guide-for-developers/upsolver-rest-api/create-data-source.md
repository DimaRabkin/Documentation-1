---
description: >-
  This article provides a guide on how to create different types of data sources
  using an API call.
---

# Create a data source

This API enables you to create a new data source. All API calls require an [API token](./).

```http
POST https://api.upsolver.com/inputs
```

## Amazon S3 \(Quick\)

Connect to your AWS S3 Bucket. 

In order for Upsolver to read events directly from your cloud storage, files should be partitioned by date and time \(which defines the folder structure in the cloud storage\).

{% hint style="info" %}
A prerequisite for defining a cloud storage data source is providing Upsolver with the appropriate credentials for reading from your cloud storage.   
**See:** [S3 connection](../../administration/connections/amazon-s3-connection.md)
{% endhint %}

#### Fields

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Optional</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">bucket</td>
      <td style="text-align:left">Bucket</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The Amazon S3 bucket to read from.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">globFilePattern</td>
      <td style="text-align:left">Glob File Pattern</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The pattern for files to ingest.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">datePattern</td>
      <td style="text-align:left">Date Pattern</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The date pattern in the file name/folder structure (e.g. <code>yyyy/MM/dd/HH/mm</code>).
        The date format specification must be set according to <a href="../../getting-started/glossary/language-guide/functions/calculated-functions/external-apis-functions.md">Java DateTimeFormatter format</a>.</td>
      <td
      style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">contentType</td>
      <td style="text-align:left">Content Format</td>
      <td style="text-align:left">ContentType</td>
      <td style="text-align:left">
        <p>The format of the messages. Supported formats are: JSON, AVRO, CSV, TSV,
          ORC, Protobuf and x-www-form-urlencoded.</p>
        <p>For self-describing formats like JSON, the schema is auto-detected. The
          body should contain of the message should contain the message itself, which
          should not be url-encoded.</p>
        <p>Messages can be compressed, Upsolver automatically detects the compression
          type.</p>
        <p>Supported compression types are: Zip, GZip, Snappy and None.</p>
        <p><b>See:</b>  <a href="content-formats.md">Content formats</a>
        </p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">compression</td>
      <td style="text-align:left">Compression</td>
      <td style="text-align:left">Compression</td>
      <td style="text-align:left">The compression in the data (Zip, GZip, Snappy, SnappyUnframed, Tar, or
        None).</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">displayData.name</td>
      <td style="text-align:left">Name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source name.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">displayData.description</td>
      <td style="text-align:left">Description</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source description.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">softRetention</td>
      <td style="text-align:left">Soft Retention</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">A setting that prevents data deletion when the retention policy in Upsolver
        activates. When enabled, the metadata is purged but the underlying data
        (e.g. S3 object) is not deleted.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">prefix</td>
      <td style="text-align:left">Folder</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">If the data resides in a sub folder within the defined cloud storage,
        specify this folder.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">startExecutionFrom</td>
      <td style="text-align:left">Start Ingestion From</td>
      <td style="text-align:left">String (ISO-8601)</td>
      <td style="text-align:left">
        <p>The time from which to ingest the data from.</p>
        <p>Files from before this time (based on the provided date pattern) are ignored.
          If you leave this field empty all files are ingested.</p>
      </td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">workspaces</td>
      <td style="text-align:left">Workspaces</td>
      <td style="text-align:left">String[]</td>
      <td style="text-align:left">The workspaces attached to this data source.</td>
      <td style="text-align:left">+</td>
    </tr>
  </tbody>
</table>

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "QuickS3StorageInputRequest",
	"bucket" : "bucket",
	"globFilePattern" : "globFilePattern",
	"datePattern" : "yyyy/MM/dd/HH/mm",
	"contentType" : {
		"clazz" : "JsonContentType"
	},
	"compression" : {
		"clazz" : "AutoDetectCompression"
	},
	"displayData" : {
		"name" : "First Amazon S3 Data Source",
		"description" : "Description of first Amazon 
S3 data source"
	},
	"softRetention" : true
}' "https://api.upsolver.com/inputs/DATA-SOURCE-ID"
```

## Amazon S3 \(Advanced\)

Connect to your AWS S3 Bucket. 

In order for Upsolver to read events directly from your cloud storage, files should be partitioned by date and time \(which defines the folder structure in the cloud storage\).

{% hint style="info" %}
A prerequisite for defining a cloud storage data source is providing Upsolver with the appropriate credentials for reading from your cloud storage.   
**See:** [S3 connection](../../administration/connections/amazon-s3-connection.md)
{% endhint %}

#### Fields

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Optional</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">displayData.name</td>
      <td style="text-align:left">Name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source name.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">displayData.description</td>
      <td style="text-align:left">Description</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source description.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">sourceStorage</td>
      <td style="text-align:left">S3 Connection</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The cloud storage to ingest files from.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">datePattern</td>
      <td style="text-align:left">Date Pattern</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The date pattern in the file name/folder structure. For example: <code>yyyy/MM/dd/HH/mm</code>.
        The date format specification must be set according to <a href="../../getting-started/glossary/language-guide/functions/calculated-functions/external-apis-functions.md">Java DateTimeFormatter format</a>.</td>
      <td
      style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">fileMatchPattern</td>
      <td style="text-align:left">File Name Pattern</td>
      <td style="text-align:left">FileNameMatcher</td>
      <td style="text-align:left">The file name pattern for the files to ingest. If all the files in the
        specified folders are relevant, specify All. The pattern given is matched
        against the file path starting from the bucket specified.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">contentType</td>
      <td style="text-align:left">Content Format</td>
      <td style="text-align:left">ContentType</td>
      <td style="text-align:left">
        <p>The format of the messages. Supported formats are: JSON, AVRO, CSV, TSV,
          ORC, Protobuf and x-www-form-urlencoded.</p>
        <p>For self-describing formats like JSON, the schema is auto-detected. The
          body should contain of the message should contain the message itself, which
          should not be url-encoded.</p>
        <p>Messages can be compressed, Upsolver automatically detects the compression
          type.</p>
        <p>Supported compression types are: Zip, GZip, Snappy and None.</p>
        <p>See <a href="content-formats.md">Content Formats</a>.</p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">computeEnvironment</td>
      <td style="text-align:left">Compute Cluster</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The compute cluster to run the calculation on. See <a href="../../administration/managing-clusters/#adding-a-compute-cluster">Adding a Compute Cluster</a>.</td>
      <td
      style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">destinationStorage</td>
      <td style="text-align:left">Target Storage</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data and metadata files for this data source will be stored in this
        storage.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">compression</td>
      <td style="text-align:left">Compression</td>
      <td style="text-align:left">Compression</td>
      <td style="text-align:left">The compression in the data (Zip, GZip, Snappy, SnappyUnframed, Tar, or
        None).</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">interval</td>
      <td style="text-align:left">Interval</td>
      <td style="text-align:left">Int (Minutes)</td>
      <td style="text-align:left">The sliding interval to wait for data.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">prefix</td>
      <td style="text-align:left">Folder</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">If the data resides in a sub folder within the defined cloud storage,
        specify this folder.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">startExecutionFrom</td>
      <td style="text-align:left">Start Ingestion From</td>
      <td style="text-align:left">String (ISO-8601)</td>
      <td style="text-align:left">
        <p>The time from which to ingest the data from.</p>
        <p>Files from before this time (based on the provided date pattern) are ignored.
          If you leave this field empty all files are ingested.</p>
      </td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">retention</td>
      <td style="text-align:left">Retention</td>
      <td style="text-align:left">Int (Minutes)</td>
      <td style="text-align:left">The retention period for the data.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">dataDumpDate</td>
      <td style="text-align:left">Data Dump Date</td>
      <td style="text-align:left">String (ISO-8601)</td>
      <td style="text-align:left">The date that the data starts.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">maxDelay</td>
      <td style="text-align:left">Max Delay</td>
      <td style="text-align:left">Int (Minutes)</td>
      <td style="text-align:left">The maximum delay to consider the data, that is, any data that arrives
        delayed by more than the max delay is filtered out.</td>
      <td style="text-align:left">+</td>
    </tr>
  </tbody>
</table>

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "CloudStorageInputRequest",
	"displayData" : {
		"name" : "First Amazon S3 Data Source",
		"description" : "Description of first Amazon 
S3 data source"
	},
	"sourceStorage" : "aa302f0a-e6ee-44aa-aa38-e28f1ff455f7",
	"datePattern" : "yyyy/MM/dd/HH/mm",
	"fileMatchPattern" : {
		"clazz" : "AllMatcher"
	},
	"contentType" : {
		"type" : "JsonContentType"
	,
	"computeEnvironment" : "53b314af-ffab-419a-9c2c-56032c6ef4c0",
	"destinationStorage" : "e019c0fe-bb80-4cf1-bc7b-aee579d8672e",
	"compression" : {
		"clazz" : "AutoDetectCompression"
	},
	"interval" : 120
}' "https://api.upsolver.com/api/v1/data-source/"
```

## Amazon Kinesis Stream \(Quick\)

Connect to your Amazon Kinesis. Upsolver can read events from your Amazon Kinesis, according to the stream you define.

{% hint style="info" %}
A prerequisite for defining an Amazon Kinesis stream connection is providing Upsolver with the appropriate credentials for reading from your Amazon Kinesis stream.   
**See:** [Kinesis connection](../../administration/connections/amazon-kinesis.md)
{% endhint %}

#### Fields

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Optional</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">region</td>
      <td style="text-align:left">Region</td>
      <td style="text-align:left">Region</td>
      <td style="text-align:left">Your AWS region.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">streamName</td>
      <td style="text-align:left">Stream</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The name of the relevant Kinesis stream.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">contentType</td>
      <td style="text-align:left">Content Format</td>
      <td style="text-align:left">ContentType</td>
      <td style="text-align:left">
        <p>The format of the messages. Supported formats are: JSON, AVRO, CSV, TSV,
          ORC, Protobuf and x-www-form-urlencoded.</p>
        <p>For self-describing formats like JSON, the schema is auto-detected. The
          body should contain of the message should contain the message itself, which
          should not be url-encoded.</p>
        <p>Messages can be compressed, Upsolver automatically detects the compression
          type.</p>
        <p>Supported compression types are: Zip, GZip, Snappy and None.</p>
        <p><b>See:</b>  <a href="content-formats.md">Content formats</a>
        </p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">compression</td>
      <td style="text-align:left">Compression</td>
      <td style="text-align:left">Compression</td>
      <td style="text-align:left">The compression in the data (Zip, GZip, Snappy, SnappyUnframed, Tar, or
        None).</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">displayData.name</td>
      <td style="text-align:left">Name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source name.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">displayData.description</td>
      <td style="text-align:left">Description</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source description.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">softRetention</td>
      <td style="text-align:left">Soft Retention</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">A setting that prevents data deletion when the retention policy in Upsolver
        activates. When enabled, the metadata is purged but the underlying data
        (e.g. S3 object) is not deleted.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">workspaces</td>
      <td style="text-align:left">Workspaces</td>
      <td style="text-align:left">String[]</td>
      <td style="text-align:left">The workspaces attached to this data source.</td>
      <td style="text-align:left">+</td>
    </tr>
  </tbody>
</table>

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "QuickKinesisInputRequest",
	"region" : "region",
	"streamName" : "streamName",
	"contentType" : {
		"type" : "JsonContentType"
	},
	"compression" : {
		"clazz" : "AutoDetectCompression"
	},
	"displayData" : {
		"name" : "First Amazon Kinesis Stream Data 
Source",
		"description" : "Description of first Amazon 
Kinesis Stream data source"
	},
	"softRetention" : true
}' "https://api.upsolver.com/api/v1/data-source/"
```

## Amazon Kinesis Stream \(Advanced\)

Connect to your Amazon Kinesis. Upsolver can read events from your Amazon Kinesis, according to the stream you define.

{% hint style="info" %}
A prerequisite for defining an Amazon Kinesis stream connection is providing Upsolver with the appropriate credentials for reading from your Amazon Kinesis stream.   
**See:** [Kinesis connection](../../administration/connections/amazon-kinesis.md)
{% endhint %}

#### Fields

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Optional</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">displayData.name</td>
      <td style="text-align:left">Name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source name.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">displayData.description</td>
      <td style="text-align:left">Description</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source description.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">contentType</td>
      <td style="text-align:left">Content Format</td>
      <td style="text-align:left">ContentType</td>
      <td style="text-align:left">
        <p>The format of the messages. Supported formats are: JSON, AVRO, CSV, TSV,
          ORC, Protobuf and x-www-form-urlencoded.</p>
        <p>For self-describing formats like JSON, the schema is auto-detected. The
          body should contain of the message should contain the message itself, which
          should not be url-encoded.</p>
        <p>Messages can be compressed, Upsolver automatically detects the compression
          type.</p>
        <p>Supported compression types are: Zip, GZip, Snappy and None.</p>
        <p><b>See:</b>  <a href="content-formats.md">Content formats</a>
        </p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">kinesisConnection</td>
      <td style="text-align:left">Kinesis Connection</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The AWS credentials to connect to Kinesis.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">streamName</td>
      <td style="text-align:left">Stream</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The name of the relevant Kinesis stream.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">readFromStart</td>
      <td style="text-align:left">Read From Start</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p>The time from which to ingest the data from.</p>
        <p>Messages from before this time will be ignored. If you leave this field
          empty all messages are ingested.</p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">computeEnvironment</td>
      <td style="text-align:left">Compute Cluster</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The compute cluster to run the calculation on. <b>See: </b><a href="../../administration/managing-clusters/#adding-a-compute-cluster">Compute cluster</a>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">connectionPointer</td>
      <td style="text-align:left">Target Storage</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data and metadata files for this data source will be stored in this
        storage.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">isOnline</td>
      <td style="text-align:left">Real Time Statistics</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">Calculate this data source&apos;s statistics in real time directly from
        the input stream if a real time cluster is deployed.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">shards</td>
      <td style="text-align:left">Shards</td>
      <td style="text-align:left">Int</td>
      <td style="text-align:left">How many readers to use in parallel to read the stream. A recommended
        value would be to increase it by 1 for every 70 MB/s sent to your topic.</td>
      <td
      style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">parallelism</td>
      <td style="text-align:left">Parallelism</td>
      <td style="text-align:left">Int</td>
      <td style="text-align:left">The number of independent shards to parse data, to increase parallelism
        and reduce latency. This should remain 1 in most cases and be no more than
        the number of shards used to read the data from the source.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">compression</td>
      <td style="text-align:left">Compression</td>
      <td style="text-align:left">Compression</td>
      <td style="text-align:left">The compression in the data (Zip, GZip, Snappy, SnappyUnframed, Tar, or
        None).</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">retention</td>
      <td style="text-align:left">Retention</td>
      <td style="text-align:left">Int (Minutes)</td>
      <td style="text-align:left">A retention period for the data in Upsolver. After this period of time
        passes, the data is deleted forever.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">endExecutionAt</td>
      <td style="text-align:left">End Read At</td>
      <td style="text-align:left">String (ISO-8601)</td>
      <td style="text-align:left">If configured, stop reading after this date.</td>
      <td style="text-align:left">+</td>
    </tr>
  </tbody>
</table>

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "KinesisInputRequest",
	"displayData" : {
		"name" : "First Amazon Kinesis Stream Data 
Source",
		"description" : "Description of first Amazon 
Kinesis Stream data source"
	},
	"contentType" : {
		"type" : "JsonContentType"
	},
	"kinesisConnection" : "dcfc39c1-c458-4ec5-87f1-0c7f437ea17e",
	"streamName" : "streamName",
	"readFromStart" : true,
	"computeEnvironment" : "fc2a356d-c3ae-4756-a4a3-1b15158df5e7",
	"connectionPointer" : "4e3787cd-daac-42ea-8dd4-642c516a4a31",
	"isOnline" : true,
	"shards" : 1,
	"parallelism" : 1,
	"compression" : {
		"clazz" : "AutoDetectCompression"
	}
}' "https://api.upsolver.com/api/v1/data-source/"
```

## Amazon S3 over SQS

Connect to your AWS S3 Bucket using SQS Notifications.

{% hint style="info" %}
You will need to configure SQS Notifications from your S3 Bucket and open permissions to read and delete messages from the SQS Queue to the same access key and secret key you entered to give Upsolver permissions to read from the S3 Bucket.   
**See:** [S3 over SQS connection](../../administration/connections/amazon-s3-over-sqs.md)
{% endhint %}

#### Fields

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Optional</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">displayData.name</td>
      <td style="text-align:left">Name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source name.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">displayData.description</td>
      <td style="text-align:left">Description</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source description.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">sourceStorage</td>
      <td style="text-align:left">Source Storage</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The cloud storage to ingest files from.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">contentType</td>
      <td style="text-align:left">Content Format</td>
      <td style="text-align:left">ContentType</td>
      <td style="text-align:left">
        <p>The format of the messages. Supported formats are: JSON, AVRO, CSV, TSV,
          ORC, Protobuf and x-www-form-urlencoded.</p>
        <p>For self-describing formats like JSON, the schema is auto-detected. The
          body should contain of the message should contain the message itself, which
          should not be url-encoded.</p>
        <p>Messages can be compressed, Upsolver automatically detects the compression
          type.</p>
        <p>Supported compression types are: Zip, GZip, Snappy and None.</p>
        <p><b>See:</b>  <a href="content-formats.md">Content formats</a>
        </p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">computeEnvironment</td>
      <td style="text-align:left">Compute Cluster</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The compute cluster to run the calculation on. <b>See:</b><a href="../../administration/managing-clusters/#adding-a-compute-cluster"> Compute cluster</a>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">destinationStorage</td>
      <td style="text-align:left">Target Storage</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data and metadata files for this data source will be stored in this
        storage.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">compression</td>
      <td style="text-align:left">Compression</td>
      <td style="text-align:left">Compression</td>
      <td style="text-align:left">The compression in the data (Zip, GZip, Snappy, SnappyUnframed, Tar, or
        None).</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">softRetention</td>
      <td style="text-align:left">Soft Retention</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">A setting that prevents data deletion when the retention policy in Upsolver
        activates. When enabled, the metadata is purged but the underlying data
        (e.g. S3 object) is not deleted.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">executionParallelism</td>
      <td style="text-align:left">Parallelism</td>
      <td style="text-align:left">Int</td>
      <td style="text-align:left">The number of independent shards to parse data, to increase parallelism
        and reduce latency. This should remain 1 in most cases and be no more than
        the number of shards used to read the data from the source.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">prefix</td>
      <td style="text-align:left">Prefix</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The prefix of the files or directories. To filter a specific directory,
        add a trailing <code>/</code>.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">suffix</td>
      <td style="text-align:left">Suffix</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The suffix of the files to read.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">startExecutionFrom</td>
      <td style="text-align:left">Start Ingestion From</td>
      <td style="text-align:left">String (ISO-8601)</td>
      <td style="text-align:left">
        <p>The time from which to ingest the data from.</p>
        <p>Messages from before this time will be ignored. If you leave this field
          empty all messages are ingested.</p>
      </td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">endExecutionAt</td>
      <td style="text-align:left">End Read At</td>
      <td style="text-align:left">String (ISO-8601)</td>
      <td style="text-align:left">If configured, stop reading after this date.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">retention</td>
      <td style="text-align:left">Retention</td>
      <td style="text-align:left">Int (Minutes)</td>
      <td style="text-align:left">A retention period for the data in Upsolver. After this period of time
        passes, the data is deleted forever.</td>
      <td style="text-align:left">+</td>
    </tr>
  </tbody>
</table>

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "S3OverSQSInputRequest",
	"displayData" : {
		"name" : "First S3 Over SQS Data Source",
		"description" : "Description of first S3 
Over SQS data source"
	},
	"sourceStorage" : "6ee598b6-4928-4b07-b532-83a79464e5bb",
	"contentType" : {
		"type" : "JsonContentType"
	},
	"computeEnvironment" : "46c2945e-5a46-4d93-9e21-5a85653c28c5",
	"destinationStorage" : "2a08601c-52d2-425e-8d2c-324dbcea5858",
	"compression" : {
		"clazz" : "AutoDetectCompression"
	},
	"softRetention" : true,
	"executionParallelism" : 1
}' "https://api.upsolver.com/api/v1/data-source/"
```

## Apache Kafka \(Quick\)

Connect to any topic on your Kafka Servers. Upsolver can read events from your Kafka cluster from the specified Kafka topic. 

{% hint style="info" %}
A prerequisite for defining a Kafka stream connection is providing Upsolver with the appropriate credentials for reading from your Kafka cluster.   
**See:** [Kafka connection](../../administration/connections/kafka-connection.md)
{% endhint %}

#### Fields

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Optional</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">kafkaHosts</td>
      <td style="text-align:left">Kafka Hosts</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The Kafka hosts separated with commas (e.g. <code>foo:9092,bar:9092</code>)</td>
      <td
      style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">topicName</td>
      <td style="text-align:left">Kafka Topic</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The Kafka topic to ingest the data from.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">contentType</td>
      <td style="text-align:left">Content Format</td>
      <td style="text-align:left">ContentType</td>
      <td style="text-align:left">
        <p>The format of the messages. Supported formats are: JSON, AVRO, CSV, TSV,
          ORC, Protobuf and x-www-form-urlencoded.</p>
        <p>For self-describing formats like JSON, the schema is auto-detected. The
          body should contain of the message should contain the message itself, which
          should not be url-encoded.</p>
        <p>Messages can be compressed, Upsolver automatically detects the compression
          type.</p>
        <p>Supported compression types are: Zip, GZip, Snappy and None.</p>
        <p><b>See:</b>  <a href="content-formats.md">Content formats</a>
        </p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">compression</td>
      <td style="text-align:left">Compression</td>
      <td style="text-align:left">Compression</td>
      <td style="text-align:left">The compression in the data (Zip, GZip, Snappy, SnappyUnframed, Tar, or
        None).</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">displayData.name</td>
      <td style="text-align:left">Name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source name.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">displayData.description</td>
      <td style="text-align:left">Description</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source description.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">softRetention</td>
      <td style="text-align:left">Soft Retention</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">A setting that prevents data deletion when the retention policy in Upsolver
        activates. When enabled, the metadata is purged but the underlying data
        (e.g. S3 object) is not deleted.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">maybekafkaVersion</td>
      <td style="text-align:left">Kafka Version</td>
      <td style="text-align:left">KafkaVersion</td>
      <td style="text-align:left">The version of the Kafka Servers. If unsure, use <code>0.10.x.x</code>.</td>
      <td
      style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">workspaces</td>
      <td style="text-align:left">Workspaces</td>
      <td style="text-align:left">String[]</td>
      <td style="text-align:left">The workspaces attached to this data source.</td>
      <td style="text-align:left">+</td>
    </tr>
  </tbody>
</table>

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "QuickKafkaInputRequest",
	"kafkaHosts" : "kafkaHosts",
	"topicName" : "topicName",
	"contentType" : {
		"type" : "JsonContentType"
	},
	"compression" : {
		"clazz" : "AutoDetectCompression"
	},
	"displayData" : {
		"name" : "First Kafka Data Source",
		"description" : "Description of first 
Kafka data source"
	},
	"softRetention" : true
}' "https://api.upsolver.com/api/v1/data-source/"
```

## Apache Kafka \(Advanced\)

Connect to any topic on your Kafka Servers. Upsolver can read events from your Kafka cluster from the specified Kafka topic. 

{% hint style="info" %}
A prerequisite for defining a Kafka stream connection is providing Upsolver with the appropriate credentials for reading from your Kafka cluster.   
**See:** [Kafka connection](../../administration/connections/kafka-connection.md)
{% endhint %}

#### Fields

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Optional</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">displayData.name</td>
      <td style="text-align:left">Name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source name.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">displayData.description</td>
      <td style="text-align:left">Description</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source description.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">kafkaVersion</td>
      <td style="text-align:left">Kafka Version</td>
      <td style="text-align:left">KafkaVersion</td>
      <td style="text-align:left">The version of the Kafka Servers. If unsure, use <code>0.10.x.x</code>.</td>
      <td
      style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">kafkaHosts</td>
      <td style="text-align:left">Kafka Hosts</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The Kafka hosts separated with commas. For example: foo:9092,bar:9092</td>
      <td
      style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">topicName</td>
      <td style="text-align:left">Kafka Topic</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The Kafka topic to ingest the data from.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">readFromStart</td>
      <td style="text-align:left">Read From Start</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">Whether to read the data from the start of the topic or to begin from
        the end.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">contentType</td>
      <td style="text-align:left">Content Format</td>
      <td style="text-align:left">ContentType</td>
      <td style="text-align:left">
        <p>The format of the messages. Supported formats are: JSON, AVRO, CSV, TSV,
          ORC, Protobuf and x-www-form-urlencoded.</p>
        <p>For self-describing formats like JSON, the schema is auto-detected. The
          body should contain of the message should contain the message itself, which
          should not be url-encoded.</p>
        <p>Messages can be compressed, Upsolver automatically detects the compression
          type.</p>
        <p>Supported compression types are: Zip, GZip, Snappy and None.</p>
        <p><b>See:</b>  <a href="content-formats.md">Content formats</a>
        </p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">computeEnvironment</td>
      <td style="text-align:left">Compute Cluster</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The compute cluster to run the calculation on. <b>See:</b>  <a href="../../administration/managing-clusters/#adding-a-compute-cluster">Compute cluster</a>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">connectionPointer</td>
      <td style="text-align:left">Target Storage</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data and metadata files for this data source will be stored in this
        storage.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">softRetention</td>
      <td style="text-align:left">Soft Retention</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">A setting that prevents data deletion when the retention policy in Upsolver
        activates. When enabled, the metadata is purged but the underlying data
        (e.g. S3 object) is not deleted.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">shards</td>
      <td style="text-align:left">Shards</td>
      <td style="text-align:left">Int</td>
      <td style="text-align:left">How many readers to use in parallel to read the stream. A recommended
        value would be to increase it by 1 for every 70 MB/s sent to your topic.</td>
      <td
      style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">executionParallelism</td>
      <td style="text-align:left">Execution Parallelism</td>
      <td style="text-align:left">Int</td>
      <td style="text-align:left">The number of independent shards to parse data, to increase parallelism
        and reduce latency. This should remain 1 in most cases and be no more than
        the number of shards used to read the data from the source.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">isOnline</td>
      <td style="text-align:left">Real Time Statistics</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">Calculate this data source&apos;s statistics in real time directly from
        the input stream if a real time cluster is deployed.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">useSsl</td>
      <td style="text-align:left">Use SSL</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">Set this to true if your connection requires SSL. Contact us to ensure
        that your SSL certificate is supported.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">storeRawData</td>
      <td style="text-align:left">Store Raw Data</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">Store an additional copy of the data in its original format.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">compression</td>
      <td style="text-align:left">Compression</td>
      <td style="text-align:left">Compression</td>
      <td style="text-align:left">The compression in the data (Zip, GZip, Snappy, SnappyUnframed, Tar, or
        None).</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">consumerProperties</td>
      <td style="text-align:left">Kafka Consumer Properties</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Extra properties for Kafka Consumer.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">retention</td>
      <td style="text-align:left">Retention</td>
      <td style="text-align:left">Int (Minutes)</td>
      <td style="text-align:left">A retention period for the data in Upsolver. After this period of time
        passes, the data is deleted forever.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">endExecutionAt</td>
      <td style="text-align:left">End Read At</td>
      <td style="text-align:left">String (ISO-8601)</td>
      <td style="text-align:left">If configured, stop reading after this date.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">workspaces</td>
      <td style="text-align:left">Workspaces</td>
      <td style="text-align:left">String[]</td>
      <td style="text-align:left">The workspaces attached to this data source.</td>
      <td style="text-align:left">+</td>
    </tr>
  </tbody>
</table>

#### Example

```bash
curl -X POST -H "content-type: application/json" 
-H "Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "KafkaInputRequest",
	"displayData" : {
		"name" : "First Kafka Data Source",
		"description" : "Description of first 
Kafka data source"
	},
	"kafkaVersion" : "0.10.x.x",
	"kafkaHosts" : "kafkaHosts",
	"topicName" : "topicName",
	"readFromStart" : true,
	"contentType" : {
		"type" : "JsonContentType"
	},
	"computeEnvironment" : "5d8b6e27-6004-48b2-8dc1-1db9f25880cb",
	"connectionPointer" : "36a1d237-1ff0-4574-972b-b071482f3d08",
	"softRetention" : true,
	"shards" : 1,
	"executionParallelism" : 1,
	"isOnline" : true,
	"useSsl" : true,
	"storeRawData" : true,
	"compression" : {
		"clazz" : "AutoDetectCompression"
	}
}' "https://api.upsolver.com/api/v1/data-source/"
```

## Azure Blob storage

Connect to your Azure Blob storage container. 

In order for Upsolver to read events directly from your cloud storage, files should be partitioned by date and time \(which defines the folder structure in the cloud storage\).

{% hint style="info" %}
A prerequisite for defining a cloud storage data source is providing Upsolver with the appropriate credentials for reading from your cloud storage.  
**See:** [Azure Blob storage connection](../../administration/connections/azure-blob-storage-connection.md)
{% endhint %}

#### Fields

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Optional</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">displayData.name</td>
      <td style="text-align:left">Name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source name.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">displayData.description</td>
      <td style="text-align:left">Description</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source description.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">sourceStorage</td>
      <td style="text-align:left">Azure Blob Storage Connection</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The cloud storage to ingest files from.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">datePattern</td>
      <td style="text-align:left">Date Pattern</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The date pattern in the file name/folder structure (e.g. <code>yyyy/MM/dd/HH/mm</code>).
        The date format specification must be set according to <a href="../../getting-started/glossary/language-guide/functions/calculated-functions/external-apis-functions.md">Java DateTimeFormatter format</a>.</td>
      <td
      style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">fileMatchPattern</td>
      <td style="text-align:left">File Name Pattern</td>
      <td style="text-align:left">FileNameMatcher</td>
      <td style="text-align:left">The file name pattern for the files to ingest. If all the files in the
        specified folders are relevant, specify All. The pattern given is matched
        against the file path starting from the storage container specified.</td>
      <td
      style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">contentType</td>
      <td style="text-align:left">Content Format</td>
      <td style="text-align:left">ContentType</td>
      <td style="text-align:left">
        <p>The format of the messages. Supported formats are: JSON, AVRO, CSV, TSV,
          ORC, Protobuf and x-www-form-urlencoded.</p>
        <p>For self-describing formats like JSON, the schema is auto-detected. The
          body should contain of the message should contain the message itself, which
          should not be url-encoded.</p>
        <p>Messages can be compressed, Upsolver automatically detects the compression
          type.</p>
        <p>Supported compression types are: Zip, GZip, Snappy and None.</p>
        <p><b>See:</b>  <a href="content-formats.md">Content formats</a>
        </p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">computeEnvironment</td>
      <td style="text-align:left">Compute Cluster</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The compute cluster to run the calculation on.
        <br /><b>See:</b><a href="../../administration/managing-clusters/#adding-a-compute-cluster"><b> </b>Compute cluster</a>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">destinationStorage</td>
      <td style="text-align:left">Target Storage</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data and metadata files for this data source will be stored in this
        storage.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">softRetention</td>
      <td style="text-align:left">Soft Retention</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">A setting that prevents data deletion when the retention policy in Upsolver
        activates. When enabled, the metadata is purged but the underlying data
        (e.g. S3 object) is not deleted.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">compression</td>
      <td style="text-align:left">Compression</td>
      <td style="text-align:left">Compression</td>
      <td style="text-align:left">The compression in the data (Zip, GZip, Snappy, SnappyUnframed, Tar, or
        None).</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">interval</td>
      <td style="text-align:left">Interval</td>
      <td style="text-align:left">Int (Minutes)</td>
      <td style="text-align:left">The sliding interval to wait for data.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">prefix</td>
      <td style="text-align:left">Folder</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">If the data resides in a sub folder within the defined cloud storage,
        specify this folder.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">initialLoadConfiguration</td>
      <td style="text-align:left">Initial Load Configuration</td>
      <td style="text-align:left">InitialLoadConfiguration</td>
      <td style="text-align:left">If you have initial data, enter in a prefix and regex pattern to list
        the relevant data and select the required files.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">startExecutionFrom</td>
      <td style="text-align:left">Start Ingestion From</td>
      <td style="text-align:left">String (ISO-8601)</td>
      <td style="text-align:left">
        <p>The time from which to ingest the data from.</p>
        <p>Files from before this time (based on the provided date pattern) are ignored.
          If you leave this field empty all files are ingested.</p>
      </td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">retention</td>
      <td style="text-align:left">Retention</td>
      <td style="text-align:left">Int (Minutes)</td>
      <td style="text-align:left">A retention period for the data in Upsolver. After this amount of time
        elapsed the data will be deleted forever.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">dataDumpDate</td>
      <td style="text-align:left">Data Dump Date</td>
      <td style="text-align:left">String (ISO-8601)</td>
      <td style="text-align:left">The date that the data starts.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">maxDelay</td>
      <td style="text-align:left">Max Delay</td>
      <td style="text-align:left">Int (Minutes)</td>
      <td style="text-align:left">The maximum delay to consider the data, that is, any data that arrives
        delayed by more than the max delay is filtered out.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">workspaces</td>
      <td style="text-align:left">Workspaces</td>
      <td style="text-align:left">String[]</td>
      <td style="text-align:left">The workspaces attached to this data source.</td>
      <td style="text-align:left">+</td>
    </tr>
  </tbody>
</table>

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "AzureBlobStorageInputRequest",
	"displayData" : {
		"name" : "First Azure Blob Storage Data 
Source",
		"description" : "Description of first Azure 
Blob Storage data source"
	},
	"sourceStorage" : "2da1c848-9c44-4b4e-a226-4ffebf0d9c49",
	"datePattern" : "yyyy/MM/dd/HH/mm",
	"fileMatchPattern" : {
		"clazz" : "AllMatcher"
	},
	"contentType" : {
		"type" : "JsonContentType"
	},
	"computeEnvironment" : "1bce245a-0c76-4fe7-acb5-6f2bf4b64d8f",
	"destinationStorage" : "004974e0-e384-466e-8ac4-7429c30614e3",
	"softRetention" : true,
	"compression" : {
		"clazz" : "AutoDetectCompression"
	},
	"interval" : 120
}' "https://api.upsolver.com/api/v1/data-source/"
```

## Google Cloud Storage

Connect to your Google Storage Bucket. 

In order for Upsolver to read events directly from your cloud strage, files should be partitioned by date and time \(which defines the folder structure in the cloud storage\)

{% hint style="info" %}
A prerequisite for defining a cloud storage data source is providing Upsolver with the appropriate credentials for reading from your cloud storage.  
**See:** [Google Storage connection](../../administration/connections/google-storage-connection.md)
{% endhint %}

#### Fields

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Optional</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">displayData.name</td>
      <td style="text-align:left">Name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source name.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">displayData.description</td>
      <td style="text-align:left">Description</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source description.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">sourceStorage</td>
      <td style="text-align:left">Google Storage Connection</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The cloud storage to ingest files from.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">datePattern</td>
      <td style="text-align:left">Date Pattern</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The date pattern in the file name/folder structure (e.g. <code>yyyy/MM/dd/HH/mm</code>).
        The date format specification must be set according to <a href="../../getting-started/glossary/language-guide/functions/calculated-functions/external-apis-functions.md">Java DateTimeFormatter format</a>.</td>
      <td
      style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">fileMatchPattern</td>
      <td style="text-align:left">File Name Pattern</td>
      <td style="text-align:left">FileNameMatcher</td>
      <td style="text-align:left">The file name pattern for the files to ingest. If all the files in the
        specified folders are relevant, specify All. The pattern given is matched
        against the file path starting from storage source specified.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">contentType</td>
      <td style="text-align:left">Content Format</td>
      <td style="text-align:left">ContentType</td>
      <td style="text-align:left">
        <p>The format of the messages. Supported formats are: JSON, AVRO, CSV, TSV,
          ORC, Protobuf and x-www-form-urlencoded.</p>
        <p>For self-describing formats like JSON, the schema is auto-detected. The
          body should contain of the message should contain the message itself, which
          should not be url-encoded.</p>
        <p>Messages can be compressed, Upsolver automatically detects the compression
          type.</p>
        <p>Supported compression types are: Zip, GZip, Snappy and None.</p>
        <p><b>See:</b>  <a href="content-formats.md">Content formats</a>
        </p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">computeEnvironment</td>
      <td style="text-align:left">Compute Cluster</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The compute cluster to run the calculation on.
        <br /><b>See: </b><a href="../../administration/managing-clusters/cluster-types/adding-a-compute-cluster.md">Compute cluster</a>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">destinationStorage</td>
      <td style="text-align:left">Target Storage</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data and metadata files for this data source will be stored in this
        storage.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">softRetention</td>
      <td style="text-align:left">Soft Retention</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">A setting that prevents data deletion when the retention policy in Upsolver
        activates. When enabled, the metadata is purged but the underlying data
        (e.g. S3 object) is not deleted.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">compression</td>
      <td style="text-align:left">Compression</td>
      <td style="text-align:left">Compression</td>
      <td style="text-align:left">The compression in the data (Zip, GZip, Snappy, SnappyUnframed, Tar, or
        None).</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">interval</td>
      <td style="text-align:left">Interval</td>
      <td style="text-align:left">Int (Minutes)</td>
      <td style="text-align:left">The sliding interval to wait for data.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">prefix</td>
      <td style="text-align:left">Folder</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">If the data resides in a sub folder within the defined cloud storage,
        specify this folder.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">initialLoadConfiguration</td>
      <td style="text-align:left">Initial Load Configuration</td>
      <td style="text-align:left">InitialLoadConfiguration</td>
      <td style="text-align:left">If you have initial data, enter in a prefix and regex pattern to list
        the relevant data and select the required files.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">startExecutionFrom</td>
      <td style="text-align:left">Start Ingestion From</td>
      <td style="text-align:left">String (ISO-8601)</td>
      <td style="text-align:left">
        <p>The time from which to ingest the data from.</p>
        <p>Files from before this time (based on the provided date pattern) are ignored.
          If you leave this field empty all files are ingested.</p>
      </td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">retention</td>
      <td style="text-align:left">Retention</td>
      <td style="text-align:left">Int (Minutes)</td>
      <td style="text-align:left">A retention period for the data in Upsolver. After this amount of time
        elapsed the data will be deleted forever.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">dataDumpDate</td>
      <td style="text-align:left">Data Dump Date</td>
      <td style="text-align:left">String (ISO-8601)</td>
      <td style="text-align:left">The date that the data starts.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">maxDelay</td>
      <td style="text-align:left">Max Delay</td>
      <td style="text-align:left">Int (Minutes)</td>
      <td style="text-align:left">The maximum delay to consider the data, that is, any data that arrives
        delayed by more than the max delay is filtered out.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">workspaces</td>
      <td style="text-align:left">Workspaces</td>
      <td style="text-align:left">String[]</td>
      <td style="text-align:left">The workspaces attached to this data source.</td>
      <td style="text-align:left">+</td>
    </tr>
  </tbody>
</table>

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "GoogleCloudStorageInputRequest",
	"displayData" : {
		"name" : "First Google Cloud Storage 
Data Source",
		"description" : "Description of first Google 
Cloud Storage data source"
	},
	"sourceStorage" : "0a617e70-c2b2-4870-a908-f4c864c4961f",
	"datePattern" : "yyyy/MM/dd/HH/mm",
	"fileMatchPattern" : {
		"clazz" : "AllMatcher"
	},
	"contentType" : {
		"type" : "JsonContentType"
	},
	"computeEnvironment" : "d4f6ee48-0782-4789-b661-4e19679a541a",
	"destinationStorage" : "8ddd7397-e1ed-4b21-a9cb-91aa923ea165",
	"softRetention" : true,
	"compression" : {
		"clazz" : "AutoDetectCompression"
	},
	"interval" : 120
}' "https://api.upsolver.com/api/v1/data-source/"
```

## Kinesis-backed HTTP

Connect your stream using HTTP requests from any source.

Once you create the connection, you will be provided with an HTTP endpoint. Upsolver receives the data as POST, with the data in the body, and the data is stored in a Kinesis Stream until processed by Upsolver.

Headers sent with the request are also ingested as part of the stream, so metadata can be added to the request header.

#### Fields

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Optional</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">displayData.name</td>
      <td style="text-align:left">Name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source name.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">displayData.description</td>
      <td style="text-align:left">Description</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source description.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">contentType</td>
      <td style="text-align:left">Content Format</td>
      <td style="text-align:left">ContentType</td>
      <td style="text-align:left">
        <p>The format of the messages. Supported formats are: JSON, AVRO, CSV, TSV,
          ORC, Protobuf and x-www-form-urlencoded.</p>
        <p>For self-describing formats like JSON, the schema is auto-detected. The
          body should contain of the message should contain the message itself, which
          should not be url-encoded.</p>
        <p>Messages can be compressed, Upsolver automatically detects the compression
          type.</p>
        <p>Supported compression types are: Zip, GZip, Snappy and None.</p>
        <p><b>See:</b>  <a href="content-formats.md">Content formats</a>
        </p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">computeEnvironment</td>
      <td style="text-align:left">Compute Cluster</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The compute cluster to run the calculation on.
        <br /><b>See:</b><a href="../../administration/managing-clusters/#adding-a-compute-cluster"> Compute cluster</a>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">ingestionEnvironment</td>
      <td style="text-align:left">Ingestion Cluster</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">storageConnection</td>
      <td style="text-align:left">Target Storage</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data and metadata files for this Data Source will be stored in this
        storage.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">kinesisConnection</td>
      <td style="text-align:left">Kinesis Connection</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data and metadata files for this Data Source will be stored in this
        storage.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">softRetention</td>
      <td style="text-align:left">Soft Retention</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">A setting that prevents data deletion when the retention policy in Upsolver
        activates. When enabled, the metadata is purged but the underlying data
        (e.g. S3 object) is not deleted.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">retention</td>
      <td style="text-align:left">Retention</td>
      <td style="text-align:left">Int (Minutes)</td>
      <td style="text-align:left">A retention period for the data in Upsolver. After this amount of time
        elapsed the data will be deleted forever.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">startExecutionFrom</td>
      <td style="text-align:left">Start Ingestion From</td>
      <td style="text-align:left">String (ISO-8601)</td>
      <td style="text-align:left">
        <p>The time from which to ingest the data from.</p>
        <p>Files from before this time (based on the provided date pattern) are ignored.
          If you leave this field empty all files are ingested.</p>
      </td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">endExecutionAt</td>
      <td style="text-align:left">End Read At</td>
      <td style="text-align:left">String (ISO-8601)</td>
      <td style="text-align:left">If configured, stop reading after this date.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">workspaces</td>
      <td style="text-align:left">Workspaces</td>
      <td style="text-align:left">String[]</td>
      <td style="text-align:left">The workspaces attached to this data source.</td>
      <td style="text-align:left">+</td>
    </tr>
  </tbody>
</table>

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "KinesisHttpInputRequest",
	"displayData" : {
		"name" : "First Kinesis backed HTTP Data 
Source",
		"description" : "Description of first Kinesis 
backed HTTP data source"
	},
	"contentType" : {
		"type" : "JsonContentType"
	},
	"computeEnvironment" : "bdb99c82-4874-4e41-b735-090cc53af71e",
	"ingestionEnvironment" : "c71ba158-8022-494e-84e1-e0623533ef1c",
	"storageConnection" : "f4376c08-1b13-495b-904f-768effa818da",
	"kinesisConnection" : "44a93a4b-5083-4f26-90cb-c3ea7284e3d3",
	"softRetention" : true
}' "https://api.upsolver.com/api/v1/data-source/"
```

## HTTP

Connect your stream using HTTP requests from any source.

Once you create the connection, you will be provided with an HTTP endpoint. Upsolver receives the data as POST, with the data in the body.

Headers sent with the request are also ingested as part of the stream, so metadata can be added to the request header.

#### Fields

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Optional</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">displayData.name</td>
      <td style="text-align:left">Name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source name.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">displayData.description</td>
      <td style="text-align:left">Description</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data source description.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">contentType</td>
      <td style="text-align:left">Content Format</td>
      <td style="text-align:left">ContentType</td>
      <td style="text-align:left">
        <p>The format of the messages. Supported formats are: JSON, AVRO, CSV, TSV,
          ORC, Protobuf and x-www-form-urlencoded.</p>
        <p>For self-describing formats like JSON, the schema is auto-detected. The
          body should contain of the message should contain the message itself, which
          should not be url-encoded.</p>
        <p>Messages can be compressed, Upsolver automatically detects the compression
          type.</p>
        <p>Supported compression types are: Zip, GZip, Snappy and None.</p>
        <p><b>See:</b>  <a href="content-formats.md">Content formats</a>
        </p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">computeEnvironment</td>
      <td style="text-align:left">Compute Cluster</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The compute cluster to run the calculation on.
        <br /><b>See:</b>  <a href="../../administration/managing-clusters/#adding-a-compute-cluster">Compute cluster</a>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">connectionPointer</td>
      <td style="text-align:left">Target Storage</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">The data and metadata files for this Data Source are stored in this storage.</td>
      <td
      style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">softRetention</td>
      <td style="text-align:left">Soft Retention</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">A setting that prevents data deletion when the retention policy in Upsolver
        activates. When enabled, the metadata is purged but the underlying data
        (e.g. S3 object) is not deleted.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">shards</td>
      <td style="text-align:left">Shards</td>
      <td style="text-align:left">Int</td>
      <td style="text-align:left">How many readers to use in parallel to read the stream. A recommended
        value would be to increase it by 1 for every 70 MB/s sent to your topic.</td>
      <td
      style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">retention</td>
      <td style="text-align:left">Retention</td>
      <td style="text-align:left">Int (Minutes)</td>
      <td style="text-align:left">A retention period for the data in Upsolver. After this amount of time
        elapsed the data will be deleted forever.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">endExecutionAt</td>
      <td style="text-align:left">End Read At</td>
      <td style="text-align:left">String (ISO-8601)</td>
      <td style="text-align:left">If configured, stop reading after this date.</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">workspaces</td>
      <td style="text-align:left">Workspaces</td>
      <td style="text-align:left">String[]</td>
      <td style="text-align:left">The workspaces attached to this data source.</td>
      <td style="text-align:left">+</td>
    </tr>
  </tbody>
</table>

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "KinesisHttpInputRequest",
	"displayData" : {
		"name" : "First Kinesis backed HTTP Data 
Source",
		"description" : "Description of first 
Kinesis backed HTTP data source"
	},
	"contentType" : {
		"type" : "JsonContentType"
	},
	"computeEnvironment" : "bdb99c82-4874-4e41-b735-090cc53af71e",
	"ingestionEnvironment" : "c71ba158-8022-494e-84e1-e0623533ef1c",
	"storageConnection" : "f4376c08-1b13-495b-904f-768effa818da",
	"kinesisConnection" : "44a93a4b-5083-4f26-90cb-c3ea7284e3d3",
	"softRetention" : true
}' "https://api.upsolver.com/api/v1/data-source/"
```

