---
description: >-
  This article walks through what it means to deploy Upsolver to Upsolver's VPC
  and how to do so.
---

# Upsolver VPC

This option allows you to deploy cluster servers to Upsolver's fully managed VPC, making it easy to get up and running quickly.

If you prefer to manage your own servers, you can use [your own VPC](private-vpc.md) instead.

## Requirements for integration

Before you can integrate your Upsolver account with AWS, you must have a user in AWS with permissions to:

* Run Cloud Formation scripts
* Create and manage user roles
* Create and manage S3 buckets

{% hint style="info" %}
**See:** [List of prerequisites for AWS](../start-using-upsolver/appendix-a-list-of-prerequisites-for-aws.md)
{% endhint %}

## Integrate AWS using Upsolver VPC

Before you can use Upsolver, you must integrate Upsolver into your AWS account in order to provide read and write access to the data Upsolver will be processing.

The following resources are created when you integrate with AWS using the **Upsolver VPC** option:

{% tabs %}
{% tab title="UpsolverRole" %}
This is the role that Upsolver's servers use to connect to and process your data.
{% endtab %}

{% tab title="Default S3 Bucket" %}
This bucket is used as the default output location for Upsolver outputs.
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**See:** [AWS role permissions](aws-role-permissions.md) for a detailed description of the permissions given to the roles.
{% endhint %}

#### To integrate AWS using Upsolver VPC:

1. Log in to your Upsolver account. You will be prompted to **integrate your account with AWS**.

2. Decide whether or not to grant Upsolver **permission to:**

{% tabs %}
{% tab title="Create Athena tables" %}
This will allow for the creation and management of Athena tables for Athena outputs created in Upsolver.
{% endtab %}

{% tab title="View Kinesis streams" %}
This will allow Upsolver to retrieve a list of your Kinesis streams in order to create a data source.
{% endtab %}
{% endtabs %}

3. Check **Create a Dedicated Upsolver User**. This option must be selected.

{% hint style="info" %}
**Note:** When Upsolver creates a role in your AWS account it will contain the required permissions and any optional permissions selected in the previous step.
{% endhint %}

4. Check **Create a Dedicated Upsolver Bucket** to create a new bucket in your account that will be the default bucket Upsolver outputs and writes intermediate files to.

5. Select the **region** where you want to run the integration to create a VPC for Upsolver servers to run in your account.

6. Click **Continue**.

7. Click **Launch Integration**; you will be directed to a **CloudFormation stack** page to create the necessary resources.

8. At the bottom of the page, check the **I acknowledge** statement and then click **Create stack**.

9. Wait for the stack creation status to change from **`CREATE_IN_PROGRESS`** to **`CREATE_COMPLETE`**.

10. Return to the Upsolver tab and wait for the integration window to indicate that the integration is complete \(The **Relaunch Integration** button will change to **Done**\).

11. Click **Done**.

{% hint style="success" %}
You can now work in Upsolver.
{% endhint %}

