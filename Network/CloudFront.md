
# CloudFront
- CDN
- data, videos, application and apis delivery
- global
- regional edge cachhes
- only http based requests

## Origins

### [[S3]]
 - For distributing files and caching them at the edge 
 - Enhanced security with CloudFront Origin Access Control (OAC) 
 - OAC is replacing Origin Access Identity (OAI) 
 - CloudFront can be used as an ingress (to upload files to S3)

### Custom Endpoint
- [[Load Balancer]]
- [[EC2]]
- [[S3]] Website
- Any HTTP backend

## Geo Restirction
- Allowlist countries
- blacklist coutries
- use for copyright laws

## Price Classes
- depends on data transfer, but is diffrent for each edge location
- price goes down if you transfer more data

### All
- all regions - best performance - highest price

### 200
- most regions - exludes most exp

### 100
- only cheapest regions 

## Cache Invalidations
- invalide via api and path

## Customization at Edge
- serverless
- customize a cdn endpoint
- pay per use

### Use cases
- Website security and privacy
- seo
- intelligent route
- bot mitigation
- real time image transform
- a/b testing
- Dynmaic Web Apps at Edge
- User prio
- tracking ad analytics
- user auth 