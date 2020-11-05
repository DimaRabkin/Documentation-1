---
description: >-
  This article provides a guide on how to create an Amazon S3 over SQS
  connection in Upsolver.
---

# Amazon S3 over SQS connection

## Create an Amazon S3 Over SQS connection

1. Select your **Credentials:**

* **Automatic**
* **Role Based**
  * **ARN Role:** The identifier for the IAM role itself.  **See:** [IAM Identifiers](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_identifiers.html)
  * **External ID \(optional\):** This is useful when you need to grant third-party access to your AWS resources.

2. Enter the **name** of your AWS S3 **bucket**.

3. \(Optional\) Enter in the **path** to your bucket.

{% hint style="info" %}
Check **Read Only** for the connection to be read only; Upsolver will not be able to write data to or delete data from the bucket.
{% endhint %}

4. **Name** this connection.

5. Click **Create**.

6. Click **Launch Integration** or the three vertical dots and select **Advanced**. In a new window, you will be directed to create a **CloudFormation stack**.  
**See:** [AWS CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html)

7. Once the stack has been completely created, return to the Upsolver tab and click **Done**. 

{% hint style="warning" %}
If the button instead says **Relaunch Integration**, check to see whether or not the status of your stack is **`CREATE_COMPLETE`**.
{% endhint %}

