---
description: >-
  This page contains a global dictionary that contains descriptions of all the
  terms that may be encountered when using Upsolver.
---

# Index

| Terms | Component | Description |
| :--- | :--- | :--- |
| \# of Arrays | data source | The number of arrays in the selected hierarchy. |
| \# of Fields | data source | The number of fields in the selected hierarchy. |
| \# of Keys | data source | The number of keys in the selected hierarchy. |
| &lt;Database&gt; Connection | output property | Connection string of database connected to this output. |
| &lt;Storage&gt; Connection | output property | Connection string for storage location. |
| &lt;Type&gt; Connection | data source property | The connection string that represents a resource and its credentials. |
| Additional Kafka Properties | output property | Tags that can be sent to external monitoring systems. |
| Additional Processing Units for Replay | cluster property | Amount of processing units for replay tasks that run on a separate cluster up to this size, billed separately. If active, it is recommended for this cluster to be at least as big as the maximum size of the cluster. |
| Additional Schemas | Avro-record property | \(Optional\) Additional Avro record schemas. |
| Aggregated | output property | Whether or not this output is aggregated. |
| Aliases | output property | The lookup table alias. |
| Allow Maintenance Access | cluster property | Whether or not Upsolver is allowed to access your instances over SSH for maintenance purposes. |
| Attached Workspaces | data source property | The workspaces attached to the data source. |
| Attached Workspaces | output property | The workspaces attached to this output. |
| Avro Record Schema | Avro-record property | \(Optional\) The Avro record schema. |
| Bytes Parsers | Avro-record property | \(Optional\) A parser for JSON-format schemas. |
| Clusters | output property | Click to edit the output clusters. |
| Compaction Shards \# | output property | The number of files that can be compacted in parallel during a compaction. |
| Compression | data source property | The compression in the data \(Zip, GZip, Snappy, SnappyUnframed, Tar, or None\). |
| Compression | output property | The compression applied to the output \(None, GZip, or Snappy\). |
| Compute Cluster | data source property | Compute cluster this data source is running on. |
| Compute Cluster | output property | The compute cluster running the calculation. |
| Connection | output property | Connection type \(e.g. Athena\). |
| Connection | output property | Elasticsearch connection string. |
| Connection | moitoring systems property | The Elasticsearch connection. |
| Connection String | moitoring systems property | The connection string to connect InfluxDB. |
| Content Format | data source property | Content format of ingested data source \(Avro, Parquet, ORC, JSON, CSV, TSV, x-www-form-urlencoded, Protobuf, Avro-record, Avro with Schema Registry, or XML\). |
| Created By | data source property | Which user this data source was created by. |
| Created By | output property | Which user this output was created by. |
| Creation Time | data source property | Time this data source was created. |
| Creation Time | output property | Time this output was created. |
| Data Dump Date | data source property | The date that the data starts. |
| Data Sources | output property | The required data sources to base the output on. |
| Database Name | output property | Output database name. |
| Database Name | moitoring systems property | The database name. |
| Datadog API Key | moitoring systems property | The API key to access Datadog. |
| Date Format | output property | How output will be partitioned by time \(e.g. yyyy/MM/dd\). |
| Date Pattern | data source property | The date pattern of the files ingested. |
| Delay | data source | How far behind the system is processing the data, in minutes. |
| Delete Indices | output property | Delete indices from ElasticSearch based on retention period. |
| Delimiter | CSV property | The delimiter between columns of data. |
| Density in Data | data source | The density in the hierarchy, that is, how many of the events in this branch of the data hierarchy include this field, expressed a percentage. |
| Density in Events | data source | How many of the events in this data source include this field, expressed as a percentage \(e.g. 20.81%\). |
| Description | data source property | Description of data source. |
| Description | output property | Description of output. |
| Distinct Values | data source | How many unique values appear in this field. |
| DNS Alias | cluster property | DNS alias for private IPs. This is an alternative option to Elastic IPs. |
| Elastic IPs | cluster property | Whether or not Elastic IP is enabled. If enabled, Elastic IPs will be created for these servers. The server instances will use these Elastic IPs, allowing you to open access for your servers in external resources. |
| Enable gzip | moitoring systems property | Enable gzip compress for the HTTP request body. |
| End Read At | data source property | When to stop reading the stream. |
| Ending At | output property | Whether to continue processing indefinitely, stop processing as soon as possible, or stop on a specific date and time. |
| ETA | data source | The expected time of arrival of the data \(e.g. when the system is ingesting the data at about the same rate as the data is being generated, this will be less than a minute\). |
| Excluded Partitions | output property | The partitions to exclude. You can import, export, or edit the list. |
| Execution Parallelism | data source property | The number of independent shards to parse data, to increase parallelism and reduce latency. This should remain 1 in most cases. |
| Expose Private IPs | cluster property | Whether or not to expose the cluster with its private IP in the DNS record. |
| Extra Security Groups | cluster property | Security groups that can be added in addition to the default security groups created by Upsolver. |
| Fail on Write Error | output property | If enabled, any error while copying to the target will cause the load to fail. If disabled the same behavior will occur after 100K errors \(The max allowed by Redshift\) |
| Field Content Samples Over Time | data source | A time-series graph of the total number of events that include the selected field. |
| Fields Breakdown | data source | A stacked bar chart \(by data type\) of the number of fields versus the density/distinct values or a stacked bar chart of the number of fields by data type. |
| Fields Statistics | data source | A list of the fields in the hierarchy element showing the Type, Density, Top Values, Key, Distinct Values, Array, First Seen, and Last Seen. |
| File Name Pattern | data source property | The file name pattern. |
| Files Being Written | data source | Number of files currently being written from this data source to outputs. |
| First Seen | data source | The first time this field included a value \(e.g. a year ago\). |
| Folder | data source property | The data folder \(e.g. billing data\). If this is not specified, the data is assumed to be in the top-level of the hierarchy. |
| Header | CSV property | If applicable, the header of the file. If you only add details for one column, additional columns will be labeled as overflow columns. |
| Header | TSV property | If applicable, the header of the file. If you only add details for one column, additional columns will be labeled as overflow columns. |
| Hosts | cluster property | Add the following host/IP mappings to the hosts file. |
| Index Name | output property | Name of index output is written to. |
| Index Partition Size | output property | Size of index partition. |
| Index Type | moitoring systems property | \(Optional\) The type of the index. |
| Infer Types | CSV property | Whether or not to infer types. If not selected, Upsolver will read all fields as strings. |
| Infer Types | TSV property | Whether or not to infer types. If not selected, Upsolver will read all fields as strings. |
| Intermediate Storage | output property | Location where Upsolver stores the intermediate bulk files before uploading. |
| Intermediate Storage Location | output property | Where Upsolver stores the intermediate bulk files before uploading. |
| Interval | data source property | The sliding interval to wait for data. |
| Is Managed | moitoring systems property | True if you are using a managed Splunk account and False otherwise. This can be inferred from the URL of your account: splunkcloud.com usually means managed and cloud.splunk.com usually means self-service. |
| Kafka Hosts | output property | Comma-separated list of host:port pairs required to connect to Kafka cluster. |
| Kafka Topic | data source property | The Kafka topic. |
| Kafka Version | data source property | The Kafka version. |
| Kinesis Connection | output property | Connection string for Kinesis stream. |
| Last Seen | data source | The last time this field included a value \(e.g. 2 minutes ago\). |
| Main File | Protobuf property | \(Optional\) The main file from the list of selected schema files. |
| Max Delay | data source property | The maximum delay to consider the data, that is, any data that arrives delayed by more than the max delay is filtered out. |
| Max Elastic IPs Num | cluster property | Maximum number of available IPs. Leave empty for no limit. |
| Message Type | Protobuf property | \(Optional\) The message type. |
| Modified By | data source property | Which user last modified this data source. |
| Modified By | output property | Which user last modified this output. |
| Modified Time | data source property | If applicable, time this data source was last modified. |
| Modified Time | output property | If applicable, time this output was last modified. |
| Name | data source property | Data source name in Upsolver. |
| Name | output property | Output name in Upsolver. |
| Name | cluster property | Cluster name. |
| Name | moitoring systems property | The name of the monitoring report. |
| Namespace | moitoring systems property | The namespace — container for CloudWatch Metrics. |
| Null Value | CSV property | If applicable, the default null value in the data. |
| Omit Key Columns | output property | Whether or not to store the key columns in the lookup table. This saves space if enabled, but prevents iteration from returning the key columns. |
| Output Format | output property | File format for output. |
| Output Interval | output property | The output interval in minutes, hours or days. |
| Output Shards \# | output property | Set the number of files to be created each interval in the output. This applies only to aggregated outputs \(for non-aggregated outputs, the Shards configuration has this effect\). |
| Override Window Size | output property | If enabled, this feature can be set to minutes, hours, or days, or Infinite Override Size. For example, if you wish to create an hourly output that will aggregate data for the last day, then the output interval should be 1 hour, but override window size should be 1 day. This option is useful when used in combination with upserts. For example, if you want the latest total count of events per user, set the Override Window to infinite; in this case, every time an event arises for a user, the updated total count for the user is upserted, and the old record is deleted. |
| Partition Size | output property | The output partition size \(Hourly, Daily, Weekly, or Yearly\). |
| Password | moitoring systems property | The InfluxDB password. |
| Path | output property | The desired path for data to be exported to. If left empty, a system generated unique path will be used. |
| Pattern | data source property | The file pattern. |
| Prefix | data source property | The file prefix. |
| Private VPC | cluster property | Your private VPC connection. |
| Processing Units | cluster property | Amount of processing units. |
| Read From Start | data source property | Whether the stream was read from the start. |
| Real Time | output property | Load data into this lookup table directly from the input stream using a real time cluster if one is deployed. |
| Real Time Statistics | data source property | Whether the data source statistics are calculated in real-time directly from the input stream. This is relevant to lookup tables, when answers are required very fast and in real-time. |
| Region | cluster property | Your AWS region. |
| Region | moitoring systems property | The CloudWatch AWS region. |
| Reporting Tags | output property | Tags that can be sent to external monitoring systems. |
| Retention | data source property | The retention policy in Upsolver in minutes, hours, or days. The data is deleted permanently after this period elapses \(unless Soft Retention is set to Yes\). By default, the data is kept forever. |
| Retention | output property | The retention policy in Upsolver in minutes, hours, or days. The data is deleted permanently after this period elapses \(unless Soft Retention is set to Yes\). By default, the data is kept forever. |
| Retention Policy | moitoring systems property | \(Optional\) The retention policy in InfluxDB. |
| Run Compactions | output property | Whether to run compactions on the output. |
| S3 Connection | output property | S3 storage location where Upsolver stores the intermediate bulk files before uploading. |
| S3 Storage | output property | S3 storage location where Upsolver stores the intermediate bulk files before uploading. |
| Scaling Strategy | cluster property | Cluster's scaling strategy. |
| Schema | output property | Schema of this output. |
| Schema files | Protobuf property | \(Optional\) Click Select to choose the required schema files. |
| Schema Registry URL | Avro with Schema Registry property | \(Optional\) The URL to the schema registry. |
| Selected | data source | The most recent data values for the selected field and columns. You can change the columns that appear by clicking Choose Columns. |
| Server Units | cluster property | Server compute units; how many compute units one server will use. Choosing a server with "high memory" indicates a server type that has less CPU units but more RAM. |
| Shards | data source property | The number of shards, and the more shards the quicker the data processing. |
| Shards \# | output property | The number of independent shards to write, to increase parallelism and reduce latency. This should remain 1 in most cases, and should never be larger than the number of shards of the data sources. |
| Show Sparse Fields | data source property | Select to show fields with density under 0.01%. |
| SignalFx Auth Token | moitoring systems property | The auth token. |
| SignalFx Region | moitoring systems property | The region where your SignalFx environment runs. |
| Skip Failed Files | output property | If enabled, when a load fails the manifest of that load will be skipped. The skipped manifest will be saved aside for manual re-processing once the copy error has been fixed. |
| Soft Retention | data source property | A setting that prevents data deletion when the retention policy in Upsolver activates. When enabled, the metadata is purged but the underlying data \(e.g. S3 object\) is not deleted. |
| Soft Retention | output property | A setting that prevents data deletion when the retention policy in Upsolver activates. When enabled, the metadata is purged but the underlying data \(e.g. S3 object\) is not deleted. |
| Speed | data source | The speed at which the data is being ingested into the data source. |
| Split Root Array | JSON property | If the content is an array of JSON records, select to split the array content into separate records. |
| Splunk Deployment Name | moitoring systems property | The deployment name. For self-service accounts with a URL in the structureprd-p-xxx.cloud.splunk.com, the deployment name is: p-xxx. For managed accounts with a URL in the structure XXX.splunkcloud.com, the deployment name is: XXX. |
| Splunk HTTP Event Collector Token | moitoring systems property | The HEC token. Enables sending data over HTTP \(or HTTPS\) directly to Splunk Enterprise or Splunk Cloud. |
| Start Execution From | output property | When execution started. |
| Start Ingesting From | data source property | When ingestion started. |
| Store JSON as String | JSON property | Whether to store the JSON in native format in a separate field. |
| Store Raw Data | data source property | Whether to store an additional copy of the data in its original format. |
| Stream Name | data source property | The Kinesis stream name. |
| Stream Name | output property | Name of stream output is written to. |
| Table Name | output property | Output table name. |
| Tabular | output property | Whether or not the output is tabular. |
| Tags | cluster property | Assign custom metadata to your cluster using tags consisting of a key and a value, both of which you define. This is a convenient way to categorize your AWS resources in different ways \(e.g. by purpose, owner, or environment\). For example, you could define a set of tags for your account's clusters that helps you track each cluster's owner or identify a production cluster versus a testing cluster. It is recommended that you create a consistent set of tags to meet your organization requirements. |
| Target Storage | data source property | Where to store the data read \(the output storage\). |
| Topic Name | output property | Name of topic this output is written to. |
| Total Values | data source | The total number of values ingested for this field. |
| Unresolved Errors | data source | Number of unresolved errors stemming from outputs created from this data source. |
| Use SSL | data source property | Whether or not to use SSL. |
| User | moitoring systems property | The InfluxDB user. |
| Value Distribution | data source | The percentage distribution of the field values. These distribution values can be exported by clicking Export. |
| Window | output property | Window of time to keep in lookup table. |
| Workspaces | cluster property | The workspaces attached to this cluster. |
| Write Logs to Upsolver | cluster property | Whether or not to write logs to Upsolver's S3 environment. |
| Written Files | data source | Number of files written to outputs from this data source. |

