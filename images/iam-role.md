## 🔐 IAM Role

<p align="center">
  <img width="1456" height="566" alt="image" src="https://github.com/user-attachments/assets/ca2af6c2-29bd-4baa-9fab-6843ce75adaa" />

</p>

Displays the **IAM Role (`three-tier-app-role`)** attached to the Amazon EC2 application server, enabling secure access to AWS services without using long-term access keys.

### Key Highlights

- Grants the EC2 instance secure, temporary AWS credentials through an IAM instance profile.
- Uses the **AmazonS3ReadOnlyAccess** managed policy to allow read-only access to Amazon S3.
- Eliminates the need to store AWS access keys on the EC2 instance, following AWS security best practices.
