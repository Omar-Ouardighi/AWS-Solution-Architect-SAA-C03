
* **Users:** mapped to a physical user, has a password for AWS Console 
* **Groups:** contains users only 
* **Policies:** JSON document that outlines permissions for users or groups 
* **Roles:** for EC2 instances or AWS services 
* **Security:** MFA + Password Policy 
* **AWS CLI:** manage your AWS services using the command-line 
* **AWS SDK:** manage your AWS services using a programming language 
* **Access Keys:** access AWS using the CLI or SDK 
* **Audit:** IAM Credential Reports & IAM Access Advisor


## IAM Policies Structure 
* Consists of 
	* Version: policy language version, always include “2012 -10 - 17” 
	* Id: an identifier for the policy (optional) 
	* Statement: one or more individual statements (required) 
* Statements consists of 
	* Sid: an identifier for the statement (optional) 
	* Effect: whether the statement allows or denies access (Allow, Deny) 
	* Principal: account/user/role to which this policy applied to 
	* Action: list of actions this policy allows or denies 
	* Resource: list of resources to which the actions applied to 
	* Condition: conditions for when this policy is in effect (optional)

## IAM Guidelines & Best Practices 
* Don’t use the root account except for AWS account setup 
* One physical user = One AWS user 
* Assign users to groups and assign permissions to groups 
* Create a strong password policy 
* Use and enforce the use of Multi Factor Authentication (MFA) 
* Create and use Roles for giving permissions to AWS services 
* Use Access Keys for Programmatic Access (CLI / SDK) 
* Audit permissions of your account using IAM Credentials Report & IAM Access Advisor 
* Never share IAM users & Access Keys

## IAM Conditions
![[Screenshot 2025-03-13 113357.png]]![[Screenshot 2025-03-13 113535.png]]


## IAM FOR [[S3]]
- s3:ListBucket permission applies to arn:aws:s3:::test  => bucket level permission 
- s3:GetObject, s3:PutObject, s3:DeleteObject applies to arn:awn:s3:::test/*  => object level permission

## IAM Roles vs Resource-Based Policies
- When you assume a role (user, application or service), you give up your original permissions and take the permissions assigned to the role 
- When using a resource-based policy, the principal doesn’t have to give up his permissions

## [[EventBridge]] – Security
- Resource-based policy: Lambda, SNS, SQS, S3 buckets, API Gateway…
- IAM role: EC2 Auto Scaling, Systems Manager Run Command, ECS task…

## IAM Permission Boundaries
- supported for users and roles (not groups)
- Use cases 
	- Delegate responsibilities to non administrators within their permission boundaries, for example create new IAM users 
	- Allow developers to self-assign policies and manage their own permissions, while making sure they can’t “escalate” their privileges (= make themselves admin)
	- Useful to restrict one specific user (instead of a whole account using Organizations & SCP)

## IAM Identity Center
- One login (single sign-on) for all your • AWS accounts in AWS Organizations
### Fine-grained Permissions and Assignments
- Multi-Account Permissions 
	- Manage access across AWS accounts in your AWS Organization 
	- Permission Sets – a collection of one or more IAM Policies assigned to users and groups to define AWS access 
- Application Assignments 
	- SSO access to many SAML 2.0 business applications (Salesforce, Box, Microsoft 365, …) 
	- Provide required URLs, certificates, and metadata 
- Attribute-Based Access Control (ABAC) 
	- Fine-grained permissions based on users’ attributes stored in IAM Identity Center Identity Store 
	- Example: cost center, title, locale, … 
	- Use case: Define permissions once, then modify AWS access by changing the attributes