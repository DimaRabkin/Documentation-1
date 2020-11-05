---
description: >-
  Increase storage and processing efficiency by pre-aggregating data before
  loading to data warehouses or log processors.
---

# Pre-aggregate data for efficiency and performance

Raw data can be very voluminous. Analysts might only need summarized data that's applicable to business.  By pre-aggregating the data as it is ingested, you’re able to improve query performance and minimize storage and compute costs.

The objective of this module is to create a summary table in Athena that contains the totals for each item sold for a given day.

Desired Output would be an **item\_summary** table with below schema:

![Reduce data volume and increase processing efficiency by summarizing data before writing to destination](../../../../.gitbook/assets/image%20%28148%29.png)

## 1. Create an Amazon Athena data output

Click on **DATA OUTPUT &gt; NEW** and **SELECT** **Amazon Athena output.** Give the output a **NAME &gt; item\_summary** and choose **DATA SOURCES &gt; Orders** Click on **NEXT** to continue.

![Create a Amazon Athena output called item\_summary](../../../../.gitbook/assets/1.gif)

## 2. Add aggregation to the data stream

From the Upsolver Transformation Screen, add **Itemid** to the output by clicking the **+** sign next to the field. Then click **Make Aggregated**  Click **OK** if the warning pops-up.

![Upsolver Transformation Screen - Make Aggregated](../../../../.gitbook/assets/2.gif)

Click on **Add Calculated Field**. Find and **SELECT** the **TO\_DATE** function. Enter **DATETIME &gt;** **data.orderDate** and **NAME &gt;** root**.date** Check the data by clicking on **PREVIEW**. If everything looks ok, click on **SAVE.**

![Transform date format to be more readable](../../../../.gitbook/assets/3%20%281%29.gif)

  
Click on **Add Aggregation** Find and **SELECT** **COUNT\(\*\)** and click on **SAVE**. This will count the number of items for a given period of time window in a stream. Click away the warning if they appear.

![Count the number of items for a given period of time](../../../../.gitbook/assets/4%20%281%29.gif)

Add another aggregation by clicking on **Add Aggregation** again. This time select **SUM** from the list and choose **data.items\[\].price** from the list. Click on **SAVE**. Dismiss any warnings that you may encounter.

![Calculate the total price of an item for a given period of time](../../../../.gitbook/assets/5%20%281%29.gif)

Add the last aggregation by clicking on **Add Aggregation**. This time select **AVG** from the list and choose **data.items\[\].price** from the list. Click on **SAVE**. Dismiss any warnings that you may encounter.

![Calculate the average price of an item for a given period of time](../../../../.gitbook/assets/6%20%281%29.gif)

## 3. Rename the fields to match the output schema

Change the output column names to  **data\_items\_itemid &gt; items\_id**  **sum\_data\_items\_price &gt; sum\_items\_price**, and **avg\_data\_items\_price &gt; avg\_items\_price** Be very careful renaming the fields, we will use them later.

![Rename fields to item\_id, sum\_items\_price and avg\_items\_price](../../../../.gitbook/assets/image%20%2817%29.png)

## 4. Define the partition strategy for writing data to Amazon Athena

{% hint style="info" %}
Proper partitioning strategy can significant improve query performance with Amazon Athena. Upsolver manages partitions and compactions automatically.
{% endhint %}

Click on **Manage Partitions** and choose **Time Partition Field &gt; date** and **Time Partition Size &gt; Daily** Click on **CLOSE**. You will see _Partitioned by event time \(Daily partitions\)_ shown on the screen instead of _processing time_.

![Partition data by day based on event time](../../../../.gitbook/assets/7.gif)

## 5. Verify your SQL and data and define run parameter

Switch to the **SQL** view. Your SQL should look similar to the following. If your SQL looks different, copy and paste it to your environment. 

```sql
SET "date" = TO_DATE(data.orderDate);
// GENERATED @ 2020-10-12T04:13:03.089790Z
SELECT PARTITION_TIME("date") AS _date_1:TIMESTAMP,
       AGGREGATION_TIME() AS processing_time:TIMESTAMP,
       data.items[].itemId AS items_id:STRING,
       "date" AS _date:TIMESTAMP,
       COUNT(*) AS "count":DOUBLE,
       SUM(data.items[].price) AS sum_items_price:DOUBLE,
       AVG(data.items[].price) AS avg_items_price:DOUBLE
  FROM "Orders"  
    GROUP BY data.items[].itemId,
          "date",
          PARTITION_TIME("date")
    APPEND ON DUPLICATE

```

Click on **PREVIEW** to verify your data. Click on **RUN** to define the Amazon Athena. Choose the **DATABASE NAME &gt; upsolver** and **TABLE NAME &gt; item\_summary** Click on **NEXT**.

![](../../../../.gitbook/assets/8.gif)

## 6. Start writing data to Amazon Athena and verify data

Leave everything on the Run page as default and click on **DEPLOY**. 

{% hint style="info" %}
The output is continuous stream by leaving **ENDING AT** as **Never**, 
{% endhint %}

![](../../../../.gitbook/assets/image%20%2867%29.png)

Upsolver starts writing data to Amazon Athena. You can click on **PROGRESS** to monitor output progress. This may take a minute.

![](../../../../.gitbook/assets/image%20%2810%29.png)

## 7. Query item\_summary table for aggregated data

{% hint style="info" %}
When Upsolver creates an upserting output to Athena, it creates two objects: a table with the suffice `_underlying_data` and a view with the output name.  When querying, you should query the VIEW, and not the underlying data.
{% endhint %}

Using Athena you can now query the data set created by Upsolver \(it may take a few minutes before the data is available\). Some sample queries that can be run are below: Click [here](https://console.aws.amazon.com/athena/home?force&region=us-east-1) to login to Athena in order to run below queries

```sql
// The number of each item sold

SELECT items_id,
         SUM("count")
FROM upsolver.item_summary
GROUP BY  items_id LIMIT 10
```

![How many of each item were sold](../../../../.gitbook/assets/image%20%2858%29.png)

```sql
// The average price of the items

SELECT "_date",
         sum("sum_items_price")/sum("count") AS avg_price
FROM upsolver.item_summary
GROUP BY  "_date" LIMIT 10
```

![Average price of the items](../../../../.gitbook/assets/image%20%2852%29.png)

