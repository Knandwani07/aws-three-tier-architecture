## 💻 Amazon EC2 Instance

<p align="center">
  <img width="1456" height="236" alt="image" src="https://github.com/user-attachments/assets/569ef911-e12f-46ee-9f1b-582963a5f781" />

</p>

Displays the **Amazon EC2 application server (`three-tier-app-server`)** running in a private subnet, hosting the web application within the three-tier architecture.

### Key Highlights

- Hosts the application on an **Amazon Linux 2023** `t3.micro` instance inside a private subnet.
- Configured without a public IP address, ensuring the application server is not directly accessible from the internet.
- Serves application traffic received from the **Application Load Balancer (ALB)** while communicating securely with the Amazon RDS database.
