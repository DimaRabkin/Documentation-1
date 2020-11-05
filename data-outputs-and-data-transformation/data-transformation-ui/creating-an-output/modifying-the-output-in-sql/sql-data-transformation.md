---
description: >-
  This article provides a quick video tutorial on SQL data transformation in
  Upsolver and also includes a corresponding written guide.
---

# Quick guide: SQL data transformation

{% embed url="https://www.youtube.com/watch?v=gbv697xZi-E&feature=youtu.be" %}

{% hint style="info" %}
Before starting to transform your data, you must have already [deployed Upsolver](../../../../getting-started/start-using-upsolver/upsolver-deployment-guide.md) and [created a data source.](../../../../connecting-data-sources/amazon-aws-data-sources/amazon-s3-data-source/quick-guide-s3-data-source-1.md)
{% endhint %}

Upsolver’s SQL transformation on data streams removes the complexity from traditional data pipeline transformations and orchestrations. 

Upsolver SQL is ANSI SQL compliant, so you don’t have to learn any special syntax to get started; it is intuitive and easy to use for anyone with basic SQL knowledge. Users write regular SQL expressions with extensions for streaming data use cases such as window aggregations, and the Upsolver engine will continuously execute the queries.

Let’s get started.

## Create an AWS Athena data output

1. Click on **Outputs** on the left and then **New** on the right upper corner.

![](../../../../.gitbook/assets/screen-shot-2020-09-04-at-8.41.17-am.png)

2. **Select** Amazon Athena as the data output.

![](../../../../.gitbook/assets/screen-shot-2020-09-04-at-8.44.17-am.png)

3. Give the data output a **name** and select your **data sources**; then click **Next**.

![](../../../../.gitbook/assets/image%20%287%29.png)

## Data transformation using SQL

1. Map your input fields to output fields by click on the add icon![](../../../../.gitbook/assets/screen-shot-2020-08-13-at-5.06.39-pm.png)next to the field. Alternatively, go directly to the SQL page and select your fields there. 

{% hint style="info" %}
Keep in mind that everything written in SQL will be automatically translated in the UI and everything changed in the UI will be reflected in SQL.
{% endhint %}

![](../../../../.gitbook/assets/image%20%2847%29.png)

2. Use **`TO_DATE`** function to parse out the **`YEAR()`** and **`MONTH()`** from the **`DATE STRING`**.

![](../../../../.gitbook/assets/image%20%28144%29.png)

3. Use **`TO_NUMBER`** to convert **`STRING`** to **`NUMBER`** for calculation.

![](../../../../.gitbook/assets/image%20%28102%29.png)

4. Use **`||`** to concatenate values from two fields together.

![](../../../../.gitbook/assets/image%20%2899%29.png)

5. Click **Preview** to ensure that your data looks correct.

![](../../../../.gitbook/assets/image%20%2860%29.png)

6. Click **Run** and input your AWS Athena information.

![](../../../../.gitbook/assets/image%20%2884%29.png)

## Configure AWS Athena run parameter and data output information

1. Enter the **S3 Storage** that the Athena table will be utilizing, then enter in the **Connection**, **Database**, and **Table** information for your target Athena environment. Click **Next**.

![](../../../../.gitbook/assets/image%20%28133%29.png)

2. Enter the run parameters for your data set. Pick the **compute cluster** you wish to utilize and the **time interval** for the data to be loaded to Athena. Click **Deploy**.

![](../../../../.gitbook/assets/image%20%2865%29.png)

3. Monitor **Current Status** and wait until the data competes loading.

![](../../../../.gitbook/assets/image%20%28100%29.png)

## Verify loaded data from AWS Athena

1. In your Athena environment, make sure the table is created correctly and data types are as expected.

![](../../../../.gitbook/assets/image%20%2819%29.png)

2. Run a simple **Select** query to make sure the data loaded to Athena correctly.

![](../../../../.gitbook/assets/image%20%2835%29.png)

## What’s next?

{% page-ref page="../../../../getting-started/tutorials-and-faq/tutorials/combining-data-from-multiple-sources.md" %}

