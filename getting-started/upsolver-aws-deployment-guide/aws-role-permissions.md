---
description: >-
  This page summarizes all of the information regarding the AWS role permissions
  necessary to integrate your account with Upsolver.
---

# AWS role permissions

When integrating with AWS, one or two managed roles are created in your account to give Upsolver the required access.

There are three role types. The role types in your account depend on the type of integration.

{% tabs %}
{% tab title="Private VPC" %}
With **My VPC** integration, two roles are created:

* **UpsolverManagementRole**
* **UpsolverServerRole**
{% endtab %}

{% tab title="Upsolver VPC" %}
With **Upsolver VPC** integration, one role is created:

* **UpsolverRole**

{% hint style="info" %}
**Note:** This role includes the permissions of both the **UpsolverManagementRole** and the **UpsolverServerRole** roles, unless otherwise stated.
{% endhint %}
{% endtab %}
{% endtabs %}

## Permissions

### **UpsolverServerRole**

This is the role that Upsolver's servers running in your VPC use to access the data in your account. The permissions given to this role are:

| Permission | Description |
| :--- | :--- |
| **s3:ListAllMyBuckets** | Allows the servers to view which buckets you have so Upsolver's UI can suggest them for your convenience. |
| **kinesis:ListStreams** | Allows the servers to identify your Kinesis Streams so that Upsolver's UI can suggest them for your convenience. |
| **arn:aws:iam::aws:policy/ AmazonAthenaFullAccess** | Allows the servers to manage your Athena tables. Athena does not allow partial permissions; full access is required. |
| **Additional data read/write permissions** | When adding data sources or creating data outputs, you may need to add read/write permissions. |

## Policies

### **Management Role**

#### Managed Policies

| Policy | Description |
| :--- | :--- |
| **AWSCloudFormationReadOnlyAccess** | Permission is required for Upsolver to identify when the initial integration completed successfully. |

#### Custom Policies

| Policies | Description |
| :--- | :--- |
| **ec2:RunInstances,  ec2:StartInstances,  ec2:TerminateInstances,  ec2:RequestSpotInstances, ec2:CancelSpotInstanceRequests,  ec2:CreateVolume,  ec2:AttachVolume,  ec2:DeleteVolume** | Allows running and stopping of Upsolver EC2 instances. |
| **ec2:DescribeInstances, ec2:DescribeSpotInstanceRequests, ec2:DescribeInstanceStatus, ec2:CreateTags, ec2:DescribeTags** | Allows monitoring of Upsolver EC2 clusters. |
| **ec2:DescribeSecurityGroups, ec2:DescribeImages, ec2:DescribeImageAttribute** | Required for Spotinst validation. |
| **ec2:AssociateAddress,  ec2:DisassociateAddress,  ec2:AllocateAddress,  ec2:ReleaseAddress, ec2:DescribeAddresses** | Allows Upsolver to use static IP addresses for discoverability. |
| **cloudwatch:PutMetricData,  cloudwatch:GetMetricStatistics,  cloudwatch:ListMetrics, cloudwatch:DescribeAlarmHistory, cloudwatch:DescribeAlarmsForMetric, cloudwatch:DescribeAlarms** | Auto Scaling against CloudWatch statistics and alarms. |
| **iam:ListPolicies, iam:GetPolicyVersion, iam:GetPolicy, iam:ListRoles, iam:ListInstanceProfiles, iam:AddRoleToInstanceProfile, iam:ListInstanceProfilesForRole, iam:ListAttachedRolePolicies, iam:ListAccountAliases, iam:PassRole** | Required for Spotinst for policy validation. |

