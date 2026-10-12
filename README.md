# AWS-Secure-Cloud-Architecture
# Secure Two-Tier AWS Cloud Architecture

## Objective
Designed and deployed a custom AWS Virtual Private Cloud (VPC) implementing the principle of least privilege. The architecture physically isolates public-facing web resources from backend data vaults to prevent unauthorized internet access and external scanning.

## Architecture Overview
* **Tier 1 (Public Subnet):** Amazon EC2 Web Server accessible via the internet for frontend user traffic.
* **Tier 2 (Private Subnet):** Amazon RDS MySQL Database completely isolated from the internet, acting as a secure data vault.

## Security Implementation
* Deployed custom AWS Security Groups acting as virtual firewalls at the instance level.
* Configured the database firewall (`DB-SG-Secure`) to reject all external internet traffic.
* Created a strict inbound rule allowing port 3306 (MySQL) traffic *only* if it originates directly from the exact Security Group attached to the EC2 Web Server (`Web-Server-SG`).

## Proof of Concept
The screenshot below demonstrates a successful "jump box" test. I securely connected to the public web server, and from the internal command line of that server, successfully queried the private database endpoint. This proves the internal subnet routing and custom Security Group rules are functioning perfectly together.

![Database Connection Proof]
