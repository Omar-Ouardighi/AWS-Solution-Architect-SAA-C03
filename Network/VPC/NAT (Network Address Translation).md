## NAT Instance (outdated, but still at the exam)
- Allows EC2 instances in private subnets to connect to the Internet
- Must be launched in a public subnet
- Must disable EC2 setting: Source / destination Check
- Must have Elastic IP attached to it
- Route Tables must be configured to route traffic from private subnets to the NAT Instance
- Pre-configured Amazon Linux AMI is available
- Not highly available / resilient setup out of the box

## NAT Gateway
- AWS-managed NAT, higher bandwidth, high availability, no administration
- NATGW is created in a specific Availability Zone, uses an Elastic IP
- Can’t be used by EC2 instance in the same subnet (only from other subnets)
- Requires an IGW (Private Subnet => NATGW => IGW)![[Screenshot 2025-03-18 144712.png]]![[Screenshot 2025-03-18 144728.png]]