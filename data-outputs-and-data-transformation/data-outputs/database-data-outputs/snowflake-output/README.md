---
description: >-
  This article provides an introduction to Snowflake along with a guide on how
  to create a Snowflake data output using Upsolver.
---

# Snowflake data output

{% hint style="info" %}
### What is Snowflake?

Snowflake is a data storage and analytics service provided as Software-as-a-Service \(SaaS\). Its data warehouse uses a SQL database engine and runs on cloud infrastructure.
{% endhint %}

## Create a Snowflake data output

1. Go to the **Outputs** page and click **New**.

2. Select **Snowflake** as your output type.

3. **Name** your output and select your **Data Sources**.

4. Select **New** to create a new table or **Existing** to output to an existing table. Then click **Next**.

{% hint style="warning" %}
If outputting to an **existing** table, complete the database options as prompted before clicking **Next** again.  
If necessary, [create a new Snowflake connection](../../../../administration/connections/snowflake-connection.md).
{% endhint %}

{% hint style="info" %}
Click **Properties** to review this output's properties.  
**See:** [Output properties](../../../data-transformation-ui/creating-an-output/modifying-the-output-properties/)
{% endhint %}

5. Click the information icon![](../../../../.gitbook/assets/image%20%283%29.png)in the fields tree to view information about a field.   
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

6. Click the information icon![](../../../../.gitbook/assets/image%20%283%29.png)next to a hierarchy element \(such as the overall data\) to review the following metrics:

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

7. Click the plus icon![](../../../../.gitbook/assets/screen-shot-2020-08-13-at-5.06.39-pm.png)in the fields tree to add a field from the data source to your output. This will be reflected under the **Data Source Field** in the **Schema** tab. 

* If required, modify the column name under **Schema Column**.
* Additionally, click the gear icon![](https://gblobscdn.gitbook.com/assets%2F-MAbbZ6XL3iXMHb3pjqP%2F-MEKfij3FS87rhZw-mF4%2F-MEKgKYGs3pZdqcjDFlE%2Fimage.png?alt=media&token=7c14e26d-c24d-4e17-a534-63702ccb86ee)to modify other details such as **Column Type** and **Size**.
* To remove a field, click the unlink icon![](https://gblobscdn.gitbook.com/assets%2F-MAbbZ6XL3iXMHb3pjqP%2F-MEKknVAn4ijxb2OOdz2%2F-MEKlGcy4WH6e7JB9144%2Fimage.png?alt=media&token=97af1f0a-6080-42ef-bf53-0e7fa5a3ddaa)to clear the column mapping then the garbage icon![](https://gblobscdn.gitbook.com/assets%2F-MAbbZ6XL3iXMHb3pjqP%2F-MEKknVAn4ijxb2OOdz2%2F-MEKlQwKUAWXd8D7iCQ9%2Fimage.png?alt=media&token=d53f44e1-a2b0-4e63-9197-c9bfd4c8d30f)to drop the column.

Alternatively, add columns by clicking **Add New Column**. 

* Provide a **Column Name** as well as select a **Column Type**. 
  * If desired, give the column a **Default Value** then click **Save**.
* This column will now be added under the **Data Source Field** in the **Schema** tab.

{% hint style="info" %}
Toggle from **UI** to **SQL** at any point to view the corresponding SQL code for your selected output.

You can also edit your output directly in SQL.  
**See:** [Transform with SQL](../../../data-transformation-ui/creating-an-output/modifying-the-output-in-sql/)
{% endhint %}

8. Add any required **calculated fields** and review them in the **Calculated Fields** tab.  
 **See:** [Adding calculated fields](../../../data-transformation-ui/creating-an-output/adding-calculated-fields.md)

9. Add any required **lookups** and review them under the **Calculated Fields** tab. 

{% tabs %}
{% tab title="Adding Lookups" %}
* [from data sources](../../../data-transformation-ui/creating-an-output/add-lookups/adding-lookups-from-data-sources.md)
* [from lookup tables](../../../data-transformation-ui/creating-an-output/add-lookups/adding-lookups-from-lookup-tables.md)
* [from reference data](../../../data-transformation-ui/creating-an-output/add-lookups/adding-lookups-from-reference-data.md)
{% endtab %}
{% endtabs %}

10. Through the **Filters** tab, add a filter like `WHERE` in SQL to the data source.  
**See:** [Adding filters](../../../data-transformation-ui/creating-an-output/adding-filters.md)

11. Click **Make Aggregated** to turn the output into an aggregated output.   
Read the warning before clicking **OK** and then add the required aggregation.   
This aggregation field will then be added to the **Schema** tab.   
**See:** [Aggregation functions](../../../../getting-started/glossary/language-guide/functions/aggregation-functions.md)

12. In the **Aggregation Calculated Fields** area under the **Calculated Fields** tab, add any required calculated fields on aggregations.   
**See:** [Functions](../../../../getting-started/glossary/language-guide/functions/), [Aggregation functions](../../../../getting-started/glossary/language-guide/functions/aggregation-functions.md)

13. To keep only the latest event per upsert key, click **More &gt; Manage Upserts** then select the following:

* **Keys:** A unique key identifying a row in the table.
* **Deletions:** The delete key \(events with the value true in their deletion key field will be deleted\).

**See:** [Data types and features](../../../../getting-started/glossary/data-types-and-features.md), [How do upserts work?](../../../../getting-started/tutorials-and-faq/faq.md#how-do-upserts-work)

{% hint style="info" %}
Click **Preview** at any time to view a preview of your current output.
{% endhint %}

14. Click **Run** and fill out the following fields:

* **Snowflake Connection:** [How to create a new Snowflake connection](../../../../administration/connections/#snowflake)
* **Schema**
* **Table Name**
* **Intermediate Storage Location:** Where Upsolver will store the intermediate bulk files which it will then load into Snowflake using the `copy into` command

**See:** [Running an output](../../../data-transformation-ui/running-an-output.md), [Database output options](../../../../getting-started/glossary/database-output-options.md)

14. Click **Next** and complete the following:

{% tabs %}
{% tab title="Compute Cluster" %}
Select the compute cluster to run the calculation on.  
Alternatively, click the drop-down and [create a new compute cluster](../../../../administration/managing-clusters/#adding-a-compute-cluster).
{% endtab %}

{% tab title="Processing Time Range" %}
The range of data to process.   
This can start from the data source beginning, now, or a custom date and time. This can never end, end now or end at a custom date and time.
{% endtab %}
{% endtabs %}

15. Finally, click **Deploy** to run the output.   
 It will show as **Running** in the output panel and is now live in production and consumes compute resources.

{% hint style="success" %}
You have now successfully outputted your table to your Snowflake database.
{% endhint %}

