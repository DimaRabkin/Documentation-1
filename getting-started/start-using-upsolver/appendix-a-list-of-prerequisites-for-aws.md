---
description: This page provides a list of prerequisites for AWS deployment.
---

# Prerequisites for AWS deployment

## Private VPC

<table>
  <thead>
    <tr>
      <th style="text-align:left">Item</th>
      <th style="text-align:left">Required</th>
      <th style="text-align:left">Default Limit</th>
      <th style="text-align:left">Comments</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">CloudFormation Stack</td>
      <td style="text-align:left">1 per integration (at least one)</td>
      <td style="text-align:left">200</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">IAM Role</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">1000</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">IAM Instance Profile</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">1000</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">S3 Bucket</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">100</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">VPC</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">5</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">Internet Gateway</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">5</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">EC2 Elastic IPs</td>
      <td style="text-align:left">2</td>
      <td style="text-align:left">5</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">EC2 Spot Instances</td>
      <td style="text-align:left">2</td>
      <td style="text-align:left">Dynamic</td>
      <td style="text-align:left">
        <p>Instance Types:</p>
        <ul>
          <li>r4.large</li>
          <li>m5.2xlarge</li>
          <li>m5d.2xlarge</li>
          <li>m5a.2xlarge</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Kinesis Stream Shard</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">200</td>
      <td style="text-align:left">Upsolver uses Kinesis Streams to balance workload between servers</td>
    </tr>
  </tbody>
</table>

## Upsolver VPC

| Item | Required | Default Limit | Comments |
| :--- | :--- | :--- | :--- |
| CloudFormation Stack | 1 per integration \(at least one\) | 200 | - |
| IAM Role | 1 | 1000 | - |
| S3 Bucket | 1 | 100 | - |

