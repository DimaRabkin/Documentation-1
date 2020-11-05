---
description: >-
  This article provides a walkthrough on how to combine data from multiple
  sources.
---

# Combine data from multiple sources

{% embed url="https://www.youtube.com/watch?v=Yxr9l-hCJB8&feature=youtu.be" %}

{% hint style="info" %}
Before combining your data sources, you must have already [deployed Upsolver](../../start-using-upsolver/upsolver-deployment-guide.md) and [created two data sources](../../../connecting-data-sources/amazon-aws-data-sources/amazon-s3-data-source/quick-guide-s3-data-source-1.md).
{% endhint %}

Most of our users have data from various types of sources including real-time streaming data as well as historical data; as such, it’s very important to be able to combine data from these sources together for analytics. 

This guide provides an overview on how to combine multiple data sources together.

Let’s get started.

## Create an AWS Athena data output

1. Click on **Outputs** on the left and then **New** on the right upper corner.

![](../../../.gitbook/assets/screen-shot-2020-09-04-at-8.41.17-am.png)

2. **Select** Amazon Athena as the data output.

![](../../../.gitbook/assets/screen-shot-2020-09-05-at-11.14.26-am.png)

3. Click on **Add** to add as many data sources as you need. Click on **Next** to continue.

![](../../../.gitbook/assets/image%20%2823%29.png)

### 

## Transform your aggregated data

1. Use the plus icon![](../../../.gitbook/assets/screen-shot-2020-08-13-at-5.06.39-pm.png)next to the data to map all of your fields to the output.

![](../../../.gitbook/assets/image%20%2830%29.png)

2. Deselect the columns that you do not wish to output.

{% hint style="info" %}
If you want to add each field individually, you can also click on the plus icon![](../../../.gitbook/assets/screen-shot-2020-08-13-at-5.06.39-pm.png)next to each field.
{% endhint %}

For this example, we are going to output all fields, so leave everything checked and click **Add Fields**.

![](../../../.gitbook/assets/image%20%2881%29.png)

3. Perform the same thing for the second data source. Click on the plus icon![](../../../.gitbook/assets/screen-shot-2020-08-13-at-5.06.39-pm.png)next to data and select **Add Fields** to add all the fields from the second data source as well.

4. Click on the **SQL** tab on the upper right hand corner.

![](../../../.gitbook/assets/image%20%28137%29.png)

5. By default, when two data sources have the same column name, Upsolver will add `_<number>` to the duplicated column. 

For example, if both data sets have a column named `id`, the output will have `id` from one data source and `id_1` from another data source. 

{% hint style="info" %}
**Note:** This behavior of not merging two columns together automatically is because not all columns with the same name mean the same thing. 

If the columns do mean the same and they should be merged, then the **`COALESCE`** statement will combine the columns from two data sources together.
{% endhint %}

![](../../../.gitbook/assets/image%20%28138%29.png)

6. Click **Preview** to review your data and then click **Run**.

![](../../../.gitbook/assets/image%20%2889%29.png)

## Configure your output

1. Input your run parameters for your output and click **Next**.

![](../../../.gitbook/assets/image%20%2894%29.png)

2. Select the **compute cluster** you wish to use. Choose the time range that you want to load your data from. 

{% hint style="info" %}
Keep in mind that for live streaming data, you should leave **Ending At** as **Never**. 
{% endhint %}

3. Click **Deploy**.

![](../../../.gitbook/assets/image%20%2854%29.png)

## Verify your output

1. Keep track of the progress of your data output from the UI. 

2. Check your output data to make sure that everything outputted correctly.

![](../../../.gitbook/assets/image%20%2868%29.png)

## What’s next?

{% page-ref page="joining-multiple-data-streams-for-real-time-analytics.md" %}

