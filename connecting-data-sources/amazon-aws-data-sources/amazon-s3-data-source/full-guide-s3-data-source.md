---
description: >-
  This article provides a full guide on how to create an Amazon S3 data source
  in Upsolver with information on how to configure the advanced settings.
---

# Full guide: S3 data source

## Create an Amazon S3 data source \(Advanced\)

1. From the **Data Sources** page, click New.

2. Select **Amazon S3**.

3. Scroll down and select the **Advanced** option.

{% hint style="info" %}
As you fill in the fields, the top matching files with their dates appear in the **Preview** pane on the right.

* ![](../../../.gitbook/assets/screen-shot-2020-08-26-at-9.52.52-am.png)indicates that the file is recognized and will be included in the data source ingestion.
* ![](../../../.gitbook/assets/screen-shot-2020-08-26-at-9.51.50-am.png)indicates that the file will not be included.

You can click **Refresh** to check on their status as you update fields.
{% endhint %}

4. From the dropdown, select the desired **S3 connection** \(or [create a new one](../../../administration/connections/amazon-s3-connection.md)\).

5. \(Optional\) Enter the **path** to the **data** **folder** in the Amazon S3 bucket \(e.g. billing data\).  
If this is not specified, the data is assumed to be in the top-level of the hierarchy. 

{% hint style="info" %}
Upsolver adds an implicit **/** before and after the folder. 

For example, if you have bucket **a**, with folder **b**, Upsolver looks for the path: **`s3://a/b/yyyy-MM-dd`**
{% endhint %}

{% hint style="warning" %}
The **full path** displayed is read only. You can use it to review the path Upsolver is using to read from S3.
{% endhint %}

6. Select or enter in the **date pattern** of the files to be ingested.  
This is autodetected but can be modified if required. 

{% hint style="info" %}
The following characters are valid: **`yyyy MM dd HH mm`**

Any other letters or characters must be wrapped in single quotes   
\(e.g. `'year='yyyy'month='MM'day='dd'hour='HH'minutes='mm`\). 

It is also possible to specify the date as follows: `d-M-yy`
{% endhint %}

7. \(Optional\) Select a time to **start ingesting files** **from**.  
This is usually auto detected, but if there is no preview, the date cannot be established and this defaults to today's date. In this case, set the required start date.

8. \(Optional\) Under **File Name Pattern**, select the **type of pattern** to use \(**All, Starts With, Ends With, Regular Expression,** or **Glob Expression**\) and then enter the **file name pattern** that specifies the file set to ingest. 

{% hint style="info" %}
If all the files in specified folders are relevant, select **All**. 

The pattern given is matched against the file path starting from the **full path** shown above.
{% endhint %}

9. Select the **content format**.   
This is typically auto-detected, but you can manually select a format \(**Avro, Parquet, ORC, JSON, CSV, TSV, x-www-form-urlencoded, Protobuf, Avro-record, Avro with Schema Registry,** or **XML**\). 

{% hint style="info" %}
If necessary, configure the content format options.   
**See:** [Data formats](../../../getting-started/glossary/data-formats.md)
{% endhint %}

10. From the dropdown, select a **compute cluster** \(or [create a new one](../../../administration/managing-clusters/cluster-types/adding-a-compute-cluster.md)\) to run the calculation on. 

{% hint style="warning" %}
A ![](../../../.gitbook/assets/screen-shot-2020-08-13-at-5.48.22-pm.png) may appear. This warning can be ignored for POCs \(proof of concept\). 

For production environments, this indicates that if you run your task retroactively \(**Start Ingestion From**\), your compute cluster will process a burst of additional tasks, possibly causing delays in outputs and lookup tables running on this cluster. 

To prevent this, go to the **Clusters** page to edit your cluster and set the **Additional Processing Units For Replay** to a number greater than 0.
{% endhint %}

11. Select a **target storage connection** \(or [create a new one](../../../administration/connections/)\) where the data read will be stored \(output storage\).

12. \(Optional\) In addition to the streaming data, you may have initial data.   
In this case, to list the relevant data, enter a **file name prefix** \(e.g. for DMS loads, enter LOAD\) under **Initial Load Configuration**.

13. \(Optional\) Under Initial Load Configuration, enter a **regex pattern** to select the required files.

14. **Name** this data source.

15. Click **Continue**. A preview of the data will appear.

16. For CSV, select a **Header**.

17. Click **Continue** again. 

{% hint style="info" %}
Parsed data samples will appear and you can review the **Sample Size**, **Parsed Successfully**, and **\# of Errors**.
{% endhint %}

18. \(Optional\) If there are any errors, click **Back** to change the settings as required.

19. Click **Create**.

{% hint style="success" %}
You can now use your Amazon S3 data source.
{% endhint %}

