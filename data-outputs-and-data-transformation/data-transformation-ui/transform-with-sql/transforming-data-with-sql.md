---
description: >-
  This article goes over the various ways to transform your data with SQL in
  Upsolver.
---

# Transforming data with SQL

Transform with SQL enables the following stream transformations:

{% tabs %}
{% tab title="Filter a stream using the WHERE clause" %}
Filter your raw data structures such as user activity, IoT and sensors data, application activity data, and online advertisements statistics. 

These data sources will often contain more data than necessary for your analysis; Upsolver allows you to filter those data structures to have only the required data.
{% endtab %}

{% tab title="Join data from several data sources" %}
Combine data from multiple sources to gather deeper insights and create aggregated views. 

Upsolver allows you to perform this with a SQL statement, much like a relational database.
{% endtab %}

{% tab title="Perform calculations and conversions" %}
Improve the quality of your data and ensure it follows standard conventions \(convert time in **Epoch** to standard **`mm/dd/yyyy`**\). 

Upsolver contains all the functions that exist in SQL, including special enrichment functions \(e.g. IP2GEO, user agent parser\) and you can add your own UDFs in Python.
{% endtab %}
{% endtabs %}

Stream transformations are configured when creating an Upsolver output.

## Filter a stream using the `WHERE` clause

Transform with SQL can filter a stream using the `WHERE` clause just like in ANSI SQL.

#### For the following examples, assume that:

1. Three events stream into the data source `heartbeat` over time:

```sql
{ "user_id": 1, "device_id": 1234, "epoch" : 1520672112456, "heart_rate" : 81}
{ "user_id": 2, "device_id": 5567, "epoch" : 1520672112456, "heart_rate" : 79}
{ "user_id": 1, "device_id": 1234, "epoch" : 1520672113456, "heart_rate" : 102}
```

| user\_id | device\_id | epoch | heart\_rate |
| :--- | :--- | :--- | :--- |
| 1 | 1234 | 1520672112456 | 81 |
| 2 | 5567 | 1520672112456 | 79 |
| 1 | 1234 | 1520672113456 | 102 |

2. Three events stream into data source `location` over time:

```sql
{"user_id": 1, "epoch" : 1573034761, "latitude" : 28.545926, "longitude" : 31.577451}
{"user_id": 2, "epoch" : 1573034761, "latitude" : 44.032321, "longitude" : 1.356295}
{"user_id": 1, "epoch" : 1573035761, "latitude" : 28.545926, "longitude" : 31.577451}
```

| user\_id | epoch | latitude | longitude |
| :--- | :--- | :--- | :--- |
| 1 | 1573034761 | 28.545926 | 31.577451 |
| 2 | 1573034761 | 44.032321 | 1.356295 |
| 1 | 1573035761 | 28.545926 | 31.577451 |

#### Example 1:

The following query:

```sql
SELECT * 
FROM heartbeat
WHERE heart_rate > 80
```

Results in the following output:

| user\_id | device\_id | epoch | heart\_rate |
| :--- | :--- | :--- | :--- |
| 1 | 1234 | 1520672112456 | 81 |
| 1 | 1234 | 1520672113456 | 102 |

We have filtered the data source ֿֿֿ`heartbeat` to get only the events where `heart_rate` is bigger than 80.

#### Example 2:

The following query:

```sql
SELECT * 
FROM heartbeat
WHERE heart_rate > 79 AND heart_rate < 102 
```

Results in the following output:

| user\_id | device\_id | epoch | heart\_rate |
| :--- | :--- | :--- | :--- |
| 1 | 1234 | 1520672112456 | 81 |

We have filtered the data source ֿֿֿ`heartbeat` to get only the events where `heart_rate` is between 79 and 102.

#### Example 3:

The following query:

```sql
SELECT * 
FROM heartbeat
WHERE heart_rate > 79 OR user_id = 2 
```

Results in the following output:

| user\_id | device\_id | epoch | heart\_rate |
| :--- | :--- | :--- | :--- |
| 1 | 1234 | 1520672112456 | 81 |
| 2 | 5567 | 1520672112456 | 79 |
| 1 | 1234 | 1520672113456 | 102 |

