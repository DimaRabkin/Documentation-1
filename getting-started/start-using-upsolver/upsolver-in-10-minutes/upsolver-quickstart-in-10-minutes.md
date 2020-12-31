---
description: This guide provides a quick tour of Upsolver for first time users.
---

# Upsolver Quickstart in 10 Minutes

## Welcome to Upsolver!

When you first log into Upsolver's [free Community Edition](https://app.upsolver.com/signup/free), you will see a link to this guide. It provides you with a quick tour of Upsolver. 

![](../../../.gitbook/assets/image%20%28214%29.png)

The sample environment provides you with a pre-created[ ](../../../connecting-data-sources/amazon-aws-data-sources/amazon-s3-data-source/quick-guide-s3-data-source-1.md)[Data Source ](../../../connecting-data-sources/amazon-aws-data-sources/amazon-s3-data-source/quick-guide-s3-data-source-1.md)that continuously parses data from an Amazon S3 bucket. 

The sample Open Lake data output transforms the data and users can query the transformed data with SQL. 

## Run sample queries

Upsolver provides you with a pre-populated worksheet that runs queries using Open Lake query engine. Click on **Explore the Quickstart Worksheet** to get started!

![](../../../.gitbook/assets/image%20%28211%29.png)

The following SQL is querying data from `orders` table that's being continuously populated by Upsolver data source called Upsolver Tutorial Orders Bucket 

{% tabs %}
{% tab title="Total order amount" %}
```sql
-- This sample query provides the total amount for each order. The data is streaming in from a S3 bucket
-- We pre-created a data source called "Upsolver Tutorial Orders Bucket". You may explore the sample
-- data source by click on DATA SOURCES on the menu bar and "Upsolver Tutorial Orders Bucket"
-- Upsolver automatically parses the data and provides data demographics and statistics information 
-- We have also created a sample data output that writes to the orders table used by this query. 
-- You may explore the existing data output by clicking on DATA OUTPUT > Orders
-- If you're interested in creating your own data source or output, please integrate with your AWS account 
-- by clicking on DATA SOURCES > NEW 
-- Happy Upsolving! 

SELECT order_date,
         order_id,
         buyer_email,
         net_total,
         sales_tax,
         net_total + sales_tax as order_total
FROM upsolver.exampledatabase.orders
WHERE  event_type = 'ORDER'
GROUP BY  1,2,3,4,5,6 limit 10
```
{% endtab %}

{% tab title="Daily order count" %}
```sql
-- This sample query provides the total order count for each day. The data is streaming in from a S3 bucket
-- We pre-created a data source called "Upsolver Tutorial Orders Bucket". You may explore the sample
-- data source by click on DATA SOURCES on the menu bar and "Upsolver Tutorial Orders Bucket"
-- Upsolver automatically parses the data and provides data demographics and statistics information 
-- We have also created a sample data output that writes to the orders table used by this query. 
-- You may explore the existing data output by clicking on DATA OUTPUT > Orders
-- If you're interested in creating your own data source or output, please integrate with your AWS account 
-- by clicking on DATA SOURCES > NEW 
-- Happy Upsolving! 

SELECT order_date,
         order_id,
         buyer_email,
         net_total,
         sales_tax,
         net_total + sales_tax as order_total
FROM upsolver.exampledatabase.orders
WHERE  event_type = 'ORDER'
GROUP BY  1,2,3,4,5,6 limit 10
```
{% endtab %}
{% endtabs %}



