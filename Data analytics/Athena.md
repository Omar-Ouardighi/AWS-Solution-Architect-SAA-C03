- Serverless query service to analyze data stored in Amazon S3 
- Uses standard SQL language to query the files (built on Presto) 
- Supports CSV, JSON, ORC, Avro, and Parquet • Pricing: $5.00 per TB of data scanned •
- Commonly used with Amazon Quicksight for reporting/dashboards 
- Use cases: Business intelligence / analytics / reporting, analyze & query VPC Flow Logs, ELB Logs, CloudTrail trails, etc... 
- Exam Tip: analyze data in S3 using serverless SQL, use Athena

## Performance Improvement
- Use columnar data for cost-savings (less scan) 
	- Apache Parquet or ORC is recommended • Huge performance improvement • Use Glue to convert your data to Parquet or ORC
- • Compress data for smaller retrievals
- Partition datasets in S3 for easy querying on virtual columns
- Use larger files (> 128 MB) to minimize overhead![[Screenshot 2025-03-11 151227.png]]