---
description: This article provides a guide on how to duplicate an output in Upsolver.
---

# Duplicate an output

All the outputs behave in a similar way. This means that you can:

1. Create an output.
2. Duplicate the output and modify the configuration \(e.g. change the type of the destination output\).
3. Run the duplicated output. This writes to new tables.

{% hint style="warning" %}
**Note:** Duplication warnings appear if there are any differences between the source output and the destination output \(e.g. if the upsert key is changed due to it not being supported in the destination output or any field type changes\). **See:** [Data types and features](../../getting-started/glossary/data-types-and-features.md)
{% endhint %}

## Duplicate an output

1. From the **Outputs** page, select the output you wish to duplicate.

2. Click **Duplicate**.

3. If necessary, change any of the following fields:

* **Name:** The name of the new output.
* **Data Sources:** The data source\(s\).
* **Output to:** Output type.

4. Click **Next**.

5. \(Optional\) Complete the fields for the new output location. These vary depending on the type of output.   
**See:** [Database output options](../../getting-started/glossary/database-output-options.md) for database outputs.

6. Click **Next**.

