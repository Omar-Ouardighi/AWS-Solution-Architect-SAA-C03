- the goal is to scale in or out to match a load
- ASG are free
- It is possible to scale an ASG based on CloudWatch alarms
- ![[Screenshot 2024-11-26 180357.png]]
## ASG Launch Template
- AMI + Instance Type 
- EC2 User Data 
- EBS Volumes 
- Security Groups 
- SSH Key Pair 
- IAM Roles for your EC2 Instances 
- Network + Subnets Information 
- Load Balancer Information 
- Min Size / Max Size / Initial Capacity 
- Scaling Policies

## Scaling policies

- Dynamic Scaling 
	- Target Tracking Scaling • Simple to set-up • Example: I want the average ASG CPU to stay at around 40% 
	- Simple / Step Scaling • When a CloudWatch alarm is triggered (example CPU > 70%), then add 2 units • When a CloudWatch alarm is triggered (example CPU < 30%), then remove 1 
- Scheduled Scaling 
	- Anticipate a scaling based on known usage patterns • Example: increase the min capacity to 10 at 5 pm on Fridays
- Predictive scaling: continuously forecast load and schedule scaling ahead

## Good metrics to scale on 
- CPUUtilization
- RequestCountPerTarget: to make sure the number of requests per EC2 instances is stable 
- Average Network In / Out (if you’re application is network bound) 
- Any custom metric (that you push using CloudWatch)

## Scaling Cooldowns
- After a scaling activity happens, you are in the cooldown period (default 300 seconds) 
- During the cooldown period, the ASG will not launch or terminate additional instances (to allow for metrics to stabilize) 
- Advice: Use a ready-to-use AMI to reduce configuration time in order to be serving request fasters and reduce the cooldown period