---
description: >-
  This article provides a list of the data source monitoring metrics available
  along with their corresponding descriptions.
---

# Monitoring metrics

## Data source metrics

<table>
  <thead>
    <tr>
      <th style="text-align:left">Metric</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p></p>
        <p><b>upsolver.data_source.failed-items</b>
        </p>
      </td>
      <td style="text-align:left">Data source parse errors</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>upsolver.data_source.handled-bytes</b>
      </td>
      <td style="text-align:left">Number of bytes handled by the data source</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>upsolver.data_source.handled-items</b>
      </td>
      <td style="text-align:left">The number of items (records) handled by the data source</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>upsolver.data_source.ingest.delay</b>
      </td>
      <td style="text-align:left">Data source ingestion delay</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>upsolver.data_source.parse.delay</b>
      </td>
      <td style="text-align:left">Data source parse delay</td>
    </tr>
  </tbody>
</table>

## Lookup table metrics

| Metric | Description |
| :--- | :--- |
| **upsolver.lookup\_table.estimated-rows** | Number of rows currently in the lookup table \(available only if the lookup table runs on a query cluster\) |
| **upsolver.lookup\_table.handled-bytes** | Number of bytes handled by the lookup table |
| **upsolver.lookup\_table.handled-items** | Number of items \(records\) handled by the lookup table |
| **upsolver.lookup\_table.delay.delay** | Lookup table delay |
| **upsolver.lookup\_table.query.hits** | Amount queries which resulted in a lookup table hit \(available only if the lookup table runs on a query cluster\) |
| **upsolver.lookup\_table.query.misses** | Amount queries which resulted in a lookup table miss \(available only if the lookup table runs on a query cluster\) |
| **upsolver.lookup\_table.query.queries** | Amount of queries sent to the lookup table \(available only if the lookup table runs on a query cluster\) |

## Output metrics

| Metric | Description |
| :--- | :--- |
| **upsolver.output.handled-bytes** | Number of bytes handled by the output |
| **upsolver.output.handled-items** | Number of items \(records\) handled by the data source |
| **upsolver.output.written-items** | Number of items written to the output destination |
| **upsolver.output.written-bytes** | The number of bytes written to the output destination |
| **upsolver.output.delay** | Output delay |
| **upsolver.output.min-delay** | Output minimum delay. This can be used as a filter for the delay metric |
| **upsolver.output.data-transformation.handled-items** | Number of items \(records\) handled during output processing \(relevant only Databases and streams outputs\) |
| **upsolver.output.data-transformation.handled-bytes** | Number of bytes handled during output processing \(relevant only Databases and streams outputs\) |
| **upsolver.output.data-transformation-delay.delay** | Delay during output processing \(relevant only Databases and streams outputs\) |
| **upsolver.output.hive.paritition\_manger.last-success-diff** | The amount of time passed since the last successful execution of the partition manager in Athena/Qubole/Redshift Spectrum outputs |

## Compute cluster and environment metrics

| Metric | Description |
| :--- | :--- |
| **upsolver.upsolver\_compute\_units.value** | The amount of Upsolver units used in a cluster |
| **upsolver.compute\_units.value** | The amount of compute units used in a cluster |
| **upsolver.environment\_utilization.value** | The average CPU load of all the servers in a cluster |

