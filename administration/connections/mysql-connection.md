---
description: This article provides a guide on creating a MySQL connection in Upsolver.
---

# MySQL connection

## Create a MySQL connection

1. Enter the **connection string** in the following format:  
`jdbc:mysql://HOST:PORT/DB_NAME` where:

* `HOST` = host name \(e.g. database instance endpoint in AWS RDS\)
* `PORT` = port number
* `DB_NAME` = database name

{% hint style="info" %}
**See:** [MySQL JDBC connection URL syntax](https://dev.mysql.com/doc/connector-j/8.0/en/connector-j-reference-jdbc-url-format.html)
{% endhint %}

2. Enter your MySQL database **username**.

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

