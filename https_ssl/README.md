# HTTPS/SSL Setup with HAProxy  
This project focuses on configuring HTTPS/SSL using HAProxy, setting up domain subdomains, and enforcing secure web traffic.  
## Features
- [x] Configure domain zones and subdomains for easier management.  
- [x] Set up SSL termination on HAProxy to handle encrypted traffic.  
- [x] Enforce HTTPS traffic to ensure secure communication.  
## 1. Configuring Subdomains
We configure the domain zone so that the subdomain `www` points to the load balancer IP (`lb-01`). Additional subdomains are added to facilitate easier access.

### Bash Script for Subdomain Information
A Bash script is required to audit domain and subdomain information. The script accepts two arguments:
- **domain** (mandatory): The domain name to audit.
- **subdomain** (optional): A specific subdomain to audit.

**Output Format:**
```
The subdomain [SUB_DOMAIN] is a [RECORD_TYPE] record and points to [DESTINATION]
```
- If only the domain is provided, the script will return information for the subdomains `www`, `lb-01`, `web-01`, and `web-02` in this order.
- If both domain and subdomain are provided, it will return information for the specified subdomain.

## 2. HAProxy SSL Termination
SSL termination allows HAProxy to handle encrypted traffic, decrypt it, and pass it to backend servers. A certificate is generated using Certbot to secure the connection.

## 3. Enforcing HTTPS Traffic
To ensure all traffic is securely transmitted, HAProxy is configured to automatically redirect HTTP traffic to HTTPS using a **301 redirect**.
