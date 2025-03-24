- IPv4 designed to provide 4.3 Billion addresses (they’ll be exhausted soon) 
- IPv6 is designed to provide 3.4 × 10,- unique IP addresses 
- Every IPv6 address in AWS is public and Internet-routable (no private range)
-  Format => x.x.x.x.x.x.x.x (x is hexadecimal, range can be from 0000 to ffff) 
- Examples: • 2001:db8:3333:4444:5555:6666:7777:8888

### IPv4 Troubleshooting
- IPv4 cannot be disabled for your VPC and subnets 
- So, if you cannot launch an EC2 instance in your subnet 
	- It’s not because it cannot acquire an IPv6 (the space is very large) 
	- It’s because there are no available IPv4 in your subnet 
- Solution: create a new IPv4 CIDR in your subnet
### Egress-only Internet Gateway
- • Used for IPv6 only  (similar to a NAT Gateway but for IPv6)
- Allows instances in your VPC outbound connections over IPv6 while preventing the internet to initiate an IPv6 connection to your instances 
- You must update the Route Tables
![[Pasted image 20250319162035.png]]