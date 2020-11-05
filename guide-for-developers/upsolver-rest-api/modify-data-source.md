---
description: This article provides a guide on how to modify data sources using an API call.
---

# Modify a data source

This API enables you to modify an existing data source. All API calls require an [API token](./).

```http
PATCH https://api.upsolver.com/inputs/DATA-SOURCE-ID
```

## Toggle soft retention

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| softRetention | Soft Retention | Boolean | This setting prevents data deletion when the retention policy in Upsolver activates. When enabled, the metadata is purged but the underlying data \(e.g. S3 object\) is not deleted. |  |

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "ToggleSoftRetention",
	"softRetention" : true
}' "https://api.upsolver.com/inputs/DATA-SOURCE-ID"
```

## Update retention

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| retention | Retention | Int \(Minutes\) | The retention period for the data in Upsolver. | + |

#### Example

```bash
curl -X POST -H "content-type: application/json" -H "Authorization: 
YOUR_TOKEN" \
-d '{
	"clazz" : "UpdateRetention",
	"retention" : 1440
}' "https://api.upsolver.com/inputs/DATA-SOURCE-ID"
```

## Update end execution at

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| endExecutionAt | End Read At | String \(ISO-8601\) | Stop reading after this date. | + |

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "UpdateEndExecutionAt",
	"endExecutionAt" : "2018-11-04T08:00:00Z"
}' "https://api.upsolver.com/inputs/DATA-SOURCE-ID"
```

## Set ingestion environment

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| environment | Ingestion Cluster | String | The compute cluster to run the calculation on.  **See:** [Compute cluster](../../administration/managing-clusters/#adding-a-compute-cluster) |  |

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
 "clazz" : "SetIngestionEnvironment",
 "environment" : "09267786-8d84-4644-adac-52601b9609bb"
}' "https://api.upsolver.com/inputs/DATA-SOURCE-ID"
```

## Set compute environment

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| environment | Environment | String | The compute cluster to run the calculation on.  **See:**[ Compute cluster](../../administration/managing-clusters/#adding-a-compute-cluster) |  |

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
  "clazz" : "SetComputeEnvironment",
  "environment" : "12ba7222-5764-4d37-8581-95ca5be4b3f7"
}' "https://api.upsolver.com/inputs/DATA-SOURCE-ID"
```

## Rename

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| name | Name | String | The data source name. |  |

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "Rename",
	"name" : "NEW_NAME"
}' "https://api.upsolver.com/inputs/DATA-SOURCE-ID"
```

## Update parallelism

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| parallelism | Parallelism | Int | The number of independent shards to parse data, to increase parallelism and reduce latency.  This should remain 1 in most cases. |  |

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "UpdateParallelism",
	"parallelism" : 1
}' "https://api.upsolver.com/inputs/DATA-SOURCE-ID"
```

## Update shard parallelism

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| parallelism | Parallelism | Int | The number of independent shards to parse data, to increase parallelism and reduce latency.  This should remain 1 in most cases. |  |

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "UpdateShardParallelism",
	"shards" : 1
}' "https://api.upsolver.com/inputs/DATA-SOURCE-ID"
```

## Update content type

#### Fields

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Optional</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">contentType</td>
      <td style="text-align:left">Content Type</td>
      <td style="text-align:left">ContentType</td>
      <td style="text-align:left">
        <p>The format of the messages. Supported formats are: JSON, AVRO, CSV, TSV,
          ORC, Protobuf and x-www-form-urlencoded.</p>
        <p>For self-describing formats like JSON, the schema is auto-detected. The
          body should contain of the message should contain the message itself, which
          should not be url-encoded.</p>
        <p>Messages can be compressed, Upsolver automatically detects the compression
          type.</p>
        <p>Supported compression types are: Zip, GZip, Snappy and None.</p>
        <p><b>See:</b>  <a href="content-formats.md">Content formats</a>
        </p>
      </td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "UpdateContentType",
	"contentType" : {
		"type" : "JsonContentType"
	}
}' "https://api.upsolver.com/inputs/DATA-SOURCE-ID"
```

## Update description

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| description | Description | String | The description of the data source. |  |

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "UpdateDescription",
	"description" : "description"
}' "https://api.upsolver.com/inputs/DATA-SOURCE-ID"
```

## Attach workspace

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| workspace | Workspace | String | The workspace to attach to this data source. |  |

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "AttachWorkspace",
	"workspace" : "workspace"
}' "https://api.upsolver.com/inputs/DATA-SOURCE-ID"
```

## Detach workspace

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| workspace | Workspace | String | The workspace to detach the data source from. |  |

#### Example

```bash
curl -X POST -H "content-type: application/json" 
-H "Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "DetachWorkspace",
	"workspace" : "workspace"
}' "https://api.upsolver.com/inputs/DATA-SOURCE-ID"
```

## Attach many workspaces

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| workspaces | Workspaces | String\[\] | The workspaces to attach this data source to. |  |

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "AttachManyWorkspaces",
	"workspaces" : "workspaces"
}' "https://api.upsolver.com/inputs/DATA-SOURCE-ID"
```

## Update connection

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| connection | Connection | String | Updating the storage location will cause new objects to be written to the new location. |  |
| moveData | Move existing objects | Boolean | Copy existing objects to the new storage location and then delete from the original location. Dependencies will continue working normally during this process. |  |

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "UpdateConnection",
	"connection" : "00dbf0e2-7c11-47f8-a672-
cacb537af190",
	"moveData" : true
}' "https://api.upsolver.com/inputs/DATA-SOURCE-ID"
```

## Stop

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "Stop"
}' "https://api.upsolver.com/inputs/DATA-SOURCE-ID"
```

## Update reporting tags

#### Fields

| Field | Name | Type | Description | Optional |
| :--- | :--- | :--- | :--- | :--- |
| reportingTags | Reporting Tags | String | Update the tags that can be sent to external monitoring systems. |  |

#### Example

```bash
curl -X POST -H "content-type: application/json" -H 
"Authorization: YOUR_TOKEN" \
-d '{
	"clazz" : "UpdateReportingTags",
	"reportingTags" : "reportingTags"
}' "https://api.upsolver.com/inputs/DATA-SOURCE-ID"
```

