---
description: >-
  This article provides a guide on how to create a Microsoft SQL Server
  connection in Upsolver.
---

# Microsoft SQL Server connection

## Create a Microsoft SQL Server connection

1. Enter the **connection string** in the following format:  
`jdbc:sqlserver://HOST:PORT;Database=DB_NAME` where:

* `HOST` = host name \(e.g. database instance endpoint in AWS RDS\)
* `PORT` = port number
* `DB_NAME` = database name

{% hint style="info" %}
**See:** [SQL Server JDBC driver connection URL](https://docs.microsoft.com/en-us/sql/connect/jdbc/building-the-connection-url?view=sql-server-ver15)
{% endhint %}

2. Enter your SQL Server database **username**.

3. \(Optional\) Enter the corresponding **password**.

4. **Name** this connection.

5. \(Optional\) Enter in the number of **concurrent connections**.

{% hint style="warning" %}
If you have **trouble connecting**, it may be a **network and security** **issue**.  
To fix this in AWS RDS, you can:

1. make your instance **publicly accessible** under the **Properties** tab
2. reconfigure the **inbound rules** for your instance's VPC security group \(allow all traffic from all sources\)

For a more secure option, you can also choose to implement ****[**VPC peering**](../../getting-started/upsolver-aws-deployment-guide/vpc-peering.md).
{% endhint %}

