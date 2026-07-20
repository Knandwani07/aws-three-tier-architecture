## 🛡️ Security Groups

## Application Load Balancer Security Group (`alb-sg`)

- Allows inbound **HTTP (Port 80)** traffic from anywhere (`0.0.0.0/0`).
- Acts as the public entry point for incoming client requests.
- Forwards traffic securely to the EC2 application server.
<p align="center">
  <img width="1456" height="545" alt="image" src="https://github.com/user-attachments/assets/458524ed-6350-4753-8d1c-92a58289e881" />
</p>

---

## Application Security Group (`app-sg`)

- Allows **HTTP (Port 80)** traffic only from the **Application Load Balancer (`alb-sg`)**.
- Prevents direct access to the EC2 instance from the internet.
- Communicates securely with the Amazon RDS database through the database security group.
  
<p align="center">
  <img width="1456" height="565" alt="image" src="https://github.com/user-attachments/assets/074e672f-8f07-429e-9c82-52c7fd1bb072" />
</p>

---

## Database Security Group (`db-sg`)

- Allows **MySQL (Port 3306)** traffic only from the **Application Security Group (`app-sg`)**.
- Prevents direct database access from the internet or other resources.
- Secures the Amazon RDS MySQL database using least-privilege network access.

<p align="center">
  <img width="1456" height="548" alt="image" src="https://github.com/user-attachments/assets/00421806-5291-4ca8-951d-db515ec8d3fd" />
</p>
