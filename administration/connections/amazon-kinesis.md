---
description: >-
  This article provides a guide on how to create an Amazon Kinesis connection in
  Upsolver.
---

# Amazon Kinesis connection

## Create an Amazon Kinesis connection

1. Select your **credentials**.

* **Automatic**
* **Role Based**
  * **ARN Role:** The identifier for the IAM role itself.  **See:** [IAM Identifiers](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_identifiers.html)
  * **External ID \(optional\):** This is useful when you need to grant third-party access to your AWS resources.

2. Select your Amazon EC2 **region**.

3. **Name** this connection.

{% hint style="info" %}
Check **Read Only** for the connection to be read only; Upsolver will not be able to write data to or delete data from the data stream.
{% endhint %}

4. Enter in the **maximum** number of parallel **writers** to Kinesis \(defaults to 20\).

5. Click **Create**.

6. Click **Launch Integration** or the three vertical dots and select **Advanced**.  
You will be directed to create a **CloudFormation stack** in a new tab.  
**See:** [AWS CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html)

7. Once the stack has been completely created, return to the Upsolver tab and click **Done**. 

{% hint style="warning" %}
If the button instead says **Relaunch Integration**, check to see whether or not the status of your stack is `CREATE_COMPLETE`.
{% endhint %}

