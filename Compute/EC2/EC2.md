It mainly consists in the capability of : 
- Renting virtual machines (EC2) 
- Storing data on virtual drives (EBS) 
- Distributing load across machines (ELB) 
- Scaling the services using an auto-scaling group (ASG)


## EC2 User Data

- It is possible to bootstrap our instances using an EC2 User data script. 
- bootstrapping means launching commands when a machine starts • That script is only run once at the instance first start 
- EC2 user data is used to automate boot tasks such as: 
	- Installing updates 
	- Installing software 
	- Downloading common files from the internet 
	- Anything you can think of 
	- The EC2 User Data Script runs with the root user

## EC2 instance types

AWS has the following naming convention: **m5.2xlarge** 
- m: instance class 
- 5: generation (AWS improves them over time) 
- 2xlarge: size within the instance class

### General Purpose type (t2, m5, m6, ... )
 
- Great for a diversity of workloads such as web servers or code repositories 
- Balance between: • Compute • Memory • Networking

### Compute Optimized (C6g, C5, ...)
- Great for compute-intensive tasks that require high performance processors: 
	- Batch processing workloads 
	- Media transcoding 
	- High performance web servers 
	- High performance computing (HPC) 
	- Scientific modeling & machine learning 
	- Dedicated gaming servers

### Memory Optimized (R5, R4, X1, ..)
- Fast performance for workloads that process large data sets in memory 
- Use cases: 
	- High performance, relational/non-relational databases 
	- Distributed web scale cache stores 
	- In-memory databases optimized for BI (business intelligence) 
	- Applications performing real-time processing of big unstructured data

### Storage Optimized (I4G, I3, D3, H1)
- Great for storage-intensive tasks that require high, sequential read and write access to large data sets on local storage 
- Use cases: 
	- High frequency online transaction processing (OLTP) systems 
	- Relational & NoSQL databases 
	- Cache for in-memory databases (for example, Redis) 
	- Data warehousing applications 
	- Distributed file systems



## EC2 Instances Purchasing Options
### On-Demand Instances
- Pay for what you use: 
	- Linux or Windows - billing per second, after the first minute 
	- All other operating systems - billing per hour 
- Has the highest cost but no upfront payment 
- No long-term commitment 
- Recommended for short-term and un-interrupted workloads, where you can't predict how the application will behave

### Reserved Instances
- Up to 72% discount compared to On-demand 
- You reserve a specific instance attributes (Instance Type, Region, Tenancy, OS) 
- Reservation Period – 1 year (+discount) or 3 years (+++discount) 
- Payment Options – No Upfront (+), Partial Upfront (++), All Upfront (+++) 
- Reserved Instance’s Scope – Regional or Zonal (reserve capacity in an AZ) 
- Recommended for steady-state usage applications (think database) 
- You can buy and sell in the Reserved Instance Marketplace
- **Convertible Reserved Instance** 
	- Can change the EC2 instance type, instance family, OS, scope and tenancy 
	- Up to 66% discount
