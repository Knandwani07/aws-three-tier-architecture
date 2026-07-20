# 🧹 Cleanup Guide

After completing the project, delete the AWS resources to avoid unnecessary charges.

## Cleanup Order

1. Delete the **Application Load Balancer**.
2. Delete the **Target Group**.
3. Terminate the **EC2 Application Instance**.
4. Delete the **EC2 Instance Connect Endpoint**.
5. Delete the **Amazon RDS MySQL Database** (disable final snapshot if not required).
6. Delete the **DB Subnet Group**.
7. Delete the **IAM Role** (`three-tier-app-role`).
8. Delete the **Security Groups** (`alb-sg`, `app-sg`, `db-sg`, `three-tier-eic-sg`).
9. Delete the **Amazon S3 Gateway VPC Endpoint**.
10. Detach and delete the **Internet Gateway**.
11. Delete the **Custom VPC** (`three-tier-vpc`).

---

## Note

Always verify that no billable resources remain in your AWS account before ending the project. This helps prevent unexpected charges.
