---
description: >-
  This article outlines a quick guide on how to start a free trial and integrate
  Upsolver with your AWS account.
---

# AWS integration

{% embed url="https://www.youtube.com/watch?v=idrDTQmOD38&feature=youtu.be" %}

To get to know Upsolver, you can try it out for [**FREE**](https://app.upsolver.com/signup). 

Upsolver supports many deployment models that suit your needs; this guide describes the fully managed option. 

{% hint style="info" %}
**See:** [Deploy Upsolver on your AWS account](integrating-upsolver-on-your-aws-account.md) to learn more about deploying Upsolver in your own VPC.
{% endhint %}

Upsolver uses S3 storage resources in your AWS account. During the sign-up process you will need to grant Upsolver privileges to access your AWS account and create an S3 bucket. When you register for a demo, you can request credit for free AWS resources if you qualify for a POC. 

## Create an organization from the signup page

1. On the Upsolver website, click [Start a Trial](https://app.upsolver.com/signup). You can also deploy Upsolver directly from the [Amazon AWS Marketplace](https://aws.amazon.com/marketplace/pp/B07T8JDQ57?ref_=srh_res_product_title).

{% hint style="info" %}
The Upsolver trial is free for 14-days and it includes access to all production features for workloads at any scale \(full production data\). 

You can request a fully-funded POC [here](https://www.upsolver.com/upsolver-poc-lp).
{% endhint %}

2. You will see the following registration form.

![](../../.gitbook/assets/screen-shot-2020-09-05-at-10.18.52-am.png)

3. Fill in this registration form.

4. Click on **Sign Up**. Your trial will be valid for 14 days. 

5. Once signed up, you will be prompted to integrate Upsolver with your AWS account.

![](../../.gitbook/assets/screen-shot-2020-09-05-at-10.27.34-am.png)

## Pre-integration requirements

1. Now that you are logged into an Upsolver organization, click on **Continue**. 

{% hint style="info" %}
Upsolver uses S3 storage resources in your AWS account, so it will bring you to the Amazon AWS login page for integration.
{% endhint %}

![](../../.gitbook/assets/screen-shot-2020-09-05-at-10.29.30-am.png)

2. Make sure you have administrator permissions for your AWS account. 

{% hint style="info" %}
If you don’t have administrator permissions, you may send the page to your AWS administrator by clicking on [**Send This Page**](../try-upsolver.md#send-this-page).
{% endhint %}

![](../../.gitbook/assets/screen-shot-2020-09-05-at-10.28.41-am.png)

## Integrate with your AWS environment

1. Click **Continue** and a CloudFormation page will open up in a new tab. 

2. Create the AWS environment for Upsolver integration by running a CloudFormation template. Check the **I acknowledge** statement at the bottom of the page and click on **Create stack**. 

{% hint style="info" %}
This should take about one minute to complete. Once it is done, you should see that the CloudFormation stacks' status is `CREATE_COMPLETE`.
{% endhint %}

![](../../.gitbook/assets/image%20%28143%29.png)

![](../../.gitbook/assets/image%20%28145%29.png)

3. Click on **Done**. You should see the page where you can create a data source.

![](https://www.upsolver.com/wp-content/uploads/2020/07/Screen-Shot-2020-07-07-at-13.39.11.png)

## What’s next?

{% page-ref page="../../connecting-data-sources/amazon-aws-data-sources/amazon-s3-data-source/quick-guide-s3-data-source-1.md" %}

