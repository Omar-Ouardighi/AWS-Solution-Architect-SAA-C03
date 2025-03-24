AWS Nameserver and Domain Name register Service.

## Features
- managed
- scalable
- authorative dns (can be updated by customer)
- registar (can register own names)
- 100% availabilty
- health checks

## Records

• How you want to route traffic for a domain
Each record contains: 
- Domain/subdomain Name – e.g., example.com 
- Record Type – e.g., A or AAAA 
- Value – e.g., 12.34.56.78 
- Routing Policy – how Route 53 responds to queries 
- TTL – amount of time the record cached at DNS Resolvers

Record Types 
- A – maps a hostname to IPv4 
- AAAA – maps a hostname to IPv6 
- CNAME – maps a hostname to another hostname 
	- The target is a domain name which must have an A or AAAA record 
	- Can’t create a CNAME record for the top node of a DNS namespace (Zone Apex) 
	- Example: you can’t create for example.com, but you can create for www.example.com 
- NS – Name Servers for the Hosted Zone 
	- Control how traffic is routed for a domain
- #### Alias
	- can target a root domain (cname can not)
	- can only be used for aws resources
	- **Targets** :
		- Elastic Load Balancers • CloudFront Distributions • API Gateway • Elastic Beanstalk environments • S3 Websites • VPC Interface Endpoints • Global Accelerator accelerator • Route 53 record in the same hosted zone
		-  *You cannot set an ALIAS record for an EC2 DNS name*

## Hosted Zones
**Public Hosted Zones** – contains records that specify how to route traffic on the Internet (public domain names) application1.mypublicdomain.com 
**Private Hosted Zones** – contain records that specify how you route traffic within one or more VPCs (private domain names) application1.company.internal

## Records TTL (Time To Live)
- High TTL – e.g., 24 hr 
	- Less traffic on Route 53 
	- Possibly outdated records
- Low TTL – e.g., 60 sec. 
- More traffic on Route 53 
- Records are outdated for less time 
- Easy to change records

**Except for Alias records, TTL is mandatory for each DNS record**

## Routing Policies
• Define how Route 53 responds to DNS queries

1. Simple:
	1. route traffic to a single resource
	2. Can specify multiple values in the same record, If multiple values are returned, a random one is chosen by the client
	3. Can’t be associated with Health Checks
2. Weighted :
	1. Control the % of the requests that go to each specific resource
	2. Can be associated with Health Checks
3. Latency-based:
	1. Redirect to the resource that has the least latency close to us
4. Failover
5. Geolocation : This routing is based on user location
6. Geoproximity:
	1. Route traffic to your resources based on the geographic location of users and resources 
	2. Ability to shift more traffic to resources based on the defined bias
7. IP-based:
	1. Routing is based on clients’ IP addresses
	2. You provide a list of CIDRs for your clients and the corresponding endpoints/locations (user-IP-to-endpoint mappings)
8. Multi-Value:
	1. Use when routing traffic to multiple resources
	2. Multi-Value is not a substitute for having an ELB