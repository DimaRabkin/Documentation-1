# EC2 Spot Instance not running

A problem starting up an EC2 Spot Instance in your account may be due to AWS Service Limits.

{% hint style="info" %}
**See:** [List of prerequisites for AWS deployment](../../start-using-upsolver/appendix-a-list-of-prerequisites-for-aws.md)
{% endhint %}

## Check if local API is up:

1. Navigate to the **EC2 Service** in the **AWS Console**.
2. Click **Instances** in the navigation pane.
3. Enter **upsolver-api** in the Search bar and press **Enter**.

If you see items in the list, the local-api is up. 

{% hint style="warning" %}
Make sure the **region** is the same as the one chosen during integration.
{% endhint %}

