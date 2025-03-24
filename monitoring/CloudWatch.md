Central service for all logs and metrics in AWS.
## Cloudwatch Metrics
- metrics for every service in AWS
- bucketed by namespaces
- Up to 30 dimensions per metric
- metrics can have timestamps
- can create dashboard
- can create custom metrics

## Cloudwatch metrics streams
- continually stream cloudwatch metrics to 
	- [[Amazon Data Firehose]] 
	- 3rd party providers
- option to filter metrics, to just send a subset
![[Screenshot 2025-03-12 120828.png]]
## Cloudwatch Logs
- Log groups (application name)
- log stream (log files, instances whitin on app, containers)
- can define log expiration days
### Targets To Send Logs To
- [[S3]]
- [[Kinesis Data Streams]] 
- [[Amazon Data Firehose]]
- [[Lambda]]
- [[OpenSearch]]

### Sources
- SDK, Cloudwatch Logs Angent, Cloudwatch unified agent
- [[Beanstalk]], collection of logs from applciation
- [[ECS]] collection from containers
-  [[Lambda]] collection from function logs
- [[VPC]] flow logs
- [[API Gateway]]
- [[CloudTrail]] based on filter
- [[Route53]] dns requests

## CloudWatch Logs Insights
- Search and analyze log data stored in CloudWatch Logs
- It’s a query engine, not a real-time engine
## CloudWatch Logs Subscriptions
- Get a real-time log events from CloudWatch Logs for processing and analysis
- Send to [[Kinesis Data Streams]], [[Amazon Data Firehose]], or [[Lambda]]
- • Subscription Filter – filter which logs are events delivered to your destination
- CloudWatch Logs Aggregation Multi-Account & Multi Region
- Cross-Account Subscription – send log events to resources in a different AWS account (KDS, KDF)
![[Screenshot 2025-03-12 122031.png]]

## CloudWatch Logs Agent & Unified Agent
- For virtual servers (EC2 instances, on-premises servers…)
- **CloudWatch Logs Agent:** old version , can only send to cloudwatch logs
- **CloudWatch Unified Agent** : 
	- Collect additional system-level metrics such as RAM, processes, etc…
	- Collect logs to send to CloudWatch Logs
	- Centralized configuration using SSM Parameter Store

## CloudWatch Alarms
- used to trigger notifications for any metric
- Alarm States: • OK • INSUFFICIENT_DATA • ALARM
- Period : Length of time in seconds to evaluate the metric
- Alarms can be created based on CloudWatch Logs Metrics Filters
### Targets
- Stop, Terminate, Reboot, or Recover an [[EC2]] Instance 
- Trigger Auto Scaling Action 
- Send notification to [[SNS]] (from which you can do pretty much anything)

### Composite Alarms
- Composite Alarms are monitoring the states of multiple other alarms
- AND and OR conditions
- Helpful to reduce “alarm noise” by creating complex composite alarms
### EC2 Instance Recovery
- Status Check : Instance status, system status, EBS status
- start recovery (move host but keep ips, metadata and placement groups)
## CloudWatch Insights and Operational Visibility
- CloudWatch Container Insights 
	- ECS, EKS, Kubernetes on EC2, Fargate, needs agent for Kubernetes 
	- Metrics and logs 
- CloudWatch Lambda Insights 
	- Detailed metrics to troubleshoot serverless applications 
- CloudWatch Contributors Insights 
	- Find “Top-N” Contributors through CloudWatch Logs 
- CloudWatch Application Insights 
	- Automatic dashboard to troubleshoot your application and related AWS services