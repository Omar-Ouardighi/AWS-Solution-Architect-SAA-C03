- Centrally manage and automate backups across AWS services
- Supports cross-region backups 
- Supports cross-account backups
- On-Demand and Scheduled backups
- You create backup policies known as Backup Plans 
	- Backup frequency (every 12 hours, daily, weekly, monthly, cron expression) •
	- Backup window 
	- Transition to Cold Storage (Never, Days, Weeks, Months, Years) 
	- Retention Period (Always, Days, Weeks, Months, Years)
![[Pasted image 20250320113609.png]]


### Vault Lock
- Enforce a WORM (Write Once Read Many) state for all the backups that you store in your AWS Backup Vault
- Additional layer of defense to protect your backups against: 
	- Inadvertent or malicious delete operations 
	- Updates that shorten or alter retention periods
- Even the root user cannot delete backups when enabled