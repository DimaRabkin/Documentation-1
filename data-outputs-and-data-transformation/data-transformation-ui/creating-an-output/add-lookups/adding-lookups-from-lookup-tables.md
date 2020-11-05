---
description: >-
  The page provides a guide on how to add lookups from lookup tables in
  Upsolver.
---

# Add lookups from lookup tables

1. Click **Add Lookup** or in the **Calculated Fields** tab, under **Lookups**, click![](../../../../.gitbook/assets/screen-shot-2020-08-28-at-11.12.30-am.png).

2. Under the **Lookup Table** tab, select a source for your lookup.

{% hint style="warning" %}
The lookup table you wish to use must be currently **running**.  
**See:** [Lookup table data output](../../../data-outputs/lookup-table-output/) if you have not yet created a lookup table.
{% endhint %}

3. Click **Next**.

4. Select a **lookup table time offset**; this enables you to sync your data. 

{% hint style="info" %}
When joining, the data source and the lookup table may not be completely in sync \(there may be a lead or a lag\). 

An event in the data source may arrive before or after the corresponding event in the lookup table. 
{% endhint %}

{% tabs %}
{% tab title="Current" %}
Use the same time as the data.
{% endtab %}

{% tab title="Past" %}
Set an interval in the past.
{% endtab %}

{% tab title="Future" %}
Set an interval in the future.

**Note:** The output will only be written once this future interval has passed.
{% endtab %}
{% endtabs %}

5. Check **Use Full History** to use all the data that was available when deploying this output for historical lookups. 

{% hint style="info" %}
When joining a stream and a lookup, generally you use the **time** field for the join. As you move forward with the stream, you join to the lookup based on the time in the lookup. 

This applies to the past data too; if processing an output for the past 12 months, the time in the lookup is used to match to the stream. This will not work in cases such as joining a stream with a year of data to a static table which has just recently been dumped. 

In this case in order to join this data, check **Use Full History**. The time of the original event is then disregarded; instead the current time is used to perform the join \(e.g. it uses the latest state of the data\).
{% endhint %}

6. Check **Filter Missing** to to filter out records that don't have a matching result from this lookup \(like `INNER JOIN` in SQL\).

7. Under **Map Key Fields**, map the lookup keys and the time field. 

{% hint style="info" %}
The field **time** is the time that the event was processed by Upsolver.   
You may choose a different field for synching purposes.
{% endhint %}

8. Select where to locate the calculated field \(e.g. **root**, **data**\) and **name** this field. This operation joins the input arrays using a cartesian product.

{% hint style="info" %}
The fields are typically added at the **root** level, however on occasion you can opt to co‑locate a field with another element in the hierarchy.
{% endhint %}

9. Click **Preview** to review your calculated field before saving; a **Field Content Samples** panel will appear on the right.

10. To add columns to the preview, click **Choose Columns** and select the desired columns. Then click **Update**.

11. Click **Save**.

{% hint style="success" %}
You can now find this lookup under **Lookups** in the sidebar or under the **Calculated Fields tab**.
{% endhint %}

