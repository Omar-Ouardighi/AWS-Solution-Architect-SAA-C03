- Classless Inter-Domain Routing – a method for allocating IP addresses
- A CIDR consists of two components
	- Base IP
	- Subnet Mask:
		- Defines how many bits can change in the IP 
		- Example: /0, /24, /32
		- Can take two forms:
			- /0 – all octets can change
			- • /8 => 255.0.0.0  – last 3 octets can change
			- /16 => 255.255.0.0  last 2 octets can change
			- /24 => 255.255.255.0  – last octet can change
			- /32 => 255.255.255.255 no octet can change

## Public vs. Private IP (IPv4)
- Private IP can only allow certain values: 
	- 10.0.0.0 – 10.255.255.255 (10.0.0.0/8) in big networks 
	- 172.16.0.0 – 172.31.255.255 (172.16.0.0/12) ç AWS default VPC in that range 
	- 192.168.0.0 – 192.168.255.255 (192.168.0.0/16)  e.g., home networks
- All the rest of the IP addresses on the Internet are Public