- Fully managed batch processing at any scale 
- Efficiently run 100,000s of computing batch jobs on AWS
- Batch will dynamically launch EC2 instances or Spot Instances
- Batch jobs are defined as Docker images and run on ECS

### Batch vs Lambda
- Lambda: • Time limit • Limited runtimes • Limited temporary disk space • Serverless
- Batch: 
	- No time limit 
	- Any runtime as long as it’s packaged as a Docker image 
	- Rely on EBS / instance store for disk space 
	- Relies on EC2 (can be managed by AWS)