---
description: This procedure describes how to configure onelogin with SAML sign-on.
---

# OneLogin with SAML sign-on

## Configure OneLogin with SAML sign-on:

1. In OneLogin, in the **Administration** console, select **Applications &gt; Applications**.

2. Click **Add App**.

3. Search for the **OneLogin SAML Test** app.

4. Using this as a base, in the **Display Name** field, enter **Upsolver**.

5. Click **Save**.

6. Copy the information from Upsolver into the following fields:

* **Single Sign on URL** — copy from the **Single Sign On URL** in Upsolver.
* **SAML Audience** — copy from the **Audience URI** in Upsolver.

{% hint style="info" %}
The **Single Sign On URL** and the **Audience URI** can both be found by navigating to the **SAML Integration** page \(**More &gt; SAML**\).
{% endhint %}

7. Select the **Parameters** tab.

8. Click the plus icon **+** to add each of the following parameters:

| Field name | Value |
| :--- | :--- |
| **email** | **Email** |
| **firstName** | **First Name** |
| **lastName** | **Last Name** |
| **groups** | **Multi-value parameter** |

{% hint style="info" %}
For each of the above parameters, select **Include in SAML Assertion** then click **Save**.
{% endhint %}

9. From the **Default if no value selected** dropdown, select **MemberOf** and **Semicolon Delimited input \(Multi-value output\)**.

10. Click **Save**.

11. In the **Parameters** tab, click **Save**.

12. Select the **SSO tab**.

13. In Upsolver, click **Edit Integration** and copy the information from the **SSO** tab in OneLogin into the following fields:

* **Single Sign On URL** — copy from the **SAML 2.0 Endpoint \(HTTP\)** field in OneLogin.
* **Identity Provider Issuer** — copy from the **Issuer URL** field in OneLogin.
* **X 509 Certificate** — copy from the **X.509 Certificate** field in OneLogin.

14. In OneLogin, in the **SSO** tab, click **Save**.

15. Select **Users**. Under the **Applications** tab, ensure that the Upsolver application appears for your user.

16. Test access to Upsolver.

17. Complete the procedure as described above.

