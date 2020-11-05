---
description: >-
  This page links to the different kinds of connections that can be made in
  Upsolver.
---

# Connections

A prerequisite for defining a cloud storage data source is providing Upsolver with the appropriate credentials for reading from your cloud storage by creating the required connection. 

{% hint style="info" %}
Navigate to the Connections page by clicking **More &gt; Connections**.
{% endhint %}

## Adding connections

From the **Connections** page, add the connections of your choice by clicking **New Connection** and selecting the connection type.

For more details, refer to the relevant data source or output below:

* [Amazon S3](amazon-s3-connection.md)
* [Amazon Kinesis](amazon-kinesis.md)
* [Amazon Redshift](amazon-redshift-connection.md)
* [Amazon Athena](amazon-athena-connection.md)
* [Amazon S3 Over SQS](amazon-s3-over-sqs.md)
* [Google Storage](google-storage-connection.md)
* [Azure Blob storage](azure-blob-storage-connection.md)
* [Snowflake](snowflake-connection.md)
* [MySQL](mysql-connection.md)
* [Elasticsearch](elasticsearch-connection.md)
* [HDFS](hdfs-connection.md)
* [Qubole](qubole-connection.md)
* [PostgreSQL](postgresql.md)
* [Microsoft SQL Server](microsoft-sql-server.md)
* [Spotinst Private VPC](spotinst-private-vpc.md)
* [Kafka](kafka-connection.md)

## Managing connections

On the **Connections** page, you will find all of your connections sorted by type.

Within each category, you will see connections listed sorted by their name with their corresponding connection string displayed underneath.

To the side of each connection, you will find a string of icons:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Icon</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">check icon
        <img src="https://gblobscdn.gitbook.com/assets%2F-MAbbZ6XL3iXMHb3pjqP%2F-MFHJmWz1M_aI-klxRf2%2F-MFHM-ZpFhZRJJI6rXTR%2Fimage.png?alt=media&amp;token=21726913-a3ae-457c-a3ba-c49a3eed74af"
        alt/>
      </td>
      <td style="text-align:left">Connection is working correctly.</td>
    </tr>
    <tr>
      <td style="text-align:left">warning icon
        <img src="https://gblobscdn.gitbook.com/assets%2F-MAbbZ6XL3iXMHb3pjqP%2F-MFHJmWz1M_aI-klxRf2%2F-MFHMBoXiT0PBOuUXTe0%2Fimage.png?alt=media&amp;token=53bd03b1-18f8-407a-8a29-b0841d955dae"
        alt/>
      </td>
      <td style="text-align:left">Error in connection.</td>
    </tr>
    <tr>
      <td style="text-align:left">copy icon
        <img src="https://gblobscdn.gitbook.com/assets%2F-MAbbZ6XL3iXMHb3pjqP%2F-MFHMJAEYgpnT5XAJQqM%2F-MFHMbCoFcHP68uodD2V%2Fimage.png?alt=media&amp;token=3c88a24c-2e45-4471-897f-a6d8bd8f1fa1"
        alt/>
      </td>
      <td style="text-align:left">Click to copy the connection ID.</td>
    </tr>
    <tr>
      <td style="text-align:left">information icon
        <img src="https://gblobscdn.gitbook.com/assets%2F-MAbbZ6XL3iXMHb3pjqP%2F-MFHMJAEYgpnT5XAJQqM%2F-MFHMkzgyNwPjnhPEfVi%2Fimage.png?alt=media&amp;token=406fe0dd-340a-4434-b419-3edba3787714"
        alt/>
      </td>
      <td style="text-align:left">Click to view where the connection is being used.</td>
    </tr>
    <tr>
      <td style="text-align:left">trash icon
        <img src="https://gblobscdn.gitbook.com/assets%2F-MAbbZ6XL3iXMHb3pjqP%2F-MFHNE5NktaUmvgB5TET%2F-MFItSCSfz_wLBlooU37%2Fimage.png?alt=media&amp;token=fb5f3e11-af3e-41f0-95b7-36aa90f3742f"
        alt/>
      </td>
      <td style="text-align:left">
        <p>If connection is not in use, this icon appears.</p>
        <p>Click to delete this connection.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">pencil icon
        <img src="https://gblobscdn.gitbook.com/assets%2F-MAbbZ6XL3iXMHb3pjqP%2F-MFHMJAEYgpnT5XAJQqM%2F-MFHMzRfezcx3d7LtYHv%2Fimage.png?alt=media&amp;token=41aefa82-47c9-4be2-9993-76c5f0c5977b"
        alt/>
      </td>
      <td style="text-align:left">Click to edit the connection details.</td>
    </tr>
  </tbody>
</table>

