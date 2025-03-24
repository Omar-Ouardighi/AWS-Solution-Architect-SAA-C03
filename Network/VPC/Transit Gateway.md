- For having transitive peering between thousands of VPC and on-premises, hub-and-spoke (star) connection
- Supports IP Multicast (not supported by any other AWS service)
- Works with Direct Connect Gateway, VPN connections
- ![[Pasted image 20250319155907.png]]
### Site-to-Site VPN ECMP
- ECMP = Equal-cost multi-path routing 
- Routing strategy to allow to forward a packet over multiple best path 
- Use case: create multiple Site to-Site VPN connections to increase the bandwidth of your connection to AWS
![[Pasted image 20250319160100.png]]