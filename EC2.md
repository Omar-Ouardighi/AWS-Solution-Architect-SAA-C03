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