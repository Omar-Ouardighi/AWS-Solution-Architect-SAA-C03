## Key Management Service
- AWS manages encryption keys for us
- Seamlessly integrated into most AWS services (EBS, S3, RDS, SSM…)
- Fully integrated with IAM for authorization
- Able to audit KMS Key usage using [[CloudTrail]]

## KMS Keys Types
- **Symmetric (AES-256 keys)**
	- Single encryption key that is used to Encrypt and Decrypt
	- You never get access to the KMS Key unencrypted (must call KMS API to use)
- **Asymmetric (RSA & ECC key pairs)**
	- Public (Encrypt) and Private Key (Decrypt) pair
	- Used for Encrypt/Decrypt, or Sign/Verify operations
	- Use case: encryption outside of AWS by users who can’t call the KMS AP

## Types of KMS Keys:
- AWS Owned Keys (free): SSE-S3, SSE-SQS, SSE-DDB (default key)
- AWS Managed Key: free (aws/service-name, example: aws/rds or aws/ebs)
- Customer managed keys created in KMS: $1 / month
- Customer managed keys imported: $1 / month
- + pay for API call to KMS ($0.03 / 10000 calls)
### Automatic Key rotation: 
- AWS-managed KMS Key: automatic every 1 year 
- Customer-managed KMS Key: (must be enabled) automatic & on-demand 
- Imported KMS Key: only manual rotation possible using alias![[Screenshot 2025-03-15 120243.png]]
### Copying Snapshots across accounts
- Create a Snapshot, encrypted with your own KMS Key (Customer Managed Key) 
- Attach a KMS **Key Policy** to authorize cross-account access 
- Share the encrypted snapshot 
- (in target) Create a copy of the Snapshot, encrypt it with a CMK in your account 
- Create a volume from the snapshot

## KMS Multi-Region Keys
- Identical KMS keys in different AWS Regions that can be used interchangeably
- Multi-Region keys have the same key ID, key material, automatic rotation…
- Encrypt in one Region and decrypt in other Regions
- KMS Multi-Region are NOT global (Primary + Replicas)
- Each Multi-Region key is managed independently'
- Use cases: global client-side encryption, encryption on Global DynamoDB, Global Aurora

### **DynamoDB Global Tables & KMS Multi-Region Keys (Client-Side Encryption)**

- **Client-Side Encryption with DynamoDB**: Encrypt specific attributes using the **DynamoDB Encryption Client** before storing them in the table.
- **Replication with Global Tables**: Encrypted data is automatically replicated across regions.
- **Multi-Region KMS Keys**: If a **multi-region key** exists in the same region as the **DynamoDB Global Table**, clients in those regions can make **low-latency API calls** to KMS for decryption.
- **Access Control**: Only clients with the **correct API key** can decrypt the data, ensuring field-level security.
### **Global Aurora & KMS Multi-Region Keys (Client-Side Encryption)**

- **Client-Side Encryption with Aurora**: Encrypt specific attributes using the **AWS Encryption SDK** before storing them in the Aurora database.
- **Replication with Aurora Global Database**: Encrypted data is automatically replicated across regions.
- **Multi-Region KMS Keys**: If a **multi-region key** exists in the same region as the **Aurora Global Database**, clients in those regions can make **low-latency API calls** to KMS for decryption.
- **Access Control**: Only clients with the **correct API key** can decrypt the data, ensuring **field-level security**—even from **database administrators**.

### **AMI Sharing Process (Encrypted via KMS)**

1. **Encryption in Source Account**: The AMI is encrypted using a **KMS key** from the source account.
2. **Grant Launch Permission**: Modify the **AMI attributes** to allow the target AWS account to launch instances.
3. **Share KMS Keys**: The **KMS key** used for encrypting the AMI’s snapshot must be shared with the **target account/IAM role**.
4. **IAM Permissions in Target Account**: The target IAM role/user must have permissions for:
    - `DescribeKey`
    - `ReEncrypt`
    - `CreateGrant`
    - `Decrypt`
5. **Optional Re-Encryption**: When launching an EC2 instance, the target account can use its **own KMS key** to re-encrypt the volumes.