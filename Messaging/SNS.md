![[Screenshot 2025-03-07 204008.png]]
## SNS + [[SQS]]: Fan Out
![[Screenshot 2025-03-07 204120.png]]
### Applications

- [[S3]] Events to multiple queues
- SNS to Amazon S3 through [[Amazon Data Firehose]]

## Amazon SNS – FIFO Topic
- Similar features as SQS FIFO: 
	- Ordering by Message Group ID (all messages in the same group are ordered) •
	- Deduplication using a Deduplication ID or Content Based Deduplication
- Can have SQS Standard and FIFO queues as subscribers 
- Limited throughput (same throughput as SQS FIFO)
## SNS FIFO + SQS FIFO: Fan Out
- In case you need fan out + ordering + deduplication

## SNS – Message Filtering
• JSON policy used to filter messages sent to SNS topic’s subscriptions
