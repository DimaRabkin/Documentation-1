---
description: >-
  This article provides a guide on how to create an Amazon Redshift connection
  in Upsolver.
---

# Amazon Redshift connection

## Create an Amazon Redshift connection

1. Enter the **connection string**.

{% hint style="info" %}
This can be found as the **JDBC URL** under your cluster's **General Information** or under **Properties** in the **Connection details** section.
{% endhint %}

It should be of the following format: `jdbc:redshift://CLUSTER_NAME.USER_WITH_REGION.redshift.amazonaws.com:PORT/DB_NAME`

2. Enter the **username** for this Redshift database.

3. Enter the corresponding **password**.

4. **Name** this connection.

5. \(Optional\) Enter in the number of **concurrent connections**.

{% hint style="warning" %}
If you experience a **SocketTimeoutException**, it is likely a **Network and Security** issue.  
To fix this, you can:

1. make your cluster **publicly accessible** under the **Properties** tab
2. reconfigure the **inbound rules** for your cluster's VPC security group \(allow all traffic from all sources\)

For a more secure option, you can also choose to implement [**VPC peering**](../../getting-started/upsolver-aws-deployment-guide/vpc-peering.md).
{% endhint %}

