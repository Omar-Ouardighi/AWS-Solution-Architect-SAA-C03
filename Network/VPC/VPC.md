## Virtual Private Cloud
- You can have multiple VPCs in an AWS region (max. 5 per region – soft limit)
- Max. CIDR per VPC is 5, for each CIDR: 
	- Min. size is /28 (16 IP addresses) 
	- Max. size is /16 (65536 IP addresses)
- Because VPC is private, only the Private IPv4 ranges are allowed:
	- 10.0.0.0 – 10.255.255.255 (10.0.0.0/8)
	- 172.16.0.0 – 172.31.255.255 (172.16.0.0/12)
	- 192.168.0.0 – 192.168.255.255 (192.168.0.0/16)
- **Your VPC CIDR should NOT overlap with your other networks (e.g., corporate)**

##  Subnet (IPv4)
- AWS reserves 5 IP addresses (first 4 & last 1) in each subnet
- These 5 IP addresses are not available for use and can’t be assigned to an EC2 instance

**Exam Tip,** if you need 29 IP addresses for EC2 instances: 
- You can’t choose a subnet of size /27 (32 IP addresses, 32 – 5 = 27 < 29) 
- You need to choose a subnet of size /26 (64 IP addresses, 64 – 5 = 59 > 29)

## Internet Gateway (IGW)
- Allows resources (e.g., EC2 instances) in a VPC connect to the Internet
- It scales horizontally and is highly available and redundant
- Must be created separately from a VPC
- One VPC can only be attached to one IGW and vice versa
- Internet Gateways on their own do not allow Internet access, Route tables must also be edited!![[Screenshot 2025-03-18 142138.png]]

## VPC Peering
- Privately connect two VPCs using AWS’ network (VPCs in different AWS accounts/regions)
- Must not have overlapping CIDRs
- VPC Peering connection is NOT transitive (must be established for each VPC that need to communicate with one another)
- You must update route tables in each VPC’s subnets to ensure EC2 instances can communicate with each other
## VPC Endpoints (AWS PrivateLink)
- VPC Endpoints (powered by AWS PrivateLink) allows you to connect to AWS services using a private network instead of using the public Internet
- They remove the need of IGW, NATGW, … to access AWS Services
- In case of issues: • Check DNS Setting Resolution in your VPC • Check Route Tables
### Types of Endpoints
- **Interface Endpoints (powered by PrivateLink)** 
	- Provisions an ENI (private IP address) as an entry point (must attach a Security Group) 
	- Supports most AWS services 
	- $ per hour + $ per GB of data processed
- **Gateway Endpoints**
	- Provisions a gateway and must be used as a target in a route table (does not use security groups) 
	- Supports both [[S3]] and [[DynamoDB]] 
	- Free 
	- Gateway is most likely going to be preferred all the time at the exam
	- ![[Screenshot 2025-03-19 123549.png]]
## VPC Flow Logs
-  Capture Information about IP traffic through your interfaces
	- VPC Flow Logs
	- Subnet Flow Logs
	- ENI Flow Logs
- Helps to monitor & troubleshoot connectivity issues 
- Flow logs data can go to S3, CloudWatch Logs, and Kinesis Data Firehose
- Captures network information from AWS managed interfaces too: ELB, RDS, ElastiCache, Redshift, WorkSpaces, NATGW, Transit Gateway…
- **Information** :ip information, port information, action (accept/reject)
- Query VPC flow logs using Athena on S3 or CloudWatch Logs Insights

- ![[Screenshot 2025-03-19 125311.png]]

### Traffic Mirroring
- Allows you to capture and inspect network traffic in your VPC 
- Route the traffic to security appliances that you manage 
- Capture the traffic 
	- From (Source) – ENIs 
	- To (Targets) – an ENI or a Network Load Balancer 
- Capture all packets or capture the packets of your interest (optionally, truncate packets) 
- Source and Target can be in the same VPC or different VPCs (VPC Peering) 
- Use cases: content inspection, threat monitoring, troubleshooting, …
![[Pasted image 20250319160612.png]]