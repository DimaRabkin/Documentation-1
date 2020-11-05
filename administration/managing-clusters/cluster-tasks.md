---
description: >-
  This article provides an overview of the information displayed in the tasks
  tab for clusters.
---

# Cluster tasks

The **Tasks** tab shows you the tasks running on the cluster; these may be tasks for data sources, outputs, lookup tables, or dashboards running on the cluster.

{% hint style="info" %}
Each task panel shows:

* name of the task
* when it was created
* whether it is running
{% endhint %}

For different types of tasks, additional pieces of information will be displayed:

### **Lookup table tasks**

* delay
* number of rows
* amount of RAM and storage used
* graph showing average queries per minute and average misses per minute based on the past 10 minutes

### **Data source tasks**

* cluster name
* number of fields
* total number of events loaded
* total number of errors
* rate of events
* graph showing volume of events over time
  * mouse over graph to view the details for a specific time period

### **Output tasks**

* output name
* delay
* number of events
* number of failures
* graph showing events over time

You can click on a specific task to view more details.

