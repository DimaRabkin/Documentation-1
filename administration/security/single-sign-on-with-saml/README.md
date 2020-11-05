---
description: This article provides a guide on how to set up SAML-based sign-on in Upsolver.
---

# Single sign-on with SAML

Upsolver supports SSO through SAML using an identity broker such as Microsoft Azure, Okta, or onelogin to allow for a secured single sign-on to Upsolver without transmitting any actual authentication credentials from your site. 

This procedure describes how to set up the SAML-based sign-on in general terms. Specific identity broker procedures follow below.

{% hint style="info" %}
### Prerequisites:

An admin user on Upsolver.
{% endhint %}

## Set up SAML-based sign-on

{% hint style="info" %}
**Note:** For more details, see the specific identity provider below.

* [Microsoft Azure](microsoft-azure-ad-with-saml-sign-on.md)
* [Okta](okta-with-saml-sign-on.md)
* [OneLogin](onelogin-with-saml-sign-on.md)
{% endhint %}

1. In your SAML-based sign-on identity provider, create a SAML application.

2. In Upsolver, click **More &gt; SAML**. 

3. Copy the Upsolver **Single Sign On URL** and **Audience URI** field values into the matching fields in your identity provider.

4. Configure the following SAML attributes: 

* **email** \(mandatory\)
* **firstName**
* **lastName**
* **groups** \(mandatory\)

5. Ensure that the required users and groups are assigned to the SAML application.

6. In Upsolver, click **More &gt; SAML**.

7. Click **Edit Integration** and copy the information from your identity provider into the following fields:

* **Single Sign On URL**
* **Identity Provider Issuer**
* **X 509 CERTIFICATE**

{% hint style="warning" %}
**Note:** At this stage, leave the **Allow Only SAML Sign On** unchecked.   
Only change this once you have tested your SAML-based sign-on!
{% endhint %}

8. From your identity provider, log in to Upsolver. The SSO group and users are automatically provisioned in Upsolver. 

{% hint style="info" %}
There are no default policies for SAML provisioned groups, so users only have permissions to sign on to Upsolver.
{% endhint %}

9. In Upsolver, click **More &gt; IAM**.

10. Select the **Groups** tab. The **SAML Provisioned Group** should appear.   
This appears as a **group name** if you are using **Active Directory**, otherwise this appears as a **group ID**.

11. Click the pencil icon ![](../../../.gitbook/assets/image%20%2824%29.png) to edit the group, and click **Add Policy** to add any required Upsolver policies.   
**See:** [Identity and access management](../identity-and-access-management/)

12. \(Optional\) To lock down Upsolver to only allow SAML sign on, click **More &gt; SAML** and select **Allow Only SAML Sign On**.

## SAML deny policy

You may want to apply the policy that denies access to updating or deleting the SAML configuration.

```sql
[
  {
    "effect": "Deny",
    "actions": [
      "organization:edit:update-saml-configuration",
      "organization:edit:delete-saml-configuration"
    ],
    "resources": [
      "*"
    ],
    "conditions": []
  }
]
```



