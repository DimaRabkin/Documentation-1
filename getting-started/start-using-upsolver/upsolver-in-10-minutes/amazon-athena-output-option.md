---
description: >-
  Process streaming data from end-to-end within 10 minutes. The data source is
  an Amazon S3 bucket (updated continuously). Upsolver processes the data and
  loads to Amazon Athena table.
---

# Amazon Athena data output

## Create a data source

1. Click on **DATA SOURCES &gt; NEW** to connect to various data sources. Upsolver works with both streaming and static data sources.

![](https://lh3.googleusercontent.com/VEBtmN-b2sXlGI8KbaKyeZtTRuXAqt4NkBess6US8LAc6NxoQAvGaQLhr_2lTKRH6V3Pe2JglaQvDSlA5hcep_DedbJFNS7ayYi2Cx-uozzUkzfZW79DqsqJutaVp6-f0l799Goz)

2. Click on **SELECT** next to **Amazon S3** data source. There are many data sources to choose from. The Quickstart uses _pre-populated_ mobile data.

![](https://lh6.googleusercontent.com/Q4l7k9KjZetrJL8f1dtauybuIMw329ecce7bib5JDhOrOl4KasXJiSBxGAbTPujlaxGUHb92okdSyGH72L_Tj_j-mVvwuyOP8je5qXfrQPkuQq5w6njRXEgPTIx-O3n-csJnPuC_)

3. Choose **BUCKET &gt;** **upsolver-tutorials-mobile-users** by clicking on the dropdown box.  Fill in **FOLDER &gt; data** and **DATE PATTERN &gt; yyyy/MM/dd/HH/** click on **CONTINUE**. Upsolver automatically verifies the files in the bucket and displays blue checkmarks next to the file name.

![](../../../.gitbook/assets/image%20%2882%29.png)

4. Upsolver automatically parses the data and displays a sample of the data that you’re working with. You can expand each record to view each event in a formatted view.

![](https://lh4.googleusercontent.com/VSsLMilef5nd-Vgy7IyjZlPk4wzq_IBmo6kLKnIcVZqgrCkmVnYUKeJuzkV5hb1ZIWX5BzjPeq4OC0BV1Cfx8oXcM3HeVf0N3B8ow229INdD-aGIkei3KPrfMn_DFhxDgQ2P-MUh)

5. Click on **CREATE** to complete the Amazon S3 Data Source. Notice the schema is automatically generated and data statistics are also displayed.

![](https://lh4.googleusercontent.com/1TzV0loU_yMvnGi1-Yxk28yrhiR1ITl0IxeZTHMKROZQsOdVctaTtmNaWTe4wS1CAp4DWIyhUGYQVF8GkTV5qKsQFIphxoemWPxNzimagThCnDD9P9FmKZewIAzZkEknvTdeM_lf)

##  **Create a data output**

1. Click on **NEW OUTPUT** on the upper right corner. \(You can also get to the output screen by clicking on OUTPUTS &gt; NEW\)

![](https://lh4.googleusercontent.com/MWKDM4NzS3bsF93Pq5DZ-4nd5QV6B7JXOS2cA1N8vy92qij_fPmPTPeilDb1XiW3DjcZMc8L0YC-62snOK6wiXnefjBe-Ppku7s9ymdk3M5sS7NEUNiYPpJaQeHTe5mYgkfgBHV0)

2. Choose **Amazon Athena** output by clicking on **SELECT**. We’re going to use Amazon Athena as our output for this tutorial. You can output to any Upsolver data outputs. 

![](../../../.gitbook/assets/image%20%28105%29.png)

3. Enter **gaming** as the name of the output. Leave everything as default and click on **NEXT**.

![](../../../.gitbook/assets/image%20%288%29.png)

4. Expand **payload** on the left hand side. Add a field to your output by clicking on the **+** sign next to the fields. The field that we’re adding is data.payload.**eventName**

![](https://lh4.googleusercontent.com/kYfGKdqytOPUi7-qXFq-lStbLuIpgE1bv8L_Q-gOPypxSCCCNmpcK7Wk-FtVcYA9d_BQKMbAzg8_Cjb36rumK2Z-QC_m921h05G4hRnss1Qxvtc1x3H_vU8ZwMc_qnOXKqVpnvAE)

## **Data transformation**

1. Rename the fields by clicking on the field under **SCHEMA COLUMN** and rename **payload.eventame** to **event\_name**

![](https://lh4.googleusercontent.com/v_6Rqnc7nFQq3xCUF4DBwELml7m1ZhvPkZIBpIZ6kg7pLHIaO1oJchci6FFf4xX-xKAswiu6GemKqHAH5_ztLKOAmh8FZa-XSthejIQDOtXmSsP-0cEt59NMJkzxqmcUEZJNPBjo)

2. Transform data.clientEventTime to from unix epoch to human readable format. Click on **Add Calculated Field** on the upper left and find the **TO\_DATE** function click on **SELECT**. Enter **data.clientEventTime** in the **DATETIME** box and give the field a **NAME** called **event\_time**. Click on **PREVIEW** to make sure the date looks right and click on **SAVE**.

![](https://lh4.googleusercontent.com/f25W44WwYgJoAEeRl7qbPUJWaou9nw9HdNm4yAG0EMpFP1SICxEnpnGgTb7lyKHOcSmFGIlsHjkPOA4bBDZDFFl4zsm3SCQ9aXC8pLXwCLdLdGlV5jMNb-2Xu2odxMLIh032F6wW)

**3.** We're going to do a simple aggregation by adding the count of events for a given time. Click over to the **SQL tab** on the upper right hand corner. Keep in mind all changes that are made in the SQL view will also be represented in the UI view and vice-versa. **Add 3 lines of SQL to the statement** \(see line **5, 6 and 8** below\) to the automatically generated SELECT statement and click on **PREVIEW** to ensure data looks correct.

![](../../../.gitbook/assets/image%20%28109%29.png)

```sql
SET event_date = UNIX_EPOCH_TO_DATE(data.clientEventTime);
// GENERATED @ 2020-10-06T19:03:53.293444Z
SELECT
  data.payload.eventName AS event_name,
  count(*) as event_count,
  event_date as "event_date"
FROM "upsolver-tutorials-mobile-users" 
  group by event_date, data.payload.eventName
```

![](https://lh4.googleusercontent.com/5a89wcupXGYZDOWAHolTXZ9vEdMSAyj0t89VA6e6mzJjVVT6fNXPEgmzdMy7Z7Xna56GNJrGxXXi1mW0oJ-WO60yIArYI6aeM0yYnUBxFBieocFKd95Du1mBtkpA8Y8OM2rpX8NL)

4. Define how to partition the table you're loading into. Click on **Manage Partitions &gt; Partition by time**. Select **Partition Field &gt; event\_date** and choose **HOURLY**. Click on **CLOSE**.

![](../../../.gitbook/assets/o0cszx6e2r.gif)

## **Connect to Amazon Athena and start streaming**

1. Click on **RUN** on the upper right corner**.** Create a new connection to Amazon Athena by choosing **CONNECTION &gt; Create your first Amazon Athena Connection**.

![](../../../.gitbook/assets/g17e0gbkts.gif)

2.  Make sure you're logged in your Amazon AWS account for the following steps.

{% hint style="info" %}
Outputting to Amazon Athena requires Upsolver to integrate with your account. If you don't have an environment available, you can try the [MySQL output ](mysql-data-output-option.md)and write to your own local environment.
{% endhint %}

Click on **INTEGRATE** and make sure you're logged in to your AWS account. For your privacy, Upsolver does not host your data.

![](../../../.gitbook/assets/image%20%2846%29.png)

3. Choose the **Multi-Tenant Deployment** option. Leave everything as default and click on **CONTINUE**. 

{% hint style="info" %}
Upsolver has many deployment models. For this quick exercise, we're going to deploy it as a fully managed service. You can also easily deploy Upsolver in your private VPC.
{% endhint %}

![](../../../.gitbook/assets/image%20%28132%29.png)

4. If you haven't logged in your AWS account, make sure you are logged in now. It will bring you to the CloudFormation stacks page for the integration. Check the **acknowledge** box and click on **Create stack**. 

![](../../../.gitbook/assets/image%20%2837%29.png)

The integration should table about 1 minute. and you will see **CREATE\_COMPLETE**. Switch back to your Upsolver environment and click on **DONE**. 

![](../../../.gitbook/assets/image%20%28129%29.png)

5. Click on **DATA OUTPUT &gt; gaming &gt; RUN.**

![](../../../.gitbook/assets/kb2sdujhxs.gif)

6. Select **S3 STORAGE &gt; S3 Default Storage** and **Connection &gt; Athena** Choose the **DATABASE NAME &gt; default** that you want the table to reside. Give the table a name **TABLE NAME &gt; shopping** Click on **NEXT**.

![](../../../.gitbook/assets/uwmp9unw9k.gif)

  
7. Use the **slide bar** to select the data from the **last day**. Keep ENDING AT as Never to ensure that the data is continuously being streamed to the table. Click on **DEPLOY**.

![](../../../.gitbook/assets/image%20%28119%29.png)

8. Upsolver starts outputting the data to Athena. Wait for a moment for the data to write to the Amazon Athena table. This might take a few minutes. You can keep track of progress under the **PROGRESS** tab.

![](../../../.gitbook/assets/image%20%2831%29.png)

## **Verify your data in Amazon Athena**

![](https://lh5.googleusercontent.com/0fxWkWrTxadsR-uuIkp9Tny0BVu2iLcCcNBBa_G5SN6wi6yOvf64W__KBgEHb24vjTWHBStlUU4LlwWNq_yqszCcdvc_c4ITRmULBgt209OxbuWtUjhS4wBRdZ0r0Dzo6lN1GVlW)

