## Database Migration Service
- Quickly and securely migrate databases to AWS, resilient, self healing
- Supports: 
	- Homogeneous migrations: ex Oracle to Oracle 
	- Heterogeneous migrations: ex Microsoft SQL Server to Aurora
- Continuous Data Replication using CDC 
- You must create an EC2 instance to perform the replication tasks
### AWS Schema Conversion Tool (SCT)
- • Convert your Database’s Schema from one engine to another
- You do not need to use SCT if you are migrating the same DB engine 
	- Ex: On-Premise PostgreSQL => RDS PostgreSQL
###  Continuous Replication
![[Pasted image 20250320111814.png]]

### Multi-AZ Deployment
- When Multi-AZ Enabled, DMS provisions and maintains a synchronously stand replica in a different AZ
- Advantages: • Provides Data Redundancy • Eliminates I/O freezes • Minimizes latency spikes

![[Pasted image 20250320112604.png]]

![[Pasted image 20250320112619.png]]