---
description: >-
  This page provides a guide on how to add lookups from data sources in
  Upsolver.
---

# Add lookups from data sources

1. Click **Add Lookup** or in the **Calculated Fields** tab, under **Lookups**, click![](../../../../.gitbook/assets/screen-shot-2020-08-28-at-11.12.30-am.png).

2. In the **Data Source** tab, select a source for your lookup.

3. Click **Next**.

4. Under **Join Fields**, select the fields to use as key columns.

5. Select at least one **aggregation** and the **field** to apply it to.  
**See:** [Aggregation functions](../../../../getting-started/glossary/language-guide/functions/aggregation-functions.md)

6. Select the desired **time frame**; this enables you to sync your data sources. 

{% hint style="info" %}
When joining two streams, they may not be completely in sync \(there may be a lead or lag\). 

An event in data source A may arrive before or after the corresponding event in data source B. The time frame is the period before and after the event in data source A arrives, to look for the join event in data source B. 

**Example:** If time frame is set to -1 and 2 hours, the system looks for a matching event in data source B in the period one hour before and two hours after the time the event arrived in data source A. ![](../../../../.gitbook/assets/screen-shot-2020-08-28-at-11.53.23-am.png)
{% endhint %}

You can also set the time frame to infinite by checking **Infinite From**. This ensures you can access all the data irrespective of when it was written.

7. Check **Use Full History** to use all the data that was available when deploying this output for historical lookups. 

{% hint style="info" %}
When joining a stream and a lookup, generally you use the **time** field for the join. As you move forward with the stream, you join to the lookup based on the time in the lookup. 

This applies to the past data too; if processing an output for the past 12 months, the time in the lookup is used to match to the stream. This will not work in cases such as joining a stream with a year of data to a static table which has just recently been dumped. 

In this case in order to join this data, check **Use Full History**. The time of the original event is then disregarded; instead the current time is used to perform the join \(e.g. it uses the latest state of the data\).
{% endhint %}

8. ****Decide whether or not to implement an **inner join**.

9. Select where to locate the calculated field \(e.g. **root**, **data**\) and **name** this field. This operation joins the input arrays using a cartesian product.

{% hint style="info" %}
The fields are typically added at the **root** level, however on occasion you can opt to co‑locate a field with another element in the hierarchy.
{% endhint %}

10. Click **Preview** to review your calculated field before saving; a **Field Content Samples** panel will appear on the right.

11. To add columns to the preview, click **Choose Columns** and select the desired columns. Then click **Update**.

12. Click **Save**.

{% hint style="success" %}
You can now find this lookup under **Lookups** in the sidebar or under the **Calculated Fields tab**.
{% endhint %}

