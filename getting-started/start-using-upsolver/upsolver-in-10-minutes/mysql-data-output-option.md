---
description: >-
  This option allows you to integrate with a local environment instead of
  integrating with AWS Athena.
---

# Local MySQL data output option

## \*\*\*\*

1. Click on **NEW OUTPUT** on the upper right corner. \(You can also get to the output screen by clicking on OUTPUTS &gt; NEW\)

![](https://lh4.googleusercontent.com/MWKDM4NzS3bsF93Pq5DZ-4nd5QV6B7JXOS2cA1N8vy92qij_fPmPTPeilDb1XiW3DjcZMc8L0YC-62snOK6wiXnefjBe-Ppku7s9ymdk3M5sS7NEUNiYPpJaQeHTe5mYgkfgBHV0)

2. Choose **MySQL** output by clicking on **SELECT**. We’re going to use MySQL as our output for this tutorial. You can output to any Upsolver data outputs. 

![](https://lh4.googleusercontent.com/PXhvs6a7EiGfmAHcgqwN3_Jwz96iPo6L17sUl5E534p062iFtkakUxPbFWcx8g2BIVYVSV26ayqeEaPMGXLmkAOXmcIoxewZkcuVT2iyOgDUlaU1860lpsaVBNCNIwk1rv3s-19T)

3. Enter **gaming** as the name of the output. Leave everything as default and click on **NEXT**.

![](https://lh5.googleusercontent.com/pwqXwMAeu4kndQzv2fMDh4-N5rB_q6S6vpsR10OEITDHI4aatdyMWBEfhO8dpdBuaxsa5hVm1195UMzW9qM38Jnb6miZ49_RR8Koi7LBaRr8v7Y2P68vzdsJFE5Ck4Ppi6ByzegG)

4. Add a field to your output by clicking on the **+** sign next to the fields. The field that we’re adding is data.payload.**eventName**

![](https://lh4.googleusercontent.com/kYfGKdqytOPUi7-qXFq-lStbLuIpgE1bv8L_Q-gOPypxSCCCNmpcK7Wk-FtVcYA9d_BQKMbAzg8_Cjb36rumK2Z-QC_m921h05G4hRnss1Qxvtc1x3H_vU8ZwMc_qnOXKqVpnvAE)

## **Data transformation**

1. Rename the fields by clicking on the field under **SCHEMA COLUMN** and rename **payload.eventname** to **event\_name**

![](https://lh4.googleusercontent.com/v_6Rqnc7nFQq3xCUF4DBwELml7m1ZhvPkZIBpIZ6kg7pLHIaO1oJchci6FFf4xX-xKAswiu6GemKqHAH5_ztLKOAmh8FZa-XSthejIQDOtXmSsP-0cEt59NMJkzxqmcUEZJNPBjo)

2. Transform data.clientEventTime to from unix epoch to human readable format. Click on **Add Calculated Field** on the upper left and find the **TO\_DATE** function click on **SELECT**. Enter **data.clientEventTime** in the **DATETIME** box and give the field a **NAME** called **event\_time**. Click on **PREVIEW** to make sure the date looks right and click on **SAVE**.

![](https://lh4.googleusercontent.com/f25W44WwYgJoAEeRl7qbPUJWaou9nw9HdNm4yAG0EMpFP1SICxEnpnGgTb7lyKHOcSmFGIlsHjkPOA4bBDZDFFl4zsm3SCQ9aXC8pLXwCLdLdGlV5jMNb-2Xu2odxMLIh032F6wW)

**3.** Add a count for each event by clicking on **Make Aggregated &gt; OK &gt; Add Aggregation**. Click on **SELECT** next to **COUNT \(\*\)**  and click on **SAVE**.

![](../../../.gitbook/assets/zgtazoayjx.gif)

{% hint style="info" %}
Click over to the **SQL tab** on the upper right hand corner. Keep in mind all changes that are made in the SQL view will also be represented in the UI view and vice-versa. You can see the work from the UI automatically generated a SELECT statement. Click on **PREVIEW** to ensure data looks correct.
{% endhint %}

## **Connect to MySQL and start streaming**

1. Click on **RUN** on the upper right corner and choose **Create a new MySQL Connection** from the **MySQL Connection** dropdown.

![](https://lh5.googleusercontent.com/ukOA0BD-g9cxsdWuJhI9ab7g_aOJZn3JpfA6PlbGmNbaeO3dcUrPXY5bskTj7gjxFqgKqYhSeoGP_Ix0lN6nj-PPI9HJEmD1jP4qxMct5aYUkd8fq3UDIJHbSOnseGepvSaSIDGc)

2.  \(Optional\) Setup a local MySQL environment if you don’t have an existing environment.

{% hint style="info" %}
If you don’t have an existing MySQL connection, you can install it locally on your computer: [download](https://dev.mysql.com/downloads/mysql/) and install the [MySQL Community Edition](https://dev.mysql.com/downloads/mysql/). Optionally, you can also download [MySQL workbench](https://dev.mysql.com/downloads/workbench/) as well. Keep in mind that other outputs will require integrations with your own AWS environment. 
{% endhint %}

* Run the following commands in your MySQL environment.

```bash
SET GLOBAL local_infile=1;
CREATE database dev;
```

* After MySQL is running locally, use [ngrok](https://dashboard.ngrok.com/get-started/setup) to  start a TCP tunnel forwarding to your local port 3306 by running `./ngrok tcp 3306` You will have the forwarding information below:

![](https://lh5.googleusercontent.com/NfaeKzR1ltLpUFuYeCvXO0G5sWMkezS7LIKOuA12PHUfViIVnQQZGid3vGfQ6_7Wi1PNRA5olAPhTeMs1jWSm8b6LTIXt4jMWH4QTUltFCVRrQyzxtjKjQumouov7DORyG88Ht-a)

3. Define MySQL Connection in the following format \(include the ngrok forwarding url from above\) and click on **CREATE**

* **CONNECTION STRING:** `jdbc:mysql://2.tcp.ngrok.io:13763/dev?useUnicode=true&useJDBCCompliantTimezoneShift=true&useLegacyDatetimeCode=false&serverTimezone=UTC`
* **USER NAME: `root`**
* **PASSWORD: `<mysql password>`**
* **NAME: `mysql-local`**

![](https://lh3.googleusercontent.com/JSPYUXzmrHF2JYV67ZzpQr1MKwWE2EyZQ9olvpU_AMx0Dh_JM_mxlceX7gveBXGMDVWuso1bxAdAwAiJ97xDbYkixOKyiS5gPwGzVT5I-6wD0ci_Y66wZaDMEJIC1Vcv2eU1mKCA)

4. Select the connection that you just defined as **MYSQL CONNECTION.** Choose **dev** under **SCHEMA** and **gaming** as **TABLE NAME.** Select **Default Storage Connection** as the **INTERMEDIATE STORAGE LOCATION** and click on **NEXT**.

![](https://lh4.googleusercontent.com/aqE5JZ6VNvoEdWFvV4kDnQItgzAXFtkXjXrztlcCF2YXVgRU8beZbrAIJ3aNR0B2BU4FVy_IcyPmRUQysC76mooR9w2ehpJlrgCJGqzo1eX8XBbumGemQbS7tk0OlQ6dh3XedX3K)

5. Choose the **COMPUTE CLUSTER** and only load from the data from last 3 days click on **DEPLOY**. Click on OK if a warning appears.  


![](https://lh4.googleusercontent.com/5b6O0ORXDmpqXiMjqsK8uGYN1KaMq5hPb_JGG4bnLinm7L9zYkdAUxF4lVWQBxa3PEKy-zgsbBU4-iJ0ChutRn4Z7Iu1FZUTL626n8o1WeReetFPUrAuNvG_RPXqngUgug7fYqbj)

5. Upsolver starts outputting the data to MySQL. Wait for a moment for the data to output.

![](https://lh3.googleusercontent.com/VwPyk_YOC03OdL3EvZBYOQFEJsOS38WMBspKx45LIV3Vg4ulerw3IXVcrqkurp0OfW-9yGsqJh0_NZfLJpjG2S1-vkeogtzkC-PsPo_zqk42pqjG2Od8VZ8vgaiGBoRjHlfCCMZE)

## **Verify your data in MySQL**

![](https://lh5.googleusercontent.com/0fxWkWrTxadsR-uuIkp9Tny0BVu2iLcCcNBBa_G5SN6wi6yOvf64W__KBgEHb24vjTWHBStlUU4LlwWNq_yqszCcdvc_c4ITRmULBgt209OxbuWtUjhS4wBRdZ0r0Dzo6lN1GVlW)



