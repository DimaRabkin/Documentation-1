---
description: >-
  This page provides a quick video tutorial on how to upsert data to Snowflake
  and also includes a corresponding written guide.
---

# Upsert data to Snowflake



{% embed url="https://www.youtube.com/watch?v=8ZpuOQ9LD3Y&feature=youtu.be" %}

{% hint style="info" %}
Before we start, you must have already [deployed Upsolver](../../../../getting-started/start-using-upsolver/upsolver-deployment-guide.md) and [created data sources](../../../../connecting-data-sources/amazon-aws-data-sources/amazon-s3-data-source/quick-guide-s3-data-source-1.md).
{% endhint %}

Upsolver can load data into many databases including Snowflake. This guide creates a Snowflake data output. It uses a key to perform Upsert to a table. This feature can be used for loading CDC data to Snowflake database.

This guide uses an example where the **existing Snowflake table** has the following data.

| Key | Value |
| :--- | :--- |
| 1 | johnny |
| 2 | joey |
| 3 | deedee |
| 4 | tommy |

{% hint style="warning" %}
The new data source has a different value for **key 4**.
{% endhint %}

| Key | Value |
| :--- | :--- |
| 1 | johnny |
| 2 | joey |
| 3 | deedee |
| 4 | **marky** |

Now let’s take a look at how Upsert works in Upsolver.

## Create a Snowflake data output

1. Click on **Outputs** on the left and then click **New** on the right upper corner.

![](../../../../.gitbook/assets/screen-shot-2020-09-04-at-8.41.17-am.png)

2. **Select** Snowflake as your data output.

![](../../../../.gitbook/assets/screen-shot-2020-09-05-at-12.15.16-pm.png)

3. Give your data output a **name**. Define your **Data Sources** and select whether is a **new table** or an **existing table**. 

{% hint style="info" %}
**Note:** This example Upserts to an existing table. 
{% endhint %}

![](../../../../.gitbook/assets/image%20%28101%29.png)

4. Click **Next.**

5. Under **Snowflake Connection**, select **Create a new Snowflake Connection**.

![](../../../../.gitbook/assets/screen-shot-2020-09-05-at-12.22.50-pm.png)

6. Fill out the **connection string** for Snowflake. Also enter your Snowflake **user name** and **password**. Provide a **name** for this output connection. Click **Create**.

{% hint style="info" %}
**See:** [Snowflake connection](../../../../administration/connections/snowflake-connection.md) for more details regarding how to configure your Snowflake connection.
{% endhint %}

![](../../../../.gitbook/assets/image%20%2853%29.png)

7. Provide details for your Snowflake environment including Snowflake **schema** and **table name**. Provide an **intermediate storage location** for data to be stored before merging to a Snowflake table. Click **Next**.

![](../../../../.gitbook/assets/image%20%28135%29.png)

## Define the key for Upsert

1. Select the SQL window from the upper right hand corner. Keep in mind that everything that you do on the UI will be reflected in SQL and vice versa. 

![](../../../../.gitbook/assets/screen-shot-2020-09-05-at-11.38.24-am.png)

2. The sample SQL uses the **`REPLACE ON DUPLICATE data.key`** statement to perform the Upsert.

![](../../../../.gitbook/assets/image%20%2876%29.png)

3. Click **Run** in the upper right hand corner.

![](../../../../.gitbook/assets/screen-shot-2020-09-05-at-12.00.11-pm.png)

4. Choose the **compute cluster** and the time range that you wish to load your data from, then click **Deploy**.

![](../../../../.gitbook/assets/image%20%28141%29.png)

5. Wait for a moment for the data to output to Snowflake.

![](../../../../.gitbook/assets/image%20%2888%29.png)

## Verify the CDC Snowflake data output

#### Before Upsert:

![](../../../../.gitbook/assets/image%20%2892%29.png)

#### After Upsert:

![](../../../../.gitbook/assets/image%20%28115%29.png)

