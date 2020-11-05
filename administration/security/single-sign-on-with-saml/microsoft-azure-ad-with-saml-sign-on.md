---
description: This procedure describes how to configure Microsoft Azure with SAML sign-on.
---

# Microsoft Azure AD with SAML sign-on

## Configure Microsoft Azure AD with SAML sign-on

1. In Microsoft Azure, in the sidebar of the **Azure Active Directory**, select **Enterprise applications**.

2. Click **New Application** and then click **Non-gallery application**.

3. In the **Name** field, enter **Upsolver** and then click **Add**.

4. Under **Getting Started**, click **Set up single sign-on** and then click **SAML**.

5. Within **Basic SAML Configuration**, click **Edit**.

6. Copy the information from Upsolver into the following fields:

* **Identifier \(Entity ID\)** — copy from the **Audience URI** in Upsolver.
* **Reply URL \(Assertion Consumer Services URL\)** — copy from the **Single Sign On URL** in Upsolver.

{% hint style="info" %}
The **Single Sign On URL** and the **Audience URI** can both be found by navigating to the **SAML Integration** page \(**More &gt; SAML**\).
{% endhint %}

7. Click **Save**.

8. Within **User Attributes and Claims**, click **Edit**.

9. Click **Add new claim** to add the following claims:

| Claim | Name | Source attribute |
| :--- | :--- | :--- |
|  | **email** | **user.mail** |
| Optional | **firstName** | **user.givenname** |
| Optional | **lastName** | **user.surname** |

10. Click **Add a group claim** and select **All groups**.

11. In the **Source attribute** field, if you are using Active Directory, select **sAMAccountName**. Otherwise, leave this as **Group ID**.

12. In the **Advanced options**, check **Customize the name of the group claim**.

13. In the **Name** field, enter **groups** then click **Save**.

14. In Upsolver, click **Edit Integration** and copy the information from the **SAML-based Sign-on** page in Azure into the following fields:

* **Single Sign On URL** — copy from the **Login URL** field in Azure.
* **Identity Provider Issuer** — copy from the **Azure AD Identifier** field in Azure.
* **X 509 Certificate** — copy from the **Certificate \(Base64\)** field in Azure.

15. To test access to Upsolver, click **Test** in Azure on the **SAML-based Sign-on** page.

16. Click **Sign in as current user**.

17. Complete the procedure as described above.

