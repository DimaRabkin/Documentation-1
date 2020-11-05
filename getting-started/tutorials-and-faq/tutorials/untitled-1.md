---
description: >-
  This article walks through a use case on how to do upserts and deletions in
  Upsolver.
---

# Upsert and delete use case

**Note:** This use case builds on the [AWS S3 to Athena simple use case](aws-s3-to-athena-use-case.md). 

Upsolver ingests raw data. You can upsert or delete events in the data lake when compaction takes place by adding an upsert.

{% tabs %}
{% tab title="Upserts" %}
When compaction takes place, only the last events per upsert key are kept. 

The upsert is the identifier of each row that is updated \(e.g. if you wanted to keep only the latest event per **host**, add the host field as the **Upsert Key**\).
{% endtab %}

{% tab title="Deletions" %}
When compaction takes place, events marked for deletion based on the delete key are deleted. 

To delete data from the data lake, you must have a boolean field which indicates when an event must be deleted. When this **Is Delete Key** field is **`true`**, the event is deleted.

If you do not have a boolean field in the source data, you can create one by using an enrichment function that returns a boolean value. 

For example, to delete all records which arrived before a specific date \(in Epoch seconds\), use the `LESS_THAN` enrichment function to create a boolean field, and then use it as the **Is Delete Field**.
{% endtab %}
{% endtabs %}

{% hint style="info" %}
#### Required Level of Expertise

* Intermediate
{% endhint %}

## Add upsert and delete keys

1. In your output, click **More &gt; Manage Upserts** and select your **upsert key**.

2. **Close** the upserts window.

{% hint style="info" %}
Now if you toggle your view from **UI** to **SQL**, you will find that the upsert key appears as `REPLACE ON DUPLICATE <UPSERT KEY>` after the `SELECT` statement.
{% endhint %}

3. Now to add a delete key, click on **More &gt; Manage Upserts** again and then select the **Deletions** tab.

4. Open the **Delete Indicator Field** dropdown and select one of the boolean fields for deletion.

5. Run the output to create the table in Athena \(the data will arrive within a couple of minutes\).  
**See:** [Running an output](../../../data-outputs-and-data-transformation/data-transformation-ui/running-an-output.md)

{% hint style="success" %}
Once the output is **Running**, to view the data in Athena, select the **Properties** tab and click on **Go to AWS Athena Console** in the sidebar.
{% endhint %}

