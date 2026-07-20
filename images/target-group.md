## 🎯 Target Group

<p align="center">
  <img width="1456" height="583" alt="image" src="https://github.com/user-attachments/assets/30e024e7-6895-4765-9418-a1855dbab062" />
</p>

Displays the **Application Load Balancer Target Group (`three-tier-tg`)** configured to route incoming HTTP requests to the Amazon EC2 application server within the custom VPC.

### Key Highlights

- Registers the **EC2 application server** as the target for incoming HTTP traffic on **Port 80**.
- Performs continuous health checks to ensure requests are routed only to healthy application instances.
- Acts as the bridge between the **Application Load Balancer (ALB)** and the private application tier, enabling reliable traffic distribution.
