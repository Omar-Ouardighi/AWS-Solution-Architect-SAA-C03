## EBS (Elastic Block Store) Volume

- An EBS Volume is a network drive you can attach to your instances while they run
	- one instance (except multi-attach io1/io2) 
	- are locked at the Availability Zone (AZ) level 
	- gp2: IO increases if the disk size increases 
	- gp3 & io1: can increase IO independently
- To migrate an EBS volume across AZ 
	- Take a snapshot 
	- Restore the snapshot to another AZ 
	- EBS backups use IO and you shouldn’t run them while your application is handling a lot of traffic
- Root EBS Volumes of instances get terminated by default if the [[EC2]] instance gets terminated. (you can disable that)

## EFS – Elastic File System
- Mounting 100s of instances across AZ 
- EFS share website files (WordPress) 
- Only for Linux Instances (POSIX) 
- EFS has a higher price point than EBS 
- Can leverage Storage Tiers for cost saving

## EC2 Instance Store 
- EBS volumes are network drives with good but “limited” performance 
- If you need a high-performance hardware disk, use EC2 Instance Store 
- Better I/O performance 
- EC2 Instance Store lose their storage if they’re stopped (ephemeral) 
- Good for buffer / cache / scratch data / temporary content 
- Risk of data loss if hardware fails 
- Backups and Replication are your responsibility