---
description: >-
  This page provides an introduction to the different types of AWS data sources
  that can be created on Upsolver.
---

# Amazon AWS data sources

## AWS data sources guides

*  [S3](amazon-s3-data-source/quick-guide-s3-data-source-1.md)
*  [Kinesis](amazon-kinesis-stream-data-source.md)
* [ S3 over SQS](amazon-s3-over-sqs-data-source.md)
*  [AppFlow](amazon-appflow-data-source/)

## [Amazon S3](amazon-s3-data-source/)

### What is Amazon S3?

**Amazon Simple Storage Service** \(or Amazon S3\) is object storage built to store and retrieve any amount of data from anywhere on the Internet. It’s a simple storage service that offers a highly durable, available, and scalable data storage infrastructure at low costs.

Amazon S3 has a web services interface that can be used to store and retrieve data at any time, from anywhere on the web. It gives developers access to the same scalable, reliable, fast, and inexpensive data storage infrastructure that Amazon uses to run its own global network of web sites.

{% hint style="info" %}
Upsolver can read events directly from your Amazon S3 bucket, assuming events are partitioned by event date \(this partitioning defines the folder structure in the cloud storage\).
{% endhint %}

{% page-ref page="amazon-s3-data-source/" %}

## [Amazon Kinesis Stream](amazon-kinesis-stream-data-source.md)

### What is Amazon Kinesis Stream?

**Amazon Kinesis Data Streams** \(KDS\) is a real-time data streaming service. 

KDS can continuously capture gigabytes of data per second from hundreds of thousands of sources such as website clickstreams, database event streams, financial transactions, social media feeds, IT logs, and location-tracking events. The data collected is available in milliseconds to enable real-time analytics use cases such as real-time dashboards, real-time anomaly detection, dynamic pricing, and more.

{% page-ref page="amazon-kinesis-stream-data-source.md" %}

## [Amazon S3 over SQS](amazon-s3-over-sqs-data-source.md)

### What is Amazon SQS?

**Amazon Simple Queue Service** \(Amazon SQS\) offers a secure, durable, and available hosted queue that lets you integrate and decouple distributed software systems and components. 

Amazon SQS offers common constructs such as [dead-letter queues](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-dead-letter-queues.html) and [cost allocation tags](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-queue-tags.html). It provides a generic web services API and it can be accessed by any programming language that the AWS SDK supports.

Amazon SQS supports both [standard](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/standard-queues.html) and [FIFO queues](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/FIFO-queues.html).

{% page-ref page="amazon-s3-over-sqs-data-source.md" %}

