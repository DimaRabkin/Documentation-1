---
description: >-
  This article maps out a simple Upsolver use case where an S3 data source is
  turned into an Athena output.
---

# AWS S3 to Athena use case

A very typical simple use case is when you have a stream of data you want to query using Amazon Athena, with the events sent to the output as they arrive from the data source.

It is very common to partition the data by the date/time of the event \(and not the date/time that the event arrived\). This ensures that events that might arrive late are stored in the correct partitions, and it also means that when you query the data, only the relevant folders are queried, improving performance.

For this example, we use a demo Amazon S3 data source called **Resource Utilization**, which is a simple stream of data that is not nested. 

![Overview of Resource Utilization data source](../../../.gitbook/assets/image%20%28123%29.png)

{% hint style="info" %}
#### Required Level of Expertise:

* Fundamental
{% endhint %}

This use case will demonstrate how to:

* [create an output](aws-s3-to-athena-use-case.md#create-an-output)
* [add fields](aws-s3-to-athena-use-case.md#add-fields)
* [partition the data](aws-s3-to-athena-use-case.md#partition-the-data)
* [run the output](aws-s3-to-athena-use-case.md#run-the-use-case-output)

**Note:** This use case only includes fields that do not require transformation and does not cover calculated fields and lookups.

## Create an output

1. Go to the **Data Sources** page and click on the desired S3 data source.

2. Click **New Output** and select **Amazon Athena**.

3. **Name** this output and click **Next**.   
**Note:** The time field is automatically added to the schema.

## Add fields

Add the simple fields that either require no data transformation or only data type transformation.

1. In the **Schema** tab, select the desired fields; for example:

* In **data &gt; tags**, select:
  * **`AWS REGION`**
  * **`BUILD_BRANCH`**
  * **`BUILD_NUMBER`**
  * **`CLOUD`**
  * **`CLUSTER_ID`**
  * **`CLUSTER_ORGANIZATION_ID`**.
* In **data &gt; fields**, select:
  * **`n_cpus`**
  * **`available_usage`**

{% hint style="warning" %}
Number fields are automatically mapped to type **`DOUBLE`** to preserve accuracy, and some fields with numbers may appear as type **`STRING`**.

If a field is comprised of integers, you can change the **column type** to **`BIGINT`**.
{% endhint %}

**Note:** To check the contents ****of a field and determine its column type, click on its information icon![](../../../.gitbook/assets/image%20%283%29.png)in the fields tree.

![](../../../.gitbook/assets/image%20%28121%29.png)

2. Update the output column names as required.

{% hint style="info" %}
If you wish, toggle the view from **UI** to **SQL** to edit the output directly in SQL.  
**See:** [Transform with SQL](../../../data-outputs-and-data-transformation/data-transformation-ui/transform-with-sql/)
{% endhint %}

## Partition the data

{% hint style="info" %}
The data is stored in folders according to the time field and by default, this is set to **Daily**. Through the **Properties** tab, this can be set to **Yearly**, **Monthly**, **Daily**, or **Hourly**.
{% endhint %}

1. Click **Manage Partitions** and click the plus icon![](../../../.gitbook/assets/image%20%2891%29.png).  
**Note:** If you had already have a suitable date source field, you could select it. In this use case, we will create a field.

2. Select **Date** and then select the desired function. In this example, we will be using`PARSE_DATE(string date, string format)`.  
**See:** [Functions](../../glossary/language-guide/functions/)

3. Specify the **date format** in [Java DateTimeFormatter format](https://docs.oracle.com/javase/9/docs/api/java/time/format/DateTimeFormatter.html) \(e.g. `yyyy-MM-dd HH:mm:ss`\).

4. Select the **date field**.

5. **Name** this field.

6. Click **Preview** to see the date conversion. 

{% hint style="warning" %}
If **N/A** appears it means that it was unable to convert the date and that you need to update the **format**.
{% endhint %}

7. Check **Add to Output Schema** to add it to your output.

8. Click **Save**. 

9. Select this field as the **Time Partition** field and close the **Manage Partitions** window.

{% hint style="warning" %}
If you experience an error updating the output, make sure your output is not currently empty.
{% endhint %}

Your parsed date field should now be added to your output.   
You can view its code by toggling from **UI** to **SQL** or going to the **Calculated Fields** tab.

## Run the output

Click **Run** to run the output to view the results.  
**See:** [Run an output](../../../data-outputs-and-data-transformation/data-transformation-ui/running-an-output.md)

