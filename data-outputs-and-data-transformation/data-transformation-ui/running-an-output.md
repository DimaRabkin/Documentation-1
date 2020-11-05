---
description: This page provides a general guide on how to run an output in Upsolver.
---

# Run an output

Once you run an output it becomes immutable \(as it is a production task\); this is to ensure data lineage.

You can also:

{% tabs %}
{% tab title="Edit an output" %}
If you then run the edited output, it automatically writes to a different location.   
It is therefore possible to identify which files were created by a specific output.

**See:** [Edit an output](editing-an-output.md)
{% endtab %}

{% tab title="Duplicate an output" %}
Once duplicated, the output can be modified as required \(e.g. change the type of the destination output\).

**See:** [Duplicate an output](duplicating-an-output.md)
{% endtab %}
{% endtabs %}

## To run an output

1. From the **Outputs** page, select the output that you want to run.

2. Click **Run**.

3. If applicable, select the **S3 Storage** to store the data of the table. 

{% hint style="info" %}
The access key of this storage must belong to the same AWS account as the access key of the connection.
{% endhint %}

4. Complete any other fields \(these vary according to the output type\):

{% tabs %}
{% tab title="Hive Metastores" %}
Select **Qubole, Athena,** or **Redshift Spectrum**.
{% endtab %}

{% tab title="Connection" %}
The required connection.

**See:** [Connections](../../administration/connections/)
{% endtab %}

{% tab title="Database Name" %}
The database name.
{% endtab %}

{% tab title="Schema" %}
The schema within the database.
{% endtab %}

{% tab title="Table Name" %}
The table to create. Table names are case-insensitive.

**Note:** Apache Spark requires lowercase table names.
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**See:** [Data outputs](../data-outputs/) for details regarding a specific output type.
{% endhint %}

5. \(Optional\) To add an additional table, click **Add** and specify the options as described in the previous step.

6. Click **Next** and complete the following:

{% tabs %}
{% tab title="Compute Cluster" %}
Select the compute cluster to run the calculation on.  
Alternatively, click the drop-down and [create a new compute cluster](../../administration/managing-clusters/#adding-a-compute-cluster).
{% endtab %}

{% tab title="Processing Time Range" %}
The range of data to process.   
This can start from the data source beginning, now, or a custom date and time. This can never end, end now, or end at a custom date and time.
{% endtab %}
{% endtabs %}

7. Click **Deploy**. 

{% hint style="info" %}
Once the output shows as **Running** in the output panel, it is live in production and consuming compute resources.
{% endhint %}

