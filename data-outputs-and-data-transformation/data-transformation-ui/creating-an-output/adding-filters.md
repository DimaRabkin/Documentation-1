---
description: This page provides a guide on how to add a filter to outputs in Upsolver.
---

# Add filters

You can add whitelist and blacklist filters to a lookup table or an output based on calculated fields that are a function of one or more fields. These functions can be a combination of built-in functions and [your own Python functions](../../../administration/python-udf.md).

## To add a filter

1. Click **Add Filter** or in the **Filters** tab, click **Add Filter**.

{% hint style="info" %}
**See:** [Functions](../../../getting-started/glossary/language-guide/functions/) to learn more about a specific filter function.
{% endhint %}

2. Click **Select** next to the desired filter function.

3. From the dropdown, select the **values** to use for each required **input**.   
You can also click on the hierarchy icon![](../../../.gitbook/assets/screen-shot-2020-08-28-at-11.19.45-am.png)to review the available fields in your data.  
Additionally, click on the add icon![](../../../.gitbook/assets/image%20%2891%29.png)to add another calculation within this function.

4. Decide whether the **Filter Type** is:

* **Whitelist:** if result `True`, keep record
* **Blacklist:** if result `True`, discard record

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
The resulting filter can now be found in the **Filters** tab under **Whitelist Filters** or **Blacklist Filters** respectively.
{% endhint %}

