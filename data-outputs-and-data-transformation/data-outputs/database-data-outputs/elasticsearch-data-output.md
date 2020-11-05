---
description: >-
  This article provides an introduction to Elasticsearch along with a guide on
  creating an Elasticsearch data output using Upsolver.
---

# Elasticsearch data output

{% hint style="info" %}
### What is Elasticsearch?

Elasticsearch is an open-source, RESTful, distributed search and analytics engine built on Apache Lucene. It is commonly used for log analytics, full-text search, security intelligence, business analytics, and operational intelligence use cases.
{% endhint %}

You can send data in the form of JSON documents to Elasticsearch using the API or ingestion tools such as [Logstash](https://aws.amazon.com/elasticsearch-service/the-elk-stack/logstash/) and [Amazon Kinesis Firehose](https://aws.amazon.com/kinesis/data-firehose/). Elasticsearch automatically stores the original document and adds a searchable reference to the document in the cluster’s index. 

You can then search and retrieve the document using the Elasticsearch API. You can also use [Kibana](https://aws.amazon.com/elasticsearch-service/the-elk-stack/kibana/), an open-source visualization tool, with Elasticsearch to visualize your data and build interactive dashboards.

## Create an Elasticsearch data output

1. Go to the **Outputs** page and click **New**.

2. Select **Elasticseaarch** as your output type.

3. **Name** your output and select your **Data Sources**, then click **Next**.

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
Read the warning before clicking **OK** and then add the required aggregation.   
This aggregation field will then be added to the **Schema** tab.   
**See:** [Aggregation Functions](../../../getting-started/glossary/language-guide/functions/aggregation-functions.md)

11. In the **Aggregation Calculated Fields** area under the **Calculated Fields** tab, add any required calculated fields on aggregations.   
**See:** [Functions](../../../getting-started/glossary/language-guide/functions/), [Aggregation Functions](../../../getting-started/glossary/language-guide/functions/aggregation-functions.md)

{% hint style="info" %}
Click **Preview** at any time to view a preview of your current output.
{% endhint %}

12. Click **Run** and fill out the following fields:

* **Connection:** [How to create an Elasticsearch connection](../../../administration/connections/elasticsearch-connection.md)
* **Index Name:** See warning below
* **Index Partition Size**
* **S3 connection:** Select an intermediate storage location where Upsolver will store the intermediate bulk files before loading it into Elasticsearch

**See:** [Running an output](../../data-transformation-ui/running-an-output.md)

{% hint style="warning" %}
The **index name** must be that of a **pre-existing index** \(Upsolver will not automatically create a new index\) and the name should be **suffixed** with the **year** \(e.g. `upsolver` → ****`upsolver_2020`\).
{% endhint %}

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
You have now successfully outputted your data to Elasticsearch.
{% endhint %}

