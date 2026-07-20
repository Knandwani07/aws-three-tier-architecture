## 🗄️ Amazon RDS MySQL Database

<p align="center">
  <img width="1456" height="272" alt="image" src="https://github.com/user-attachments/assets/06c3e730-bca0-480b-b362-1a2aaf6d8045" />
</p>

Displays the **Amazon RDS MySQL database (`three-tier-db`)** deployed within the private database tier, providing a managed, secure, and highly available relational database for the application.

### Key Highlights

- Runs a **MySQL Community** database on a **db.t3.micro** instance within the custom VPC.
- Deployed in private subnets and protected by the **Database Security Group (`db-sg`)**, preventing direct internet access.
- Stores application data securely while allowing connections only from the **EC2 application server**.
