- • Provides governance, compliance and audit for your AWS Account 
- CloudTrail is enabled by default! 
- Get an history of events / API calls made within your AWS Account
- Can put logs from CloudTrail into CloudWatch Logs or S3 
- A trail can be applied to All Regions (default) or a single Region.
- Events are stored for 90 days in CloudTrail
- To keep events beyond this period, log them to S3 and use Athena
## CloudTrail Events
### Management Events: 
- Operations that are performed on resources in your AWS account
- enabled by default
### Data Events: 
- By default, data events are not logged (because high volume operations)
### CloudTrail Insights Events:
- Enable CloudTrail Insights to detect unusual activity