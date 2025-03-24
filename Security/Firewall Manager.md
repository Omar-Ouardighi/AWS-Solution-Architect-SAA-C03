- Manage rules in all accounts of an AWS Organization
- Security policy: common set of security rules 
	- WAF rules (Application Load Balancer, API Gateways, CloudFront) 
	- AWS Shield Advanced (ALB, CLB, NLB, Elastic IP, CloudFront) 
	- Security Groups for EC2, Application Load BAlancer and ENI resources in VPC 
	- AWS Network Firewall (VPC Level) 
	- Amazon Route 53 Resolver DNS Firewall 
	- Policies are created at the region level
- Rules are applied to new resources as they are created (good for compliance) across all and future accounts in your Organization

## WAF vs. Firewall Manager vs. Shield
- WAF, Shield and Firewall Manager are used together for comprehensive protection 
- Define your Web ACL rules in WAF
- For granular protection of your resources, WAF alone is the correct choice 
- If you want to use AWS WAF across accounts, accelerate WAF configuration, automate the protection of new resources, use Firewall Manager with AWS WAF 
- Shield Advanced adds additional features on top of AWS WAF, such as dedicated support from the Shield Response Team (SRT) and advanced reporting. 
- If you’re prone to frequent DDoS attacks, consider purchasing Shield Advanced