## Amazon Managed Streaming for Apache Kafka (Amazon MSK)
- Alternative to Amazon Kinesis 
- Fully managed Apache Kafka on AWS
- Data is stored in EBS volume for as long as you want
- Serverless option
- 
- ![[Screenshot 2025-03-11 165234.png]]

## Kinesis Data Streams vs. Amazon MSK
- [[Kinesis Data Streams]] :
	- 1 MB message size limit 
	- Data Streams with Shards 
	- Shard Splitting & Merging 
	- TLS In-flight encryption 
	- KMS at-rest encryption
- MSK :
	- 1MB default, configure for higher (ex: 10MB) 
	- Kafka Topics with Partitions 
	- Can only add partitions to a topic 
	- PLAINTEXT or TLS In-flight Encryption 
	- KMS at-rest encryption