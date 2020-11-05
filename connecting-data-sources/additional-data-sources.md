---
description: >-
  This article provides an introduction to how Upsolver works with file uploads
  along with a guide on how to upload files as a data source in Upsolver.
---

# File upload data source

## How Upsolver works with file upload

Upsolver supports uploading files, which is useful for an end-to-end, one-off data outsource test. 

{% hint style="warning" %}
The uploaded files are not linked to the source files. To work with linked data, use [reference data](../administration/reference-data.md).
{% endhint %}

If a file is compressed, Upsolver will automatically detect the compression type.

{% hint style="info" %}
Supported compression types are: **Zip, GZip, Snappy,** and **None**.   
Upsolver supports ZIP files that contain files of the same type. 

**Note:** There is a file upload limit of 100mb \(per file\).
{% endhint %}

The schema will be auto-detected for **self-describing formats** like JSON; you will be prompted to add header information for other formats.

For **x-www-form-urlencoded** content, the body should contain the message itself, which should not be url-encoded.

## Create a file upload data source

1. From the **Data Sources** page, click **New**.

2. Select **File Upload**.

3. Drag and drop the files onto the page or click **Browse** to select the required files.

4. **Name** this data source \(defaults to the file name\).

5. Select the **content format**. This is typically auto-detected, but you can manually select a format. 

{% hint style="info" %}
If necessary, configure the content format options.   
**See:** [Data formats](../getting-started/glossary/data-formats.md)
{% endhint %}

6. Click **Continue** to preview your data and review the following metrics:

* **Sample Size**
* **Parsed Successfully** 
* **\# of Errors**

7. \(Optional\) If there are any errors, click **Back** to change the settings as required.

8. Click **Create**.

{% hint style="success" %}
You can now use your uploaded data source.
{% endhint %}

