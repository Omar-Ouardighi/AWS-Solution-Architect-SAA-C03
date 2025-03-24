• Need to define two terms: 
- RPO: Recovery Point Objective 
- RTO: Recovery Time Objective
![[Pasted image 20250320105445.png]]

## Disaster Recovery Strategies
### Backup and Restore (High RPO)
![[Pasted image 20250320105725.png]]

### Pilot light
- A small version of the app is always running in the cloud 
- Faster than Backup and Restore as critical systems are already up

### Warm Standby
- Full system is up and running, but at minimum size 
- Upon disaster, we can scale to production load
### Multi Site / Hot Site Approach
- Very low RTO (minutes or seconds) – very expensive 
- Full Production Scale is running AWS and On Premise
### All AWS Multi Region
![[Pasted image 20250320110119.png]]

## Disaster Recovery Tips
- Backup 
	- EBS Snapshots, RDS automated backups / Snapshots, etc… 
	- Regular pushes to S3 / S3 IA / Glacier, Lifecycle Policy, Cross Region Replication 
	- From On-Premise: Snowball or Storage Gateway 
- High Availability 
	- Use Route53 to migrate DNS over from Region to Region 
	- RDS Multi-AZ, ElastiCache Multi-AZ, EFS, S3 
	- Site to Site VPN as a recovery from Direct Connect 
- Replication 
	- RDS Replication (Cross Region), AWS Aurora + Global Databases 
	- Database replication from on-premises to RDS •
	- Storage Gateway 
- Automation 
	- CloudFormation / Elastic Beanstalk to re-create a whole new environment 
	- Recover / Reboot EC2 instances with CloudWatch if alarms fail 
	- AWS Lambda functions for customized automations 
- Chaos 
	- Netflix has a “simian-army” randomly terminating EC2