---
description: >-
  This page provides a comprehensive list of output properties along with their
  corresponding descriptions
---

# Output properties

To modify a property, simply go to the **Properties** tab and click on the pencil icon![](https://gblobscdn.gitbook.com/assets%2F-MAbbZ6XL3iXMHb3pjqP%2F-MF710zjyG0lukV90o0R%2F-MF72tpoG-yBWH_AWsf4%2Fimage.png?alt=media&token=08a91822-caad-46f1-9790-2c8fe201ae8e).

{% hint style="info" %}
**Note:** Not all properties can be modified.
{% endhint %}

## Properties

* [General](general-properties.md)
* [Hive Metastore](./#hive-metastore)
* [Resources](./#resources)
* [Scheduling](./#scheduling)
* [Advanced](./#advanced)
* [Display Data](./#display-data)
* [Sidebar](./#sidebar)

{% hint style="warning" %}
**Note:** Properties listed below may not apply to all outputs.
{% endhint %}

## General

[See the full list here.](general-properties.md)

## Hive Metastore

| Property | Description |
| :--- | :--- |
| **Connection** | Connection type \(e.g. Athena\). |
| **Database Name** | Output database name. |
| **Table Name** | Output table name. |

## Resources

| Property | Description |
| :--- | :--- |
| **Compute Cluster** | The compute cluster running the calculation. |

## Scheduling

| Property | Description |
| :--- | :--- |
| **Output Interval** | The output interval in minutes, hours or days. |
| **Ending At** | Whether to continue processing indefinitely, stop processing as soon as possible, or stop on a specific date and time. |
| **Soft Retention** | A setting that prevents data deletion when the retention policy in Upsolver activates. When enabled, the metadata is purged but the underlying data \(e.g. S3 object\) is not deleted. |
| **Retention** | The retention policy in Upsolver in minutes, hours, or days. The data is deleted permanently after this period elapses \(unless **Soft Retention** is set to **Yes**\). By default, the data is kept forever. |
| **Start Execution From** | When execution started. |

## Advanced

| Property | Description |
| :--- | :--- |
| **Shards \#** | The number of independent shards to write, to increase parallelism and reduce latency. This should remain 1 in most cases, and should never be larger than the number of shards of the data sources. |
| **Output Shards \#** | Set the number of files to be created each interval in the output. This applies only to aggregated outputs \(for non-aggregated outputs, the Shards configuration has this effect\). |
| **Compaction Shards \#** | The number of files that can be compacted in parallel during a compaction. |

## Display Data

| Property | Description |
| :--- | :--- |
| **Name** | Output name in Upsolver. |
| **Description** | Description of output. |
| **Creation Time** | Time this output was created. |
| **Created By** | Which user this output was created by. |
| **Modified Time** | If applicable, time this output was last modified. |
| **Modified By** | Which user last modified this output. |

## Sidebar

| Property | Description |
| :--- | :--- |
| **Aggregated** | Whether or not this output is aggregated. |
| **Aliases** | The lookup table alias. |
| **Clusters** | Click to edit the output clusters. |
| **Attached Workspaces** | The workspaces attached to this output. |

