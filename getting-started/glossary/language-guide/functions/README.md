---
description: This article provides an overview of aggregations and calculated fields.
---

# Functions

## [Aggregations](aggregation-functions.md)

Aggregations are functions for grouping multiple events together to form a more significant result, and they can return a single value or a hash table depending on the function.

Unlike databases, Upsolver runs continuous queries and not ad-hoc queries. Therefore, aggregation results are incrementally updated with every incoming event, and aggregation functions require windowing to split a stream into buckets of data that can be aggregated.

{% page-ref page="aggregation-functions.md" %}

## [Calculated fields](calculated-functions/)

A calculated field is a field that wasn't part of an incoming event but is added into the event by using one of Upsolver's functions.

Examples: 

* extracting city from IP
* running a regular expression
* performing a mathematical operation

{% hint style="info" %}
Please note that:

**Calculated fields** do not create any physical storage. They are executed at run-time if they are needed in a deployed lookup table or output.

**Functions input parameters** are limited to fields in the incoming event, constant values, and other calculated fields. It's possible to use fields from various hierarchical locations.

**Functions output parameter** is a single value or an array that can be placed at any hierarchical location within the event.

**Functions** are built to handle both single values and arrays so be sure to check each one in the documentation.
{% endhint %}

{% page-ref page="calculated-functions/" %}

