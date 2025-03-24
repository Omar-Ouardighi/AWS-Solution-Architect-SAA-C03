- AWS Lambda + API Gateway: No infrastructure to manage
- Support for the WebSocket Protocol 
- Handle API versioning (v1, v2…) 
- Handle different environments (dev, test, prod…) 
- Handle security (Authentication and Authorization) 
- Create API keys, handle request throttling 
- Swagger / Open API import to quickly define APIs 
- Transform and validate requests and responses 
- Generate SDK and API specifications 
- Cache API responses

## Targets
- Lambda for REST
- any HTTP endpoint
- any AWS API ([[StepFunction]], [[SQS]], ...)

## Endpoint Types

- **Edge-Optimized (default)**: For global clients 
	- Requests are routed through the CloudFront Edge locations (improves latency) 
	- The API Gateway still lives in only one region
- **Regional:** 
	- For clients within the same region 
	- Could manually combine with CloudFront (more control over the caching strategies and the distribution) 
- **Private:** 
	- Can only be accessed from your VPC using an interface VPC endpoint (ENI) 
	- Use a resource policy to define access

## Security
### Authentication
- [[IAM]] Roles (for internal Application)
- [[Cognito]] for External Users
- Custom Authorized (using [[Lambda]] and own code)

### Custom Domain  name HTTP Security
- use [[ACM]]
- [[ACM]] cert must be in us east 1 for Edge Optimized
- If using Regional endpoint, the certificate must be in the API Gateway region
- Must setup CNAME or A-alias record in  [[Route53]]