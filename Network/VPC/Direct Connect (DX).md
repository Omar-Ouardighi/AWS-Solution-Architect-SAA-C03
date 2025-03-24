- Provides a dedicated private connection from a remote network to your VPC 
- Dedicated connection must be setup between your DC and AWS Direct Connect locations 
- You need to setup a Virtual Private Gateway on your VPC 
- Access public resources (S3) and private (EC2) on same connection
- Use Cases: 
	- Increase bandwidth throughput - working with large data sets – lower cost 
	- More consistent network experience - applications using real-time data feeds •
	- Hybrid Environments (on prem + cloud) 
- Supports both IPv4 and IPv6
## Direct Connect Diagram
![[Screenshot 2025-03-19 154443.png]]
### Direct Connect Gateway
• If you want to setup a Direct Connect to one or more VPC in many different regions (same account), you must use a Direct Connect Gateway

## Connection Types
- • Lead times are often longer than 1 month to establish a new connection
- Dedicated Connections: 1Gbps,10 Gbps and 100 Gbps capacity
	- Request made to AWS first, then completed by AWS Direct Connect Partners
- Hosted Connections: 50Mbps, 500 Mbps, to 10 Gbps
	- Connection requests are made via AWS Direct Connect Partners

## Encryption
- Data in transit is not encrypted but is private
- AWS Direct Connect + VPN provides an IPsec-encrypted private connection

## Resiliency
## ![[Pasted image 20250319155024.png]]

### Site-to-Site VPN connection as a backup 
In case Direct Connect fails, you can set up a backup Direct Connect connection (expensive), or a Site-to-Site VPN connection

![[Pasted image 20250319155330.png]]