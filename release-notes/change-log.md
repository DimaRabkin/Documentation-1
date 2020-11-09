---
description: This article tracks the changes and updates to Upsolver.
---

# Change log

## 2020

## 2020/11/08
 * QuboleClient: fix a bug in partition values with zero leading
 * SQL: Support DELETE WHERE syntax for Is Delete Field in Hive output with upserts
 * API: Fixed a bug with adding filter in aggregated output
 * Record To Json Function: Bug fixes
 * Cluster syncronization: Stability fixes
 * Hive output: Fixed a bug that caused the output to stuck after an edit
 
### 2020/11/01

* Deployment: Allow deploy Upsolver servers to Azure
* Add support for Azure EventsHub data source
* Athena: Create Glue database if doesn't exist
* Functions: Fixed a bug in TO\_DATE function
* Function: Added new function: RECORD\_TO\_JSON
* Query Cluster: Improvements in the underlying files cache
* SQL: Show validation error when mapping an array to unrelated path
* SQL: Show validation error when mapping null without specifying type
* API: When creating data source, fixed a bug when previewing large file with tar compression
* API: Fixed high CPU on boot

### 2020/10/21

* Kafka data source: support reading custom kafka headers
* Metastore Ouptut: support running Athena/Qubole output without partitioning by time
* Snowflake Output: support Azure storage as the intermediate storage
* Compute Cluster Infra: optimize threads when running low priority tasks
* ETL: Improved target path inference for some scenarios
* Monitoring Task: fixed failure when one of the monitoring reporters is not avaiable
* SQL: Fixed validation of inline functions in aggregations
* Metastore Output: set the table location to the root path of the output
* Qubole: allow defining if TIMESTAMP fields will be created as TIMESTAMP or BIGINT columns in the table per output
* Qubole: Added feature flag to deprecate the "SET hive.on.master=?" statement
* Elasticsearch Output: Fixed a bug that could cause high memory usage

### 2020/10/15

* Add Amazon AppFlow support
* Zip Function- Added optional field names
* Api - Fixed validation message for Kafka input
* Elastic Search - upgraded client version

### 2020/10/13

* S3 Data source with Parquet Content Format - when the file is not a parquet file, handle it as a parse error
* Added Free plan
* SQL - Fixed a duplication issue when function target name and select target name are the same
* Hive Metastore Output with Upsert keys - Trigger compactions in a better way to avoid compacting in a loop
* SQL - Fixed target path inferrence of key columns with inline functions on aggregated outputs
* API - Allow setting higher number of shards in the output than number of execution parallelism in the data source. This will parallel the data by the data source files
* Support "SELECT \* " in cloud storage outputs with parquet content format
* API - Fixed a bug that allowed creating more than one draft in the same output

### 2020/10/05

* Show number of sparse fields inside fields tree in inputs and outputs and allow to toggle the filter

### 2020/10/01

* Jdbc data source: use field types from the table definition
* PostgreSQL output: support timestamptz data type
* UI: New modal when adding multiple fields in tabular outputs to prevent cartesian product between unrelated arrays
* No need to specify a target field for filters when creating a filter from the UI
* Some bug fixes in API

### 2020/09/30 - SNAPSHOT

* Query Agent - Support round robin
* "No Local API" page - Show "Connection Established" instead of error when able to connect
* Input creation preview - Filter big JSONs and let the user know about it

### 2020/09/23

* Performance improvements in internal cache mechanism 
* Performance improvements in Hive Metastore outputs Raw Blame 
* Fixed bug that caused Hive Metastore outputs with upserts to stuck after editing a new version 
* Avro w/ Schema Registry Content Format: Support Tagged Avro Schema Registry 
* Improved target path calculation of inline functions 
* Added validation when deploying a draft that the start time is not after the end time of the previous version 
* SQL: Disable automatic column name generation 
* Support cancelling pending integration 

### 2020/09/14 

* No Local API Page: Fixed showing "You can't connect" instead of "local DNS resolve" error 
* CloudFormation: link to the right region in deploy stack 
* Less API Calls to Cloud Storage in order to check completion of tasks 
* Calculated Function `TO_DATE`: Changed threshold to not return negative dates 
* Fixed bug with PostgreSQL outputs not allowing to alter the column types 

