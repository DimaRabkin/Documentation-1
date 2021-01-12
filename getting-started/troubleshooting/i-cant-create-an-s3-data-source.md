# I can't create an S3 data source

For normal S3 Data Sources \(without SQS\), your data needs to be sorted lexicographically. 

Our system should be able to detect the lexicographic date pattern from the list of your files. If it fails, try narrowing down the list by entering the path to your files.

## Example:

If the list of files is:

* `s3://bucket/input/a/2019/01/01/00/00/file.txt`
* `s3://bucket/input/a/2019/01/01/00/01/file.txt`
* `s3://bucket/input/a/2019/01/01/00/02/file.txt`
* `s3://bucket/input/a/2019/01/01/00/03/file.txt`

Enter **`input/a`** in the folder field. 

You can also try setting the **Start Ingestion From** field to a time when there is data.

{% hint style="info" %}
If neither of these suggestions help,  please file a ticket via [Upsolver Support Protal](https://support.upsolver.com/hc/en-us).
{% endhint %}

