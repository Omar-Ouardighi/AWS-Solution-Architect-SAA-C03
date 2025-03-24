## Features
- NoSQL
- Fully managed, highly available with replication across multiple AZs
- Low cost and auto-scaling capabilities
- Standard & Infrequent Access (IA) Table Class
- Millions of requests per seconds, trillions of row, 100s of TB of storage
- in DynamoDB you can **rapidly evolve schemas**
- The maximum size of an item in a DynamoDB table is 400kb
## Read/Write Capacity Modes
### Provisioned Mode (default)
- You specify the number of reads/writes per second
- Pay for provisioned Read Capacity Units (RCU) & Write Capacity Units (WCU) 
- Possibility to add auto-scaling mode for RCU & WCU
### On-Demand Mode
- Read/writes automatically scale up/down with your workloads
-  No capacity planning needed
- Pay for what you use, more expensive  
- Great for unpredictable workloads, steep sudden spikes
## DynamoDB Accelerator (DAX)
- in memory cache for DynamoDB 
- Help solve read congestion by caching
- microsecond read latency
![[Screenshot 2025-03-10 175719.png]]


## Dynamo DB Stream
- event processing
- invoke [[Lambda]] or send to [[Kinesis]]
- 24 hour retention 
- limited number of consumers

## Dynamo DB Kinesis Data Steams
- 1 year retention
- all features of [[Kinesis]]
- High # of consumers


## Global Tables
- Make a DynamoDB table accessible with low latency in multiple-regions
- active/active setup for multi region
- two way replication
- must enable Streams as prerequiste
## DynamoDB –Time To Live (TTL)
- Automatically delete items after an expiry timestamp 
- Use cases: reduce stored data by keeping only current items, adhere to regulatory obligations, web session handling…
## Backups
- automated backups up to 35 days with PITR to restore to new table
- on demand backups

## Integration with Amazon [[S3]]
- Export to S3 (must enable PITR)
	- Export in DynamoDB JSON or ION format
- Import from S3
	- Import CSV, DynamoDB JSON or ION format
	- Creates a new table

## Security
- support [[KMS]] Customer Managed Key