# Amazon AppFlow data source

To help you get started with Upsolver, you can try it out for free. Sign up for [**Upsolver Dedicated Compute**](https://app.upsolver.com/signup) ****subscription to use Amazon AppFlow. It gives you free Upsolver units \(UUs\), units of processing capability per hour based on VM instance type.

You can also use Upsolver through [AWS Marketplace](https://aws.amazon.com/marketplace/pp/B07T8JDQ57?ref_=srh_res_product_title). All of the options will allow you to ingest data to Amazon S3, perform transformations with simple SQL, and output to your favorite database or analytics tools—in minutes.What is Amazon AppFlow

{% hint style="info" %}
Amazon AppFlow is a fully managed integration service that enables you to securely transfer data between Software-as-a-Service \(SaaS\) applications like Salesforce, Marketo, Slack, and ServiceNow, and AWS services like Amazon Athena, Amazon S3 and Amazon Redshift, in just a few clicks.
{% endhint %}

## Create an Amazon AppFlow data source connection

This example reads data from Google Analytics using Amazon AppFlow and utilizing Upsolver for data transformation.

1. Navigate to **DATA SOURCE &gt; NEW**.

![](../../../.gitbook/assets/image%20%28199%29.png)

2. Find **Amazon AppFlow** and click on **SELECT**. 

![](../../../.gitbook/assets/image%20%28182%29.png)

3. Click on **Create your first Amazon AppFlow Connection** under **APPFLOW CONNECTION**

![](../../../.gitbook/assets/image%20%28194%29.png)

{% hint style="danger" %}
Make sure you're logged into the AWS account that you're running AppFlow from.
{% endhint %}

4. Define the connection integration information. Click on **LAUNCH INTEGRATION**.

* **NAME** is the name of the connection between Upsolver and Amazon AppFlow. You will use this connection for the data coming from Amazon AppFlow to Upsolver. You can create multiple data sources using the same connection. 
* **BUCKET NAME** is the S3 bucket that AppFlow sends its data for Upsolver to process. The example shown below has the BUCKET NAME called **googleanalytics**. The integration will automatically create a Amazon S3 bucket name called **appsolver-appflow-googleanalytics.** This is the bucket that you will select when you set up your Flow later on. 

![](../../../.gitbook/assets/image%20%28203%29.png)

5. Scroll down on the CloudFormation page and check the **I acknowledge box** and click on **Create Stack**.

![](../../../.gitbook/assets/image%20%28190%29.png)

6. Wait until the integration is complete.

![](../../../.gitbook/assets/image%20%28204%29.png)

7. Navigate back to Upsolver and click on **DONE**. 

![](../../../.gitbook/assets/image%20%28200%29.png)

## Create a flow on Amazon AppFlow

1. Navigate to your AppFlow service in your AWS environment and click on **Create flow**.

![](../../../.gitbook/assets/image%20%28181%29.png)

2. Give the flow a name and description. This example collects data from google analytics. Click on **Next**.

![](../../../.gitbook/assets/image%20%28198%29.png)

3. You may choose any sources Choose **Google Analytics** as your source and click on **Connect**.

![](../../../.gitbook/assets/image%20%28184%29.png)

4. Enter your Google Analytics information, give the connection a name and click on **Continue**. 

{% hint style="info" %}
If you don't know your Google Analytics Client ID and Client Secret, please follow [these steps](setup-google-analytics-client-id-and-client-secret..md) to set it up.
{% endhint %}

![](../../../.gitbook/assets/image%20%28197%29.png)

5. Fill out the required fields for your source. For Google Analytics, you will see AppFlow requesting access to your Google account.

![](../../../.gitbook/assets/image%20%28195%29.png)

6. Choose Upsolver as your destination. From the first section - _Create an Amazon Appflow data source connection_ step 4, you've created an AppFlow connection with BUCKET NAME called googleanalytics. Behind the scenes, it automatically created an Amazon S3 bucket called **upsolver-appflow-googleanalytics**. This bucket will show up as an option when you create an Upsolver destination. Select the **upsolver-appflow-googleanalytics** bucket.

![](../../../.gitbook/assets/image%20%28189%29.png)

7. Choose your Flow trigger \(how frequently do you want the flow to run\) and click on **Next**.

![](../../../.gitbook/assets/image%20%28205%29.png)

8. Check the fields that you want to work with and click on **Map fields directly**.

![](../../../.gitbook/assets/image%20%28180%29.png)

9. Verify that all needed fields from Google Analytics are selected and click on **Next**.

![](../../../.gitbook/assets/image%20%28193%29.png)

10. Click on **Next** and skip the filters. We can filter data with Upsolver if needed.

![](../../../.gitbook/assets/image%20%28196%29.png)

11. Review your Flow definition and click on **Create flow**.

![](../../../.gitbook/assets/image%20%28185%29.png)

12. Click on **Run flow** and verify that the Flow ran successfully under Run history tab.

![](../../../.gitbook/assets/image%20%28183%29.png)

## Create an AppFlow data source

1. Navigate back to the data source setup page by clicking on **DATA SOURCE &gt; NEW**.

![](../../../.gitbook/assets/image%20%28199%29.png)

2. Find **Amazon AppFlow** and click on **SELECT**. 

![](../../../.gitbook/assets/image%20%28182%29.png)

3. Fill out the information and choose the connection that you've created from the first section and click on **CONTINUE**.

![](../../../.gitbook/assets/image%20%28192%29.png)

4. Verify that the sample data coming from Google Analytics Flow that you created from the previous section and click on **CREATE**.

![](../../../.gitbook/assets/image%20%28191%29.png)

Congratulations! You have created an Upsolver Amazon AppFlow data source. Now you can transform or enrich the data using any built-in [data outputs](../../../data-outputs-and-data-transformation/data-outputs/).

![](../../../.gitbook/assets/image%20%28201%29.png)