```http
{
    "Statement": [
    "Action": [
        "ec2:DescribeSpotInstanceRequests",
        "ec2:DescribeAddresses",
        "ec2:DescribeInstances",
        "ec2:DescribeSecurityGroups",
        "ec2:DescribeInstanceStatus",
        "ec2:DescribeTags",
        "ec2:DescribeImages",
        "ec2:DescribeImageAttribute",
         "ec2:DescribeSpotPriceHistory",
        "cloudwatch:PutMetricData",
        "cloudwatch:GetMetricStatistics",
        "cloudwatch:ListMetrics",
        "cloudwatch:DescribeAlarmHistory",
        "cloudwatch:DescribeAlarmsForMetric",
        "cloudwatch:DescribeAlarms",
        "iam:ListPolicies",
        "iam:GetPolicyVersion",
        "iam:GetPolicy",
        "iam:ListRoles",
        "iam:ListInstanceProfiles",
        "iam:AddRoleToInstanceProfile",
        "iam:ListInstanceProfilesForRole",
        "iam:ListAttachedRolePolicies",
        "iam:ListAccountAliases",
        "iam:PassRole"
    ],
    "Resource": [
        "*"
    ],
    "Effect": "Allow"
        },
        {
    "Action": [
        "ec2:RequestSpotInstances",
        "ec2:CancelSpotInstanceRequests",
        "ec2:CreateTags",
        "ec2:AssociateAddress",
        "ec2:DisassociateAddress",
        "ec2:AllocateAddress",
        "ec2:ReleaseAddress"
    ],
    "Resource": [
        "*"
    ],
    "Effect": "Allow"
        },
        {
    "Condition": {
        "StringLike": {
            "aws:RequestTag/Name": "*upsolver*"
        }
    },
    "Action": [
        "ec2:CreateVolume",
        "ec2:RunInstances"
    ],
    "Resource": [
        "*"
    ],
    "Effect": "Allow"
        },
        {
    "Condition": {
        "StringLike": {
            "ec2:ResourceTag/Name": "*upsolver*"
        }
    },
    "Action": [
        "ec2:TerminateInstances",
        "ec2:StartInstances",
        "ec2:AttachVolume",
        "ec2:DeleteVolume",
        "ec2:RunInstances"
    ],
    "Resource": [
        "*"
    ],
    "Effect": "Allow"
        },
        {
    "Action": [
        "ec2:RunInstances"
    ],
    "Resource": [
        "arn:aws:ec2:*:*:network-interface/*",
        "arn:aws:ec2:*:*:subnet/*",
        "arn:aws:ec2:*::image/*"
    ],
    "Effect": "Allow"
        }
    ]
}
```

### **Server Role**

#### Managed Policies

<table>
  <thead>
    <tr>
      <th style="text-align:left">Policy</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>AmazonAthenaFullAccess</b>
      </td>
      <td style="text-align:left">
        <p>Allows the servers to manage your Athena tables. Athena does not allow
          partial permissions; full access is required.</p>
        <p>To configure finely grained permissions, use AWS Lake Formation.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>AWSCloudFormationReadOnlyAccess</b>
      </td>
      <td style="text-align:left">Required for Upsolver to identify when potential follow-up integrations
        have completed successfully.</td>
    </tr>
  </tbody>
</table>

#### Custom Policy:

```http
{
    "Statement": [
        {
    "Sid": "upsolverBucketAccess",
    "Action": [
        "s3:*"
    ],
    "Resource": [
        "arn:aws:s3:::us-east-1-upsolver-UPSOLVER_ORG_ID",
        "arn:aws:s3:::us-east-1-upsolver-UPSOLVER_ORG_ID/*"
    ],
    "Effect": "Allow"
        },
        {
    "Sid": "listStreams",
    "Action": [
        "kinesis:ListStreams"
    ],
    "Resource": [
        "*"
    ],
    "Effect": "Allow"
        },
        {
    "Sid": "upsolverManagedStream",
    "Action": [
        "kinesis:*"
    ],
    "Resource": [
        "arn:aws:kinesis:*:*:stream/upsolver_*"
    ],
    "Effect": "Allow"
        },
        {
    "Sid": "sendScalingMetrics",
    "Action": [
        "cloudwatch:PutMetricData"
    ],
    "Resource": [
        "*"
    ],
    "Effect": "Allow"
        }
    ]
}
```

