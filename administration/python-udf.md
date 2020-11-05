---
description: This article provides information on how to use Python UDFs in Upsolver.
---

# Python UDF

You can extend Upsolver by adding user-defined Python functions through the Python UDF page \(**More &gt; Python UDF**\). These functions can also be disabled once they are no longer needed.

You can also add PMML functions \(version 3.x-4.x\).   
These are parsed using the following library: [https://github.com/jpmml/jpmml-evaluator](https://github.com/jpmml/jpmml-evaluator)

## Add a Python/PMML function

1. From the **Python UDF** page, click **New Python UDF** or click the vertical dots next to it to select **New PMML UDF**.

2. Click **Select**.

3. Once you've selected the file to import from your computer, click **Open**. A list of all the functions defined in the file along with their docstring will appear.

4. Select a function to add by clicking the toggle![](../.gitbook/assets/screen-shot-2020-08-30-at-12.37.43-pm.png) next to it.

5. Once selected, you will be able to configure the input parameters and return value types \(e.g. **Any, String, Number, Boolean**\).

6. Check **Array** next to any input or return value that should be array.

{% hint style="info" %}
You can test out your UDF on a data source by clicking **Preview**. 

A pane will appear on the right where you can select input parameters from an existing data source.
{% endhint %}

7. Click **Add**.

## Rename a Python/PMML function

1. On the **Python UDF** page, click the pencil icon![](../.gitbook/assets/image%20%2824%29.png).

2. Modify the **name** as desired.

3. Click **Update**.

## Disable a Python/PMML function

{% hint style="info" %}
When adding calculated fields, disabled functions will be marked as deprecated and are not available for use.

If you disable a custom function that is already in use \(e.g. in a lookup table enriched using the deprecated function\), the function is still available, ensuring that nothing is broken.
{% endhint %}

1. On the **Python UDF** page, click the X icon![](../.gitbook/assets/screen-shot-2020-08-30-at-12.51.38-pm.png)next to the function to disable.

2. Click **Yes** to confirm.

{% hint style="success" %}
The function has now moved to the **Deprecated Functions** list.
{% endhint %}

## Enable a Python function

1. On the **Python UDF** page, click the check icon![](../.gitbook/assets/image%20%2814%29.png)next to the function to enable under the **Deprecated Functions** list.

2. Click **Yes** to confirm. 

{% hint style="success" %}
The function has now moved to the list of active functions.
{% endhint %}

