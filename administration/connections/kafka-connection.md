---
description: This article provides a guide on how to create a Kafka connection in Upsolver.
---

# Kafka connection

## Create a Kafka connection

1. Enter in the **`host:port`** for your **Kafka cluster**.

{% hint style="info" %}
If there are multiple hosts, the format should be `host1:port1, host2:port2, ...`
{% endhint %}

2. Select a **topic name**.

{% hint style="warning" %}
**Note:** This should be a pre-existing topic in your cluster.
{% endhint %}

3. \(Optional\) Add any additional **properties** necessary for the **Kafka producer**.  
The format should look as follows:

```bash
bootstrap.servers = HOST:PORT
security.protocol = SASL_SSL
sasl.jaas.config = org.apache.kafka.common.security.plain.PlainLoginModule   required username = "API_KEY"   password = "SECRET";
ssl.endpoint.identification.algorithm = https
sasl.mechanism = PLAIN
```

where:

* `HOST:PORT` = the same Kafka host\(s\) entered in step 1
* `API_KEY` = an API key for your Kafka cluster
* `SECRET` = the corresponding secret for your API key

{% hint style="warning" %}
Experiencing issues connecting? You may need to peer your VPC with the VPC created for Upsolver.  
**See:** [VPC peering](../../getting-started/upsolver-aws-deployment-guide/vpc-peering.md)
{% endhint %}

