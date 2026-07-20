# 🚀 Deployment Guide

This guide walks through the complete deployment of the **AWS Three-Tier Architecture** from creating the networking infrastructure to deploying and testing the application.

---

# Deployment Overview

The deployment consists of the following stages:

1. Create the Amazon VPC
2. Verify the network layout
3. Configure Security Groups
4. Create the IAM Role
5. Launch the Application EC2 Instance
6. Create the DB Subnet Group
7. Deploy the Amazon RDS MySQL Database
8. Create the EC2 Instance Connect Endpoint
9. Configure Secure Administrative Access
10. Verify Amazon S3 Connectivity
11. Verify Amazon RDS Connectivity
12. Deploy the Application Load Balancer
13. Install and Configure the Web Server
14. Verify the Application

---

# Step 1 – Create the Amazon VPC

Create a custom Virtual Private Cloud using the **VPC and More** wizard.

Configuration:

| Setting | Value |
|----------|-------|
| Name | three-tier-vpc |
| IPv4 CIDR | 10.0.0.0/16 |
| Availability Zones | 2 |
| Public Subnets | 2 |
| Private Subnets | 2 |
| NAT Gateway | None |
| VPC Endpoint | Amazon S3 Gateway |

Once configured, create the VPC.

---

# Step 2 – Verify the Network Layout

After the VPC has been created, verify the following resources:

- Two Public Subnets
- Two Private Subnets
- Internet Gateway
- Route Tables
- Amazon S3 Gateway VPC Endpoint

Ensure both public subnets have **Auto-Assign Public IP** enabled.

---

# Step 3 – Configure Security Groups

Create three Security Groups.

## Application Load Balancer Security Group (alb-sg)

Inbound Rules

| Type | Port | Source |
|------|------|--------|
| HTTP | 80 | 0.0.0.0/0 |

---

## Application Server Security Group (app-sg)

Inbound Rules

| Type | Port | Source |
|------|------|--------|
| HTTP | 80 | alb-sg |

---

## Database Security Group (db-sg)

Inbound Rules

| Type | Port | Source |
|------|------|--------|
| MySQL | 3306 | app-sg |

---

# Step 4 – Create the IAM Role

Create an IAM Role for the EC2 instance.

Configuration

| Setting | Value |
|----------|-------|
| Trusted Entity | EC2 |
| Policy | AmazonS3ReadOnlyAccess |
| Role Name | three-tier-app-role |

Attach the role to the application server during launch.

---

# Step 5 – Launch the Application Server

Launch an Amazon EC2 instance.

Configuration

| Setting | Value |
|----------|-------|
| Name | three-tier-app-server |
| AMI | Amazon Linux 2023 |
| Instance Type | t3.micro |
| VPC | three-tier-vpc |
| Subnet | Private Subnet |
| Public IP | Disabled |
| Security Group | app-sg |
| IAM Role | three-tier-app-role |

Launch the instance.

---

# Step 6 – Create the Database Subnet Group

Navigate to **Amazon RDS → Subnet Groups**.

Configuration

| Setting | Value |
|----------|-------|
| Name | three-tier-db-subnet-group |
| VPC | three-tier-vpc |
| Availability Zones | Both AZs |
| Subnets | Both Private Subnets |

Create the subnet group.

---

# Step 7 – Deploy Amazon RDS

Create a MySQL database.

Configuration

| Setting | Value |
|----------|-------|
| Engine | MySQL |
| Template | Free Tier |
| Identifier | three-tier-db |
| Instance Class | db.t3.micro |
| Public Access | No |
| VPC | three-tier-vpc |
| DB Subnet Group | three-tier-db-subnet-group |
| Security Group | db-sg |

Wait until the database becomes **Available**.

---

# Step 8 – Create the EC2 Instance Connect Endpoint

Navigate to

**VPC → Endpoints → Create Endpoint**

Configuration

| Setting | Value |
|----------|-------|
| Service | EC2 Instance Connect Endpoint |
| Name | three-tier-eic-endpoint |
| VPC | three-tier-vpc |
| Subnet | Private Subnet |
| Security Group | three-tier-eic-sg |

Create the endpoint.

---

# Step 9 – Configure Secure Administrative Access

Update **app-sg**.

Add the following inbound rule.

| Type | Port | Source |
|------|------|--------|
| SSH | 22 | three-tier-eic-sg |

This allows administrators to securely connect to the private EC2 instance.

---

# Step 10 – Verify Amazon S3 Connectivity

Connect to the EC2 instance using the EC2 Instance Connect Endpoint.

Verify the AWS CLI.

```bash
aws --version
```

List available S3 buckets.

```bash
aws s3 ls
```

If the command succeeds without a public IP or NAT Gateway, the Gateway VPC Endpoint is functioning correctly.

---

# Step 11 – Verify Amazon RDS Connectivity

Install the MySQL client.

```bash
sudo dnf install mysql105 -y
```

Connect to the database.

```bash
mysql -h <RDS-ENDPOINT> \
-u admin \
-p
```

A successful connection confirms secure communication between the application and database tiers.

---

# Step 12 – Deploy the Application Load Balancer

## Create Target Group

Configuration

| Setting | Value |
|----------|-------|
| Target Type | Instance |
| Name | three-tier-tg |
| Protocol | HTTP |
| Port | 80 |
| VPC | three-tier-vpc |

Register the EC2 application server.

---

## Create Application Load Balancer

Configuration

| Setting | Value |
|----------|-------|
| Name | three-tier-alb |
| Scheme | Internet-facing |
| VPC | three-tier-vpc |
| Public Subnets | Both Public Subnets |
| Security Group | alb-sg |
| Listener | HTTP :80 |
| Target Group | three-tier-tg |

Create the load balancer.

---

# Step 13 – Install the Web Server

Connect to the EC2 instance.

Install Apache.

```bash
sudo dnf install httpd -y
```

Enable Apache.

```bash
sudo systemctl enable httpd
```

Start Apache.

```bash
sudo systemctl start httpd
```

Create a sample web page.

```bash
echo "<h1>AWS Three-Tier Architecture</h1>" | sudo tee /var/www/html/index.html
```

---

# Step 14 – Verify Target Health

Navigate to

**EC2 → Target Groups**

Wait until the application server status changes to

**Healthy**

---

# Step 15 – Verify the Application

Open the DNS name of the Application Load Balancer.

You should see the sample web page:

```text
AWS Three-Tier Architecture
```

This confirms that:

- Internet traffic reaches the Application Load Balancer.
- The ALB forwards requests to the private EC2 instance.
- The application is running successfully.
- The three-tier architecture has been deployed correctly.

---

# Deployment Validation Checklist

-  VPC created successfully
-  Public and Private Subnets configured
-  Internet Gateway attached
-  Route Tables configured
-  Security Groups configured
-  IAM Role attached to EC2
-  Private EC2 instance deployed
-  Amazon RDS database deployed
-  EC2 Instance Connect Endpoint configured
-  Amazon S3 Gateway VPC Endpoint operational
-  Application Load Balancer deployed
-  Target Group healthy
-  Apache web server running
-  Application accessible through the ALB
-  EC2 successfully connected to Amazon RDS
-  EC2 successfully accessed Amazon S3 privately

---

# Deployment Complete 

You have successfully deployed a secure **AWS Three-Tier Architecture** featuring:

- Internet-facing Application Load Balancer
- Private EC2 Application Tier
- Private Amazon RDS MySQL Database
- Secure administrative access using EC2 Instance Connect Endpoint
- Private Amazon S3 connectivity through a Gateway VPC Endpoint
- Layered security using IAM Roles and Security Groups
- Production-style AWS networking following best practices