We have filtered the data source ֿֿֿ`heartbeat` to get only the events where `heart_rate` is greater than 79 **or** has `user_id` equal to 2.

## Join data from several data sources

You can use Transform with SQL to combine data from your streaming data source with data arriving in other streams, historical aggregations, or reference data files by using the `JOIN` syntax. 

The result of the Transform with SQL join is a new table that is populated with the column values that you specify in the `SELECT` statement.

With Transform with SQL, there is no need to write code in any programming language such as Java or Python to join data from various data sources—all you need is to use the Transform with SQL `JOIN`.

### **`JOIN` clause:**

Transform with SQL `JOIN` clause uses the following syntax:

```sql
[ { INNER | LEFT [ OUTER ] } ] JOIN [ LATEST ]
    { table_name  ( query_expr ) } [ [ AS ] alias ] [ WAIT integer { MINUTE[S]  HOUR[S]  DAY[S] } [ ALIGNED ] ]
    { ON bool_expression | USING ( field_name [, ...] ) }
```

For the following example, assume that we have the following events structure in a data source **clicks** over time:

```sql
{"user_id" : 1, "campaign_id" : "camp1"}
{"user_id" : 2, "campaign_id" : "camp2"}
```

| user\_id | campaign\_id |
| :--- | :--- |
| 1 | "camp1" |
| 2 | "camp2" |

Also assume that we have the following events in a data source **orders** over time:

```sql
{"user_id" : 1, "credit_card_type" : "VISA", "order_price" : 150 }
{"user_id" : 1, "credit_card_type" : "VISA", "order_price" : 50}
{"user_id" : 2, "credit_card_type" : "AMEX", "order_price" : 20}
```

| user\_id | credit\_card\_type | order\_price |
| :--- | :--- | :--- |
| 1 | "VISA" | 150 |
| 1 | "VISA" | 50 |
| 2 | "AMEX" | 20 |

If we define a table as:

```sql
SELECT user_id, campaign_id
FROM clicks JOIN (SELECT COUNT_DISTINCT(*) as user_orders,
User_id AS user_id
    FROM orders
    Group by user_id) user_purchases
    ON user_purchases.user_id = user_id
```

We will have the following table as output:

| user\_id | campaign\_id | user\_orders |
| :--- | :--- | :--- |
| 1 | "camp1" | 2 |
| 2 | "camp2" | 1 |

### **Join requirements:**

{% tabs %}
{% tab title="Join table" %}
The join table must be either a lookup table or reference data.
{% endtab %}

{% tab title="ON statement" %}
The `ON` statement must be in one of the following forms:

* `lookup_key_1 = expression AND lookup_key_2 = expression ...`
* `lookup_key_1 IN (expression1, ...) AND lookup_key_2 IN (expression1, ...) ...`

{% hint style="info" %}
**Note:** Each key in the lookup table must be mapped to one or more expressions using either **`=`** or **`IN`** within the `ON` statement.
{% endhint %}
{% endtab %}
{% endtabs %}

### **Synchronize streams:**

Since Upsolver is a streaming system, all joins are applied in stream time. We will illustrate how to use the following:

* \`\`[`WAIT`](transforming-data-with-sql.md#wait-interval)\`\`
* \`\`[`ALIGNED`](transforming-data-with-sql.md#aligned)\`\`
* \`\`[`LATEST`](transforming-data-with-sql.md#latest)\`\`

To demonstrate the concepts, assume we have the following data sources:

{% tabs %}
{% tab title="main data source" %}
| id | time |
| :--- | :--- |
| 1 | 14/10/2019 00:00 |
| 1 | 14/10/2019 00:01 |
| 1 | 14/10/2019 00:02 |
| 1 | 14/10/2019 00:04 |
| 1 | 14/10/2019 05:00 |
{% endtab %}

{% tab title="lookup data source" %}
| id | time | value |
| :--- | :--- | :--- |
| 1 | 14/10/2019 00:00 | 1 |
| 1 | 14/10/2019 00:01 | 2 |
| 1 | 14/10/2019 00:02 | 3 |
| 1 | 14/10/2019 05:00 | 4 |
{% endtab %}
{% endtabs %}

For the above data sources:

* `id` is an **integer**
* `time` is a **timestamp** in **`DD/MM/YYYY HH:MM`** format 
  * represents the event's creation time

#### **`WAIT` interval**

In order to synchronize between streams, Transform with SQL supports the `WAIT integer { MINUTE[S] HOUR[S] DAY[S] } [ ALIGNED ]` syntax.

If `WAIT X MINUTES` \(where `X` is an **integer**\) is specified, Upsolver ensures that the state of the joined look-up table is ready `X` minutes ahead of the data being processed. This will cause the output to be delayed by `X` minutes.

We will demonstrate this using the following SQL query:

```sql
SELECT id,				
	   value,
	   Time
