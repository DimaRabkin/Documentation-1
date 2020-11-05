---
description: This article goes over how to aggregate streaming data using SQL in Upsolver.
---

# Aggregate streaming data

An aggregation is the pre-calculated result of a query. Unlike a simple `VIEW`, the result of an aggregation is stored in a table. 

Aggregations are used when immediate response is needed and the query which the aggregation is based on would take too long to produce a result. 

Aggregations have to be refreshed once in a while, but how often depends on its requirements and content. Essentially, an aggregation can be refreshed immediately or deferred; it can be refreshed fully or to a certain point in time.

{% hint style="info" %}
Transform with SQL supports several aggregation functions. You can use these functions to build aggregations over streamed data.   
**See:** [Aggregation functions](../../../getting-started/glossary/language-guide/functions/aggregation-functions.md)
{% endhint %}

For the following examples, we will assume the **`events`** stream contains several events, in the following format:

```sql
{"user_id" : Integer, "event_time": epoch seconds, "action_type" : String}
```

## Aggregate results in Upsolver output using SQL

Aggregations are performed using the `GROUP BY` statement.

#### Structure:

```sql
GROUP BY { expression | 

    { ROLLUP  CUBE  GROUPING SETS } ( { expression  ( expression [, ...] ) } [, ...] ) } [, ...]

    [ { WINDOW  MAX  DELAY } integer { MINUTE[S]  HOUR[S]  DAY[S] } ]

    [ APPEND ON DUPLICATE ]
```

### **Create a table with unique key**

We will demonstrate the creation of a table with unique key using the `GROUP BY` statement.

Count all the distinct events per user and per date:

```sql
SELECT user_id, UNIX_EPOCH_TO_DATE(event_time), COUNT(*) events
  FROM events
 GROUP BY user_id, UNIX_EPOCH_TO_DATE(event_time)
```

{% hint style="info" %}
**Note:** When performing the above query \(and any aggregation\), Upsolver's default behavior is to replace an existing row in the table when its aggregation is being updated.

To avoid replacing, you can use the Transform with SQL **`APPEND ON DUPLICATE`** feature.
{% endhint %}

### **`APPEND ON DUPLICATE`**

This allows queries to be defined the same way they would have been in a non-streaming context.

By setting `APPEND ON DUPLICATE`, the table will instead be **appended to**, resulting in multiple rows with the same keys in the final table.

The following query demonstrates how to use `APPEND ON DUPLICATE`:

```sql
SELECT user_id, UNIX_EPOCH_TO_DATE(event_time), COUNT(*) events
  FROM events
 GROUP BY user_id, UNIX_EPOCH_TO_DATE(event_time)
 APPEND ON DUPLICATE
```

Using `APPEND ON DUPLICATE` will result in having several rows per `user_id` and `event_time` in the output table, each with a different amount of events.

### **Aggregate records over a sliding window**

The `WINDOW` clause optionally sets the amount of time until data is expired out of the result.

For example, if it is set to 30 days, data older than 30 days is removed from the output aggregations. This is a sliding window configuration that moves forwards every minute.

To demonstrate this we will use the following query which counts all the **events per user** and `event_time` and aggregate those over a 30 days window:

```sql
SELECT user_id, UNIX_EPOCH_TO_DATE(event_time), count(*) events
  FROM events
 GROUP BY user_id, UNIX_EPOCH_TO_DATE(event_time)
   WINDOW 30 days
```

### **Aggregate records using `MAX DELAY`**

The `MAX DELAY` will filter out data that arrives delayed by more than the max delay.

{% hint style="info" %}
**Note:** When using `MAX DELAY` the group by must include a date or timestamp field.
{% endhint %}

Count all the **events per user** and `event_time` up to 3 days back:

```sql
SELECT user_id, UNIX_EPOCH_TO_DATE(event_time), count(*) events
  FROM events
 GROUP BY user_id, UNIX_EPOCH_TO_DATE(event_time)
   MAX DELAY 3 days
```

