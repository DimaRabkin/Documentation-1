---
description: >-
  This article provides an overview of reference data along with guides on how
  to upload and delete reference data.
---

# Reference data

You can upload reference data, for example, if you purchase third-party data by either importing a file or linking to the data by configuring a connection and file path.

Click **More &gt; Reference Data** to navigate to the **Reference Data** page; there you will find the following information displayed:

{% tabs %}
{% tab title="Name" %}
The name of the reference data.
{% endtab %}

{% tab title="Path" %}
The file path to the reference data.
{% endtab %}

{% tab title="Type" %}
The file type of the reference data \(e.g. Avro, Parquet, ORC, JSON, CSV, TSV, x-www-form-urlencoded, Protobuf, Avro-record, Avro with Schema Registry\).
{% endtab %}

{% tab title="\# Fields" %}
The number of fields in the reference data.
{% endtab %}

{% tab title="\# Rows" %}
The number of rows in the reference data.
{% endtab %}

{% tab title="Description" %}
A description of the reference data.
{% endtab %}
{% endtabs %}

{% hint style="info" %}
From this page, you can also:

* [Upload reference data](reference-data.md#upload-reference-data)
* [Delete reference data](reference-data.md#delete-reference-data)
{% endhint %}

## Upload reference data

1. From the **Reference Data** page, click **New**.

2. Choose to either [import a file](reference-data.md#import-a-file) or [configure a file location](reference-data.md#configure-a-file-location).

3. Click **Preview** to see a preview of the file and the **\# of Rows**, **\# of Fields**, and **Stream Size**.

4. Click **Save**. 

{% hint style="success" %}
The reference data is added and appears in the table in the **Reference Data** page.
{% endhint %}

### Import a file

1. Click **Import**.

2. Select the desired file and click **Open**. 

3. Once the file is uploaded, the file **name** and the **format** is autodetected.

4. \(Optional\) Click **Copy** to copy the location of the uploaded file.   
The location includes the S3 default output storage and the file path \(e.g. **`s3://<bucket-name>/reference-data/d97bf6a1-e41a-42b1-af49-6b8702761576/1000 Sales Records.csv`** where **`reference-data/d97bf6a1-e41a-42b1-af49-6b8702761576/1000 Sales Records.csv`** is the file path\).

### Configure a file location

1. Select a **connection** \(or [create a new connection](connections/)\) and enter the **file path**.

2. Change the **name** if required.

3. Select the **content format** and fill in the corresponding fields if necessary.

{% tabs %}
{% tab title="Auto Detect Types" %}
For CSV, TSV and x-www-form-urlencoded formats, you can select to auto detect the types.
{% endtab %}

{% tab title="Header" %}
For CSV and TSV formats, the content header.   
If you only add details for one column, additional columns will be labeled as overflow columns.
{% endtab %}

{% tab title="Delimiter" %}
For CSV format, the delimiter between columns of data.
{% endtab %}

{% tab title="Null Value" %}
For CSV format, the value to be interpreted as a null value.
{% endtab %}

{% tab title="Schema" %}
For Protobuf format, you can click **Select** to choose the required schema files.
{% endtab %}

{% tab title="Main File" %}
For Protobuf format, select the main file from the list of selected schema files.
{% endtab %}

{% tab title="Message Type" %}
For Protobuf format, enter the message type.
{% endtab %}
{% endtabs %}

## Delete reference data

When you delete reference data, the link to the reference data is removed from Upsolver. The data itself is not deleted.

1. Click **MORE**.
2. Select **Reference Data**.
3. Click ![](../.gitbook/assets/image%20%282%29.png).

