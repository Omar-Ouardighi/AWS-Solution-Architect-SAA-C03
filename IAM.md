
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