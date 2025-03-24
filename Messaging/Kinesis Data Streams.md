capture, process, and store data streams in real time

- Retention between 1 day to 365 days 
- Ability to reprocess (replay) data 
- Once data is inserted in Kinesis, it can’t be deleted (immutability) 
- Data that shares the same partition goes to the same shard (ordering) 
- Producers: AWS SDK, Kinesis Producer Library (KPL), Kinesis Agent 
- Consumers: 
	- Write your own: Kinesis Client Library (KCL), AWS SDK 
	- Managed:  [[Lambda]], [[Amazon Data Firehose]], [[Managed Apache Flink]]


## Capacity Modes
- Provisioned mode:
	- choose the number of shards
	- Each shard gets 1MB/s in (or 1000 records per second)
	- Each shard gets 2MB/s out (classic or enhanced fan-out consumer)
	- You pay per shard provisioned per hour
- On-demand mode:
	- No need to provision or manage the capacity
	- 4 MB/s in or 4000 records per second
	- Scales automatically
	- Pay per stream per hour & data in/out per GB
	- 