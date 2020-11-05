---
description: >-
  This article provides a guide on how to create an Amazon S3 connection in
  Upsolver.
---

# Amazon S3 connection

## Create an Amazon S3 connection

1. Select your **credentials:**

* **Automatic**
* **Role Based**
  * **ARN Role:** The identifier for the IAM role itself.  **See:** [IAM Identifiers](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_identifiers.html)
  * **External ID \(optional\):** This is useful when you need to grant third-party access to your AWS resources.

2. Enter the **name** of your AWS S3 **bucket**.

3. \(Optional\) Enter in the **path** to your bucket.

{% hint style="info" %}
Check **Read Only** for the connection to be read only; Upsolver will not be able to write data to or delete data from the bucket.
{% endhint %}

4. **Name** this connection \(defaults to bucket name\).

5. Select the **Server Side Encryption Key:**

* **Default Encryption Key**
* **AWS Managed Key**
* **Customer Managed Key**

6. Click **Create**.

