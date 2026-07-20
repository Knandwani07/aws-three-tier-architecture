# 🖼️ Images & Screenshots

This folder contains screenshots captured throughout the implementation of the **AWS Three-Tier Architecture** project. Each document provides a visual representation of an AWS resource or service along with a brief explanation of its role within the three-tier architecture.

These screenshots serve as evidence of the successful deployment, configuration, verification, and testing of the infrastructure while demonstrating AWS networking, security, and application deployment best practices.

---

## 📂 Contents

| File | Description |
|------|-------------|
| `vpc.md` | Custom Amazon VPC with public and private subnets across two Availability Zones. |
| `subnets.md` | Public and private subnet configuration used to separate application layers. |
| `security-groups.md` | Security Groups implementing least-privilege communication between the ALB, EC2 instance, and RDS database. |
| `iam-role.md` | IAM role attached to the EC2 instance for secure access to Amazon S3. |
| `ec2-instance.md` | Private Amazon EC2 application server hosting the web application. |
| `db-subnet-group.md` | Database subnet group containing private subnets for Amazon RDS deployment. |
| `rds-database.md` | Amazon RDS MySQL database deployed securely within private subnets. |
| `ec2-instance-connect-endpoint.md` | EC2 Instance Connect Endpoint providing secure administrative access to the private EC2 instance. |
| `s3-gateway-endpoint.md` | Amazon S3 Gateway VPC Endpoint enabling private S3 connectivity without a NAT Gateway. |
| `target-group.md` | Application Load Balancer target group configured to forward traffic to the EC2 instance. |
| `application-load-balancer.md` | Internet-facing Application Load Balancer distributing incoming HTTP traffic. |
| `target-health.md` | Healthy target status confirming successful communication between the ALB and EC2 instance. |
| `application-output.md` | Browser output confirming successful deployment and accessibility of the web application. |

---

## 🎯 Purpose

The screenshots in this folder help demonstrate:

- Deployment of AWS networking components
- Secure VPC and subnet configuration
- Layered security using Security Groups
- IAM Role configuration
- Private EC2 application deployment
- Secure Amazon RDS database deployment
- EC2 Instance Connect Endpoint configuration
- Private Amazon S3 access through a Gateway VPC Endpoint
- Application Load Balancer configuration
- Successful application deployment and verification

Together, these images provide a visual walkthrough of the complete AWS Three-Tier Architecture, showcasing networking, security, application deployment, and infrastructure validation using AWS best practices.