### 2020/09/07 

* Support Workspaces in Clusters 
* Catch all errors from GCP / Azure and show in UI 
* Hive Metastore Outputs: the column names `year`, `month`, `day`, and `hour` are now reserved 

### 2020/08/31 

* Big performance improvements for replay in Kinesis & Kafka Data Sources 
* Big performance improvements for replay in Hive Metastore Outputs 

### 2020/08/24 

* Compute Cluster: IO Tasks will now run only on Master cluster and will never run on Replay Cluster 
* Compute Cluster: Option to limit number of Elastic IPs allocated for the cluster 
* Added `XX_HASH` and `SORT_BY` calculated functions 
* UI : Support literal inputs in aggregations 

### 2020/08/17 

* Performance improvements to Hive Metastore Outputs 
* Fixed bug with very large parquet file outputs used to make servers crash on OOM 
* Preview Output will now stop after 15 seconds instead of making the API server hang 
* Support Redshift and PostgreSQL in JDBC Data Source 
* UI: Output - New Partitions Modal 

### 2020/08/10 

* SQL now supports target site inference, this fixes a lot of confusing bug when using arrays with calculated functions 
* SQL: Fixed bug with throwing 500 errors on missing properties of calculated functions 
* Athena Output: new outputs will not nest compaction files for better compatibility support with external systems 

### 2020/08/03 

* Fixed bug when previewing completed Output with Lookups 
* Update Retention validation message is now dismissible 
* Regex and Split Content Formats have been added for better compatibility with custom data formats 

### 2020/07/27 

* MS SQL Server Output 
* Elasticsearch Output: Removed `index_type` argument, using `_doc` / `doc` by default 
* UI: overhauled the properties pages 
* UI: Split field statistics by Data Source in Output page 

### 2020/07/20 

* `JSON_TO_RECORD` calculated functinon: Allow whitespace in CSV mapping definition and improve exception handling 
* Athena Output: Faster replays when run compactions is set to false 
* Less red notification errors due to internal errors 
* Aggregated Outputs now delete the intermediate aggregations immediately after outputing the data \(instead of waiting to the retention period, if defined\) 

### 2020/07/13 

* MySQL Output: Fixed bug with quote followed by delimiter char inside the data to output 
* Create Calculated Function: Fixed a bug with the default output path calculation 
* JDBC Data Source now supports creating new tables instead of only inserting data to existing tables 
* JDBC Connections: indicative validation error messages on creation 

### 2020/07/06 

* PostgreSQL Output 
* Writing logs to Customer Bucket now supports writing to specific path in the customer's bucket 
* SQL: Show indicative error when trying to filter subquery 
* MySQL Output: Fixed writing of date/time fields 
* UI: Refined the time range picker 
* New boolean operators and calculated functions: `AND`, `OR`, `NOT`, and `IS DISTINCT FROM` now works like in SQL 
* UI: Calculated Functions Gallery now matches to the SQL syntax 

### 2020/06/29 

* Redshift: Support configuring 
* Added `TO_DATE` calculated function \(converts strings to dates without having to insert format\) 
* Added `APPROX_COUNT_DISTINCT_EACH` aggregation 
* IAM Role Credentials: Assume role via the Server Role created in the AWS Integration 
* Booting a Cluster after stopping it for a while is faster 
* SQL: infer null type instead of asking the user to explicit insert the type of the null \(`null:string`\) 
* SQS: Allow configuring KMS key 
* UI: Fixes to "Add Lookup to Data Source" page 
* S3: Show the right action on access error

### 2020/06/22 

* UI: Charts now shows shared crosshair between graphs 
* "Update Shards" error message is now more informative 
* Added deployment support to more AWS regions 
* Fixed rare case where AWS Redshift Output would duplicate data 
* Fixed bug where multiple rows with the same Upsert Key would insert in the same output interval in Snowflake and Redshift Upsert Outputs 

### 2020/06/15 

