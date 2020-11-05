---
description: >-
  This article provides brief guide on how to create an Amazon S3 data source in
  Upsolver.
---

# Amazon S3 data source

Creating an Amazon S3 data source on Upsolver is very simple. 

Upsolver will auto-detect the file formats date pattern and show you a preview of the top files to be ingested with their corresponding dates. It will also auto-detect when to start the ingestion from. 

By default, data will be ingested into the default target storage.

{% hint style="info" %}
There is also an [**Advanced option**](full-guide-s3-data-source.md) available to customize the data source by: 

* specifying a file name pattern
* specifying the content format and its associated content format options  \(e.g. custom delimiter for CSV\)
* selecting a specific compute cluster
* selecting a target storage option
{% endhint %}

{% page-ref page="quick-guide-s3-data-source-1.md" %}

{% page-ref page="full-guide-s3-data-source.md" %}

## Create an Amazon S3 data source:

1. From the **Data Sources** page, click **New**.

2. Select **Amazon S3**. 

{% hint style="info" %}
As you fill in the fields, the top matching files with their dates appear in the **Preview** pane on the right.

* ![](../../../.gitbook/assets/screen-shot-2020-08-26-at-9.52.52-am.png)indicates that the file is recognized and will be included in the data source ingestion.
* ![](../../../.gitbook/assets/screen-shot-2020-08-26-at-9.51.50-am.png)indicates that the file will not be included.

You can click **Refresh** to check on their status as you update fields.
{% endhint %}

3. Select the **Amazon S3** **bucket** to read from.

4. \(Optional\) Enter the **path** to the **data** **folder** in the Amazon S3 bucket \(e.g. billing data\).  
If this is not specified, the data is assumed to be in the top-level of the hierarchy. 

{% hint style="info" %}
Upsolver adds an implicit **`/`** before and after the folder. 

For example, if you have bucket **`a`**, with folder **`b`**, Upsolver looks for the path: **`s3://a/b/yyyy-MM-dd`**
{% endhint %}

5. In **Glob File Pattern**, specify the **file set to ingest** by using a file pattern with wildcard characters \(where \* means ingest all files\).

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

8. **Name** this data source.

9. \(Optional\) If you would like to **customize** the data source by:

* specifying a file name pattern
* specifying the content format and its associated content format options  \(e.g. custom delimiter for CSV\)
* selecting a specific compute cluster
* selecting a target storage option

{% hint style="info" %}
**See:** [Advanced options](full-guide-s3-data-source.md)
{% endhint %}

10. Click **Continue**.

{% hint style="info" %}
If the content type is not automatically identified, you will be prompted to select the **Content Format** and configure any related options.   
**See:** [Data formats](../../../getting-started/glossary/data-formats.md)
{% endhint %}

11. In the S3 Bucket Integration window, click **Launch Integration** to launch the AWS CloudFormation page in a new tab.

12. Check the **I acknowledge** statement and click **Create Stack**.

{% hint style="success" %}
Once the stack has been successfully created with the required resources, the message in Upsolver will disappear automatically. 

You can now use your Amazon S3 data source.
{% endhint %}

