---
description: >-
  This article provides an overview of the properties displayed under the
  properties tab for clusters.
---

# Cluster properties

If applicable, click the pen icon![](../../.gitbook/assets/image%20%2845%29.png)to edit a property. 

## Display data

| Property | Description |
| :--- | :--- |
| **Name** | Cluster name. |

## Upsolver

<table>
  <thead>
    <tr>
      <th style="text-align:left">Property</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>Processing Units</b>
      </td>
      <td style="text-align:left">Amount of processing units.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Private VPC</b>
      </td>
      <td style="text-align:left">Your private VPC connection.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Hosts</b>
      </td>
      <td style="text-align:left">Add the following host/IP mappings to the hosts file.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Write Logs to Upsolver</b>
      </td>
      <td style="text-align:left">Whether or not to write logs to Upsolver&apos;s S3 environment.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Additional Processing Units for Replay</b>
      </td>
      <td style="text-align:left">
        <p>Amount of processing units for replay tasks that run on a separate cluster
          up to this size, billed separately.</p>
        <p>If active, it is recommended for this cluster to be at least as big as
          the maximum size of the cluster.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Workspaces</b>
      </td>
      <td style="text-align:left">The workspaces attached to this cluster.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Tags</b>
      </td>
      <td style="text-align:left">Assign custom metadata to your cluster using tags consisting of a key
        and a value, both of which you define.
        <br />This is a convenient way to categorize your AWS resources in different
        ways (e.g. by purpose, owner, or environment). For example, you could define
        a set of tags for your account&apos;s clusters that helps you track each
        cluster&apos;s owner or identify a production cluster versus a testing
        cluster. It is recommended that you create a consistent set of tags to
        meet your organization requirements.</td>
    </tr>
  </tbody>
</table>

## AWS

<table>
  <thead>
    <tr>
      <th style="text-align:left">Property</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>Region</b>
      </td>
      <td style="text-align:left">Your AWS region.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Elastic IPs</b>
      </td>
      <td style="text-align:left">
        <p>Whether or not Elastic IP is enabled.</p>
        <p>If enabled, Elastic IPs will be created for these servers.</p>
        <p>The server instances will use these Elastic IPs, allowing you to open
          access for your servers in external resources.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Max Elastic IPs Num</b>
      </td>
      <td style="text-align:left">Maximum number of available IPs. Leave empty for no limit.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Server Units</b>
      </td>
      <td style="text-align:left">
        <p>Server compute units; how many compute units one server will use.</p>
        <p>Choosing a server with &quot;high memory&quot; indicates a server type
          that has less CPU units but more RAM.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Extra Security Groups</b>
      </td>
      <td style="text-align:left">Security groups that can be added in addition to the default security
        groups created by Upsolver.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Allow Maintenance Access</b>
      </td>
      <td style="text-align:left">Whether or not Upsolver is allowed to access your instances over SSH for
        maintenance purposes.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Expose Private IPs</b>
      </td>
      <td style="text-align:left">Whether or not to expose the cluster with its private IP in the DNS record.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>DNS Alias</b>
      </td>
      <td style="text-align:left">DNS alias for private IPs. This is an alternative option to Elastic IPs.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Scaling Strategy</b>
      </td>
      <td style="text-align:left">
        <p>Cluster&apos;s scaling strategy.</p>
        <p><b>See:</b>  <a href="cluster-types/adding-a-compute-cluster.md#scaling-strategy">Scaling strategy</a>
        </p>
      </td>
    </tr>
  </tbody>
</table>

