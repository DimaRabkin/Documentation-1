---
description: This article provides a guide on how to create a compute cluster in Upsolver.
---

# Compute cluster

## Add a compute cluster

1. From the **Clusters page**, click **New &gt; Compute**.

2. **Name** this cluster.

3. \(Optional\) Select your **AWS** **region**.

4. \(Optional\) Select your **private VPC**.

{% hint style="info" %}
Check **Elastic IPs** to create Elastic IPs for these servers. 

The server instances will use these Elastic IPs allowing you to open access for your servers in external resources.
{% endhint %}

5. Select your **server compute units** to define the compute units one server will use.   
Choosing a server with '**high-memory**' indicates a server type which has **less CPU** units but has **more RAM**.

6. Select a range of **processing units** between 1 and 64.

7. \(Optional\) Select a range for **additional processing units for replay** from 0 up to 64.

{% hint style="info" %}
When configured, replay tasks will **run** on a **separate cluster** up to this size, which is **billed separately**. 

If active, it is recommended for this cluster to be at least as big as the maximum size of the cluster.
{% endhint %}

8. Choose a [**scaling strategy**](adding-a-compute-cluster.md#scaling-strategy).

9. Check **Allow Maintenance Access** if you wish to allow Upsolver to access your instances over SSH for maintenance purposes.

10. Click **Create**.

## Scaling Strategy

When selecting scaling options, consider the following:

### Scale Up

* **Low Cost**
  * looks exclusively at the work backlog, so it should reach 100% CPU and after a while scale up.
* **Low Latency**
  * scales up if the average CPU is over 80%.
* **Consistent Low Latency**
  * scales up if the average CPU is over 60%.

### Scale Down

* **Low Cost** and **Low Latency**
  * check that the expected CPU after scaling down is below 70%. 
    * This means that if there are 3 servers, they must be below 47% CPU.
      * $$47 \cdot 3 = 141 \longrightarrow 141 / 2 = 70.5$$
      * or 70.5% CPU for 2 servers
* **Consistent Low Latency**
  * applies the same checking, but the threshold is 50%. 
  * This logic is to prevent scaling up and down in rapid succession.

