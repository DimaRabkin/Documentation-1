---
description: Upsolver architecture and its components.
---

# Upsolver components

## Servers

### API Server

The API Server is responsible for user interaction. Every time a user triggers an action that requires a response, the request interacts with the API Server. 

* Upsolver fully managed architecture does not require a dedicated API Servers. It utilizes the Global API Server to interact with Upsolver. 
* Private VPC deployment architecture requires access to the data in order to display information in the UI. The API Server is required to be deployed in the user’s private VPC. The users will need access to the API Server to access the website. The API server will typically have the HTTPS port open for the users to access through a component such as VPN. 

### Compute Cluster 

Upsolver Compute Cluster is a group of EC2 instances that are responsible for data processing. These servers are the compute power for transforming, aggregating, and enriching the data in Upsolver.  They don’t interact with outside processes. The instances pull work and process the data, then write the data to S3. 

### Query Cluster

Query cluster is for users that want to populate [Lookup Table](https://www.upsolver.com/)s for dashboards or applications. It allows Lookup Tables to be loaded into memory and waits for user requests. The Query Cluster is an optional component. It is not a requirement for Upsolver. If the Lookup Tables are used for joins between data streams, a Query Cluster is not required because Upsolver manages the Lookup Tables automatically. A Query Cluster is only required when a user wants to manually interact with Lookup Tables. 

## Resources

### Kinesis Stream

Upsolver utilizes the Kinesis Stream to allow servers to communicate with each other. Rather than communicating with each other directly, all servers report information to Kinesis, each server will pull data from Kinesis to discover information about other servers. 

All servers will send and pull information to the Kinesis Stream to communicate state and synchronize the work between the servers that are running in the account.

* Upsolver fully managed architecture deployed in Upsolver’s environment
* Private VPC deployment architecture deployed in the user’s AWS account

### Metadata store

The Metadata Store is a global component for Upsolver fully managed deployment model and Private VPC deployment model. It’s a centralized space to store the configurations. If a user creates an object in Upsolver, the definitions will always be stored in the global Metadata Store. The Metadata Store is a Key-Value store that the clients communicate using the API Server. Clients don’t interact with the Metadata Store directly. Outgoing traffic will go through the API server, the purpose of it is to store and request information from the KV store. The same entities are reflected on S3 in the user’s account to provide durability. The production servers will only pull data from S3. In the unlikely event of the global environment being unavailable, it will not impact any data being processed. 

The servers report to several Kinesis streams including status of the tasks and operational metrics such as CPU and memory. It keeps track of servers’ health and the information is used to replace servers if necessary. Servers report some of the metrics directly to the user's CloudWatch environment, which is used for scaling and auto-healing of the cluster. The metrics are also used for spinning up and down servers. Servers report additional metrics to Upsolver managed Kinesis streams such as billing information and telemetry data. The data being reported directly to CloudWatch is operational data about the servers. 

### Logs and environment 

By default, logs are sent to an Upsolver bucket. Application logs are sent to a centralized location for easy debugging. Optionally, the users can choose to send the logs to their own dedicated bucket if direct access to the logs is desired. 

The Upsolver environment pulls data from various locations. Environment configurations including geo IP map, user agent map files are pulled from global configurations as well as static initialization files. They’re pulled from various buckets on Amazon S3. During the initialization phase, the servers also install components such as Java and Docker containers pulled from Upsolver’s dockerhub repository. Servers also report to the monitoring infrastructure which is InfluxDB. 

Upsolver’s web interface is hosted on a CDN out of an Amazon S3 bucket. The web interface accesses the private API directly to populate the entities. 

