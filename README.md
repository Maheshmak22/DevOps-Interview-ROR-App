# 🚀 Ruby on Rails Application Deployment on AWS (ECS + Terraform)

This project demonstrates how to deploy a Ruby on Rails application to AWS using Terraform, Docker, GitHub Actions, and ECS Fargate. It includes infrastructure as code, CI/CD, and integrations with RDS and S3.

---

## 📁 Project Structure

DevOps-Interview-ROR-App/
├── terraform/ # Terraform IaC files
├── .github/workflows/ # GitHub Actions CI/CD pipeline
├── README.md # This file

---

## 🧱 AWS Infrastructure (Terraform)

- VPC with public/private subnets
- Application Load Balancer (ALB)
- ECS Cluster + Fargate Service
- RDS PostgreSQL (private subnet)
- S3 Bucket for app storage
- IAM Role for ECS to access S3
- ECR Repository for Docker image

---

## 🔧 GitHub Secrets (for CI/CD)

| Secret Name              | Description                          |
|--------------------------|--------------------------------------|
| `AWS_ACCESS_KEY_ID`      | IAM user's access key                |
| `AWS_SECRET_ACCESS_KEY`  | IAM user's secret                    |
| `AWS_REGION`             | e.g. `ap-south-1`                    |
| `ECR_REPOSITORY`         | Full ECR URI for image push          |

---

## 🚀 Deployment Steps

1. **Clone the repo & switch to deployment branch**
   ```bash
   git clone https://github.com/<your-username>/DevOps-Interview-ROR-App.git
   cd DevOps-Interview-ROR-App
   git checkout ecs-deployment
   
Terraform Deploy:
 cd terraform
 terraform init
 terraform apply 

GitHub Actions CI/CD:

Push code to ecs-deployment branch.

This triggers docker-build.yml to:

Build image from docker/app/Dockerfile

Push to ECR

ECS pulls & deploys

Access Application:

After deployment, get the ALB DNS from Terraform output or AWS Console:
Example Endpoint: http://<alb-dns>.ap-south-1.elb.amazonaws.com


Access Application:
