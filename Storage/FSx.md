• Launch 3rd party high-performance file systems on AWS
## 1. Amazon FSx for Windows (File Server)
- fully managed Windows file system share drive
- can be mounted on linux EC2 instances
- Microsoft Active Directory integration
- Supports Microsoft's Distributed File System (DFS) Namespaces
- Data is backed-up daily to S3
- Can be accessed from your on-premises infrastructure (VPN or Direct Connect)
- Can be configured to be Multi-AZ (high availability)
## 2. FSx for Lustre
- Lustre is a type of parallel distributed file system, for large-scale computing
- usage : ML, HPC, Video Processing, Financial Modeling, Electronic Design Automation
- integration with S3
- •Can be used from on-premises servers (VPN or Direct Connect)
- Deployment options:
	- **Scratch File System** : temporary storage, short-term processing, optimiize cost, data is not replicated
	-  **Persistent File System** : Long-term storage,  Data is replicated within same AZ,  long-term processing, sensitive data

## 3. FSx for NetApp ONTAP
- File System compatible with NFS, SMB, iSCSI protocol
- Move workloads running on ONTAP or NAS to AWS
- Works with: • Linux • Windows • MacOS • VMware Cloud on AWS • Amazon Workspaces & AppStream 2.0 • Amazon EC2, ECS and EKS
- • Storage shrinks or grows automatically
- • Point-in-time instantaneous cloning (helpful for testing new workloads)
- Snapshots, replication, low-cost, compression and data de-duplication

## 4. FSx for OpenZFS
- Managed OpenZFS file system on AWS 
- File System compatible with NFS (v3, v4, v4.1, v4.2)
- Move workloads running on ZFS to AWS 
- Works with: • Linux • Windows • MacOS • VMware Cloud on AWS • Amazon Workspaces & AppStream 2.0 • Amazon EC2, ECS and EKS
- Up to 1,000,000 IOPS with < 0.5ms latency
- Snapshots, compression and low-cost 
- Point-in-time instantaneous cloning (helpful for testing new workloads)