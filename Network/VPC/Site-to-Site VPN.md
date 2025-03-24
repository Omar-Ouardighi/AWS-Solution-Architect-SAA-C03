### Virtual Private Gateway (VGW
- VPN concentrator on the AWS side of the VPN connection
- VGW is created and attached to the VPC from which you want to create the Site-to-Site VPN connection

### Customer Gateway (CGW)
- Software application or physical device on customer side of the VPN connection
- **What IP address to use?** 
	- Public Internet-routable IP address for your Customer Gateway device 
	- If it’s behind a NAT device that’s enabled for NAT traversal (NAT-T), use the public IP address of the NAT device

### Site-to-Site VPN Connections
- **Important step:** enable Route Propagation for the Virtual Private Gateway in the route table that is associated with your subnets 
- If you need to ping your EC2 instances from on-premises, make sure you add the ICMP protocol on the inbound of your security group![[Screenshot 2025-03-19 130455.png]]
## VPN CloudHub
- Provide secure communication between multiple sites, if you have multiple VPN connections
- To set it up, connect multiple VPN connections on the same VGW, setup dynamic routing and configure route tables