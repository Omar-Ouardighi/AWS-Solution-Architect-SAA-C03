
Highly-secure, portable devices to collect and process data at the edge, and migrate data into and out of AWS

If it takes more than a week to transfer over the network, use Snowball devices!

## What is Edge Computing?
- Process data while it’s being created on an edge location
- These locations may have limited internet and no access to computing power
- We setup a Snowball Edge / Snowcone device to do edge computing 
	- Snowcone: 2 CPUs, 4 GB of memory, wired or wireless access 
	- Snowball Edge Compute Optimized (dedicated for that use case) & Storage Optimized •
	- Run EC2 Instances or Lambda functions at the edge

## Snowball into Glacier
- Snowball cannot import to Glacier directly 
- You must use Amazon S3 first, in combination with an S3 lifecycle policy