## 🪣 Amazon S3 Gateway VPC Endpoint Verification

<p align="center">
 <img width="993" height="158" alt="image" src="https://github.com/user-attachments/assets/5462c7c7-9301-48d8-8cd4-8a89012d7734" />

</p>

Displays the successful verification of **private Amazon S3 connectivity** from the EC2 application server using the AWS CLI, confirming that S3 access is available through the **Gateway VPC Endpoint** without requiring a public IP address or NAT Gateway.

### Key Highlights

- Verifies that the **AWS CLI** is installed and configured on the private EC2 instance.
- Successfully executes the `aws s3 ls` command from the private subnet, demonstrating private connectivity to Amazon S3.
- Confirms that the **Gateway VPC Endpoint** enables secure and cost-effective S3 access without routing traffic over the public internet
