- Virtual functions – no servers to manage! 
- Limited by time - short executions 
- Run on-demand 
- Scaling is automated!

## Limits per region
- **Execution** : 
	- Memory allocation: 128 MB – 10GB (1 MB increments) 
	- Maximum execution time: 900 seconds (15 minutes) 
	- Environment variables (4 KB) 
	- Disk capacity in the “function container” (in /tmp): 512 MB to 10GB 
	- Concurrency executions: 1000 (can be increased)
- **Deployment**
	- deployment size (compressed .zip): 50 MB
	- Size of uncompressed deployment (code + dependencies): 250 MB
	- Can use the /tmp directory to load other files at startup
	- Size of environment variables: 4 KB
## Lambda snapstart
 - When enabled, function is invoked from a preinitialized state (no function initialization from scratch)
 - When you publish a new version: 
	 - Lambda initializes your function 
	 - Takes a snapshot of memory and disk state of the initialized function 
	 - Snapshot is cached for low-latency access
## CloudFront Functions & Lambda@Edge
Edge Function: A code that you write and attach to CloudFront distributions • Runs close to your users to minimize latency

### CloudFront Functions
- For high-scale, latency-sensitive CDN customizations
- Sub-ms startup times, millions of requests/second
- USE CASES :
	- Cache key normalization
	- Header manipulation
	-  URL rewrites or redirects
	-  Request authentication & authorization
### Lambda@Edge
-  Scales to 1000s of requests/second
-  Lambda functions written in NodeJS or Python
- USE CASES :
	- Longer execution time (several ms)
	- Adjustable CPU or memory
	- Your code depends on a 3rd libraries (e.g., AWS SDK to access other AWS services)
	- Network access to use external services for processing
	- File system access or access to the body of HTTP requests

## Lambda in VPC
- By default, your Lambda function is launched outside your own VPC (in an AWS -owned VPC)
- You must define the VPC ID, the Subnets and the Security Groups • Lambda will create an ENI (Elastic Network Interface) in your subnets

## Lambda with RDS Proxy
If Lambda functions directly access your database, they may open too many connections under high load![[Screenshot 2025-03-10 160332.png]]

## Invoking Lambda from RDS & Aurora
- Allows you to process data events from within a database
- • Supported for RDS for PostgreSQL and Aurora MySQL
- Must allow outbound traffic to your Lambda function from within your DB instance (Public, NAT GW, VPC Endpoints)
- DB instance must have the required permissions to invoke the Lambda function
## RDS Event Notifications
- Notifications that tells information about the DB instance itself (created, stopped, start, …)
- • You don’t have any information about the data itself
- Send notifications to SNS or subscribe to events using EventBridge