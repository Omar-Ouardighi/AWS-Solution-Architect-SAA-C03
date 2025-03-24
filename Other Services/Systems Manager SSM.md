## Session manager
- Allows you to start a secure shell on your EC2 and on-premises servers
- No SSH access, bastion hosts, or SSH keys needed 
- No port 22 needed (better security)
- end session log data to S3 or CloudWatch Logs

## Run Command
- Execute a document (= script) or just run a command
- No need for SSH
- Command Output can be shown in the AWS Console, sent to S3 bucket or CloudWatch Logs
- ![[Pasted image 20250321151243.png]]

## Patch Manager
- Automates the process of patching managed instances
- OS updates, applications updates, security updates
- Patch on-demand or on a schedule using Maintenance Windows
![[Pasted image 20250321151354.png]]

## Maintenance Windows
- Defines a schedule for when to perform actions on your instances
- Maintenance Window contains • Schedule • Duration • Set of registered instances • Set of registered tasks

## Automation
- Simplifies common maintenance and deployment tasks of EC2 instances and other AWS resources 
- Examples: restart instances, create an AMI, EBS snapshot 
- Automation Runbook – SSM Documents to define actions preformed on your EC2 instances or AWS resources (pre-defined or custom)
- ![[Pasted image 20250321151649.png]]