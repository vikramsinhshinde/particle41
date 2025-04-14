# 🛠️ Particle41 DevOps Challenge

This project is a minimal Flask-based web application deployed using AWS ECS with Terraform. It returns the server's public IP and a timestamp.

## ✅ Challenge Objectives

- Develop a simple web app that returns a timestamp and IP.
- Containerize it using Docker.
- Deploy it to AWS using ECS (Fargate).
- Use Terraform for infrastructure provisioning.
- Optional: Add a CI/CD pipeline and HTTPS support.

---

## 🚀 Tech Stack

- Python + Flask
- Docker
- AWS (ECS, ECR, IAM, VPC)
- Terraform
- (Optional: GitHub Actions for CI/CD)

---

## 📦 Application Overview

**Endpoint:**

```bash
curl http://<PUBLIC-IP>:5000
# particle41

Sample Output:

json
Copy
Edit
{
  "ip": "3.7.248.**",
  "timestamp": "2025-04-14T13:14:28.209162"
}
🧱 Project Structure
bash
Copy
Edit
.
├── app/
│   └── app.py                  # Flask app
├── Dockerfile                  # Docker image definition
├── infra/
│   └── main.tf                 # Terraform file to deploy AWS infrastructure
├── .gitignore
└── README.md                   # You're here!
🐳 Docker Instructions
1. Build & Push to ECR
bash
Copy
Edit
docker build -t simpletimeservice .
aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin <aws_account_id>.dkr.ecr.ap-south-1.amazonaws.com
docker tag simpletimeservice:latest <aws_account_id>.dkr.ecr.ap-south-1.amazonaws.com/simpletimeservice
docker push <aws_account_id>.dkr.ecr.ap-south-1.amazonaws.com/simpletimeservice
⚙️ Terraform Instructions
1. Initialize Terraform
bash
Copy
Edit
cd infra
terraform init
2. Apply Infrastructure
bash
Copy
Edit
terraform apply
This will:

Create an ECS cluster

Define the ECS task and service

Set up IAM roles and ECR

Run the Docker container on Fargate

🌐 Accessing the App
After terraform apply, get the public IP of the Fargate container (or EC2 if used) and access it:

bash
Copy
Edit
curl http://<public-ip>:5000
🔐 Optional Improvements
 Attach Application Load Balancer (ALB)

 Register domain with Route53

 Enable HTTPS via AWS ACM

 Configure CI/CD via GitHub Actions

 Set up CloudWatch logging and alerts

🧹 Cleanup
To destroy all resources:

bash
Copy
Edit
terraform destroy
👨‍💻 Author
Vikramsinh Shinde
DevOps & Cloud Architect
LinkedIn |


