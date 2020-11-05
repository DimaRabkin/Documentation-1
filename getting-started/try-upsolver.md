---
description: >-
  This page provides a short guide on signing up for a free account through the
  Upsolver website.
---

# Try Upsolver for free

To help you get started with Upsolver, you can try it out for free. You can choose between [**Upsolver Dedicated Compute**](https://app.upsolver.com/signup) ****and [**Community**](https://app.upsolver.com/signup/free) subscriptions. Both options give you free Upsolver units \(UUs\), units of processing capability per hour based on VM instance type.

Upsolver Dedicated Compute is more flexible, but Upsolver uses compute and S3 storage resources in your AWS account. During the sign-up process you grant Upsolver privileges to access your AWS account and an S3 bucket.

Upsolver Community is fully resourced; you are not required to supply any compute or storage resources.

You can also use Upsolver through [AWS Marketplace](https://aws.amazon.com/marketplace/pp/B07T8JDQ57?ref_=srh_res_product_title). All of the options will allow you to ingest data to Amazon S3, perform transformations with simple SQL, and output to your favorite database or analytics tools—in minutes.

## Try Upsolver for free - Community

1. Go to [https://app.upsolver.com/signup/free](https://app.upsolver.com/signup/free)

2. Enter your contact details and click **Sign Up**. An email message will be sent to the email account specified for verification.

3. Follow the [10 minute tutorial](start-using-upsolver/upsolver-in-10-minutes/) for an end-to-end quick tour of Upsolver

## Try Upsolver for free - Dedicated compute

1. Go to [https://app.upsolver.com/signup](https://app.upsolver.com/signup)

2. Enter your contact details and click **Sign Up**. An email message will be sent to the email account specified for verification.

3. When you log in, you may choose between deploying in Amazon AWS or Microsoft Azure

If you don’t have access to your AWS or Azure account, you can [**send the page**](https://upsolver.gitbook.io/upsolver-1/getting-started/try-upsolver#send-this-page) to someone else on your team.

4. You may choose between **Deploy to My AWS Account** which deploys Upsolver in your own VPC or **Multi-Tenant Deployment** - Upsolver hosts and manages the compute.  Click [here](upsolver-concepts/deployment-models.md) for more information.

5. Make sure you allow appropriate access to your AWS account and click **CONTINUE**.

6. In the **AWS CloudFormation page**, check the **I acknowledge** statement and click **Create Stack**.

7. Once the stack is successfully created \(this will take a couple of minutes; you will see that the status of your stack says `CREATE_COMPLETE` once it is finished\), the **Integration Completed** message appears in Upsolver.

8. Click **Done**.

You can now work in Upsolver.

## Send this page <a id="send-this-page"></a>

1. Click **SEND THIS PAGE.**

2. \(Optional\) Add any **S3 Buckets Containing Your Data** and **Kinesis Streams Containing Your Data**.

3. Click **Generate Link**.

4. Click **Copy** and then send the link to the relevant team member. This link can be pasted into the browser and used to create the required CloudFormation stack.[  
](https://upsolver.gitbook.io/upsolver-1/)

{% hint style="info" %}
If you don’t have access to your AWS account, you can [**send the page**](try-upsolver.md#send-this-page) to someone else on your team.
{% endhint %}

7. Select a **region** and click **Continue**.

{% hint style="info" %}
By default, Upsolver deploys the servers for processing and running jobs on the Upsolver AWS account, but the data is never stored there.

**See:** [Integrating Upsolver on your AWS account](start-using-upsolver/) if you would prefer to deploy the processing on your own AWS account.
{% endhint %}

8. Click **Launch Integration**.

9. In the **AWS CloudFormation page**, check the **I acknowledge** statement and click **Create Stack**.

10. Once the stack is successfully created \(this will take a couple of minutes; you will see that the status of your stack says 

