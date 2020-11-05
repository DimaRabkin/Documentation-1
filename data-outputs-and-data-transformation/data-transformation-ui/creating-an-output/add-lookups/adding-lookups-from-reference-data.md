---
description: >-
  This article provides a guide on how to add lookups to lookup tables (or
  outputs) from reference data.
---

# Adding lookups from reference data

1. Click **Add Lookup** or in the **Calculated Fields** tab, under **Lookups**, click![](../../../../.gitbook/assets/screen-shot-2020-08-28-at-11.12.30-am.png).

2. Under the **Reference Data** tab, select a source for your lookup \(or [create a new one](../../../../administration/reference-data.md)\).

3. Click **Next**.

4. Under **Key Fields**, select the fields to use as key columns and map it to a field in your output.

5. \(Optional\) Select the **value fields**.

6. Under **Refresh Interval Seconds**, input the number of seconds between attempts to refresh the reference data file.

7. Select where to locate the calculated field \(e.g. **root**, **data**\) and **name** this field. This operation joins the input arrays using a cartesian product.

{% hint style="info" %}
The fields are typically added at the **root** level, however on occasion you can opt to co‑locate a field with another element in the hierarchy.
{% endhint %}

8. Click **Preview** to review your calculated field before saving; a **Field Content Samples** panel will appear on the right.

9. To add columns to the preview, click **Choose Columns** and select the desired columns. Then click **Update**.

10. Click **Save**.

{% hint style="success" %}
You can now find this lookup under **Lookups** in the sidebar or under the **Calculated Fields tab**.
{% endhint %}

