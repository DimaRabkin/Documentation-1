---
description: >-
  This page provides a guide on how to add calculated fields to outputs in
  Upsolver.
---

# Add calculated fields

You can add calculated fields to lookup tables and outputs. 

Calculated fields are fields based on a function of one or more fields. These can be a combination of built-in functions and [your own Python functions](../../../administration/python-udf.md).

If the calculated field results in a boolean response, you can define whether the resulting calculation should be saved as a whitelist filter or a blacklist filter.

## To add calculated fields

1. Click **Add Calculated Field** or under the **Calculated Fields** tab, click the add icon![](../../../.gitbook/assets/screen-shot-2020-08-28-at-11.12.30-am.png).

{% hint style="info" %}
**See:** [Functions](../../../getting-started/glossary/language-guide/functions/) to learn more about a specific calculated field.
{% endhint %}

2. Click **Select** next to the desired calculated function.

3. From the dropdown, select the **values** to use for each required **input**.   
You can also click on the hierarchy icon![](../../../.gitbook/assets/screen-shot-2020-08-28-at-11.19.45-am.png)to review the available fields in your data.  
Additionally, click on the add icon![](../../../.gitbook/assets/image%20%2891%29.png)to add another calculation within this function.

4. If the calculated field results in a **boolean** response, select whether the **Filter Type** is:

* **Whitelist:** if result `True`, keep record
* **Blacklist:** if result `True`, discard record

{% hint style="info" %}
Once saved, the resulting filter will appear in the **Filters** tab under **Whitelist Filters** or **Blacklist Filters** respectively.
{% endhint %}

5. Select where to locate the calculated field \(e.g. **root**, **data**\) and **name** this field. This operation joins the input arrays using a cartesian product.

{% hint style="info" %}
The fields are typically added at the **root** level, however on occasion you can opt to co‑locate a field with another element in the hierarchy.
{% endhint %}

6. Click **Preview** to review your calculated field before saving; a **Field Content Samples** panel will appear on the right.

7. To add columns to the preview, click **Choose Columns** and select the desired columns. Then click **Update**.

{% hint style="info" %}
Toggle from **From** to **Code** to review the calculated field as code.
{% endhint %}

8. Click **Save**.

{% hint style="success" %}
You have now successfully created a calculated field.
{% endhint %}

