---
description: >-
  This page provides a guide on how to connect Redshift Spectrum to Glue Data
  Catalog.
---

# Connect Redshift Spectrum to Glue Data Catalog

{% hint style="info" %}
To connect Redshift to the AWS Glue Data Catalog, you need to:

* [ ] [Create a role for Redshift Spectrum](connecting-redshift-spectrum-to-glue-data-catalog.md#creating-a-role-for-redshift-spectrum)
* [ ] [Select a review policy](connecting-redshift-spectrum-to-glue-data-catalog.md#selecting-a-review-policy)
* [ ] [Create external schema](connecting-redshift-spectrum-to-glue-data-catalog.md#creating-external-schema)
{% endhint %}

## Create a role for Redshift Spectrum

1. Sign in to the AWS console.

2. Open the IAM console at [https://console.aws.amazon.com/iam](https://console.aws.amazon.com/iam).

3. In the navigation pane, click **Roles**.

4. Click **Create Role**.

5. Select **Redshift** from the list of services.

6. In the **Select your use case** section, select **Redshift &gt; Customizable**.

7. Click **Next: Permissions**.

8. Click **Next: Tags**.

9. Click **Next: Review**.

10. Enter a name for your role \(e.g. **redshiftSpectrumRole**\).

11. Click **Create Role**.

12. On the **Roles** page, look for the role just created \(by name\) and select it.

13. Select **Add Inline Policy**.

![Add Inline Policy Button](https://docs.upsolver.com/Content/Resources/Images/Upsolver%20Content%20Extra/Creating%20a%20Role%20for%20Redshift%20Spectrum.png)

14. Select **JSON Editing Option**.

![JSON Editing Option](https://docs.upsolver.com/Content/Resources/Images/Upsolver%20Content%20Extra/Creating%20a%20Role%20for%20Redshift%20Spectrum_1.png)

15. Paste the following policy into the editor \(clear the default base policy before pasting\):

```bash
{
    "Version": "2012-10-17",
    "Statement": [
            {
                "Effect": "Allow",
                "Action": ["s3:Get*", "s3:List*"],
                "Resource": "*"
            },
            {
                "Effect": "Allow",
                "Action": [
                    "glue:CreateDatabase",
                    "glue:DeleteDatabase",
                    "glue:GetDatabase",
                    "glue:GetDatabases",
                    "glue:UpdateDatabase",
                    "glue:CreateTable",
                    "glue:DeleteTable",
                    "glue:BatchDeleteTable",
                    "glue:UpdateTable",
                    "glue:GetTable",
                    "glue:GetTables",
                    "glue:BatchCreatePartition",
                    "glue:CreatePartition",
                    "glue:DeletePartition",
                    "glue:BatchDeletePartition",
                    "glue:UpdatePartition",
                    "glue:GetPartition",
                    "glue:GetPartitions",
                    "glue:BatchGetPartition",
                       "lakeformation:GetDataAccess"
                ],
                "Resource": [
                    "*"
                ]
            }
        ]
}
```

16. Click **Review Policy**.

17. Give a name to your policy \(for example, **redshiftSpectrum**\).

18. Click **Create Policy**.

19. Make a note of the role ARN and keep it handy - you will need this for the external schema creation.

20. Open the Redshift console at [https://console.aws.amazon.com/redshift](https://console.aws.amazon.com/redshift).

21. Select **CLUSTERS**.

22. For each cluster that will use Redshift, click on the required cluster.

23. In the **Cluster Properties** section, select **IAM roles**.

24. Locate and select the role you created.

25. Click **Apply changes**.

## Select a review policy

1. Select a name for the policy, for example, **redshiftSpectrum**.

2. Select **Create Policy**.

3. Make a note of the role ARN \(it is required for external schema creation\).

4. Open the **Redshift** console at [https://console.aws.amazon.com/redshift](https://console.aws.amazon.com/redshift).

5. Select **Clusters**.

6. Perform the following actions for each Redshift cluster on which you want to use 

* Redshift Spectrum:
* Select the cluster.
* In the Cluster Properties section, select **See IAM roles**.
* Locate and select the previously created role name.

7. Click **Apply Changes**.

## Create external schema

1. Run the following query in the cluster \(this can be done either via the **Query Editor** section under the Redshift Management Console or via your favorite SQL editor\).

```sql
 create external schema spectrum_schema from data catalog
 database 'database name'
 iam_role 'the role ARN created above'
 create external database if not exists;					
```

2. Open the **Lake Formation** console at: [https://console.aws.amazon.com/lakeformation](https://console.aws.amazon.com/lakeformation)

3. In the navigation pane, select **Permissions &gt; Data permissions**.

4. Provide the following information:

| Prompt | Details |
| :--- | :--- |
| **IAM role** | Select the IAM role created, **redshiftSpectrumRole**, as the IAM role.  The **Amazon Redshift Query Editor** uses this IAM role for permission to access the data. **See:** [Create an IAM role for Amazon Redshift](https://docs.aws.amazon.com/redshift/latest/dg/c-getting-started-using-spectrum-create-role.html) |
| **Database** | Select your **Lake Formation** database. |
| **Table** | Select a table within the database to query. |
| **Columns** | Select **All Columns**. |

5. Select **Select permission**.

6. Click **Save**.

