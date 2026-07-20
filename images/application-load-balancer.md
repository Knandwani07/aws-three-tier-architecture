## ⚖️ Application Load Balancer

<p align="center">
 <img width="1456" height="562" alt="image" src="https://github.com/user-attachments/assets/afd0882d-ae64-4bf8-9cc7-15038324dccf" />
</p>

Displays the **Application Load Balancer (`three-tier-alb`)** deployed across public subnets, serving as the internet-facing entry point for the three-tier architecture.

### Key Highlights

- Receives incoming **HTTP requests** from users and distributes traffic to the EC2 application server.
- Deployed across **multiple Availability Zones** to improve application availability and fault tolerance.
- Integrates with the **Target Group** to route requests only to healthy application instances, ensuring reliable application access.

