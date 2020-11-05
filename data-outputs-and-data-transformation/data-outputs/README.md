---
description: >-
  This page provides an overview of the different data outputs that can be
  created in Upsolver.
---

# Data outputs

Upsolver supports sending data to various data outputs including Amazon Athena, Redshift Spectrum, Upsolver, and more.

## Storage

These data outputs enable you to write data to blob storage and continue processing in these systems \(e.g. send data to S3 then trigger notifications and send emails\).

#### Storage outputs options:

* [Amazon S3](amazon-aws-data-outputs/amazon-s3-output.md)
* [HDFS](hdfs-data-output.md)
* [Google Storage](google-storage-data-output.md)
* [Microsoft Azure](microsoft-azure-storage-data-output.md)

## [Amazon Athena](amazon-aws-data-outputs/amazon-athena-output/)

Athena is a managed query engine over the data stored in files in Amazon S3.  Through a configuration in the Glue Data Catalog \(a metastore that holds the metadata of the location and format of the files\), Athena is able to provide SQL access to the data.

Amazon Athena is a core data output that enables you to get your data into a data lake and query it in a cost-effective manner. After the data is organized, compacted, and stored in an Athena table on Amazon S3, you can run fast, cheap queries on the data lake. 

A queryable data lake is a useful step in the process as it allows you to inspect your data and run ad-hoc queries to understand your data \(using an SQL interface\) before writing to a database \(which is more expensive and requires a database\). Data is stored in parquet format; it is columnar and partitioned, thus enabling you to query only the data you need. 

There are also significant cost/speed benefits to using Athena as it only charges for data scanned \(e.g. $X per TB\). 

For example, a 100 MB compressed parquet file may include a GB of raw data. If you only query one out of the ten columns in the data file, you are only charged for scanning 10 MB of data. 

Athena also allows you to partition the data by date \(e.g. per year\). This date will appear as a column and can be added to your `WHERE` clause. Since Athena resolves this condition first and only scans the relevant partitions, this will further reduce the cost. 

Consider if you have stored 50 TB of data over two years at a rate of 50 GB of data a week:

* If you only need to query the past 5 weeks, you will be querying only 250 GB of data.
* If you only need to access a tenth of the columns, this means that you are only paying to access 25 GB.

As a result, you can pay just cents for a query instead of hundreds of dollars. This huge reduction in cost makes data that would have previously been too expensive to use now useable.

{% hint style="info" %}
Athena is a server-less architecture. If you require control of the servers, consider using Qubole.
{% endhint %}

{% page-ref page="amazon-aws-data-outputs/amazon-athena-output/" %}

## [Amazon Redshift Spectrum](amazon-aws-data-outputs/redshift-spectrum-output/)

Redshift Spectrum provides similar functionality to Amazon Athena at a similar cost. The data is stored in an Amazon S3 bucket that is connected to a Redshift cluster. Since the data is partitioned, any query looks in the relevant partition only. 

A Redshift Spectrum data output provides you with speedy and cost-effective access to data and is also useful for querying and joining data in S3 and a Redshift Spectrum DB.

{% page-ref page="amazon-aws-data-outputs/amazon-redshift-output.md" %}

## Streams

These data outputs enable you to stream your events to your Amazon Kinesis stream or Apache Kafka topic.

{% page-ref page="amazon-aws-data-outputs/amazon-kinesis-output.md" %}

{% page-ref page="kafka.md" %}

## Database

Database data outputs are used when projects require a specific database output.

One use case would be if you write all your data into staging tables, use periodic queries to aggregate the data, and then write this to the final data tables \(this follows an Extract Load Translate methodology\). You may then clear your staging tables periodically, preserving only the transformed data, ensuring that excessive storage is not required and controlling the costs. 

{% hint style="warning" %}
Given that the cost of a database is hundreds of times the cost of storing data in S3, it is important to plan your DB data outputs very carefully. 
{% endhint %}

A common scenario for customers moving to Upsolver is to store the raw data in one of the more cost-effective data sources, pre-aggregate the data, and then write the output to the smaller tables on the database.

Another use case would be storing log analytics in Elasticsearch, resulting in a fast-growing database with many duplicates. By deduping the data, it would be possible to make significant savings without losing any fidelity.

#### Database output options:

* [Amazon Redshift](amazon-aws-data-outputs/amazon-redshift-output.md)
* [Snowflake](database-data-outputs/snowflake-output/)
* [MySQL](database-data-outputs/mysql-output.md)
* [PostgreSQL](database-data-outputs/postgresql-data-output.md)
* [Microsoft SQL Server](database-data-outputs/microsoft-sql-server-data-output.md)
* [Elasticsearch](database-data-outputs/elasticsearch-data-output.md)

## [Upsolver](upsolver-output.md)

Upsolver is the data output for plain ETLs and is useful when you need to transform data and create a new data source with this transformed data. Typically this would include cleaning up and sanitizing data, ordering data, aggregating data, and/or splitting data into multiple streams. 

This sort of data output can be created as part of a pre-preparation process. Once the data source is created this can be duplicated and the output type can be switched.

{% page-ref page="upsolver-output.md" %}

## [Qubole](qubole-data-output.md)

Upsolver supports Qubole, a cloud-native data platform external system that provides you with managed clusters on various open sources systems such as Presto \(which is the engine under Athena\). 

With Qubole, you have control over the servers and can spin up additional servers if required. Qubole pricing is based on servers and not on data, making it more cost effective if you have huge volumes of data to query.

{% hint style="info" %}
**Note:** The output for Athena, Redshift Spectrum, and Qubole are all equivalent \(the files are stored and managed in the same way\).
{% endhint %}

{% page-ref page="qubole-data-output.md" %}

## [Lookup tables](lookup-table-output/)

Lookup tables are defined as a transformation like any other output, with the output being a key-value store that you can query to enable faster lookups \(e.g. to get all users who clicked on a specific ad in "real-time"\).

Lookup tables are useful for:

{% tabs %}
{% tab title="Join between streams" %}
By querying a lookup table, it is possible to enrich one stream with data from another stream.
{% endtab %}

{% tab title="Flattening data" %}
Given that storing data in a data lake is comparatively cheap, it may be useful to flatten relational data. 

This means that it is not necessary to consider joins when querying data, making it easier to extract the required data.
{% endtab %}

{% tab title="Real-time aggregations" %}
An Upsolver lookup table replaces ETL code and a serving DB like Redis or Cassandra. 

When a lookup table is defined as real time, instead of waiting until the data is written to S3 and to the disk, the event’s details \(the delta\) are updated directly in-memory and only then stored in S3. This can be useful in cases such as supplying data on a user in real-time while the user is browsing a website.
{% endtab %}
{% endtabs %}

{% page-ref page="lookup-table-output/" %}

