- Postgres and MySQL are both supported as Aurora DB (that means your drivers will work as if Aurora was a Postgres or MySQL database)
- Aurora storage automatically grows in increments of 10GB, up to 128 TB.
- Aurora can have up to 15 replicas and the replication process is faster than MySQL (sub 10 ms replica lag)
- Failover in Aurora is instantaneous. It’s HA (High Availability) native.
- Aurora costs more than [[RDS]] (20% more) – but is more efficient
## Aurora High Availability and Read Scaling
- 6 copies of your data across 3 AZ: 
	- 4 copies out of 6 needed for writes 
	- 3 copies out of 6 need for reads 
	- Self healing with peer-to-peer replication 
	- Storage is striped across 100s of volumes 
- One Aurora Instance takes writes (master) 
- Automated failover for master in less than 30 seconds 
- Master + up to 15 Aurora Read Replicas serve reads 
- **Support for Cross Region Replication**
![[Screenshot 2025-02-28 172508.png]]

## Features of Aurora 
- Automatic fail-over 
- Backup and Recovery 
- Isolation and security 
- Industry compliance 
- Push-button scaling 
- Automated Patching with Zero Downtime 
- Advanced Monitoring 
- Routine Maintenance 
- Backtrack: restore data at any point of time without using backups

## Aurora – Custom Endpoints

![[Screenshot 2025-02-28 172754.png]]


## Aurora Serverless
- Automated database instantiation and auto scaling based on actual usage 
- Good for infrequent, intermittent or unpredictable workloads 
- No capacity planning needed 
- Pay per second, can be more cost-effective
- client talks to aurora proxy fleet

## Global Aurora
- **Aurora Cross Region Read Replicas**: 
	- Useful for disaster recovery 
	- Simple to put in place
- **Aurora Global Database (recommended)**:
	- 1 primary region for read an write
	- up to 5 secondary read regions
	- up to 16 read replicas for each read region
	- **less than 1 second for replication across region**
## Aurora machine learning
- ML based predications to your apps via SQL

	### **Use cases**
	- fraud detection
	- add targeting
	- sentiment analysis
	- product recommendations
	
	### **Services**
	- [[SageMaker]]
	- [[Comprehend]]

## Aurora Backups

### Automated 
- 1 to 35 days
- can not be disabled
- point in time recovery in that timeframe

### Manual
- triggered by user
- keep as long as user wants

## Restore
- Restoring a RDS / Aurora backup or a snapshot creates a new database