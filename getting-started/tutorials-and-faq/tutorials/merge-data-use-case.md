---
description: >-
  This article outlines a use case in which you merge data from two sources
  together to create a final output.
---

# Merge data use case

A very common use case is merging data from a data stream \(A\) with a reference data source \(B\). This requires you to use a field to lookup \(and merge\) data from the reference data source \(B\) with the data stream \(A\) and then save the resulting data in the output.

This can be achieved by adding a lookup to the output and specifying the matching key. Any data brought in from the data source \(B\) comes in via an aggregation in the lookup. 

For example, you can use the `LAST` aggregation function to select the last value of a field within a time window. This can also be used to look up user information that is stored in a user data table—that is, given the `USER_ID`, look up the `USER_DETAIL`, `USER_DETAIL2`, and so on.

{% hint style="info" %}
#### Required Level of Expertise

* Intermediate
{% endhint %}

## Add a lookup

1. On the **Outputs** page, select the desired output and click **Edit** \(or [create a new output](../../../data-outputs-and-data-transformation/data-transformation-ui/creating-an-output/)\).

2. Click **Add** **Lookup** and select the lookup source \(e.g. an existing data source or lookup table\). Then click **Next**.

3. In **Join Fields**, select the field to join to in data source \(B\) \(e.g.`USER_ID`\).   
The matching field in data stream \(A\) is selected automatically.

{% hint style="warning" %}
**Note:** The field on the left is the field in data source \(B\) that we are looking up from. The field on the right is the key from data stream \(A\).
{% endhint %}

4. Add aggregations; for example:

* `LAST(USER_ID)`
* `LAST(USER_DETAIL1)`
* `LAST(USER_DETAIL2)`

5. Set the **Time Frame** to infinite, by entering **-10000** in the **From** field.   
This ensures you can access all the data irrespective of when it was written.

6. Select **Use Full History** to treats the data source \(B\) as a reference data table.   
This is useful if the latest view of the data is required, and the actual time that the data was written is irrelevant.

7. Enter an **Alias** for the lookup and click **Save**.

{% hint style="info" %}
Toggle from the **UI** to **SQL** view to see the `JOIN` statement \(it can appear as part of a `WITH` statement or inline\).
{% endhint %}

8. Click **Run** and fill in the required details to deploy the output.  
**See:** [Run an output](../../../data-outputs-and-data-transformation/data-transformation-ui/running-an-output.md)

