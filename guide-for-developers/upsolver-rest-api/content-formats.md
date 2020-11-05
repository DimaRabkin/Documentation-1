---
description: >-
  This page provides a guide on how to configure different content formats in
  Upsolver using API calls.
---

# API content formats

## Auto-Detect

#### Example

```http
{
	"clazz" : "AutoDetectContentType"
}
```

## Avro

#### Example

```http
{
	"clazz" : "AvroContentType"
}
```

## Parquet

#### Example

```http
{
	"clazz" : "ParquetContentType"
}
```

## ORC

#### Example

```http
{
	"clazz" : "OrcContentType"
}
```

## JSON

JSON data. Multiple JSONs can be read from a single file/record by appending them with optional whitespace in between.

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| nestedJsonPaths | Nested Json Paths | \[\]\[\] | Paths to string fields that contain a "stringified" JSON that should be parsed into the schema. Each such path is represented as an array of the path parts. | + |
| nestedJsons | Nested Jsons | NestedPath\[\] | Paths to string fields that contain a "stringified" JSON that should be parsed into the schema. Each such path is represented as an array of the path parts. | + |
| splitRootArray | Split Root Array | Boolean | If the root object is an array, it can either be parsed as separate events, or as a single event which contains only an array. | + |
| keepOriginalNestedJsonString | Keep Original Nested Json String | Boolean | When using the nestedJsonPaths parameter, the original JSON string can optionally be kept in addition to the parsed value. If this is selected, the parsed data is stored in a record with the suffix `_parsed`. | + |
| storeJsonAsString | Store Json As String | Boolean | Whether to store the JSON in native format in a separate field. | + |

#### Example

```http
{
	"clazz" : "JsonContentType"
}
```

## CSV

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| inferTypes | Infer Types | Boolean | Whether or not to infer types. If not selected, Upsolver will read all fields as strings. |  |
| header | Header | String | If applicable, the header of the file. If you only add details for one column, additional columns will be labeled as overflow columns. |  |
| delimiter | Delimiter | Char | The delimiter between columns of data. | + |
| nullValue | Null Value | String | If applicable, the default null value in the data. | + |
| nestedJsons | Nested Jsons | NestedPath\[\] | Paths to string fields that contain a "stringified" JSON that should be parsed into the schema. Each such path is represented as an array of the path parts. | + |
| keepOriginalNestedJsonString | Keep Original Nested Json String | Boolean | When using the nestedJsonPaths parameter, the original JSON string can optionally be kept in addition to the parsed value. If this is selected, the parsed data will be stored in a record with the suffix `_parsed`. | + |

#### Example

```http
{
	"clazz" : "CsvContentType",
	"inferTypes" : true,
	"header" : "header1,header2,header2"
}
```

## TSV

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| inferTypes | Infer Types | Boolean | Whether or not to infer types. If not selected, Upsolver will read all fields as strings. |  |
| header | Header | String | If applicable, the header of the file. If you only add details for one column, additional columns will be labeled as overflow columns. |  |
| nestedJsons | Nested Jsons | NestedPath\[\] | Paths to string fields that contain a "stringified" JSON that should be parsed into the schema. Each such path is represented as an array of the path parts. | + |
| keepOriginalNestedJsonString | Keep Original Nested Json String | Boolean | When using the nestedJsonPaths parameter, the original JSON string can optionally be kept in addition to the parsed value. If this is selected, the parsed data will be stored in a record with the suffix `_parsed`. | + |

#### Example

```http
{
	"clazz" : "TsvContentType",
	"inferTypes" : true,
	"header" : "header1,header2,header2"
}
```

## x-www-form-urlencoded

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| inferTypes | Infer Types | Boolean | Whether or not to infer types. If not selected, Upsolver will read all fields as strings. |  |

#### Example

```http
{
	"clazz" : "WWWFormUrlEncodedType",
	"inferTypes" : true,
}
```

## Protobuf

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| schemaFiles | Schema Files | SchemaFile\[\] |  |  |
| mainFile | Main File | String | The main file from the list of selected schema files. |  |
| messageType | Message Type | String | The message type. |  |
| bytesParsers | Bytes Parsers | BytesParser\[\] | BytesParsers can be used to define special parsing behavior for 'bytes' fields in the schema. |  |
| bytesParsers.path | Path | String | The path to the field that should use this parser. |  |
| bytesParsers.parserSchema | Parser Schema | String | The schema that the parser will use.  In CSV and TSV formats, it should be a comma-delimited list of the field names in the CSV/TSV rows.  In the Avro format, it should be the Avro schema used to decode the bytes of the inner field. | + |
| bytesParsers.schemaType | Schema Type | String | The type of parser to use. Supported types are JSON, CSv, TSF, or Avro. | + |

#### Example

```http
{
	"clazz" : "ProtobufContentType",
	"schemaFiles" : "schemaFiles",
	"mainFile" : "mainFile",
	"messageType" : "messageType",
	"bytesParsers" : "bytesParsers"
}
```

## Avro-record

Individual Avro records without the framing or schema.

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| schema | Schema | String | The Avro schema used to decode the messages. Note that the behavior is undefined if the schema does not match the data. |  |
| bytesParsers | Bytes Parsers | BytesParser\[\] | BytesParsers can be used to define special parsing behavior for 'bytes' fields in the schema. | + |
| bytesParsers.path | Path | String | The path to the field that should use this parser. |  |
| bytesParsers.parserSchema | Parser Schema | String | The schema that the parser will use. In CSv and TSV formats, it should be a comma-delimited list of the field names in the CSV/TSV rows.  In the Avro format, it should be the Avro schema used to decode the bytes of the inner field. | + |
| bytesParsers.schemaType | Schema Type | String | The type of parser to use. Supported types are JSON, CSV, TSV, or Avro. | + |

#### Example

```http
{
	"clazz" : "AvroRecordContentType",
	"schema" : "{ \"type\": \"record\", \"name\": 
\"root\", \"fields\": [ {\"name\": \"value\", \"type\": 
\"string\" } ] }"
}
```

## Avrow/ Schema Registry

Individual Avro records with schema provided by Schema Registry.

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| schemaRegistryUrl | Schema Registry Url | String | The URL of getting schema where `{id}` is the ID of the schema. |  |
| schemaRegistryFormat | Schema Registry Format | SchemaRegistryFormat | The strategy used to encode the schema version into every message. | + |
| bytesParsers | Bytes Parsers | BytesParser\[\] | BytesParsers can be used to define special parsing behavior for 'bytes' fields in the schema. |  |
| bytesParsers.path | Path | String | The path to the field that should use this parser. |  |
| bytesParsers.parserSchema | Parser Schema | String | The schema that the parser will use.  In CSV and TSV formats, it should be a comma-delimited list of the field names in the CSV/TSV rows. In the Avro format, it should be the Avro schema used to decode the bytes of the inner field. | + |
| bytesParsers.schemaType | Schema Type | String | The type of parser to use. Supported types are JSON, CSV, TSV, or Avro. | + |

#### Example

```http
{
	"clazz" : "AvroSchemaRegistryContentType",
	"schemaRegistryUrl" : "schemaRegistryUrl"
}
```

## XML

XML data. Multiple XMLs can be read from a single file/record by appending them with optional whitespace in between.

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| storeRootAsString | Store Root As String | Boolean | Whether to store the XML root in native format in a separate field. | + |

#### Example

```http
{
	"clazz" : "XmlContentType",
}
```

