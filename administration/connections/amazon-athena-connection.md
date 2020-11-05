---
description: >-
  This article provides a guide on creating an Amazon Athena connection in
  Upsolver.
---

# Amazon Athena connection

## Create an Amazon Athena connection

1. Select your **credentials:**

* **Automatic**
* **Role Based**
  * **ARN Role:** The identifier for the IAM role itself.  **See:** [IAM Identifiers](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_identifiers.html)
  * **External ID \(optional\):** This is useful when you need to grant third-party access to your AWS resources.

2. Fill in the **query result location** with the S3 location to which your query results are written \(e.g. `s3://company.query-results-bucket/`\).

{% hint style="info" %}
The default location for a given region is available under **Settings** in the Athena console and can be used here if desired.
{% endhint %}

3. Select your Amazon EC2 **region**.

4. Finally, **name** this connection, then click **Create**.