* Git Integration: Don't cancel git integration after one failure to push changes 
* UI now allows operating aggregated outputs without key columns \(Aggregate all data within the output interval\) 
* UI: Refinments in the Fields Tree 
* Snowflake Output: Better replay performance with sparse Data Sources 
* Added `EXTRACT`, `MILLISECOND`, `SECOND`, `MINUTE`, `HOUR`, `DAY`, `DAY_OF_MONTH`, `DAY_OF_WEEK`, `DAY_OF_YEAR`, `WEEK`, `MONTH`, `QUARTER`, `YEAR`, and `YEAR_OF_WEEK` date extraction calculated functions 
* Fixed bug with `REPLACE` calculated function could throw errors in some cases 

### 2020/06/08 

* Added `RPAD`, `LPAD`, `STRPOS`, `DATE_ADD`, and `DATE_DIFF` calculated functions 
* Private API now uses `r5` instead of `r4` instances in AWS by default 
* SQL: Better error messages for inline features 

### 2020/06/01 

* The "Archive" operation has removed from the System, Deleted items can be seen using the "Trash" button in the list view 
* JDBC Data Source: Support Start Time 
* Multiple Bug Fixes in Snowflake Output 
* Added `DATE_TRUNC` calculated function 
* Fixed bug with copying big files in S3 
* UI Performance enhancements 

### 2020/05/25 

* Update Configuration of Upsert Outputs using the UI 
* Allow writing logs from Upsolver to Customer requested location as well as Upsolver 
* Reduced dramatically the number of API class to Cloud Storage

### 2020/05/18

* Performance improvements and bug fixes

### 2020/05/04

* Data Sources:
  * JDBC: Added support for connecting to an Oracle DB
  * Bug fix for event type statistics breakdown in local APIs
  * Performance and cost improvements

### 2020/04/27

* Revised output preview screen
* Minor bug fixes and improvements

### 2020/04/20

* Data Sources:
  * S3 Over SQS: Allow creating Data Sources from multiple connections with the same prefix
* Outputs:
  * Added output to Snowflake
  * Monitoring improvements

### 2020/04/06

* Data Sources:
  * Added properties to Upsolver data source.
  * Kafka: Added support for custom consumer/producer properties.
* Outputs:
  * UI improvements in sources fields tree
  * Kafka: Added support for custom consumer/producer properties.
* Monitoring Repots:
  * Added Splunk export support

### 2020/03/30

* UI updates and performance improvements

### 2020/03/16

* Data Sources:
  * Split meta-data by Event Type field - you are now able to split and view your data source by the desired field in your data source.
* Outputs:
  * SELECT \* is supported for Upsolver and Elasticsearch outputs.
  * Added Amazon Kinesis connector.
  * Qubole connector now supports using an HTTPs proxy address to override the endpoint used to access Qubole.
* IAM:
  * Added support for SAML with provisioning capabilities.

### 2020/03/09

* Clusters:
  * Compute cluster monitoring: Compute Units Graph was updated and now provides a breakdown of the compute units used by each task \(Data Source/Output/Lookup Table\).

### 2020/02/24

* Outputs:
  * Elasticsearch: Editing the connection string is now supported - as long as the new nodes belong to the same cluster.
  * Elasticsearch: Added support for setting the event to \_doc.

### 2020/02/18

* Transform with SQL:
  * Added support for partitioning configuration.
  * Casting improvements.
* Outputs:
  * Redshift: Added support for configuring fail on write error. If enabled, any error while copying data to Redshift will cause the entire bulk to be skipped. The skipped manifest will be saved aside for manual re-processing once the copy error has been fixed. If disabled the same behavior will occur after 100K errors \(The max allowed by Redshift\).
* Monitoring Reporting:
  * A bug caused false reported delay \(in rare cases\) was fixed.

### 2020/02/10

* Data Sources:
  * JDBC Data Source - added support for PostgreSQL.

### 2020/02/05

* Outputs:
  * Added UUID Generator Calculated Function
* Transform with SQL:
  * Added support for SQL comments using `--` \(see example below\)
  * Improved error messages

