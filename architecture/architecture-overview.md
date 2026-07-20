# 🏛️ Architecture Overview

<img width="2048" height="1152" alt="Architetural-diagram" src="https://github.com/user-attachments/assets/bd2ecdec-cddc-4b84-a67d-5abad54531c9" />


The architecture implements a **secure, production-style three-tier web application** on AWS by separating the infrastructure into **presentation**, **application**, and **database** tiers. Each tier is isolated using Amazon VPC networking and Security Groups, ensuring that every component communicates only with the resources it requires.

The solution is deployed inside a custom **Amazon VPC (10.0.0.0/16)** spanning **two Availability Zones** for improved availability. Public subnets host the internet-facing **Application Load Balancer (ALB)**, while private subnets host the **Amazon EC2 application server** and the **Amazon RDS MySQL database**, preventing direct internet access to critical resources.

The **Application Load Balancer** receives incoming HTTP requests from users through the **Internet Gateway** and forwards traffic to the private EC2 application server. The application server processes client requests and securely communicates with the private Amazon RDS MySQL database to store and retrieve application data.

To maintain a secure environment, the architecture uses **Security Groups** with least-privilege access:

- **alb-sg** allows HTTP traffic from the internet to the Application Load Balancer.
- **app-sg** allows HTTP traffic only from the ALB and SSH access only through the EC2 Instance Connect Endpoint.
- **db-sg** allows MySQL traffic only from the application server.

Administrative access is provided through an **EC2 Instance Connect Endpoint**, enabling secure connectivity to the private EC2 instance without assigning a public IP address or deploying a bastion host.

The application server accesses Amazon S3 privately using an **Amazon S3 Gateway VPC Endpoint**, eliminating the need for a NAT Gateway while reducing infrastructure costs and keeping traffic within the AWS network.

---

## 🏗️ Architecture Components

### 🌐 Amazon VPC

Provides an isolated networking environment using the CIDR block **10.0.0.0/16**, hosting all infrastructure components.

### 🌍 Availability Zones

The architecture spans **two Availability Zones (AZ1 and AZ2)** to improve resilience and follow AWS high-availability design principles.

### 📡 Public Subnets

Two public subnets host the **Application Load Balancer**, allowing inbound internet traffic while keeping backend resources private.

### 🔒 Private Subnets

Two private subnets host the **EC2 application server** and **Amazon RDS MySQL database**, preventing direct internet exposure.

### 🌐 Internet Gateway (IGW)

Enables internet connectivity for the public subnets, allowing users to reach the Application Load Balancer.

### ⚖️ Application Load Balancer (ALB)

Distributes incoming HTTP requests to the application server, acting as the public entry point for the application.

### 💻 Amazon EC2 Application Server

Runs the Apache web server and application logic inside a private subnet without a public IP address.

### 🗄️ Amazon RDS MySQL

Provides a managed relational database hosted in private subnets, accessible only from the application tier.

### 🔑 EC2 Instance Connect Endpoint

Enables secure administrative access to the private EC2 instance without exposing SSH to the public internet.

### 🪣 Amazon S3 Gateway VPC Endpoint

Allows private connectivity from the EC2 instance to Amazon S3 without requiring a NAT Gateway or internet access.

### 🛡️ Security Groups

Implement layered network security by allowing communication only between the required infrastructure components.

### 🗺️ Route Tables

Control network traffic between subnets, the Internet Gateway, and the Amazon S3 Gateway VPC Endpoint.

---

## 🔄 Traffic Flow

1. A user accesses the web application through the internet.
2. The request enters the VPC through the **Internet Gateway (IGW)**.
3. The **Application Load Balancer (ALB)** receives the request in the public subnets.
4. The ALB forwards the request to the **private EC2 application server**.
5. The application server processes the request and communicates with the **Amazon RDS MySQL database**.
6. The database returns the requested data to the application server.
7. The application server sends the response back through the ALB to the user.
8. When required, the EC2 instance securely accesses Amazon S3 through the **Gateway VPC Endpoint** without traversing the public internet.

---

## 🔒 Security Highlights

- Internet access is restricted to the **Application Load Balancer** only.
- The **EC2 application server** is deployed without a public IP address.
- The **Amazon RDS database** resides entirely within private subnets.
- Security Groups enforce **least-privilege** communication between application layers.
- Administrative access is provided exclusively through the **EC2 Instance Connect Endpoint**.
- Amazon S3 is accessed privately using a **Gateway VPC Endpoint**, removing the need for a NAT Gateway.
- The architecture follows AWS networking and security best practices by isolating workloads and minimizing the attack surface.
