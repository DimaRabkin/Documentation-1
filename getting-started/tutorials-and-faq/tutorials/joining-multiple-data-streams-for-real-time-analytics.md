---
description: >-
  This article provides a walkthrough on how to join multiple data streams for
  real-time analytics.
---

# Join multiple data streams for real-time analytics

{% embed url="https://www.youtube.com/watch?v=iQAwiq7P\_CQ&feature=youtu.be" %}

{% hint style="info" %}
Before performing a join on multiple data streams, you must have already [deployed Upsolver](../../start-using-upsolver/upsolver-deployment-guide.md) and [created data sources](../../../connecting-data-sources/amazon-aws-data-sources/amazon-s3-data-source/quick-guide-s3-data-source-1.md).
{% endhint %}

Performing a join on multiple data streams is easy with Upsolver. 

This guide provides the instructions on joining: 

* `impressions`: primary data source with ad campaign information
* `clicks`: secondary data stream tracking number of clicks on an ad

{% hint style="warning" %}
**Note:** All clicks will be associated with an ad impression, but not all ad impressions will result in clicks.
{% endhint %}

## Create an Athena data output and define a data source

![](../../../.gitbook/assets/image%20%28126%29.png)

1. Click on **Outputs** on the left and then **New** on the right upper corner.

![](../../../.gitbook/assets/screen-shot-2020-09-04-at-8.41.17-am.png)

2. **Select** Amazon Athena as the data output.

![](../../../.gitbook/assets/screen-shot-2020-09-05-at-11.14.26-am.png)

3. Click **Add** to add as many data sources as you need. Click **Next** to continue.

![](../../../.gitbook/assets/image%20%28111%29.png)

## Join two data streams together and perform data transformation

![](../../../.gitbook/assets/image%20%285%29.png)

1. Select the SQL window from the upper right hand corner.

![](../../../.gitbook/assets/screen-shot-2020-09-05-at-11.38.24-am.png)

2. The sample SQL below performs a `LEFT OUTER JOIN` between `impressions` and `clicks` data streams. 

Behind the scenes, the `LEFT OUTER JOIN` is creating a lookup table, enabling users to index data by a set of keys and then retrieve the results in milliseconds.

{% code title="Sample SQL" %}
```sql
SELECT data.id AS impression_id, 
    data.win_timestamp AS impression_time, 
    data.campaign_id AS campaign_id, 
    data.exch_user AS user_id, 
    IF_ELSE(click_data.click_time IS NULL, 0, 1) AS is_click 
        -- if click_time exists returns 1, else returns 0
FROM Impressions LEFT OUTER JOIN 
    (SELECT data.id AS imp_id, 
        LAST(data.click_timestamp) AS click_time 
            -- last click_timestamp is the click_time
    FROM Clicks GROUP BY data.id) 
AS click_data WAIT 10 MINUTES ON click_data.imp_id = data.id 
    -- wait for 10 minutes before performing the join since clicks usually arrive after impressions.
```
{% endcode %}

{% hint style="info" %}
Read more about Upsolver lookup tables [here](https://www.upsolver.com/blog/lookup-tables-decoupled-alternative-cassandra).
{% endhint %}

## Define Athena output parameters

![](../../../.gitbook/assets/image%20%2820%29.png)

1. Define storage, database, and table information for your Athena environment and click **Next**.

![](../../../.gitbook/assets/image%20%2813%29.png)

2. Define the **compute cluster** that you would like to use and the **time range** of the data you would like to output. 

{% hint style="info" %}
Keep in mind that setting **Ending At** to **Never** means the output will be a continuous stream. 
{% endhint %}

3. Click **Deploy**.

![](../../../.gitbook/assets/image%20%2848%29.png)

## Check output data and run analytics

1. Check to make sure the output data is up to date by clicking on the **Progress** tab.

![](../../../.gitbook/assets/image%20%2834%29.png)

2. Run a query in Athena to make sure you get the correct results.

{% code title="Athena query" %}
```sql
SELECT campaign_id, 
    SUM(is_click)/COUNT(*) AS CTR
        -- to get the click through rate: 
        -- divide the sum of clicks for a campaign with the total number of impressions 
FROM impression_clicks
GROUP BY campaign_id
```
{% endcode %}

![](../../../.gitbook/assets/image%20%2827%29.png)

## What’s next?

{% page-ref page="using-upsolver-to-index-less-data-into-splunk.md" %}

