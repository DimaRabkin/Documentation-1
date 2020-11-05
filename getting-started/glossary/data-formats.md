---
description: >-
  This page goes over the different data formats available in Upsolver and, if
  applicable, their corresponding configuration options.
---

# Data formats

When creating a data source, the content format is typically auto detected, but you can manually select a format and specify additional details, as required.

The following content formats are supported:

* [Avro](data-formats.md#avro)
* [Parquet](data-formats.md#parquet)
* [ORC](data-formats.md#orc)
* [JSON](data-formats.md#json)
* [CSV](data-formats.md#csv)
* [TSV](data-formats.md#tsv)
* [x-www-form-urlencoded](data-formats.md#x-www-form-urlencoded)
* [Protobuf](data-formats.md#protobuf)
* [Avro-record](data-formats.md#avro-record)
  * For Amazon S3, Azure Blob Storage, Google Cloud Storage or File Upload data sources.
* [Avro-record](data-formats.md#avro-record-1)
  * For Amazon Kinesis, Kafka, S3 Over SQS.
* [Avro with Schema Registry](data-formats.md#avro-with-schema-registry)
* [XML](data-formats.md#xml)

## Avro

The schema is auto detected.

## Parquet

The schema is auto detected.

## ORC

The schema is auto detected.

## JSON

The schema is auto detected. The body should contain the message itself, which should not be url-encoded.

{% tabs %}
{% tab title="Store JSON as String" %}
\(Optional\) Whether to store the JSON in native format in a separate field.
{% endtab %}
{% endtabs %}

## CSV

{% tabs %}
{% tab title="Infer Types" %}
\(Optional\) Select whether to auto detect the types.   
If not selected, Upsolver will read all fields as strings.
{% endtab %}

{% tab title="Header" %}
\(Optional\) The content header. 

If you only add details for one column, additional columns will be labeled as overflow columns.
{% endtab %}

{% tab title="Delimiter" %}
\(Optional\) The delimiter between columns of data.
{% endtab %}

{% tab title="Null Value" %}
\(Optional\) The value to be interpreted as a null value.
{% endtab %}
{% endtabs %}

## TSV

{% tabs %}
{% tab title="Infer Types" %}
\(Optional\) Whether to auto detect the types.
{% endtab %}

{% tab title="Header" %}
\(Optional\) The content header. 

If you only add details for one column, additional columns will be labeled as overflow columns.
{% endtab %}
{% endtabs %}

## **x-www-form-urlencoded**

The body should contain the message itself, which should not be url-encoded.

## Protobuf

{% tabs %}
{% tab title="Schema files" %}
\(Optional\) Click **Select** to choose the required schema files.
{% endtab %}

{% tab title="Main File" %}
\(Optional\) The main file from the list of selected schema files.
{% endtab %}

{% tab title="Message Type" %}
\(Optional\) The message type.
{% endtab %}
{% endtabs %}

## Avro-record

For Amazon S3, Azure Blob Storage, Google Cloud Storage or File Upload data sources.

{% tabs %}
{% tab title="Avro Record Schema" %}
\(Optional\) The Avro record schema.
{% endtab %}
{% endtabs %}

## Avro-record

For Amazon Kinesis, Kafka, S3 Over SQS.

{% tabs %}
{% tab title="Avro Record Schema" %}
The Avro record schema.
{% endtab %}

{% tab title="Bytes Parsers" %}
\(Optional\) A parser for JSON-format schemas.
{% endtab %}

{% tab title="Additional Schemas" %}
\(Optional\) Additional Avro record schemas.
{% endtab %}
{% endtabs %}

## Avro with Schema Registry

{% tabs %}
{% tab title="Schema Registry URL" %}
\(Optional\) The URL to the schema registry.
{% endtab %}
{% endtabs %}

## **XML**

The schema is auto-detected.

