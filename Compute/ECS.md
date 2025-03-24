Amazon’s own container platform

## EC2 launch Type
- you must provision & maintain the infrastructure (the EC2 instances)
- Launch Docker containers on AWS = Launch ECS Tasks on ECS Clusters
- Each EC2 Instance must run the ECS Agent to register in the ECS Cluster

## Fargate Launch Type
- You do not provision the infrastructure
- Serverless
- AWS just runs ECS Tasks for you based on the CPU / RAM you need
- To scale, just increase the number of tasks. Simple - no more EC2 instances
## IAM Roles for ECS

- **EC2 Instance Profile (EC2 Launch Type only):**
	- Used by the ECS agent
	-  Makes API calls to ECS service
	- Pull Docker image from ECR
	- Send container logs to CloudWatch Logs
	- Reference sensitive data in Secrets Manager or SSM Parameter Store
- **ECS Task Role**
	- Defines Permissons for the code running in the container (access to other services)
	- Use different roles for the different ECS Services you run
## Load Balancer Integrations
- Application Load Balancer supported and works for most use cases
- Network Load Balancer recommended only for high throughput / high performance use cases, or to pair it with AWS Private Link

## Data Volumes (EFS)
- Mount EFS file systems onto ECS tasks
- Works for both EC2 and Fargate launch types
- Fargate + EFS = Serverless
- Use cases: persistent multi-AZ shared storage for your containers
- Note: • Amazon S3 cannot be mounted as a file system

## ECS Service Auto Scaling
- Automatically increase/decrease the desired number of ECS tasks
- Uses AWS Application Auto Scaling to scale on CPU, MEMORY or ALB Request Count Per Target 
- Modes:
	- Target Tracking
	- Step Scaling
	- Scheduled Scaling
- Fargate Auto Scaling is much easier to setup (because Serverless)
- • ECS Service Auto Scaling (task level) ≠ EC2 Auto Scaling (EC2 instance level)
## Amazon ECR
Store and manage Docker images on AWS
Fully integrated with ECS, backed by Amazon S3
Access is controlled through IAM (permission errors => policy)
## Solutions Architecture
![[Screenshot 2025-03-10 113608.png]]

![[Screenshot 2025-03-10 113613.png]]

![[Screenshot 2025-03-10 113619.png]]

![[Screenshot 2025-03-10 113556.png]]

![[Screenshot 2025-03-10 113601.png]]