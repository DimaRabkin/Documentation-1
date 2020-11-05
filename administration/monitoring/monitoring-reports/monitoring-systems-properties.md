---
description: >-
  This article provides a list of the different monitoring system properties
  along with their corresponding description.
---

# Monitoring system properties

* [Datadog](monitoring-systems-properties.md#datadog)
* [Amazon CloudWatch](monitoring-systems-properties.md#amazon-cloudwatch)
* [InfluxDB](monitoring-systems-properties.md#influxdb)
* [Elasticsearch](monitoring-systems-properties.md#elasticsearch)
* [SignalFx](monitoring-systems-properties.md#signalfx)
* [Splunk](monitoring-systems-properties.md#splunk)

## Datadog

{% tabs %}
{% tab title="Name" %}
The name of the monitoring report.
{% endtab %}

{% tab title="Datadog API Key" %}
The API key to access Datadog.
{% endtab %}
{% endtabs %}

## Amazon CloudWatch

{% tabs %}
{% tab title="Name" %}
The name of the monitoring report.
{% endtab %}

{% tab title="Namespace" %}
The namespace — container for CloudWatch Metrics.
{% endtab %}

{% tab title="Region" %}
The CloudWatch AWS region.
{% endtab %}
{% endtabs %}

## InfluxDB

{% tabs %}
{% tab title="Name" %}
The name of the monitoring report.
{% endtab %}

{% tab title="Connection String" %}
The connection string to connect InfluxDB.
{% endtab %}

{% tab title="User" %}
The InfluxDB user.
{% endtab %}

{% tab title="Password" %}
The InfluxDB password.
{% endtab %}

{% tab title="Database Name" %}
The database name.
{% endtab %}

{% tab title="Retention Policy" %}
\(Optional\) The retention policy in InfluxDB.
{% endtab %}

{% tab title="Enable gzip" %}
Enable gzip compress for the HTTP request body.
{% endtab %}
{% endtabs %}

## Elasticsearch

{% tabs %}
{% tab title="Name" %}
The name of the monitoring report.
{% endtab %}

{% tab title="Connection" %}
Choose your Elasticsearch connection from the list of connection or [configure a new one](../../connections/elasticsearch-connection.md). 
{% endtab %}

{% tab title="Index Type" %}
\(Optional\) The type of the index.
{% endtab %}
{% endtabs %}

## SignalFx

{% tabs %}
{% tab title="Name" %}
The name of the monitoring report.
{% endtab %}

{% tab title="SignalFx Auth Token" %}
The auth token.
{% endtab %}

{% tab title="SignalFx Region" %}
The region where your SignalFx environment runs.
{% endtab %}
{% endtabs %}

## Splunk

{% tabs %}
{% tab title="Name" %}
The name of the monitoring report.
{% endtab %}

{% tab title="Splunk Deployment Name" %}
The deployment name. 

For self-service accounts with a URL in the structure`prd-p-xxx.cloud.splunk.com`, the deployment name is: `p-xxx`.

For managed accounts with a URL in the structure `XXX.splunkcloud.com`, the deployment name is: `XXX`.
{% endtab %}

{% tab title="Is Managed" %}
**True** if you are using a managed Splunk account and **False** otherwise. 

This can be inferred from the URL of your account: 

* **splunkcloud.com** usually means managed
* **cloud.splunk.com** usually means self-service
{% endtab %}

{% tab title="Splunk HTTP Event Collector Token" %}
The HEC token. 

Enables sending data over HTTP \(or HTTPS\) directly to Splunk Enterprise or Splunk Cloud.
{% endtab %}
{% endtabs %}

