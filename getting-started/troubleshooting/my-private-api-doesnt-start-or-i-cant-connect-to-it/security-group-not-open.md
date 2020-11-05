# Security group not open

{% hint style="info" %}
The security group of the local API might not be open to your address. 

You can look for the security group created by the CloudFormation stack and open ports 80 and 443 to your IP address.
{% endhint %}

## Configure inbound rules:

1. Navigate to the **EC2 Service** in the **AWS Console**.

2. Click **Security Groups** \(under **Network & Security**\) in the navigation pane.

3. Type **Upsolver VPC Security Group** in the Search bar and click **Enter**.  
The security group created by Upsolver is displayed in the list below the search bar.

4. Right-click the security group and select **Edit Inbound Rules**.

5. Add two rules and configure them as follows:

| Type | Protocol | Port Range | Source | Description |
| :--- | :--- | :--- | :--- | :--- |
| HTTP | TCP | 80 | My IP | HTTP For \(e.g., San Francisco Offices\) |
| HTTPS | TCP | 443 | My IP | HTTPS For \(e.g., San Francisco Offices\) |

6. Click **Save**. It may take up to a minute for the local API to be reachable by your network.

