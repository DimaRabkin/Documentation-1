---
description: >-
  This article provides a guide on the steps necessary to implement VPC peering
  in AWS.
---

# VPC peering

In order to connect to other EC2 resources \(e.g. Kafka, databases, etc.\), you need to peer the VPC in which the resources are allocated and the private VPC created by the integration.

{% hint style="info" %}
To peer the VPC, you need to:

* [ ] [Rename Upsolver private VPC](vpc-peering.md#renaming-upsolver-private-vpc)
* [ ] [Create VPC peering](vpc-peering.md#creating-vpc-peering)
* [ ] [Alter the route tables](vpc-peering.md#altering-the-route-tables)
* [ ] [Alter security groups](vpc-peering.md#altering-security-groups)
{% endhint %}

## Rename Upsolver private VPC

1. Navigate to the [**AWS VPC Dashboard**](https://console.aws.amazon.com/vpc/home).

2. Ensure the correct **region** is selected in the navigation pane.

3. Click **Your VPCs** in the navigation pane.

4. Locate the **VPC created by Upsolver.**

{% hint style="info" %}
This can be done by:

* looking for the **IPv4 CIDR** value \(which should be the value entered during **Integration**\) 

or:

* clicking the **Tags** card in the details pane
* look for the VPC that has the tag **aws:cloudformation:logical-id** with the value **UpsolverDefaultVPC**
{% endhint %}

5. **Rename** the **VPC** by clicking the pencil icon while hovering over the name of the selected VPC in the table.

## Create VPC peering

1. In the navigation pane, select **Peering Connections**.

2. Click **Create Peering Connection** and fill in the form.

3. Give the **peering connection name** a meaningful name \(e.g. Upsolver to Kafka\).

4. Select the **resources VPC** as the **requester**.

5. Select **Upsolver Private VPC** as the **accepter**.

6. Submit the form and click **OK**.

7. Right-click the new **VPC Peering Connection** and then click **Accept Request**.

{% hint style="info" %}
Follow the on-screen instructions to accept the request.
{% endhint %}

## Alter the route tables

To enable the VPCs to access one another, it is necessary to alter the route tables in both VPCs.

{% hint style="warning" %}
Make sure you include a **note** in each **VPC IPv4 CIDR** \(this can be done by navigating to **Your VPCs**\).
{% endhint %}

1. In the navigation pane, click **Route Tables**.

2. Locate and select your VPC’s **route table**.

3. In the details pane, click **Routes &gt; Edit Routes**.

4. Click **Add Route** and enter the details below:

| Field | Details |
| :--- | :--- |
| **Destination** | Enter the **Upsolver VPC IPv4 CIDR**. |
| **Target** | Select **Peering connection** and choose the connection. |

5. Submit the form and click **Close**.

6. If the VPC contains multiple route tables, **repeat** steps 2-4 **for each Route Table** on your VPC.

7. **Repeat** steps 2-5, this time locating the **route tables of Upsolver Private VPC** and in the **destination** \(in step 4\) fill in **your VPC IPv4 CIDR**.

## Alter security groups

{% hint style="info" %}
Now that the VPCs are peered, you need to alter the security groups of your instances to allow inbound and outbound connections from the Upsolver Private VPC.
{% endhint %}

1. Navigate to [**AWS EC2 Dashboard**](https://console.aws.amazon.com/ec2/v2/). 

2. Ensure the **correct region** is selected in the navigation pane.

3. Click **Instances** in the navigation pane.

4. Locate your instances and **find** a suitable **security group** or **attach a new security group** to all of the instances accessible to Upsolver Private VPC.

5. Navigate to the security group by **selecting** the **group** in the details pane.

6. Click **Inbound &gt; Edit**.

7. Add a rule with the details below:

| Field | Details |
| :--- | :--- |
| **Type** | All Traffic. |
| **Source** | Custom; enter **Upsolver Private VPC IPv4 CIDR** in the text box. |
| **Description** | Upsolver Private VPC. |

{% hint style="info" %}
If you know the specific ports that should be accessible to Upsolver Private VPC, you can customize the rule.
{% endhint %}

8. If there is no shared security group between all the instances, **repeat** steps 5-7 **for all the security groups** **needed**.

