# Assignment: Redis Helm Chart & Terraform EKS Cluster

This document provides the necessary steps to deploy a **Redis Cluster using Helm** and an **EKS Cluster using Terraform**.

---

## Table of Contents
- [Prerequisites](#prerequisites)
- [Part 1: Redis Helm Chart](#part-1-redis-helm-chart)
  - [Step 1: Install Dependencies](#step-1-install-dependencies)
  - [Step 2: Create the Helm Chart](#step-2-create-the-helm-chart)
  - [Step 3: Configure the Helm Chart](#step-3-configure-the-helm-chart)
  - [Step 4: Package and Deploy the Chart](#step-4-package-and-deploy-the-chart)
- [Part 2: Terraform EKS Cluster](#part-2-terraform-eks-cluster)
  - [Step 1: Install Terraform & AWS CLI](#step-1-install-terraform--aws-cli)
  - [Step 2: Create Terraform Files](#step-2-create-terraform-files)
  - [Step 3: Initialize and Deploy with Terraform](#step-3-initialize-and-deploy-with-terraform)
- [Packaging & Submission](#packaging--submission)
- [Notes](#notes)

---

## Prerequisites

Ensure the following tools are installed:
- Ubuntu 20.04+
- Helm 3
- Kubectl
- Terraform (v1.x)
- AWS CLI v2
- A Kubernetes cluster (Minikube, Kind, or AWS EKS)
- AWS credentials with permissions to create VPCs, subnets, IAM roles, and EKS clusters

---

## Part 1: Redis Helm Chart

### Step 1: Install Dependencies

```bash
# Update system
sudo apt update && sudo apt install -y unzip curl wget

# Install Helm 3
curl -fsSL https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

# Install kubectl
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/

# Verify installations
helm version
kubectl version --client
```

### Step 2: Create the Helm Chart
1. Create a new Helm chart for Redis.
2. Set up a `values.yaml` file to define Redis configurations.

### Step 3: Configure the Helm Chart
1. Enable Redis clustering.
2. Configure replication and persistence.
3. Define Kubernetes services, StatefulSets.

### Step 4: Package and Deploy the Chart
1. Package the Helm chart.
2. Deploy Redis using `helm install`.
3. Verify the Redis cluster status.

---

## Part 2: Terraform EKS Cluster

### Step 1: Install Terraform & AWS CLI
1. Install Terraform and AWS CLI.
```
# Install Terraform
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
sudo apt update && sudo apt install terraform -y

# Install AWS CLI
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install

# Verify installation
terraform -v
aws --version
```
2. Configure AWS credentials.
   
### Step 2: Create Terraform Files
1. Define a `main.tf` file to provision EKS.
2. Create VPC, subnets, IAM roles, and security groups.
3. Define worker nodes and cluster configurations.

### Step 3: Initialize and Deploy with Terraform
1. Run `terraform init` to initialize.
2. Run `terraform plan` to check the execution plan.
3. Run `terraform apply` to deploy the EKS cluster.
4. Verify the EKS cluster using `kubectl`.

---

## Packaging & Submission

- **Redis Helm Chart:** Package and submit as a `.tar` file.
- **Terraform EKS Cluster:** Submit Terraform scripts as a file.(Cannot upload the tar file because it is too big.)

---

