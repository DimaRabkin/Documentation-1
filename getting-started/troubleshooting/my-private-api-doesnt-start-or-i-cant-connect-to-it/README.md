# My private API doesn't start or I can't connect to it

The initial AWS Integration takes time, especially in My VPC mode. 

Once the integration is done, it should take up to 5 minutes until the Local API is up. If the Local API is still unavailable beyond that time period, it might be the result of one of the following issues:

* [Elastic IPs limit reached](elastic-ips-limit-reached.md)
* [EC2 Spot Instance not running](ec2-spot-instance-not-running.md)
* [DNS cache](dns-cache.md)
* [Security group not open](security-group-not-open.md)

{% hint style="info" %}
If none of the above applies to your situation, contact us via the intercom widget or by mail: support@upsolver.com.
{% endhint %}

