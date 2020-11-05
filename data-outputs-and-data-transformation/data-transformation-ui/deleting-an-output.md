---
description: This article provides a guide on how to delete an output in Upsolver.
---

# Delete an output

{% hint style="info" %}
In order to delete an output, its status must be current **paused**.  
**See:** [Stop an output](stopping-an-output.md)
{% endhint %}

## Delete a stopped output

1. From the **Outputs** page, select the **Paused** output you wish to archive.

2. Click **Delete**.

{% hint style="warning" %}
You will be warned if this output has any existing references that may be affected by its deletion.
{% endhint %}

3. Check **Delete Data** to delete the data that has been created in your cloud storage for this object.

4. \(Optional\) If you chose to delete the data, select a **compute cluster** to execute the deletion.

5. Click **Delete**. This output has now been moved to **Trash**.

## Restore a deleted output

1. From the **Outputs** page, check **Trash** to view your deleted outputs.

2. Select the **output** you wish to restore.

3. Click **Restore**.

