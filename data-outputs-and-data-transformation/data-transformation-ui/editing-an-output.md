---
description: This article provides a guide on how to edit an output in Upsolver.
---

# Edit an output

In order to ensure data lineage, once you run an output it becomes immutable \(as it is a production task\). However, you can still edit the output, but it does not stop it from running.

Changes to the output are saved automatically and the edited output is still the same logical output \(effectively equivalent to a new version of an existing output\). 

{% hint style="info" %}
The output appears in **Draft** mode while it is being edited and it appears as a separate tile in the **Outputs** page. 

A suffix **`_<Number>`** is added to the ID of the output to indicate that it is a new version of the output.
{% endhint %}

Once you have edited the output, you can duplicate, discard, or run the edited output.

When you run the edited output, you can choose:

* To alter the existing table and write to a different location in the existing output data table, making it possible to identify which files were created by which version of the output.
* Create a new table. This is equivalent to duplicating the output. The existing table and output are not affected in any way by this operation.

{% hint style="warning" %}
**Note:** You can only edit the contents of a new lookup table that has not yet run. 

Once a lookup table has run, you cannot edit the lookup table. Instead duplicate the lookup table and edit the copy.
{% endhint %}

## Edit an output

1. From the **Outputs page**, select the output you wish to edit.

2. Click **Edit**.

3. Edit the output as required.

4. Click one of the following options:

{% tabs %}
{% tab title="Discard Draft" %}
Abandons the edited output.
{% endtab %}

{% tab title="Duplicate" %}
Duplicates the edited output.
{% endtab %}

{% tab title="Run" %}
Runs the edited output.

To run the output: 

1. Select whether to **Alter Existing Table** or **Create New Table**.
2. Click **Next**.

If you selected **Create New Table**:

* The **Duplicate Output** window will appear. 
* This is equivalent to duplicating the output. 
* **See:** [Duplicating an output](duplicating-an-output.md)

If you selected **Alter Existing Table**:

* The **Run** window will appear. 
* Select the **Compute Cluster** and select the **Processing Time Range**. 
* The original output **finishes running** at the time when the new edited output starts running. 
* The data from the new version of the output is located in a **separate folder**. 
* If you select a date and time in the past, any data stored after that date by the original output is **deleted**, and the new output processes the data from that point in time onwards. 
* The original and new locations are transparent to the user.
{% endtab %}
{% endtabs %}

