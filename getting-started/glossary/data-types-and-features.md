---
description: >-
  This page provides an overview of the data types supported by different
  outputs. It also indicates whether or not the output supports upserts,
  aggregations, and SQL.
---

# Data types and features

When creating an output, these specific data types are supported. Additionally, upserts, aggregations, and SQL are supported for most of the outputs.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Output</th>
      <th style="text-align:left">Data Types</th>
      <th style="text-align:left">Upserts</th>
      <th style="text-align:left">Aggregations</th>
      <th style="text-align:left">SQL</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Athena</td>
      <td style="text-align:left">
        <p><code>DOUBLE</code>
        </p>
        <p><code>BIGINT</code>
        </p>
        <p><code>BOOLEAN</code>
        </p>
        <p><code>STRING</code>
        </p>
        <p><code>TIMESTAMP</code>
        </p>
        <p><code>DECIMAL(18,2)</code>
        </p>
        <p><code>DECIMAL(18,5)</code>
        </p>
        <p><code>DECIMAL(18,6)</code>
        </p>
      </td>
      <td style="text-align:left">+</td>
      <td style="text-align:left">+</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">Redshift Spectrum</td>
      <td style="text-align:left">
        <p><code>DOUBLE</code>
        </p>
        <p><code>BIGINT</code>
        </p>
        <p><code>BOOLEAN</code>
        </p>
        <p><code>STRING</code>
        </p>
        <p><code>TIMESTAMP</code>
        </p>
        <p><code>DECIMAL(18,2)</code>
        </p>
        <p><code>DECIMAL(18,5)</code>
        </p>
        <p><code>DECIMAL(18,6)</code>
        </p>
        <p><b>See:</b>  <a href="data-types-and-features.md#note-1">Note 1</a>
        </p>
      </td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">+</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">Upsolver</td>
      <td style="text-align:left">
        <p><code>BOOLEAN</code>
        </p>
        <p><code>STRING</code>
        </p>
        <p>Number</p>
      </td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">+</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">Redshift</td>
      <td style="text-align:left">
        <p>N/A</p>
        <p><b>See:</b>  <a href="data-types-and-features.md#note-3">Note 3</a>
        </p>
      </td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">+</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">MySQL</td>
      <td style="text-align:left">
        <p>N/A</p>
        <p><b>See:</b>  <a href="data-types-and-features.md#note-3">Note 3</a>
        </p>
      </td>
      <td style="text-align:left">
        <p>+</p>
        <p><b>See:</b>  <a href="data-types-and-features.md#note-4">Note 4</a>
        </p>
      </td>
      <td style="text-align:left">+</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">Apache Kafka</td>
      <td style="text-align:left">
        <p>N/A</p>
        <p><b>See:</b>  <a href="data-types-and-features.md#note-3">Note 3</a>
        </p>
      </td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">+</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">Amazon Kinesis</td>
      <td style="text-align:left">
        <p>N/A</p>
        <p><b>See:</b>  <a href="data-types-and-features.md#note-3">Note 3</a>
        </p>
      </td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">+</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">Elasticsearch</td>
      <td style="text-align:left">
        <p>N/A</p>
        <p><b>See:</b>  <a href="data-types-and-features.md#note-3">Note 3</a>
        </p>
      </td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">+</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">Amazon S3</td>
      <td style="text-align:left">
        <p>N/A</p>
        <p><b>See:</b>  <a href="data-types-and-features.md#note-2">Note 2</a>
        </p>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left">+</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">HDFS</td>
      <td style="text-align:left">
        <p>N/A</p>
        <p><b>See:</b>  <a href="data-types-and-features.md#note-2">Note 2</a>
        </p>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left">+</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">Google Storage</td>
      <td style="text-align:left">
        <p>N/A</p>
        <p><b>See:</b>  <a href="data-types-and-features.md#note-2">Note 2</a>
        </p>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left">+</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">Microsoft Azure Storage</td>
      <td style="text-align:left">
        <p>N/A</p>
        <p><b>See:</b>  <a href="data-types-and-features.md#note-2">Note 2</a>
        </p>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left">+</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">Qubole</td>
      <td style="text-align:left">
        <p><code>DOUBLE</code>
        </p>
        <p><code>BIGINT</code>
        </p>
        <p><code>BOOLEAN</code>
        </p>
        <p><code>STRING</code>
        </p>
        <p><code>TIMESTAMP</code>
        </p>
        <p><code>DECIMAL(18,2)</code>
        </p>
        <p><code>DECIMAL(18,5)</code>
        </p>
        <p><code>DECIMAL(18,6)</code>
        </p>
      </td>
      <td style="text-align:left">+</td>
      <td style="text-align:left">+</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">Amazon SageMaker</td>
      <td style="text-align:left">
        <p>N/A</p>
        <p><b>See:</b>  <a href="data-types-and-features.md#note-2">Note 2</a>
        </p>
      </td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">+</td>
      <td style="text-align:left">+</td>
    </tr>
    <tr>
      <td style="text-align:left">Lookup Table</td>
      <td style="text-align:left">
        <p><code>BOOLEAN</code>
        </p>
        <p><code>STRING</code>
        </p>
        <p><code>NUMBER</code>
        </p>
        <p><code>TIMESTAMP</code>
        </p>
        <p><code>NESTED TYPES</code>
        </p>
      </td>
      <td style="text-align:left">+</td>
      <td style="text-align:left">
        <p>+</p>
        <p><b>See:</b>  <a href="data-types-and-features.md#note-5">Note 5</a>
        </p>
      </td>
      <td style="text-align:left">+</td>
    </tr>
  </tbody>
</table>

### Note 1

Not fully automated.

### Note 2

The type is selected based on the output types. You can cast fields to get any types supported by the output format.

### Note 3

You cannot choose the destination data type as it is fetched from the original database.

### Note 4

Supported by definition. If a Primary Key \(PK\) is configured in the database, we will only have the latest record per PK.

### Note 5

Only aggregations by key are supported for lookup tables.

