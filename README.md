# Building a Secure Three-Tier Architecture on AWS 🛡️

## 📖 About this Project

The **AWS Three-Tier Architecture** is a production-style cloud infrastructure project that demonstrates how to build a secure, scalable, and highly available web application using core AWS services. The architecture follows the industry-standard three-tier design pattern by separating the presentation, application, and database layers, enabling improved security, fault isolation, and maintainability.

The infrastructure is built on a custom Amazon VPC with public and private subnets spanning multiple Availability Zones. An internet-facing Application Load Balancer (ALB) routes incoming traffic to a private Amazon EC2 application server, while application data is securely stored in a private Amazon RDS MySQL database. To strengthen security, the project implements least-privilege Security Groups, IAM Roles, EC2 Instance Connect Endpoint for secure administrative access, and an Amazon S3 Gateway VPC Endpoint for private access to Amazon S3 without requiring a NAT Gateway.

This project demonstrates real-world AWS networking principles and serves as a strong foundation for deploying production-ready cloud applications while following AWS architectural and security best practices.

---

## 🎯 Project Objectives

- Design and deploy a production-style AWS three-tier architecture.
- Create a custom Amazon VPC with public and private subnets.
- Configure secure networking using Route Tables and an Internet Gateway.
- Deploy an internet-facing Application Load Balancer.
- Launch a private Amazon EC2 application server.
- Deploy an Amazon RDS MySQL database in private subnets.
- Configure least-privilege Security Groups between infrastructure layers.
- Implement IAM Roles for secure AWS service access.
- Enable secure administration using EC2 Instance Connect Endpoint.
- Provide private Amazon S3 connectivity through a Gateway VPC Endpoint.
- Demonstrate AWS networking, security, and infrastructure best practices.

---

## 🛠️ Technologies Used

| Service | Purpose |
|----------|---------|
| Amazon VPC | Network isolation |
| Public & Private Subnets | Multi-tier network architecture |
| Internet Gateway | Internet connectivity |
| Route Tables | Traffic routing |
| Application Load Balancer (ALB) | Load balancing |
| Amazon EC2 | Application hosting |
| Amazon RDS (MySQL) | Managed relational database |
| Security Groups | Layered network security |
| IAM Roles | Secure AWS permissions |
| EC2 Instance Connect Endpoint | Secure access to private EC2 instances |
| Amazon S3 Gateway VPC Endpoint | Private S3 connectivity |
| Apache HTTP Server | Web server |
| Amazon Linux 2023 | EC2 operating system |

---

## 📂 Project Structure

```text
aws-three-tier-architecture/
│
├── architecture/
│   ├── architecture-diagram.png
│   ├── architecture-overview.md
│   └── README.md
│
├── docs/
│   ├── deployment-guide.md
│   ├── execution-workflow.md
│   ├── cleanup-guide.md
│   └── README.md
│
├── scripts/
│   ├── install-apache.sh
│   ├── sample-index.html
│   └── README.md
│
├── images/
│   ├── README.md
│   ├── vpc.png
│   ├── subnets.png
│   ├── security-groups.png
│   ├── iam-role.png
│   ├── ec2-instance.png
│   ├── rds-database.png
│   ├── db-subnet-group.png
│   ├── ec2-instance-connect-endpoint.png
│   ├── s3-gateway-endpoint.png
│   ├── application-load-balancer.png
│   ├── target-group.png
│   ├── target-health.png
│   └── application-output.png
│
├── .gitignore
├── LICENSE
└── README.md
```

---

## 📋 Prerequisites

Before deploying this project, ensure you have:

- An AWS account with permissions to create AWS resources such as VPCs, EC2 instances, RDS databases, IAM roles, and load balancers.
- A basic understanding of AWS networking concepts, including VPCs, subnets, and routing.
- Familiarity with the AWS Management Console and basic Linux commands.

---

## 📚 Concepts Covered

This project demonstrates practical implementation of the following AWS concepts:

- Three-Tier Architecture
- Least Privilege Access
- Private Infrastructure Design
- Production-Style AWS Networking
- Secure Application Deployment
- Cost Optimization Without NAT Gateway
- AWS Well-Architected Best Practices

---

## 🤝 Let's Connect

- 💼 **LinkedIn:** https://www.linkedin.com/in/khushi-nandwani/
- 💻 **GitHub:** https://github.com/Knandwani07
- 📬 **Substack:** https://substack.com/@knandwani07
- ✍️ **Dev Community:** https://dev.to/khushi_nandwani07
- 📝 **Medium:** https://medium.com/@khushinandwanii
- 🌐 **Portfolio:** https://main.d1n4wt6uo5bfx6.amplifyapp.com/

---

⭐ **If you found this project helpful, consider giving it a star!**


---
