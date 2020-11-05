---
description: This article provides a general guide on how to create an output in Upsolver.
---

# Create an output

1. From the **Outputs** page, click **New**.

2. Select the desired output type.

{% hint style="info" %}
For more detailed instructions tailored to a specific output type,   
**See:** [Data outputs](../../data-outputs/)
{% endhint %}

3. **Name** this output.

4. If prompted, select whether the output should be **Tabular** or **Hierarchical**.

5. Select the input **data source**.

6. For databases, choose either to **create** a new table or output to an **existing** one.

7. Click **Next**.

{% hint style="warning" %}
If you selected to output to an existing table in a database, you will need to configure the database options.  
**See:**[ Database output options](../../../getting-started/glossary/database-output-options.md)
{% endhint %}

{% hint style="info" %}
Click **Properties** to review this output's properties.  
**See:** [Output properties](modifying-the-output-properties/)
{% endhint %}

8. Click the information icon![](../../../.gitbook/assets/image%20%283%29.png)in the fields tree to view information about a field.   
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

9. Click the information icon![](../../../.gitbook/assets/image%20%283%29.png)next to a hierarchy element \(such as the overall data\) to review the following metrics:

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

10. Click the plus icon![](../../../.gitbook/assets/screen-shot-2020-08-13-at-5.06.39-pm.png)in the fields tree to add a field from the data source to your output. This will be reflected under the **Data Source Field** in the **Schema** tab.   
If required, modify the **Output Column Name** and the **Column Type**.

{% hint style="warning" %}
**Note:** All numbers are mapped to **doubles** by default. Change this to **`BIGINT`** if you know that your numbers are integers.
{% endhint %}

{% hint style="info" %}
Toggle from **UI** to **SQL** at any point to view the corresponding SQL code for your selected output.  
**See:** [Modify an output in SQL](modifying-the-output-in-sql/)
{% endhint %}

11. Add any required **calculated fields** and review them in the **Calculated Fields** tab.  
 **See:** [Add calculated fields](adding-calculated-fields.md)

12. Add any required **lookups** and review them under the **Calculated Fields** tab. 

{% tabs %}
{% tab title="Adding Lookups" %}
* [from data sources](add-lookups/adding-lookups-from-data-sources.md)
* [from lookup tables](add-lookups/adding-lookups-from-lookup-tables.md)
* [from reference data](add-lookups/adding-lookups-from-reference-data.md)
{% endtab %}
{% endtabs %}

13. Through the **Filters** tab, add a filter like `WHERE` in SQL to the data source.  
**See:** [Add filters](adding-filters.md)

14. Click **Make Aggregated** to turn the output into an aggregated output.   
Read the warning before clicking **OK** and then add the required aggregation.   
This aggregation field will then be added to the **Schema** tab.   
**See:** [Aggregation functions](../../../getting-started/glossary/language-guide/functions/aggregation-functions.md)

15. In the **Aggregation Calculated Fields** area under the **Calculated Fields** tab, add any required calculated fields on aggregations.   
**See:** [Functions](../../../getting-started/glossary/language-guide/functions/), [Aggregation functions](../../../getting-started/glossary/language-guide/functions/aggregation-functions.md)

16. If applicable, partition the data by clicking **More &gt; Manage Partitions** and then selecting the following:

* **Key:** Partitions the data table using one or more fields \(or calculated fields\)
* **Partitioning Time:** Partitions the data table using a specific time field

17. If applicable, keep only the latest event per upsert key by clicking **More &gt; Manage Upserts** and selecting the following:

* **Keys:** A unique key identifying a row in the table
* **Deletions:** The delete key \(events with the value true in their deletion key field will be deleted\)

**See:** [Data types and features](../../../getting-started/glossary/data-types-and-features.md), [How do upserts work?](../../../getting-started/tutorials-and-faq/faq.md#how-do-upserts-work)

{% hint style="info" %}
Click **Preview** at any time to view a preview of your current output.
{% endhint %}

18. Click **Run** and fill out the required fields to properly deploy your output.

{% page-ref page="../running-an-output.md" %}

