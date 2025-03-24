![[Screenshot 2025-03-18 114749.png]]
#### **Edge Location Mitigation (BP1, BP3)**

- **CloudFront & Global Accelerator**: Protects against **DDoS attacks (SYN floods, UDP reflection)** by handling traffic at the edge.
- **Route 53**: Ensures **resilient DNS resolution** with built-in DDoS protection.

#### **Infrastructure Layer Defense**

- **Global Accelerator, Route 53, CloudFront, ELB (BP1, BP3, BP6)**: Distributes traffic to protect EC2 from high loads.
- **Auto Scaling (BP7)**: Adjusts EC2 capacity to handle sudden traffic surges.
- **Elastic Load Balancing (BP6)**: Scales with traffic and balances loads across instances.

#### **Application Layer Defense**

- **CloudFront & AWS WAF (BP1, BP2)**: Filters malicious requests, caches static content, and blocks bad IPs.
- **Shield Advanced (BP1, BP2, BP6)**: **Automated L7 DDoS mitigation**, dynamically deploying WAF rules.

#### **Attack Surface Reduction**

- **Obfuscate Backends (BP1, BP4, BP6)**: Use **CloudFront, API Gateway, ELB** to hide resources like EC2 and Lambda.
- **Security Groups & NACLs (BP5)**: Restrict access at subnet or instance level.
- **Protect API Endpoints (BP4)**: Use **WAF + API Gateway** to enforce rate limits, filter headers, and require API keys.