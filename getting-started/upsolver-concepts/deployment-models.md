---
description: Upsolver can be deployed in Upsolver’s account or the user’s account.
---

# Deployment models

## Upsolver Fully Managed Deployment

In the Upsolver deployment, compute servers are running in the Upsolver’s account. The data resides in the user’s S3 bucket. Data processing takes place outside of the user’s account. The data and data access is granted from outside of the user’s account. Upsolver processes the data and writes it back to the user’s S3 bucket. This model allows Upsolver processes to access the user’s data.

## Private VPC Deployment

The user can deploy Upsolver in their own private VPC. It is recommended to create a new VPC for the Upsolver’s deployment. Deploying to an existing private VPC is also supported. The Upsolver Compute Servers will run in the user’s own AWS account. The difference between Private VPC deployment model and the Upsolver fully managed deployment model are:

* User pays for the compute since it’s deployed in its own VPC
* Setup takes a little longer than Upsolver managed deployment

The servers are managed the same way and behave the same way. The only difference between Upsolver managed deployment and user’s VPC deployment is where the servers are spun up. 

When deploying Upsolver to a user’s VPC, users have two options:

* Default \(recommended\): deploy into a new VPC. The deployment CloudFormation creates all the necessary components to ensure everything will work as expected. This option also ensures easier resource management and security configurations.
* Existing VPC: requires additional security configurations and Upsolver resources will be managed along with existing resources within the VPC.

Data encryption will be defined as part of the connection to the S3 bucket itself. All communications are over HTTPS. All data is encrypted on the wire using SSL. 

As a Cloud native solution, Upsolver does not store any data locally on the server. The only data being stored is in S3. The user can choose between  server side encryption or client side encryption within the connection to S3. 

Upsolver integrates with Cloud provider’s native KMS solutions. The users have the following three options:

1. Default encryption - existing S3 default configuration
2. Server-side encryption using Amazon KMS \(SSE-KMS\) - User provides the key’s ARN
3. Server-side encryption using Customer-Managed Keys \(SSE-CME\) - User provides the encryption key

