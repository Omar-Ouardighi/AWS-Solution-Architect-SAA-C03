Amazon Elastic Kubernetes Service
- EKS supports EC2 if you want to deploy worker nodes or Fargate to deploy serverless containers
- Use case: if your company is already using Kubernetes on-premises or in another cloud, and wants to migrate to AWS using Kubernetes

## Node Types
### Manged Node Groups
- Creates and manages Nodes (EC2 instances) for you
- ASG managed by [[EKS]]
- Supports on demand and spot instances

### Self Managed
- Nodes created by you and registered to the EKS cluster and managed by an ASG
- Can use prebuild [[EKS]] optimized AMi
- Supports on demand or spot instaces

### Fargate
- No nodes, instances or maintance required

## Data volumes
- Need to specify storage class
- EBS 
- EFS (works with fargate)
- FSxLustre
- [[FSx]] for NetApp ONETAP