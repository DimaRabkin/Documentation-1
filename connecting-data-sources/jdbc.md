---
description: >-
  This article provides an introduction to JDBC along with a guide on how to
  create a JDBC data source in Upsolver.
---

# JDBC data source

{% hint style="info" %}
### What is JDBC?

Java Database Connectivity \(JDBC\) is an application programming interface \(API\) for the programming language Java, which defines how a client may access a database. It is a Java-based data access technology used for Java database connectivity and is part of the Java Standard Edition platform from Oracle Corporation.
{% endhint %}

Upsolver supports uploading data from the following JDBC sources:

* Microsoft SQL Server
* MySQL
* PostgreSQL
* Amazon Redshift
* Snowflake
* Oracle

Other databases can also be added. Please [contact Upsolver](https://www.upsolver.com/contact).

## JDBC data source connector CDC support

The JDBC data source has three operating modes for determining changes.

1. **By a timestamp column**
2. **By an auto-incrementing key**
3. **Capture the entire table periodically** \(mainly used for loading reference data periodically\)

Mode 1 and 2 require the table containing a column that Upsolver can query from to detect new changes. The column must be updated every time Upsolver reads the change to the given row. A combination of both mode 1 and mode 2 can be used together as well.

The JDBC data source default behavior performs a full initial load followed by incremental updates. 

## Create a JDBC data source

1. From the **Data Sources** page, click New.

2. Select **JDBC**.

3. **Name** this data source.

4. From the dropdown, select a **compute cluster** \(or [create a new one](../administration/managing-clusters/cluster-types/adding-a-compute-cluster.md)\) to run the calculation on. 

5. Select a **target storage connection** \(or [create a new one](../administration/connections/)\) where the data read will be stored \(output storage\).

6. Under **Parallelism**, enter in the number of independent shards to parse data, increase parallelism, and reduce latency. 

{% hint style="warning" %}
This should remain 1 in most cases and be no more than the number of shards used to read the data from the source.
{% endhint %}

7. Enter the **JDBC connection string**.

{% hint style="info" %}
**See:** [Connections](../administration/connections/) for more information on the string format for a specific connection type.
{% endhint %}

8. \(Optional\) Configure any **additional** **properties** necessary to make the connection.

9. Enter in the connection **username**.

10. Enter in the corresponding **password**.

11. Enter the name of the **table** to connect to.

12. \(Optional\) Identify an **incrementing column**. 

{% hint style="info" %}
This is a column that is always incrementing in value. 

Every time the data is ingested, it starts with the number following the last number loaded \(e.g. an ID column\). 
{% endhint %}

{% hint style="warning" %}
If you do not specify an incrementing column, Upsolver will automatically try and identify an incrementing column.
{% endhint %}

13.  \(Optional\) Identify any **timestamp columns**.

{% hint style="info" %}
This is a column with a timestamp. When the data source executes, it queries the data for rows with a more recent timestamp.

Multiple timestamp columns are also supported. If you specify multiple timestamp columns, the query uses the first non-empty time stamp that it finds. 
{% endhint %}

**Examples:** 

* If you have two columns `(time1, time2)` and a specific row only has an entry in `time2`, this will be used. 
* If there is an entry in both `time1` and `time2`, it uses the timestamp from `time1`.

{% hint style="info" %}
You can also specify both an **incrementing column** and **timestamp columns**.

In this case, it queries the data for rows with a more recent timestamp, or rows with a pre-existing timestamp but with an higher value in the incrementing column.
{% endhint %}

14. \(Optional\) Set a **read delay** \(in terms of seconds\) to provide a buffer for how far back in time to look in the data. 

{% hint style="info" %}
This can be useful in cases such as when the timestamp column is rounded to minutes, a read delay of 30 seconds can ensure that you do not miss any relevant rows.
{% endhint %}

15. \(Optional\) Enter the **full load interval**.

16. Click **Continue** to preview your data and review the following metrics:

* **Sample Size**
* **Parsed Successfully** 
* **\# of Errors**

17. \(Optional\) If there are any errors, click **Back** to change the settings as required.

18. Click **Create**.

{% hint style="success" %}
You can now use your JDBC data source.
{% endhint %}

