---
description: >-
  This article provides an introduction to Amazon SageMaker along with a guide
  on creating an Amazon SageMaker data output using Upsolver.
---

# Amazon SageMaker data output

{% hint style="info" %}
### What is Amazon SageMaker?

Amazon SageMaker enables developers to operate at a number of levels of abstraction when training and deploying machine learning models. 
{% endhint %}

At its highest level of abstraction, SageMaker provides pre-trained machine-learning \(ML\) models that can be deployed as-is. 

In addition, SageMaker provides a number of built-in ML algorithms that developers can train on their own data. Further, SageMaker provides managed instances of [TensorFlow](https://en.wikipedia.org/wiki/TensorFlow) and [Apache MXNet](https://en.wikipedia.org/wiki/Apache_MXNet), where developers can create their own ML algorithms from scratch. 

Regardless of which level of abstraction is used, a developer can connect their SageMaker-enabled ML models to other [AWS](https://en.wikipedia.org/wiki/Amazon_Web_Services) services, such as the [Amazon DynamoDB](https://en.wikipedia.org/wiki/Amazon_DynamoDB) database for structured data storage, AWS Batch for offline batch processing, or Amazon Kinesis for real-time processing.

## Create an Amazon SageMaker data output

1. Go to the **Outputs** page and click **New**.

2. Select **Amazon SageMaker** as your output type.

3. **Name** your output and select whether the output should be **Tabular** or **Hierarchical**.  
After adding your **Data Sources**, click **Next**.

{% hint style="info" %}
Click **Properties** to review this output's properties.  
**See:** [Output properties](../../data-transformation-ui/creating-an-output/modifying-the-output-properties/)
{% endhint %}

4. Click the information icon![](../../../.gitbook/assets/image%20%283%29.png)in the fields tree to view information about a field.   
The following will be displayed:

{% tabs %}
{% tab title="Density in Events" %}
How many of the events in this data source include this field, expressed as a percentage \(e.g. 20.81%\).
{% endtab %}

{% tab title="Density in Data" %}
The density in the hierarchy \(how many of the events in this branch of the data hierarchy include this field\), expressed a percentage.
{% endtab %}

{% tab title="Distinct Values" %}
How many unique values appear in this field.
{% endtab %}

{% tab title="Total Values" %}
The total number of values ingested for this field.
{% endtab %}

{% tab title="First Seen" %}
The first time this field included a value, for example, **a year ago**.
{% endtab %}

{% tab title="Last Seen" %}
The last time this field included a value, for example, **2 minutes ago**.
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Value Distribution" %}
The percentage distribution of the field values. These distribution values can be exported by clicking **Export**.
{% endtab %}

{% tab title="Field Content Samples Over Time" %}
A time-series graph of the total number of events that include the selected field.
{% endtab %}

{% tab title="Selected" %}
The most recent data values for the selected field and columns. You can change the columns that appear by clicking **Choose Columns**.
{% endtab %}
{% endtabs %}

5. Click the information icon![](../../../.gitbook/assets/image%20%283%29.png)next to a hierarchy element \(such as the overall data\) to review the following metrics:

{% tabs %}
{% tab title="\# of Fields" %}
The number of fields in the selected hierarchy.
{% endtab %}

{% tab title="\# of Keys" %}
The number of keys in the selected hierarchy.
{% endtab %}

{% tab title="\# of Arrays" %}
The number of arrays in the selected hierarchy.
{% endtab %}

{% tab title="Fields Breakdown" %}
A stacked bar chart \(by data type\) of the number of fields versus the density/distinct values or a stacked bar chart of the number of fields by data type.
{% endtab %}

{% tab title="Fields Statistics" %}
A list of the fields in the hierarchy element, including **Type, Density, Top Values, Key, Distinct Values, Array, First Seen,** and **Last Seen**.
{% endtab %}
{% endtabs %}

6. Click the plus icon![](../../../.gitbook/assets/screen-shot-2020-08-13-at-5.06.39-pm.png)in the fields tree to add a field from the data source to your output. This will be reflected under the **Data Source Field** in the **Schema** tab.   
If required, modify the **Output Column Name**.

{% hint style="info" %}
Toggle from **UI** to **SQL** at any point to view the corresponding SQL code for your selected output.

You can also edit your output directly in SQL.  
**See:** [Transform with SQL](../../data-transformation-ui/creating-an-output/modifying-the-output-in-sql/)
{% endhint %}

7. Add any required **calculated fields** and review them in the **Calculated Fields** tab.  
 **See:** [Adding Calculated Fields](../../data-transformation-ui/creating-an-output/adding-calculated-fields.md)

8. Add any required **lookups** and review them under the **Calculated Fields** tab. 

{% tabs %}
{% tab title="Adding Lookups" %}
* [from data sources](../../data-transformation-ui/creating-an-output/add-lookups/adding-lookups-from-data-sources.md)
* [from lookup tables](../../data-transformation-ui/creating-an-output/add-lookups/adding-lookups-from-lookup-tables.md)
* [from reference data](../../data-transformation-ui/creating-an-output/add-lookups/adding-lookups-from-reference-data.md)
{% endtab %}
{% endtabs %}

9. Through the **Filters** tab, add a filter like `WHERE` in SQL to the data source.  
**See:** [Adding Filters](../../data-transformation-ui/creating-an-output/adding-filters.md)

10. Click **Make Aggregated** to turn the output into an aggregated output.   
Read the **warning** before clicking **OK** and then add the required aggregation.   
This aggregation field will then be added to the **Schema** tab.   
**See:** [Aggregation Functions](../../../getting-started/glossary/language-guide/functions/aggregation-functions.md)

11. In the **Aggregation Calculated Fields** area under the **Calculated Fields** tab, add any required calculated fields on aggregations.   
**See:** [Functions](../../../getting-started/glossary/language-guide/functions/), [Aggregation Functions](../../../getting-started/glossary/language-guide/functions/aggregation-functions.md)

{% hint style="info" %}
Click **Preview** at any time to view a preview of your current output.
{% endhint %}

12. Click **Run** and select a pre-exiting **S3 connection** or [create a new one](../../../administration/connections/amazon-s3-connection.md).

**See:** [Running an output](../../data-transformation-ui/running-an-output.md), [How to create a new Amazon S3 connection](../../../administration/connections/amazon-s3-connection.md)

13. Click **Next** and complete the following:

{% tabs %}
{% tab title="Compute Cluster" %}
Select the compute cluster to run the calculation on.  
Alternatively, click the drop-down and [create a new compute cluster](../../../administration/managing-clusters/#adding-a-compute-cluster).
{% endtab %}

{% tab title="Processing Time Range" %}
The range of data to process.   
This can start from the data source beginning, now, or a custom date and time. This can never end, end now, or end at a custom date and time.
{% endtab %}
{% endtabs %}

14. Finally, click **Deploy** to run the output.   
 It will show as **Running** in the output panel and is now live in production and consumes compute resources.

{% hint style="success" %}
Your output has now been added to your **S3 bucket**.  
To easily navigate to your output, click **Properties** then **View output in AWS S3 Console**, which will take you to the SageMaker outputs folder in your S3 storage bucket.
{% endhint %}

