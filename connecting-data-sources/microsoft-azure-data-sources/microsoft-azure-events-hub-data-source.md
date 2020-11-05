---
description: This article describes how to connect Upsolver to Azure Event Hubs source.
---

# Azure Event Hubs data source

{% hint style="info" %}
### What is Azure Event Hubs?

Event Hubs is a fully managed, real-time data ingestion service that’s simple, trusted, and scalable. Stream millions of events per second from any source to build dynamic data pipelines and immediately respond to business challenges.Before creating a data source, you must have a working Event Hub. Follow instructions [here](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-create) if you haven't created an Event Hub.
{% endhint %}



1. Click on **DATA SOURCES &gt; NEW** and find **Azure** **Event Hubs &gt; SELECT**

![](../../.gitbook/assets/image%20%281%29.png)

2. Fill out the required information and click on **Create your first Azure Event Hub Connection**

![](../../.gitbook/assets/image%20%2832%29.png)

3. Fill out the required information to connect to your Azure Event Hub and click on **CREATE**.

![](../../.gitbook/assets/image%20%2885%29.png)

{% hint style="info" %}
Note: use the **Connection string-primary key** as the **CONNECTION STRING**
{% endhint %}

![](../../.gitbook/assets/image%20%2839%29.png)

4. Fill out the form accordingly with the connection from the last step selected and click on **CONTINUE**.

![](../../.gitbook/assets/image%20%28131%29.png)

5. Check the Parsed Data Sample. If everything looks correct, click on **CREATE**.

![](../../.gitbook/assets/image%20%2829%29.png)

6. You should see the data source page. Congratulations! You're ready to create a [data output](../../data-outputs-and-data-transformation/data-outputs/).

![](../../.gitbook/assets/image%20%2833%29.png)

{% hint style="info" %}
If you experience any issues connecting to your Event Hub, please file open a [case](../../support/login-upsolver-support-portal.md). 
{% endhint %}



