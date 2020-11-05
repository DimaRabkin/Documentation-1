---
description: This article provides a guide on creating a Qubole connection in Upsolver.
---

# Qubole connection

## Create a Qubole connection

1. Enter your Qubole account's **API token**.

{% hint style="info" %}
This can be found under **My Accounts** in the **Control Panel**.  
**See:** [Qubole API Authentication](https://docs.qubole.com/en/latest/rest-api/api_overview.html#authentication)
{% endhint %}

2. **Name** this connection.

3. Select your **region**.

4. \(Optional\) Select your **Presto Query Label**.  
This cluster will be used for metadata queries which require a presto cluster. If left empty the default cluster will be used.

5. \(Optional\) Select your **Hive Query Label**.  
This cluster will be used for metadata queries which require a hive cluster. If left empty the default cluster will be used.

6. Uncheck **Set Avro Schema** if you do not wish to set `avro.schema.literal` property when creating external tables.

7. \(Optional\) If you wish to override the endpoint used to access Qubole, enter in a **Qubole Endpoint Override**. This can be used in conjunction with a reverse proxy to limit access to Qubole from specific IPs.

8. \(Optional\) Enter in an **HTTP** **Proxy Address** to be used for requests.   
The address must be in the format `host:port`.   
If the port is omitted port 1080 is used by default.

9. Click **Create**.

