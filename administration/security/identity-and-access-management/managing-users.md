---
description: This article provides a guide on how to manage users in Upsolver.
---

# Manage users

A user is assigned to one or more groups and inherits the policies assigned to each of those groups. A user may also be assigned policies directly.

* [Create a user](./#create-a-user)
* [Edit a user](./#edit-a-user)
* [Add groups or policies to multiple users](./#add-groups-or-policies-to-multiple-users)
* [Delete users](./#delete-users)

## **Create a user**

{% hint style="info" %}
You can create a new user and assign them to one or more groups and optionally assign them direct policies. 

This user will receive an email invitation. If they do not receive the invitation, ask the user to check their junk mail.
{% endhint %}

1. From the **IAM** page, in the **Users** tab, click **New User**.

2. Enter in the user's **email**.

3. Enter the user's **name**.

4. Select at least one **group** to add the user to.

5. \(Optional\) Select any **policies** to apply to the user.

6. Click **Invite**.

{% hint style="info" %}
The user will be added to the **Pending Invites** list while an email invitation will be sent to the user email provided.

Once the user accepts the invitation, they appear in the **Approved Users** list.
{% endhint %}

{% hint style="warning" %}
If they do not receive an invitation, ask the user to check their junk main.
{% endhint %}

## **Edit a user**

1. From the **IAM** page, in the **Users** tab, select a **user**.

2. To **add a group**, under **Groups**, click **Add Group**. Select a group and then click **Apply**.   
The associated policies will be added to the **Policies** area.

3. To **delete a group**, click the trash icon![](../../../.gitbook/assets/image%20%282%29.png)in the group row under **Groups**.

4. To **add a direct policy**, under **Policies**, click **Add Policy**. Select a policy and then click **Apply**.

5. To **delete a policy**, click the trash icon![](../../../.gitbook/assets/image%20%282%29.png)in the policy row under **Policies**.

## **Add groups or policies to multiple users**

1. From the **IAM** page, in the **Users** tab, check![](../../../.gitbook/assets/screen-shot-2020-08-25-at-12.41.22-pm.png)the desired users.

2. Click **Add to Groups**. Select the desired groups and then click **Apply**.

3. Click **Attach Policies**. Select the desired policies and then click **Apply**.

## **Delete users:**

1. From the **IAM** page, in the **Users** tab, check![](../../../.gitbook/assets/screen-shot-2020-08-25-at-12.41.22-pm.png)the users to delete.

2. Click **Delete**. A confirmation message will appear.

3. To delete the users, click **Yes**.

