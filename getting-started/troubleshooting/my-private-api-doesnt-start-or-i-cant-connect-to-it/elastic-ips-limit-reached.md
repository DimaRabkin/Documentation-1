# Elastic IPs limit reached

{% hint style="info" %}
Before deploying a cluster to your Private VPC, Upsolver allocates Elastic IP addresses to make sure that servers are discoverable.
{% endhint %}

## For API and query clusters:

Elastic IP addresses are **mandatory**.

## For compute clusters:

Elastic IP addresses are **optional** and **can be** **edited** from the UI. 

To edit, select the compute cluster in question: 

1. Click the vertical dots next to the **Stop** button.
2. Click **Edit** and clear the **Elastic IPs checkbox**. 

{% hint style="info" %}
**Note:** when the Elastic IPs option is not selected, external resources \(e.g., Redshift or Elasticsearch\) will not be able to recognize the compute cluster servers by their IP addresses.
{% endhint %}

## For compute or query clusters with **Auto Scaling** turned on: 

Upsolver allocates Elastic IP addresses for a cluster according the maximum number of servers.

## For compute clusters with additional processing units for replay: 

Upsolver also allocates Elastic IP addresses for those processing units.

## AWS Elastic IP limit:

The number of Elastic IPs that an account in AWS can allocate is **limited per region**. 

{% hint style="info" %}
You can raise the limit of Elastic IPs by [sending a request to Amazon Web Services via this form](https://console.aws.amazon.com/support/v1#case/create?issueType=service-limit-increase&limitType=service-code-elastic-ips-ec2-classic&serviceLimitIncreaseType=elastic-ips&type=service_limit_increase). 

In the **Limit type**, select **Elastic IPs** and select the relevant **region**.
{% endhint %}

If Upsolver is unable to allocate Elastic IPs because the limit is exceeded, a notification will pop up containing a link to this page.

