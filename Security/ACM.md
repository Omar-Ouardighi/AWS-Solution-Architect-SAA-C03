# AWS Certificate Manager
- manage, provision and deploy SSL Certs
- Provide in-flight encryption for websites (HTTPS)
- certs created by ACM are automatically renewed
- Integrations with (load TLS certificates on) • Elastic Load Balancers (CLB, ALB, NLB) • CloudFront Distributions • APIs on API Gateway
- Cannot use ACM with EC2 (can’t be extracted)
## Requesting Public Certificates
- List domain names to be included in the certificate
- Select Validation Method: DNS Validation or Email validation
- It will take a few hours to get verified
- The Public Certificate will be enrolled for automatic renewal
## Importing Public Certificates
- No automatic renewal
- ACM sends daily expiration events
- AWS Config has a managed rule named acm-certificate-expiration-check to check for expiring certificates (configurable number of days)
## ACM – Integration with API Gateway
- Create a Custom domain Name in API Gateway
- **Edge-Optimized (default):** For global clients
	- The TLS Certificate must be in the same region as CloudFront, in us-east-1
- **Regional**
	- The TLS Certificate must be imported on API Gateway, in the same region as the API Stage

## IAM certificate Store
- used for regions where ACM is not available
- can be used via cli