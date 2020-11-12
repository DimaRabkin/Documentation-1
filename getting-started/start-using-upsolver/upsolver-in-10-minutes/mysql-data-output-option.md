---
description: >-
  Process streaming data from end-to-end within 10 minutes. The data source is
  an Amazon S3 bucket (updated continuously). Upsolver processes the data and
  loads to your local MySQL environment.
---

# Local MySQL data output

To help you get started with Upsolver, you can try it out for free. You can choose between [**Upsolver Dedicated Compute**](https://app.upsolver.com/signup) ****and [**Community**](https://app.upsolver.com/signup/free) subscriptions. Both options give you free Upsolver units \(UUs\), units of processing capability per hour based on VM instance type.

## Create a data source

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

1. Click on **NEW OUTPUT** on the upper right corner. \(You can also get to the output screen by clicking on **OUTPUTS &gt; NEW**\)

![](https://lh4.googleusercontent.com/MWKDM4NzS3bsF93Pq5DZ-4nd5QV6B7JXOS2cA1N8vy92qij_fPmPTPeilDb1XiW3DjcZMc8L0YC-62snOK6wiXnefjBe-Ppku7s9ymdk3M5sS7NEUNiYPpJaQeHTe5mYgkfgBHV0)

2. Choose **MySQL** output by clicking on **SELECT**. We’re going to use MySQL as our output for this tutorial. You can output to any Upsolver data outputs. 

![](https://lh4.googleusercontent.com/PXhvs6a7EiGfmAHcgqwN3_Jwz96iPo6L17sUl5E534p062iFtkakUxPbFWcx8g2BIVYVSV26ayqeEaPMGXLmkAOXmcIoxewZkcuVT2iyOgDUlaU1860lpsaVBNCNIwk1rv3s-19T)

3. Enter **gaming** as the name of the output. Leave everything as default and click on **NEXT**.

![](https://lh5.googleusercontent.com/pwqXwMAeu4kndQzv2fMDh4-N5rB_q6S6vpsR10OEITDHI4aatdyMWBEfhO8dpdBuaxsa5hVm1195UMzW9qM38Jnb6miZ49_RR8Koi7LBaRr8v7Y2P68vzdsJFE5Ck4Ppi6ByzegG)

4. Expand the **payload** field. Add a field to your output by clicking on the **+** sign next to **eventName**. The field that we’re adding is. **data.payload.eventName**.

![](https://lh4.googleusercontent.com/kYfGKdqytOPUi7-qXFq-lStbLuIpgE1bv8L_Q-gOPypxSCCCNmpcK7Wk-FtVcYA9d_BQKMbAzg8_Cjb36rumK2Z-QC_m921h05G4hRnss1Qxvtc1x3H_vU8ZwMc_qnOXKqVpnvAE)

## **Data transformation**

1. Rename the fields by clicking on the field under **SCHEMA COLUMN** and rename **payload.eventname** to **event\_name**

![](https://lh4.googleusercontent.com/v_6Rqnc7nFQq3xCUF4DBwELml7m1ZhvPkZIBpIZ6kg7pLHIaO1oJchci6FFf4xX-xKAswiu6GemKqHAH5_ztLKOAmh8FZa-XSthejIQDOtXmSsP-0cEt59NMJkzxqmcUEZJNPBjo)

2. Transform **data.clientEventTime** to from unix epoch to human readable format in UTC. Click on **Add Calculated Field** on the upper left and find the **TO\_DATE** function, then click on **SELECT**. Enter **data.clientEventTime** in the **DATETIME** box and give the field a **NAME** called **event\_time**. Click on **PREVIEW** to make sure the date looks right and click on **SAVE**. 

![Click on Add Calculated Field](../../../.gitbook/assets/image%20%28161%29.png)

![Find the TO\_DATE\(\) function and click on SELECT](../../../.gitbook/assets/image%20%28160%29.png)

![Convert data.clientEventTime and to human readable format in UTC. Click on PREVIEW and SAVE. ](../../../.gitbook/assets/image%20%28159%29.png)

3. Add **event\_time** to your output by clicking on **+** next to the field. 

![](../../../.gitbook/assets/czjgup6d4l.gif)

4. Add a count for each event by clicking on **Make Aggregated &gt; OK &gt; Add Aggregation**. Click on **SELECT** next to **COUNT \(\*\)**  and click on **SAVE**.

![Click on Make Aggregated](../../../.gitbook/assets/image%20%28162%29.png)

![Click OK](../../../.gitbook/assets/image%20%28156%29.png)

![Click on Add Aggregation and SELECT COUNT\(\*\)](../../../.gitbook/assets/image%20%28158%29.png)

![Click on SAVE](../../../.gitbook/assets/image%20%28154%29.png)

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
CREATE database dev;
```

* After MySQL is running locally, use [ngrok](https://dashboard.ngrok.com/get-started/setup) to  start a TCP tunnel forwarding to your local port 3306 by running `./ngrok tcp 3306` You will have the forwarding information below:

![](https://lh5.googleusercontent.com/NfaeKzR1ltLpUFuYeCvXO0G5sWMkezS7LIKOuA12PHUfViIVnQQZGid3vGfQ6_7Wi1PNRA5olAPhTeMs1jWSm8b6LTIXt4jMWH4QTUltFCVRrQyzxtjKjQumouov7DORyG88Ht-a)

3. Define MySQL Connection in the following format \(include the **ngrok** forwarding url from above\) and click on **CREATE**

* **CONNECTION STRING:** `jdbc:mysql://2.tcp.ngrok.io:13763/dev?useUnicode=true&useJDBCCompliantTimezoneShift=true&useLegacyDatetimeCode=false&serverTimezone=UTC`
* **USER NAME: `root`**
* **PASSWORD: `<mysql password>`**
* **NAME: `mysql-local`**

4. Select the connection that you just defined as **MYSQL CONNECTION.** Choose **dev** under **SCHEMA** and **gaming** as **TABLE NAME.** Select **Default Storage Connection** as the **INTERMEDIATE STORAGE LOCATION** and click on **NEXT**.

![](https://lh4.googleusercontent.com/aqE5JZ6VNvoEdWFvV4kDnQItgzAXFtkXjXrztlcCF2YXVgRU8beZbrAIJ3aNR0B2BU4FVy_IcyPmRUQysC76mooR9w2ehpJlrgCJGqzo1eX8XBbumGemQbS7tk0OlQ6dh3XedX3K)

5. Use the sliding bar to only load from the data from last day click on **DEPLOY**. Keep in mind that **ENDING AT** set as **Never** means it's a continuous data stream. Click on OK if a warning appears.  


![](../../../.gitbook/assets/image%20%28155%29.png)

6. Upsolver starts outputting the data to MySQL. Wait for a moment for the data to output.

![](https://lh3.googleusercontent.com/VwPyk_YOC03OdL3EvZBYOQFEJsOS38WMBspKx45LIV3Vg4ulerw3IXVcrqkurp0OfW-9yGsqJh0_NZfLJpjG2S1-vkeogtzkC-PsPo_zqk42pqjG2Od8VZ8vgaiGBoRjHlfCCMZE)

## **Verify your data in MySQL**

![](https://lh5.googleusercontent.com/0fxWkWrTxadsR-uuIkp9Tny0BVu2iLcCcNBBa_G5SN6wi6yOvf64W__KBgEHb24vjTWHBStlUU4LlwWNq_yqszCcdvc_c4ITRmULBgt209OxbuWtUjhS4wBRdZ0r0Dzo6lN1GVlW)



