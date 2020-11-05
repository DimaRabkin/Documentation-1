# My compute cluster doesn't start

There might be a problem starting up EC2 Spot Instance in your account due to AWS Service Limits. 

{% hint style="info" %}
**See:** [List of prerequisites for AWS](../start-using-upsolver/appendix-a-list-of-prerequisites-for-aws.md)
{% endhint %}

## Check if your compute cluster is up:

1. Navigate to the **EC2 Service** in the **AWS Console**.

2. Click **Instances** \(under **Instances**\) in the navigation pane.

3. Type **upsolver-data-updates** in the Search bar and click **Enter**.

{% hint style="info" %}
If items appear in the list, the compute cluster is up.
{% endhint %}

4. If you have **multiple compute clusters** and you want to check if a specific compute cluster's instances are up, type **cluster\_name** in the Search box.

5. Click **cluster\_name** under tag keys to view a menu containing the names of Upsolver clusters that are running in your AWS Account.

6. Click a specific cluster name and verify there are items in the list for that specific cluster.

