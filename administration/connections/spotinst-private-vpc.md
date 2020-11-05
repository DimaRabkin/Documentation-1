---
description: >-
  This article provides a guide on how to create a Spotinst Private VPC
  connection in Upsolver.
---

# Spotinst Private VPC connection

## Create a new Spotinst Private VPC connection

1. **Name** this connection.

2. Under **subnet CIDR**, enter in the range of IPv4 addresses for your VPC in CIDR block format. Leave the default range if you don't need to peer the VPC.

3. Select your **AWS region**.

4. Enter in your **Spotinst token**.

5. Enter in your **Spotinst account ID**.

6. Click **Show Advanced** to edit the following options:

{% tabs %}
{% tab title="Ingress Traffic CIDR List" %}
Enter a **comma-separated list** of **CIDR blocks** that will be configured for ingress traffic in the VPC. 

By default, this field contains 0.0.0.0/0 \(meaning that all the machines inside the VPC have access\) and your current IP address. You should add your office IP and any other IP you would like to be able to use Upsolver from.
{% endtab %}

{% tab title="Allow Upsolver Access" %}
If checked, Upsolver's office IP will be added to the ingress permissions for the VPC. This will allow Upsolver to easily assist you with any issues or questions.
{% endtab %}
{% endtabs %}

7. Click **Launch Integration**; you will be directed to a **CloudFormation stack** page to create the necessary resources.

8. At the bottom of the page, check the **I acknowledge** statement and then click **Create stack**.

9. Wait for the stack creation status to change from **`CREATE_IN_PROGRESS`** to **`CREATE_COMPLETE`**.

10. Return to the Upsolver tab and wait for the integration window to indicate that the integration is complete \(The **Relaunch Integration** button will change to **Done**\).

11. Click **Done**.

{% hint style="success" %}
You have now created a private VPC connection in Upsolver.
{% endhint %}

