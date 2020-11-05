---
description: >-
  This article provides a guide on how to create an Elasticsearch connection in
  Upsolver.
---

# Elasticsearch connection

## Create an Elasticsearch connection

1. Enter the **connection string** in the following format:

`elasticsearch://HOST:PORT?cluster.name=MY_CLUSTER&ssl=true` where:

* `HOST` = host name
* `PORT` = port number
* `MY_CLUSTER` = your cluster's name

{% hint style="info" %}
**See:** [Elasticsearch connection string](https://help.compose.com/docs/elasticsearch-connecting-to-elasticsearch)
{% endhint %}

2. Enter your MySQL database **username**.

3. \(Optional\) Enter the corresponding **password**.

4. **Name** this connection.

5. \(Optional\) Enter in the number of **concurrent connections**.

