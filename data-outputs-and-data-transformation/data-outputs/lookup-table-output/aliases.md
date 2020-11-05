---
description: >-
  This article provides an overview of lookup table aliases and provides a guide
  on how to create, edit, and delete an alias.
---

# Lookup table alias

{% hint style="info" %}
### What is a lookup table alias?

A lookup table alias includes a custom token \(either entered manually or system generated\) that is used by the API as an identifier. 
{% endhint %}

This can be useful in cases when you want to test various lookup tables before selecting one for production. 

Once you finalize the lookup table required, you can edit the lookup table alias to use the required lookup table. The custom token remains unchanged, and the solution using the API does not need to be updated.

To view your lookup table aliases, click **More &gt; Aliases**.

On this page, you will find a list of:

* **Attached Aliases:** The aliases that are **linked** to lookup tables.
* **Unattached Aliases:** The aliases that are **not linked** to lookup tables.

From this page, you can also:

* [Create an alias](aliases.md#create-a-lookup-table-alias)
* [Edit an alias](aliases.md#edit-a-lookup-table-alias)
* [Delete an alias](aliases.md#delete-a-lookup-table-alias)

## Create a lookup table alias

1. From the **Aliases page**, click **New**.

2. **Name** your lookup table alias.

3. \(Optional\) Enter a **description** of your alias.

4. \(Optional\) Enter in the unique API token as the **custom token**.

{% hint style="info" %}
Leave the **Custom Token** field empty to use a system-generated token.
{% endhint %}

5. \(Optional\) **Select** a **lookup table** to link to the alias.

6. Click **Save**.

## Edit a lookup table alias

{% hint style="info" %}
You can edit a lookup table alias, but you cannot modify the custom token.
{% endhint %}

1. From the **Aliases page**, click the pencil icon![](../../../.gitbook/assets/image%20%2824%29.png).

2. Edit the desired alias details:

* **Name:** The lookup table alias name.
* **Description \(optional\):** A description of the lookup table alias.
* **Select Lookup Table \(optional\):** The lookup table to link to the alias.

3. Click **Save**.

## Delete a lookup table alias

1. From the **Aliases page**, click the trash icon![](../../../.gitbook/assets/image%20%282%29.png).