```sql
SELECT your_Select_clause -- your comment
FROM your_table -- another comment
```

### 2020/01/30

* Data Sources:
  * Parquet reader: support INT96 timestamps and non-canonical field names
  * Added support for LZO decompression
  * Added a JDBC connector
* Outputs:
  * Support correcting a specific time frame in an output
  * Added UpdateSql programmatic API operation for creating outputs

### 2020/01/22

* IAML
  * Multi-organization support
* Outputs:
  * Support lazy load of lookup tables
  * Support querying lookup table in SQL
  * Support sharding of aggregated outputs
* Data Sources:
  * Support S3 data source initial load configuration
  * Support non-lexicographic date patterns in S3
  * UI & performance improvements

### 2020/01/13

* Data Sources:
  * Support XML as content type

### 2020/01/06

* Performance improvements and bug fixes

## 2019

### 2019/12/22

* Outputs:
  * Elasticsearch - Add option not to delete indices from Elasticsearch based on retention
* Transform with SQL:
  * Support data source features
* UI:
  * Outputs - Add support for filtering the Preview when in SQL mode
  * Performance improvements

### 2019/12/16

* Data Sources:
  * Support changing the number of shards using increments of one \(instead of multiplies of two\)
* Outputs:
  * Athena - add support for excluding partitions from the table
* Transform with SQL:
  * Support default field names instead of col\_x
  * Generate SQL for running Outputs
  * Refer to fields by index in the GROUP BY statement

### 2019/12/09

* UI improvements and bug fixes

### 2019/12/03

* Outputs:
  * Add support for Redshift Spectrum
  * Update table schema in Qubole is now optional \(the default behavior would be to update\)

### 2019/11/17

* Outputs:
  * Allow switching between raw and aggregated modes
  * Added QUERY\_STRING\_TO\_RECORD calculated function for query string extractions
* Transform with SQL:
  * Unify SQL code blocks into a single block

### 2019/11/10

* Athena Upserts: Update and delete existing data in your Data Lake
* Transform with SQL:
  * Support having statement in Aggregated Outputs
  * Support DECIMAL types
  * Support Athena Upserts
* S3 Output: JSON files will end with one "\n" instead of two "\n" \(as stated in jsonlines.org\)

### 2019/10/31

* When deploying an output, "Now" is resolved when submitting the form
* Connections and Clusters can be attached to Workspaces
* IAM: Lists of Data Sources, Outputs, Lookup Tables, Connections and Clusters are filtered by the user "list" permission

### 2019/09/23

* UI improvements
  * Fixed bug on lookup to COLLECT\_SET\_EACH column
* Stability improvements

### 2019/09/02

* Allow changing default organization connection
* Added decimal support to Athena Outputs
* Allow turning off/on compactions in Athena Outputs
* Better support for Data Sources with large amounts of fields
* Notebook \(Beta\)

`JOIN`

`GROUP BY`

`HAVING`

### 2019/07/08

* Various Performance Improvements in UI
* Added ZIP Calculated Function to ZIP between multiple arrays
* MySQL Output: Row is replaced if duplicate key is found
* Notebook \(Beta\)

`like / not like syntax (e.g. “name” like ‘a__%’)`

`not in syntax (e.g. “status” not in (“failed”, “canceled”))`

`= as equality operator syntax (e.g. “status” = ‘ok’ instead of “status” == ‘ok’)`

* Better error messages

### 2019/06/24

* Lookup Tables / API Playground
* Support querying multiple rows
* Auto complete for keys
* Querying on specific time range
* Notebook \(Beta\): a better way to create enrichments

### 2019/06/17

* Calculated Functions: Added numeric in feature \(e.g. “data.a”:number in \(1,2,3\)\)
* Parse Avro data using Confluent Schema Registry

### 2019/06/03

* Various Performance Improvements in UI
* Show connection errors when creating/editing MySQL/Redshift Output
* Fixed intermittent recoverable errors in tasks
* Fixed delay when using the same connection for multiple Redshift/Elasticsearch Outputs

### 2019/05/26

