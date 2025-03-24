- Redshift is based on PostgreSQL, but it’s not used for OLTP 
- It’s OLAP – online analytical processing (analytics and data warehousing) 
- 10x better performance than other data warehouses, scale to PBs of data 
- Columnar storage of data (instead of row based) & parallel query engine 
- Two modes: Provisioned cluster or Serverless cluster 
-  vs Athena: faster queries / joins / aggregations thanks to indexes
![[Screenshot 2025-03-11 151929.png]]
## Snapshots & DR
- Redshift has “Multi-AZ” mode for some clusters
- Snapshots are point-in-time backups of a cluster, stored internally in S3
- You can restore a snapshot into a new cluster
- Automated: every 8 hours, every 5 GB, or on a schedule. Set retention between 1 to 35 days •
- Manual: snapshot is retained until you delete it
- You can configure Amazon Redshift to automatically copy snapshots (automated or manual) of a cluster to another AWS Region![[Screenshot 2025-03-11 152217.png]]

## Redshift Spectrum
- Query data that is already in S3 without loading it
- Must have a Redshift cluster available to start the query
- The query is then submitted to thousands of Redshift Spectrum nodes