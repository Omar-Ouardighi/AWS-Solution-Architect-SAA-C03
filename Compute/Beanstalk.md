• Managed service 
	Automatically handles capacity provisioning, load balancing, scaling, application health monitoring, instance configuration

## Elastic Beanstalk – Components

- **Application**: collection of Elastic Beanstalk components (environments, versions, configurations, …) 
- **Application Version:** an iteration of your application code 
- **Environment** 
	- Collection of AWS resources running an application version (only one application version at a time) 
	- Tiers: Web Server Environment Tier & Worker Environment Tier 
	- You can create multiple environments (dev, test, prod, …)

**Worker Tier** : Scale based on the number of SQS messages

## Deployement Modes

- Single Instance Great for dev
- High Availability with Load Balancer Great for prod