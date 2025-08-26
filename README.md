# Creating-EKS-clusters-with-AWS-VPC-using-Terraform

## Introduction
This project provisions a production-ready Amazon EKS cluster inside a well-architected AWS VPC using Terraform. It codifies the full networking and cluster baseline—multi-AZ VPC with public/private subnets and NAT, an EKS control plane, managed node groups, and secure defaults like private API endpoints and IRSA (IAM Roles for Service Accounts). The goal is to give teams a clean, repeatable foundation for running Kubernetes on AWS with sensible trade-offs for cost, security, and reliability.

Why this stack? Terraform keeps your infrastructure versioned and reviewable; EKS removes the toil of managing control-plane components; the VPC layout and tagging strategy make it easy to scale, observe, and control costs across environments (dev/stage/prod).

## Project Layout
<img width="683" height="384" alt="Screenshot 2025-08-25 at 10 43 58 PM" src="https://github.com/user-attachments/assets/e26d888f-1851-47c6-af8f-17738ec943e5" />


## Steps:
### Step 1: Download AWS CLI and Terraform
### Step 2: Use `aws configure` to connect your AWS account with Terraform
### Step 3: Write these Terraform scripts:
main.tf: Terraform entrypoint for EKS + node capacity (and related resources).

provider.tf: Script to set up which providers Terraform should use and how to connect to AWS.

### Step 4: Use the following commands:
`terraform init` →  sets up Terraform in the project by downloading required providers and initializing the working directory.

`terraform plan` → Previews what infrastructure changes Terraform will make on AWS based on your .tf files.

`terraform apply` → Executes those planned changes to actually create or update the AWS infrastructure (like the EKS cluster in this project).

### Step 5: Connect to the EKS Cluster
Run `  aws eks update-kubeconfig --region us-east-1 --name my-cluster-eks` to connect to the EKS cluster.

### Step 6: Check pods and nodes
Check pods using `kubectl get pods`

Check nodes using `kubectl get nodes`

### VPC Mapping:
<img width="1106" height="344" alt="Screenshot 2025-08-25 at 10 46 31 PM" src="https://github.com/user-attachments/assets/3097c4a0-3e14-4038-be93-5a48ea5b024b" />

