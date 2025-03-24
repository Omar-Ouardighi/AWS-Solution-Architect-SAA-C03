- ElastiCache is to get managed Redis or Memcached 
- Caches are in-memory databases with really high performance, low latency 
- Helps reduce load off of databases for read intensive workloads 
- Helps make your application stateless 
- AWS takes care of OS maintenance / patching, optimizations, setup, configuration, monitoring, failure recovery and backups 
- **Using ElastiCache involves heavy application code changes**![[Screenshot 2025-02-28 182022.png]]
## Cache Security
- ElastiCache supports IAM Authentication for Redis 
- IAM policies on ElastiCache are only used for AWS API-level security 
- Redis AUTH 
	- You can set a “password/token” when you create a Redis cluster 
	- This is an extra level of security for your cache (on top of security groups) 
	- Support SSL in flight encryption 
- Memcached 
	- Supports SASL-based authentication (advanced)

## Loading patterns
- lazy (all read data is cached, but can become stale)
- write through (adds or updates to the db are mirrored in the cache)
- session store (expire data with time to live)
### Redis Use Case 
- Gaming Leaderboards are computationally complex 
- Redis Sorted sets guarantee both uniqueness and element ordering 
- Each time a new element added, it’s ranked in real time, then added in correct orde