* Experimental: updating / deleting rows in output to Athena, you can try it out by using the “Upsert Key” and “Is Delete Field” special fields

### 2019/05/19

* Ingestion - Added “index” header to all messages \(useful when ingesting multiple events in one message\)
* Hive Metastore Outputs now drops duplicate logical partitions
* API - list Output / Materialized Views returns faster
* GDPR - Materialized Views now supports deleting rows
* Physical Deletion runs much faster with fewer operations on the underlying Cloud Storage
* Retention is now set on Materialized Views created by DEDUP features

### 2019/05/14

* Data Source - Simplified creation of Kafka, Kinesis and AWS S3 Data Sources

### 2019/05/13

* Replay Cluster - Fixes some cases where the replay cluster might not shut down

### 2019/05/06

* Qubole Client - set hive.on.master and use database for all queries
* Performance improvements for retention
* Elasticsearch Output - Better retry mechanism

### 2019/04/22

* Athena - Switch to using Glue API for all DDL statements
* Monitoring Tab - fix bug that would display some rows twice
* Outputs page - Correct the range of some of the graphs
* Add timeout to copy/read S3 requests to prevent processing delays
* Data Source - show a preview of data immediately upon creation
* Improve UI performance related to connections page

### 2019/04/08

* Dry run environment support
* Monitoring - added written items and written bytes
* Monitoring - added original-task-name tag to all metrics
* Qubole - set hive.on.master=false
* Permissions - added policy editor
* Athena - reduce spam of Athena history
* Athena - drop table when deleting an output if the option is selected
* Kafka - support changing the number of shards in the UI
* Some performance improvements
* UI - Added multi-unmap fields \(for Avishai\)

### 2019/04/01

* Increase Kafka consumer version to 2.1.1
* Monitor delay in managing partitions
* Bug fix - add connection timeout to ElasticSearch connections
* Remove dependency on Upsolver DynamoDB for servers starting up

## 2018

### 2018/11/15

* Data Sources / Materialized Views / Outputs: Toggle between card view and table view

### 2018/11/14

* Translate Calculated Function: Show CSV Editor for the dictionary field
* Cluster Details Page: show the elastic IPs of the Cluster
* Outputs: Qubole Output
* Outputs: Usability Improvements in Creation/Deploy flow
* Upsolver Language: `"data.str":string in ('a','b','c')` syntax
* Upsolver Language: supports coalesce operator

`"data.str":string? # COALESCE("data.str":string, '')`

`"data.str":string?'default-value' # COALESCE("data.str":string, 'default-value')`

`"data.bool":boolean? # COALESCE("data.bool":boolean, false)`

`"data.bool":boolean?true # COALESCE("data.bool":boolean, true)`

`"data.number":number? # COALESCE("data.number":number, 0)`

`"data.number":number?2.5 # COALESCE("data.number":number, 2.5)`

### 2018/06/26

* Output / Materialized Views: Added ability to edit the Data Sources from the properties tab \(Only if the object isn't deployed yet\)

### 2018/06/18

* Aggregated Output: Added option to add calculated fields over aggregations

### 2018/06/17

* Compute Cluster: Allow to spin up "Replay" Cluster when needed
* Outputs: Edit S3 and Upsolver Outputs
* Filters: Improved UX \(Whitelist and Blacklist Filters\)
* Materialized Views: Time Series Aggregations are shown as graphs in the Data Sample tab

### 2018/03/01

* Materialized Views: Added an API to iterate the MVs
* Added Time Zone Offset Function
* Outputs: Added automatic time field to Athena and Upsolver outputs
* Calculated Fields: Support editing of calculated fields inputs and parameters
* Users can now create readonly S3 Connections
* Athena Output now supports setting of event time which is used for partitioning
* Elasticsearch Output now supports retention
* Various performance improvements to UI
* Support filtering on time range in Data Source inspection page
* Support for editing lookup enrichments
* Monitoring now shows Materialized Views that are used in Lookup enrichments
* Improvements to Auto Scaling
* Support non string Key Columns in Materialized Views
* Aggregated output doesn't change the type of the Key Columns to string anymore