From "main data source"
LEFT JOIN LATEST
	(
	  SELECT id, LAST(value) value
	  FROM "lookup data source"
	  GROUP BY id
	) l WAIT 1 MINUTE
	ON l.id = id
```

The result of this query is as follows:

![](https://docs.upsolver.com/Content/Resources/MarkdownConversion/UpSQL/TransformingData/images/Join-Data1.png)

Note that while performing the `JOIN`, we wait 1 minute for each event in **`main data source`** before creating the output. 

If we look at the first row in the above table, we can see that for time **`14/10/2019 00:00`** we take into consideration only the first event in **`lookup data source`** which has the same value in the time field—that event arrived in `1 MINUTE` delay. 

This is the behavior since for each event in **`main data source`**, we look at the matching events in **`lookup data source`** which has values in their time field which are less than `14/10/2019 00:00` plus 1 minute \(due to `WAIT 1 MINUTE` statement\) which results in `00:01` as a time comparator. The only event which complies with this comparator is the first event in **`lookup data source`** which has `00:00` in its time field. 

Without using `WAIT 1 MINUTE`, the result would be:

![](https://docs.upsolver.com/Content/Resources/MarkdownConversion/UpSQL/TransformingData/images/Join-Data0.png)

If we look again at the first row in the above table, we can see that for time `14/10/2019 00:00`, we have no event with time prior to `14/10/2019 00:00` \(excluding this timestamp itself\). 

As such, since we did not use the `WAIT` statement, for the timestamp `14/10/2019 00:00` in **`main data source`**, ****we will look for matching events in **`lookup data source`** with time less than `14/10/2019 00:00`. Since such an event does not exist, the value is null.

#### **`ALIGNED`**

If the keyword `ALIGNED` is used, calculating the query's result will wait for the next aligned window. For example, data arriving after `08:35` and before `08:40` will wait until `08:40`.

The alignment is done using unix epoch time, so `WAIT 1 DAY` will wait until `00:00 UTC` of the following day.

We will demonstrate this using the following Transform with SQL query:

```sql
SELECT id,				
	   value,
	   Time
From "main data source"
LEFT JOIN
	(
	  SELECT id, LAST(value) value
	  FROM "lookup data source"
	  GROUP BY id
	) l WAIT 5 HOURS ALIGNED
	ON l.id = id
```

The result of this query is the following:

![](https://docs.upsolver.com/Content/Resources/MarkdownConversion/UpSQL/TransformingData/images/Join-Data2.png)

Note that while performing the join, we wait 5 hours to be aligned before creating the output. This means that for every event in our **`main data source`**, we would wait for the event on `14/19/2019 05:00` to create the output. That is why the **`value`** column in the output has the value 4 for all of the events.

#### **`LATEST`**

When running a query over historical data, Upsolver maintains the time relation between streams the same way that it would when processing data that is up to date. 

The `LATEST` keyword is intended to handle situations where initial data is dumped into a lookup table after the source stream started running. This forces the query to use the state of the joined lookup table that exists when it is run for all historical data. Data that arrived after the query was run will not be affected by `LATEST`. 

We will demonstrate this using the following Transform with SQL query:

```sql
SELECT id,				
	   value,
	   Time
