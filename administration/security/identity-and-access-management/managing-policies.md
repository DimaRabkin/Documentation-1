---
description: This article provides a guide on how to manage policies in Upsolver.
---

# Manage policies

## **Create a policy**

{% hint style="info" %}
You can create a new policy that includes one or more statements. 

The statement details the edit and view actions allowed or denied for the selected namespace, and the resources that the statement applies to. 

Each statement defines access to a namespace \(e.g. **input** or **\*** for all namespaces\). 

You can also apply additional conditions to a statement, such as which workspaces to apply the statement to, and whether to apply it to all resources or only to resources that are running or not running.
{% endhint %}

The following namespaces are available:

* workspace
* input
* output
* lookup-table
* iam
* organization
* monitoring
* notifications
* billing
* cluster
* udf
* connection
* reference-data
* \*

You can define a policy using the [**Form**](managing-policies.md#create-a-policy-in-the-form) or [**JSON**](managing-policies.md#create-a-policy-using-json) \(either by editing the JSON or importing a JSON file\).

### Create a policy in the Form

1. From the **IAM** page, in the **Policies** tab, click **New Policy**.

2. **Name** the policy.

{% hint style="info" %}
As you build your policy a preview of the policy appears in the **Preview** pane.
{% endhint %}

3. In the **Namespace** tab, select a **Namespace**.

4. Click **Next**.

5. In the **Actions** tab, select the **Policy Type** \(**Allow** or **Deny**\).

6. Under **Actions**, select the required **edit** and/or **view**.

7. Click **Next**.

8. In the **Resources** tab, if applicable, select the **Resources** to apply this statement to.

9. \(Optional\) Select the **Workspaces** to apply this statement to.

10. \(Optional\) Select whether to apply the statement to resources that are running.

11. To add more statements to the policy, click **Add Statement** and then repeat the steps above.

12. Once you have added all desired statements, click **Save**.

### Create a policy using JSON

1. From the **IAM** page, in the **Policies** tab, click **New Policy**.

2. **Name** the policy.

3. Toggle from **Form** to **JSON**.

4. Type the desired permissions in **JSON** format directly into the **Statements** area or click **Select** to import a file.

{% hint style="info" %}
For details regarding specific permissions, see: [Permissions list](../../../getting-started/glossary/permissions-list.md)
{% endhint %}

5. Click **Save**.

## **Edit a policy**

1. From the **IAM** page, in the **Policies** tab, click the pencil icon![](../../../.gitbook/assets/image%20%2824%29.png) in the row of the policy to edit.

2. In the **Policy** area, click **Edit**.

3. Make the desired changes.

4. Click **Apply**.

## **Delete a policy**

1. From the **IAM** page, in the **Policies** tab, click the pencil icon![](../../../.gitbook/assets/image%20%2824%29.png) in the row of the policy to delete.

2. Click **Delete**. A confirmation message will appear. 

3. To delete the policy, click **Yes**.

