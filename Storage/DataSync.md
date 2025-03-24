- Move large amount of data to and from 
	- On-premises / other cloud to AWS (NFS, SMB, HDFS, S3 API…) – needs agent •
	- AWS to AWS (different storage services) – no agent needed
- Can synchronize to: • Amazon S3 (any storage classes – including Glacier) • Amazon EFS • Amazon FSx (Windows, Lustre, NetApp, OpenZFS...)
- • Replication tasks can be scheduled hourly, daily, weekly
- File permissions and metadata are preserved (NFS POSIX, SMB…)
- • One agent task can use 10 Gbps, can setup a bandwidth limit![[Screenshot 2025-03-07 160820.png]]

![[Screenshot 2025-03-07 160834.png]]