- Protects your web applications from common web exploits (Layer 7)
- Layer 7 is HTTP (vs Layer 4 is TCP/UDP)
- Deploy on 
	- Application Load Balancer 
	- API Gateway 
	- CloudFront 
	- AppSync GraphQL API 
	- Cognito User Pool

## Web ACL ((Web Access Control List))
- up to 10k ips per set/rule
- HTTP headers, HTTP body, or URI strings Protects from common attack - SQL injection and Cross-Site Scripting (XSS)
- size constraints
- geo matching (block countries)
- rate based rules for DDoS protection
- rules are regional, for [[Cloudfront]] they are global
- A rule group is a reusable set of rules that you can add to a web ACL![[Screenshot 2025-03-17 123651.png]]