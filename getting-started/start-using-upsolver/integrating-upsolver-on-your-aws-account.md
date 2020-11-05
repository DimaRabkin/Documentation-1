---
description: This page provides a tutorial on how to deploy Upsolver to your private VPC.
---

# Deploy Upsolver on your AWS account

{% hint style="info" %}
**Note:** You may prefer to deploy the processing on your own AWS account. In any event, data is never stored on the Upsolver AWS account.
{% endhint %}

## How to deploy Upsolver on your AWS account:

1. In the **Integrate Upsolver with your AWS Account** window, click **click here**.

![The message displayed](../../.gitbook/assets/screen-shot-2020-08-31-at-10.50.58-am.png)

2. Decide whether or not to grant Upsolver **permission to:**

{% tabs %}
{% tab title="Create Athena tables" %}
This will allow for the creation and management of Athena tables for Athena outputs created in Upsolver.
{% endtab %}

{% tab title="View Kinesis streams" %}
This will allow Upsolver to retrieve a list of your Kinesis streams in order to create a data source.
{% endtab %}
{% endtabs %}

4. Check **Create a Dedicated Upsolver User**. This option must be selected.

{% hint style="info" %}
**Note:** When Upsolver creates a role in your AWS account it will contain the required permissions and any optional permissions selected in the previous step.
{% endhint %}

5. Check **Create a Dedicated Upsolver Bucket** to create a new bucket in your account. This will be the default bucket that intermediate files and Upsolver outputs are written to.

6. Select the **cluster deployment method**. To use your own VPC in your AWS account, select **My VPC**, **My VPC with Spotinst Account**, or **My Existing VPC**. 

{% hint style="info" %}
**Note:** This only affects where the processing servers are deployed, as your data is never stored on the Upsolver AWS account and never leaves your AWS bucket.
{% endhint %}

7. Under **VPC CIDR**, enter in the range of IPv4 addresses for your VPC in CIDR block format. Leave the default range if you don't need to [peer the VPC](../upsolver-aws-deployment-guide/vpc-peering.md).

8. In the **Ingress Traffic CIDR List** field, enter a comma-separated list of CIDR ranges from which the local API server will be accessible. 

{% hint style="info" %}
By default, this field contains 0.0.0.0/0 \(meaning that all the machines inside the VPC have access\) and your current IP address. 

You should add your office IP and any other IP from which you would like to be able to use Upsolver.
{% endhint %}

9. Check **Allow Upsolver Access** to add Upsolver's office IP address to the ingress permissions for the VPC. This will allow Upsolver to easily assist you with any issues or questions.

10. If you selected **My VPC with My Spotinst Account** as your cluster deployment type, fill in your **AWS Spotinst token** and **account ID**.

11. If you selected **My Existing VPC** as your cluster deployment type, configure the following options:

{% tabs %}
{% tab title="VPC ID" %}
Enter in the **ID** of the VPC you wish to use.
{% endtab %}

{% tab title="Subnets" %}
Fill in the list of subnets to deploy Upsolver servers in by inputting their **availability zone** and **subnet ID**. You can also import this information from a CSV.

**Note:** The subnets must have outbound internet traffic access.
{% endtab %}

{% tab title="Spotinst" %}
If you're using Spotinst, you can optionally also enter in your **token** and **account ID** that will give Upsolver permissions to create machines in your AWS environment.
{% endtab %}
{% endtabs %}

12. Select the **region** where you want to run the integration to create a VPC for Upsolver servers to run in your account.

13. Click **Continue**.

14. Click **Launch Integration**; you will be directed to a **CloudFormation stack** page to create the necessary resources.

15. At the bottom of the page, check the **I acknowledge** statement and then click **Create stack**.

16. Wait for the stack creation status to change from **`CREATE_IN_PROGRESS`** to **`CREATE_COMPLETE`**.

17. Return to the Upsolver tab and wait for the integration window to indicate that the integration is complete \(The **Relaunch Integration** button will change to **Done**\).

18. Click **Done**.

{% hint style="success" %}
You can now work in Upsolver.
{% endhint %}

