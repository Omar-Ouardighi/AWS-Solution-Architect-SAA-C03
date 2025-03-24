- Helps with auditing and recording compliance of your AWS resources 
- Helps record configurations and changes over time 
- Questions that can be solved by AWS Config: • Is there unrestricted SSH access to my security groups? • Do my buckets have any public access? • How has my ALB configuration changed over time? 
- You can receive alerts (SNS notifications) for any changes
- Possibility of storing the configuration data into S3 

## Config Rules
- Can use AWS managed config rules (over 75) 
- Can make custom config rules (must be defined in AWS Lambda)
- AWS Config Rules does not prevent actions from happening (no deny)
- Automate remediation of non-compliant resources using SSM Automation Documents