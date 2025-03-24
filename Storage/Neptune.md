- Fully managed graph database
- Highly available across 3 AZ, with up to 15 read replicas
- Can store up to billions of relations and query the graph with milliseconds latency
- Great for knowledge graphs (Wikipedia), fraud detection, recommendation engines, social networking

## Neptune Streams
- Real-time ordered sequence of every change to your graph data
- Changes are available immediately after writing
- • No duplicates, strict order
- Streams data is accessible in an HTTP REST API
- Use cases: 
	- Send notifications when certain changes are made 
	- Maintain your graph data synchronized in another data store (e.g., S3, OpenSearch, ElastiCache) 
	- Replicate data across regions in Neptune