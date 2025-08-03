# 🚀 CI/CD Pipeline for Maven Java App on AWS

## 📌 Overview

This project demonstrates a complete **CI/CD pipeline** built on AWS for a **Java Maven application** using **Corretto 8**. The process automates building, packaging, and deploying the app from a developer EC2 instance to a production EC2 instance, with infrastructure managed via **CloudFormation (IaC)**.

---

## 🧱 Architecture Summary

### 🔧 Dev Tools & Services
- **Java 8 (Corretto)**, **Maven**
- **Git**, **GitHub PAT for push access**

### ☁️ AWS Services Used
- **EC2 (Dev & Prod)**: Dev for setup and build; Prod for deployment (ARM template)
- **IAM**: Roles for EC2 and CodeArtifact
- **CodeArtifact**: Maven repository
- **S3**: Stores built artifacts
- **CodeBuild**: Builds and pushes artifact to S3
- **CodeDeploy**: Deploys app to Prod EC2
- **CloudFormation**: Scans and defines infra as IaC

---

## 🔄 Pipeline Flow

1. ✅ Launch EC2 Dev instance
   - SSH access, install Git, Java 8 Corretto, and Maven
   - Clone project, modify `index.jsp`, initialize GitHub connection (via PAT)
   - Push code to GitHub

2. 📦 Configure CodeArtifact
   - Setup Maven settings
   - Build project and push to CodeArtifact/S3

3. 🏗️ Setup Production Environment
   - Use ARM template to provision EC2 Prod + networking (VPC, subnets, security groups)
   - Assign IAM role for deployment

4. ⚙️ Configure CI/CD
   - **CodeBuild**: Pulls from GitHub, builds, uploads to S3
   - **CodeDeploy**: Deploys to Prod EC2 on trigger

5. 📜 Infrastructure as Code
   - Scan with CloudFormation to generate a full template of the architecture

---

## 🗂️ Project Highlights

| Stage       | Tool / Service             |
|-------------|----------------------------|
| Development | EC2 (Dev), GitHub, Maven, Java |
| Build       | CodeArtifact, CodeBuild, S3 |
| Deploy      | EC2 (Prod), CodeDeploy     |
| IaC         | CloudFormation (generated) |

---

## 🧪 Result

After pushing to GitHub, the pipeline:
- Automatically builds the project
- Stores the artifact in S3
- Triggers CodeDeploy to update the Prod EC2
- Final result: `index.jsp` shows _"Welcome to the CI/CD test application"_ on the deployed app

---

## 🖼️ Screenshots

### 🔹 EC2 Dev Instance
![EC2 Dev Instance](screenshots/EC2_dev_instance.png)

---

### 🔹 SSH into EC2
![SSH into EC2](screenshots/SSH_ec2_and_installing.png)

---

### 🔹 Installing Maven and Java
![Installing Maven and Java](screenshots/intalling_mvn_and_java.png)

---

### 🔹 Maven and Java installed
![Lambda Console](screenshots/mvn_java_installed.png)

---

### 🔹 Generating Maven Project
![API Lambda Integration](screenshots/generating_mvn_project.png)

---

### 🔹 Maven Build Success
![API Prod Stage](screenshots/mvn_build_success.png)

---

### 🔹 Installing Git
![Lambda Console](screenshots/Installing_git.png)

---

### 🔹 GitHub repo
![Lambda Code](screenshots/github_repo.png)

---

### 🔹 First Git Push
![Lambda Role](screenshots/first_git_push.png)

---

### 🔹 CodeArtifact
![DynamoDB Console](screenshots/CodeArtifact.png)

---

### 🔹 EC2 Connected to CodeArtifact - Project Building
![DynamoDB Console](screenshots/connecting_to_codeartifact_and_building_project.png)

---

### 🔹 Artifact Stored in S3
![DynamoDB Console](screenshots/S3_stored_artifact.png)

---

### 🔹 Prod EC2 Instance
![DynamoDB Console](screenshots/prod_instance.png)

---

### 🔹 CodeBuild Build Succeeded
![DynamoDB Console](screenshots/CodeBuild_succeeded.png)

---

### 🔹 CodeDeploy Deployment Succeeded
![DynamoDB Console](screenshots/Deployment_succeeded.png)

---

### 🔹 App Demo
![DynamoDB Console](screenshots/Deployed_app_success.png)

---

### 🔹 IAM Roles
![DynamoDB Console](screenshots/IAM_roles.png)

---

### 🔹 Role Exemple
![DynamoDB Console](screenshots/role_exemple.png)

---

### 🔹 CloudFormation Template Generation . IaC
![DynamoDB Console](screenshots/Template_generation_IaC.png)

---





## 🧱 IaC Template

 ![The infrastructure was scanned and exported into a CloudFormation template.](devops-app-template.yaml)

---


