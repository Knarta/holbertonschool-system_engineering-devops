# Distributed Web Infrastructure Design

## Component Explanations

### 1. Load Balancer (HAProxy)
- **Purpose**: Distributes incoming traffic across multiple servers to ensure high availability and reliability
- **Distribution Algorithm**: Round Robin
  - Works by distributing requests sequentially to each server in the pool
  - Each server gets an equal number of requests
  - Simple and effective for most use cases
- **Active-Active vs Active-Passive**:
  - Active-Active: All servers are running and handling traffic simultaneously
  - Active-Passive: One server handles traffic while others are on standby
  - This setup uses Active-Active for better resource utilization and higher availability

### 2. Web Servers (Nginx)
- **Purpose**: Serves static content and acts as a reverse proxy
- **Benefits**:
  - High performance for static content
  - Efficient handling of concurrent connections
  - SSL termination capability

### 3. Application Servers
- **Purpose**: Runs the application code and handles dynamic content
- **Benefits**:
  - Separation of concerns from web server
  - Better resource management
  - Easier scaling of application logic

### 4. Application Files
- **Purpose**: Contains the website's codebase
- **Benefits**:
  - Centralized code management
  - Easier deployment and updates
  - Version control integration

### 5. Database (MySQL)
- **Primary-Replica Setup**:
  - Primary node handles write operations
  - Replica node handles read operations
  - Automatic replication from Primary to Replica
  - Benefits:
    - Improved read performance
    - Data redundancy
    - Better availability

## Infrastructure Issues

### 1. Single Points of Failure (SPOF)
- Load Balancer: If it fails, the entire system becomes unavailable
- Primary Database: If it fails, write operations are affected
- No backup power supply
- No geographic redundancy

### 2. Security Issues
- No firewall implementation
- No HTTPS/SSL implementation
- No DDoS protection
- No WAF (Web Application Firewall)
- No encryption for data in transit

### 3. Monitoring Issues
- No monitoring system in place
- No alerting system
- No logging system
- No performance metrics collection
- No uptime monitoring

## Recommendations for Improvement

1. **High Availability**:
   - Implement redundant load balancers
   - Add geographic redundancy
   - Implement automatic failover

2. **Security**:
   - Implement SSL/TLS
   - Add WAF
   - Configure firewalls
   - Implement DDoS protection
   - Add encryption for data in transit

3. **Monitoring**:
   - Implement monitoring tools (e.g., Prometheus, Grafana)
   - Set up logging (e.g., ELK Stack)
   - Configure alerting
   - Add performance monitoring
   - Implement uptime monitoring 