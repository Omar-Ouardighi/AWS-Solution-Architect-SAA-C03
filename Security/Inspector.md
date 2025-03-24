
- automatic Security assessments
- continues scanning of infrastructure
- Package vulnerabilities (EC2, ECR & Lambda)
- Network reachability (EC2)
- generates Risk Score
- Reporting & integration with AWS Security Hub 
- Send findings to Amazon Event Bridge
- **Remember: only for EC2 instances, Container Images & Lambda functions**

## [[EC2]]
- useses AWS System Manager Agent
- Analyze against unintended network accessibility
- analyse running os against known vulns

## Containers pushed to ECR
- Assessment of Container Images as they are pushed

## For [[Lambda]] Functions
- Identifies software vulnerabilities in function code and package dependencies 
- Assessment of functions as they are deployed
![[Screenshot 2025-03-18 120121.png]]