From "main data source"
LEFT JOIN LATEST
	(
	  SELECT id, LAST(value) value
	  FROM "lookup data source"
	  GROUP BY id
	) l WAIT 1 MINUTE 
						ON l.id = id 
```

The result of this query depends on the time you run it relative to the event's time.

If the query run time is less than the event’s creation time field \(e.g. if you run the query on `13/10/2019 09:00`\), the result is:

![](https://docs.upsolver.com/Content/Resources/MarkdownConversion/UpSQL/TransformingData/images/Join-Data3.png)

If the query run time is greater than the event’s creation time, we relate to the query's run time instead of the event creation time field. For example, if you run the query on `15/10/2019 09:00`, the result is:

![](https://docs.upsolver.com/Content/Resources/MarkdownConversion/UpSQL/TransformingData/images/Join-Data4.png)

## Perform calculations and conversions

Transform with SQL enables you to improve the quality of your data and ensure it follows standard conventions \(e.g. convert time in Epoch to standard `mm/dd/yyyy`\).

Upsolver contains all the functions that exist in SQL as [built-in functions](../../../getting-started/glossary/language-guide/sql.md), including special enrichment functions \(e.g. IP2GEO, user agent parser\), and you can also add your own [User Defined Functions](../../../administration/python-udf.md) \(UDFs\) in Python.

{% hint style="info" %}
Built-in functions and UDFs can be applied on either flat or hierarchical data.  
**See:** [Query hierarchical data](query-hierarchical-data.md)
{% endhint %}

#### **For the following examples, we will assume that:**

1. Three events stream into the data source `heartbeat` over time:

```sql
{ "user_id": 1, "device_id": 1234, "epoch" : 1520672112456, "heart_rate" : 81}
{ "user_id": 2, "device_id": 5567, "epoch" : 1520672112456, "heart_rate" : 79}
{ "user_id": 1, "device_id": 1234, "epoch" : 1520672113456, "heart_rate" : 102}
```

| user\_id | device\_id | epoch | heart\_rate |
| :--- | :--- | :--- | :--- |
| 1 | 1234 | 1520672112456 | 81 |
| 2 | 5567 | 1520672112456 | 79 |
| 1 | 1234 | 1520672113456 | 102 |

2. Three events stream into data source `location` over time:

```sql
{"user_id": 1, "epoch" : 1573034761, "latitude" : 28.545926, "longitude" : 31.577451}
{"user_id": 2, "epoch" : 1573034761, "latitude" : 44.032321, "longitude" : 1.356295}
{"user_id": 1, "epoch" : 1573035761, "latitude" : 28.545926, "longitude" : 31.577451}
```

| user\_id | epoch | latitude | longitude |
| :--- | :--- | :--- | :--- |
| 1 | 1573034761 | 28.545926 | 31.577451 |
| 2 | 1573034761 | 44.032321 | 1.356295 |
| 1 | 1573035761 | 28.545926 | 31.577451 |

We will use the built-in function `UNIX_EPOCH_TO_DATE` which converts unix epoch date to a date as follows:

![UNIX\_EPOCH\_TO\_DATE examples](https://docs.upsolver.com/Content/Resources/MarkdownConversion/UpSQL/TransformingData/images/Perform-Calculations0.png)

The following query creates an output which is based on a stream transformation using `UNIX_EPOCH_TO_DATA` in the `SELECT` clause:

```sql
SELECT user_id, device_id, UNIX_EPOCH_TO_DATA(epoch) as date
FROM heartbeat
```

The result of the query will be the following output:

| user\_id | device\_id | date |
| :--- | :--- | :--- |
| 1 | 1234 | "2018-03-10T08:55:12.456Z" |
| 2 | 5567 | "2018-03-10T08:55:12.456Z" |
| 1 | 1234 | "2018-03-10T08:55:13.456Z" |

The following query creates an output which is based on a stream transformation using `UNIX_EPOCH_TO_DATA` in two steps:

1. Calculate the transformation:

```sql
SET human_readable_date = UNIX_EPOCH_TO_DATA(epoch);
```

2. Use the calculated transformation in the query:

```sql
SELECT user_id, device_id, human_readable_date
FROM heartbeat
```

