---
description: >-
  This article provides a guide on how to create a Google Storage connection in
  Upsolver.
---

# Google Storage connection

## Create a Google Storage connection

1. Enter the **project ID**.

2. Enter the **name** of your Google Storage **bucket**.

3. In **Credentials JSON**, enter in the service account certificate information.  
To learn more about service accounts, [click here](https://cloud.google.com/iam/docs/service-accounts).

To obtain the certificate information:

1. Create a **service account** for your project. **See:** [Creating and managing service accounts](https://cloud.google.com/iam/docs/creating-managing-service-accounts#iam-service-accounts-create-console)
2. Create a corresponding **service account key**. **See:** [Creating and managing service account keys](https://cloud.google.com/iam/docs/creating-managing-service-account-keys)

{% hint style="warning" %}
Be sure to select **JSON** as your **key type**!
{% endhint %}

Copy-paste the contents of this service account JSON key into the **JSON credentials** field.

The final JSON format should look as follows:

```javascript
{
  "type": "service_account",
  "project_id": YOUR_PROJECT_ID,
  "private_key_id": YOUR_PRIVATE_KEY_ID,
  "private_key": -----BEGIN PRIVATE KEY-----YOUR PRIVATE KEY\n-----END PRIVATE KEY-----\n,
  "client_email": CLIENT_EMAIL"@developer.gserviceaccount.com",
  "client_id": CLIENT_ID,
  "auth_uri": "https://accounts.google.com/o/oauth2/auth",
  "token_uri": "https://oauth2.googleapis.com/token",
  "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
  "client_x509_cert_url": "https://www.googleapis.com/robot/v1/metadata/x509/"CLIENT_EMAIL
}
```

4. \(Optional\) Enter in the **path** to your bucket.

{% hint style="info" %}
Check **Read Only** for the connection to be read only; Upsolver will not be able to write data to or delete data from the bucket.
{% endhint %}

5. Finally, **name** this connection, then click **Create**.

## 

