---
description: >-
  This article walks through what it means to deploy Upsolver to your own VPC
  and how to do so.
---

# Private VPC

You can deploy your cluster and API servers to your own VPC in AWS. 

Private VPC mode gives you **full security control** over the data that Upsolver handles and ensures the data being processed never leaves your AWS account. Upsolver's global API server will not have access to your data in this deployment mode; therefore, this mode requires running an API server in the VPC.

If you prefer Upsolver to manage and host your servers, you can use [Upsolver's managed VPC](upsolver-vpc.md) instead.

{% hint style="info" %}
If you have **already integrated your account** with AWS using the Upsolver VPC, you may now want to change your servers over to run on your own VPC.

To do this, add a [Spotinst Private VPC connection](../../administration/connections/spotinst-private-vpc.md).
{% endhint %}

## Requirements for integration

In order to integrate your Upsolver account with AWS, you must have an AWS user with permissions to:

* Run CloudFormation scripts
* Create and manage user roles
* Create and manage S3 buckets
* Create VPCs and related resources \(ACLs, Subnets, ...\)

{% hint style="info" %}
**See:** [Prerequisites for AWS deployment](../start-using-upsolver/appendix-a-list-of-prerequisites-for-aws.md#private-vpc)
{% endhint %}

## Integrate with AWS using your own VPC

You must integrate Upsolver into your AWS account to provide read and write access to the data to be processed.

The following resources are created when you integrate with AWS using the **My VPC** option:

{% tabs %}
{% tab title="UpsolverServerRole" %}
This role is used by your EC2 servers during start up and it also provides data access.
{% endtab %}

{% tab title="UpsolverManagementRole" %}
This role is used by Upsolver to create and manage our servers in your VPC and it provides no data access; your data remains inaccessible from outside the account.
{% endtab %}

{% tab title="Default S3 Bucket" %}
This bucket is used as the default output location for Upsolver outputs.
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**See:** [AWS role permissions](aws-role-permissions.md) for a detailed description of the permissions given to the roles.
{% endhint %}

#### To integrate AWS with your own VPC:

1. Log in to your Upsolver account. You will be prompted to **integrate your account with AWS**.

2. Within the message displayed, click **click here**.

![The message displayed](../../.gitbook/assets/screen-shot-2020-08-31-at-10.50.58-am.png)

3. Decide whether or not to grant Upsolver **permission to:**

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

7. Under **VPC CIDR**, enter in the range of IPv4 addresses for your VPC in CIDR block format. Leave the default range if you don't need to peer the VPC.

8. In the **Ingress Traffic CIDR List** field, enter a comma-separated list of CIDR ranges from which the local API server will be accessible. 

{% hint style="info" %}
By default, this field contains 0.0.0.0/0 \(meaning that all the machines inside the VPC have access\) and your current IP address. 

You should add your office IP and any other IP you would like to be able to use Upsolver from.
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