## Savings Plans
- Get a discount based on long-term usage (up to 72% - same as RIs) 
- Commit to a certain type of usage ($10/hour for 1 or 3 years) 
- Usage beyond EC2 Savings Plans is billed at the On-Demand price 
- Locked to a specific instance family & AWS region (e.g., M5 in us-east-1) 
- Flexible across: 
	- Instance Size (e.g., m5.xlarge, m5.2xlarge) 
	- OS (e.g., Linux, Windows) 
	- Tenancy (Host, Dedicated, Default
### EC2 Spot Instances 
- Can get a discount of up to 90% compared to On-demand 
- Instances that you can “lose” at any point of time if your max price is less than the current spot price 
- Define max spot price and get the instance while current spot price < max
- The MOST cost-efficient instances in AWS 
- Useful for workloads that are resilient to failure 
	- Batch jobs 
	- Data analysis 
	- Image processing 
	- Any distributed workloads 
	- Workloads with a flexible start and end time 
- **Not suitable for critical jobs or databases**

### Dedicated Hosts
- A physical server with EC2 instance capacity fully dedicated to your use 
- Allows you address compliance requirements and use your existing server bound software licenses (per-socket, per-core, pe—VM software licenses) 
- Purchasing Options: 
	- On-demand – pay per second for active Dedicated Host 
	- Reserved - 1 or 3 years (No Upfront, Partial Upfront, All Upfront) 
- The most expensive option 
- Useful for software that have complicated licensing model (BYOL – Bring Your Own License) 
- Or for companies that have strong regulatory or compliance needs

### Dedicated Instances
- Instances run on hardware that’s dedicated to you 
- May share hardware with other instances in same account 
- No control over instance placement (can move hardware after Stop / Start)

### Capacity Reservations 
- Reserve On-Demand instances capacity in a specific AZ for any duration 
- You always have access to EC2 capacity when you need it 
- No time commitment (create/cancel anytime), no billing discounts 
- Combine with Regional Reserved Instances and Savings Plans to benefit from billing discounts 
- You’re charged at On-Demand rate whether you run instances or not 
- Suitable for short-term, uninterrupted workloads that needs to be in a specific AZ

### Spot Fleets
- Spot Fleets = set of Spot Instances + (optional) On-Demand Instances 
- The Spot Fleet will try to meet the target capacity with price constraints 
	- Define possible launch pools: instance type (m5.large), OS, Availability Zone 
	- Can have multiple launch pools, so that the fleet can choose 
	- Spot Fleet stops launching instances when reaching capacity or max cost 
- Strategies to allocate Spot Instances: 
	- lowestPrice: from the pool with the lowest price (cost optimization, short workload) 
	- diversified: distributed across all pools (great for availability, long workloads) 
	- capacityOptimized: pool with the optimal capacity for the number of instances 
	- priceCapacityOptimized (recommended): pools with highest capacity available, then select the pool with the lowest price (best choice for most workloads) 
- Spot Fleets allow us to automatically request Spot Instances with the lowest price

## Networking in EC2

### Private vs Public IP (IPv4)
- ***Public IP***: 
	- Public IP means the machine can be identified on the internet (WWW) 
	- Must be unique across the whole web (not two machines can have the same public IP). 
	- Can be geo-located easily 
- ***Private IP:*** 
	- Private IP means the machine can only be identified on a private network  
	- The IP must be unique across the private network 
	- BUT two different private networks (two companies) can have the same IPs. 
	- Machines connect to WWW using a NAT + internet gateway (a proxy) 
	- Only a specified range of IPs can be used as private IP

### Elastic IPs 
- When you stop and then start an EC2 instance, it can change its public IP. 
- If you need to have a fixed public IP for your instance, you need an Elastic IP 
- You can attach it to one instance at a time
- With an Elastic IP address, you can mask the failure of an instance or software by rapidly remapping the address to another instance in your account. 
- You can only have 5 Elastic IP in your account (you can ask AWS to increase that). 
- Overall, try to avoid using Elastic IP: 
	- They often reflect poor architectural decisions 
	- Instead, use a random public IP and register a DNS name to it 
	- Or use a Load Balancer and don’t use a public IP

## Placement Groups
- Placement group defines the placement strategy for the EC2 instances.
- When you create a placement group, you specify one of the following strategies for the group: 
	- **Cluster**—clusters instances into a low-latency group in a single Availability Zone 
		- Pros : great network
		- Cons : If the AZ fails, all instances fails at the same time
		- Use case: • Big Data job that needs to complete fast • Application that needs extremely low latency and high network throughput
	- **Spread**—spreads instances across underlying hardware (max 7 instances per group per AZ) 
		- Pros: •Can span across Availability Zones (AZ) • Reduced risk in simultaneous failure • EC2 Instances are on different physical hardware 
		- Cons: • Limited to 7 instances per AZ per placement group 
		- Use case: •Application that needs to maximize high availability •Critical Applications where each instance must be isolated from failure from each other
	- **Partition**—spreads instances across many different partitions (which rely on different sets of racks) within an AZ. Scales to 100s of EC2 instances per group
		- Up to 7 partitions per AZ • Can span across multiple AZs in the same region • The instances in a partition do not share racks with the instances in the other partitions • A partition failure can affect many EC2 but won’t affect other partitions • EC2 instances get access to the partition information as metadata 
		- Use cases: HDFS, HBase, Cassandra, Kafka
### Elastic Network Interfaces (ENI)
- Logical component in a VPC that represents a virtual network card 
- The ENI can have the following attributes: 
	- Primary private IPv4, one or more secondary IPv4 
	- One Elastic IP (IPv4) per private IPv4 
	- One Public IPv4 
	- One or more security groups 
	- A MAC address 
- You can create ENI independently and attach them on the fly (move them) on EC2 instances for failover 
- Bound to a specific availability zone (AZ)
## EC2 Hibernate 
- The in-memory (RAM) state is preserved  (< 150gb)
- The instance boot is much faster! (the OS is not stopped / restarted) 
- Under the hood: the RAM state is written to a file in the root EBS volume 
- The root EBS volume must be encrypted 
- Use cases: • Long-running processing • Saving the RAM state • Services that take time to initialize
- An instance can NOT be hibernated more than 60 days