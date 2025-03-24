## Network Access Control List
- NACL are like a firewall which control traffic from and to subnets
- One NACL per subnet, new subnets are assigned the Default NACL
### Default NACL
- Accepts everything inbound/outbound with the subnets it’s associated with 
- Do NOT modify the Default NACL, instead create custom NACLs

### Ephemeral Ports
- Clients connect to a defined port, and expect a response on an ephemeral port
- Different Operating Systems use different port ranges, examples: 
	- IANA & MS Windows 10 è 49152 – 65535 
	- Many Linux Kernels è 32768 – 60999![[Screenshot 2025-03-19 112303.png]]


## Security Group vs. NACLs

![[Screenshot 2025-03-19 112315.png]]