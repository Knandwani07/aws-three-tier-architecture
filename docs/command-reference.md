# 💻 Commands Reference

This document contains the AWS CLI and Linux commands used throughout the deployment and verification of the **AWS Three-Tier Architecture** project, along with a brief explanation of each command.

---

## 📦 Install Apache HTTP Server

```bash
sudo dnf install -y httpd
```

Installs the Apache HTTP Server on the Amazon EC2 instance.

---

## ▶️ Enable Apache Service

```bash
sudo systemctl enable httpd
```

Configures Apache to start automatically whenever the EC2 instance boots.

---

## 🚀 Start Apache Service

```bash
sudo systemctl start httpd
```

Starts the Apache web server.

---

## 📊 Check Apache Service Status

```bash
sudo systemctl status httpd
```

Displays the current status of the Apache service.

---

## 🌐 Create the Default Web Page

```bash
echo "<h1>Three-Tier AWS Architecture</h1>" | sudo tee /var/www/html/index.html
```

Creates a simple HTML page that is served by Apache.

---

## 🔍 Verify AWS CLI Installation

```bash
aws --version
```

Displays the installed AWS CLI version.

---

## 🪣 Verify Amazon S3 Connectivity

```bash
aws s3 ls
```

Lists accessible Amazon S3 buckets to verify private connectivity through the Gateway VPC Endpoint.

---

## 🗄️ Install MySQL Client

```bash
sudo dnf install -y mariadb105
```

Installs the MySQL/MariaDB client required to connect to the Amazon RDS database.

---

## 🔗 Connect to Amazon RDS

```bash
mysql -h <RDS-ENDPOINT> -u admin -p
```

Connects securely to the Amazon RDS MySQL database.

---

## 🧹 Stop Apache Service

```bash
sudo systemctl stop httpd
```

Stops the Apache web server.

---

## 🔄 Restart Apache Service

```bash
sudo systemctl restart httpd
```

Restarts the Apache service after configuration or content changes.

---

## 📌 Reload Apache Configuration

```bash
sudo systemctl reload httpd
```

Reloads the Apache configuration without restarting the service.
