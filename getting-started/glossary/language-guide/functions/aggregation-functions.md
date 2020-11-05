---
description: This page goes over all of the aggregation functions available in Upsolver.
---

# Aggregation functions

Aggregations are functions for grouping multiple events together to form a more significant result.

Unlike databases, Upsolver runs continuous queries and not ad-hoc queries. Therefore, aggregation results are incrementally updated with every incoming event, and aggregation functions require windowing to split a stream into buckets of data that can be aggregated.

## `COUNT(*)`

The number of items in the time window.

## `COUNT`

The number of values in the time window.

#### Example:

For the following stream of events:

```sql
{"id": "1", "data": 2}
{"id": "1", "data": 3}
{"id": "2", "data": 5}
{"id": "3", "data": 8}
```

Using this aggregation with primary key `id` and `COUNT(data)` produces the following data:

| Primary Key `id` | `COUNT(data)` |
| :--- | :--- |
| 1 | 2 |
| 2 | 1 |
| 3 | 1 |

## `COUNT_IF`

The number of `true` values in the time window.

## `COUNT_DISTINCT`

Counts the number of distinct values that appeared in the column per key value.

#### Example:

For the following stream of events:

```sql
{"id": "1", "data": "a"}
{"id": "1", "data": "b"}
{"id": "2", "data": "c"}
{"id": "2", "data": "c"}
{"id": "3", "data": "c"}
```

Using this aggregation with primary key `id` and `COUNT_DISTINCT(data)` produces the following data:

| Primary Key `id` | `COUNT_DISTINCT(data)` |
| :--- | :--- |
| 1 | 2 |
| 2 | 1 |
| 3 | 1 |

## `STRING_MAX`

The maximum string value in the time window sorted case-sensitive lexicographically.

## `STRING_MIN`

The minimum string value in the time window sorted case-sensitive lexicographically.

## `MAX`

The maximum value in the time window.

#### Example:

For the following stream of events:

```sql
{"id": "1", "data": 2}
{"id": "1", "data": 3}
{"id": "2", "data": 5}
{"id": "3", "data": 8}
```

Using this aggregation with primary key `id` and `MAX(data)` produces the following data:

| Primary Key `id` | `MAX(data)` |
| :--- | :--- |
| 1 | 3 |
| 2 | 5 |
| 3 | 8 |

## `MIN`

The minimum value in the time window.

#### Example:

For the following stream of events:

```sql
{"id": "1", "data": 2}
{"id": "1", "data": 3}
{"id": "2", "data": 5}
{"id": "3", "data": 8}
```

Using this aggregation with primary key `id` and `MIN(data)` produces the following data:

| Primary Key `id` | `MIN(data)` |
| :--- | :--- |
| 1 | 2 |
| 2 | 5 |
| 3 | 8 |

## `SUM`

The sum of the values in the time window.

#### Example:

For the following stream of events:

```sql
{"id": "1", "data": 2}
{"id": "1", "data": 3}
{"id": "2", "data": 5}
{"id": "3", "data": 8}
```

Using this aggregation with primary key `id` and `SUM(data)` produces the following data:

| Primary Key `id` | `SUM(data)` |
| :--- | :--- |
| 1 | 5 |
| 2 | 5 |
| 3 | 8 |

## `AVG`

The average value in the time window.

## `DELETE`

Delete the record when this is set.

## `STD_DEV`

The standard deviation of values in the time window.

## `LAST`

The last value in the time window.

#### Example:

For the following stream of events:

```sql
{"id": "1", "data": 3}
{"id": "1", "data": 2}
{"id": "2", "data": 5}
{"id": "3", "data": 8}
```

Using this aggregation with primary key `id` and `LAST(data)` produces the following data:

| Primary Key `id` | `LAST(data)` |
| :--- | :--- |
| 1 | 2 |
| 2 | 5 |
| 3 | 8 |

## `LAST_ARRAY`

The last array of values in the time window.

## `FIRST`

The first value in the time window.

#### Example:

For the following stream of events:

```sql
{"id": "1", "data": 3}
{"id": "1", "data": 2}
{"id": "2", "data": 5}
{"id": "3", "data": 8}
```

Using this aggregation with primary key `id` and `SUM(data)` produces the following data:

| Primary Key `id` | `FIRST(data)` |
| :--- | :--- |
| 1 | 3 |
| 2 | 5 |
| 3 | 8 |

## `FIRST_ARRAY`

The first array of values in the time window.

## `APPROX_COUNT_DISTINCT`

The approximate number of distinct values in the time window. 

Use this function instead of `COUNT_DISTINCT` to improve performance, but only when there are not many \(under 1M\) rows in the result.

## `GRAPH`

Stores the max/min/avg/sum/last of the values per time interval.

## `SESSION_COUNT`

Stores the number of sessions. 

{% hint style="info" %}
A session includes all the events in the aggregation that are at most `windowSize` apart in their value.
{% endhint %}

#### Example:

For the following stream of events:

```sql
{"id": "John", "time": 1}
{"id": "John", "time": 4}
{"id": "John", "time": 2}
{"id": "John", "time": 7}
```

Using this aggregation with primary key `id` and `SESSION_COUNT(time, 2)` will produce the following data:

| Primary Key `id` | `SESSION _COUNT(time, 2)` |
| :--- | :--- |
| "John" | 2 |

With `SESSION_COUNT(time, 2)`, a session is defined as a distance between two events of up to or including 2. Thus, 1, 2, and 4 are one session and 7 is the second session.

## `WEIGHTED_AVERAGE`

The weighted average of a value in the time window.

## `DECAYED_SUM`

Performs a sum on the value and decays that sum based on the decay factor and how old the original data is.

