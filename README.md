# 🚀 React Vite CI/CD Pipeline on Amazon EKS using Jenkins

> End-to-End DevOps Project demonstrating Continuous Integration and Continuous Deployment (CI/CD) using Jenkins, Docker, Amazon ECR, and Amazon EKS.

---

## 📖 Project Overview

This project demonstrates how to automate the deployment of a React Vite application using a complete CI/CD pipeline.

Whenever a developer pushes code to GitHub, Jenkins automatically:

- Checks out the latest source code
- Installs project dependencies
- Builds the React application
- Builds a Docker image
- Pushes the Docker image to Amazon ECR
- Deploys the latest version to Amazon EKS
- Performs a rolling update with zero downtime

The entire deployment process is fully automated without manual intervention.

---

# 🏗️ Architecture

```
                Developer
                    │
             git push (GitHub)
                    │
                    ▼
          GitHub Repository
                    │
          GitHub Webhook Trigger
                    │
                    ▼
            Jenkins (EC2)
                    │
      ┌─────────────┼──────────────┐
      │             │              │
      ▼             ▼              ▼
 Checkout      Build React     Build Docker
                    │
                    ▼
          Push Image to Amazon ECR
                    │
                    ▼
          Deploy to Amazon EKS
                    │
                    ▼
        Kubernetes Deployment
                    │
                    ▼
         Kubernetes Service (ELB)
                    │
                    ▼
          React Application Live
```

---

# ⚙️ Tech Stack

## Cloud

- Amazon EC2
- Amazon EKS
- Amazon ECR
- AWS IAM

## DevOps

- Jenkins
- Docker
- Kubernetes
- Git
- GitHub
- AWS CLI
- kubectl
- eksctl

## Frontend

- React
- Vite
- Node.js

---

# 📂 Project Structure

```
react-vite-app/
│
├── src/
├── public/
├── Dockerfile
├── .dockerignore
├── deployment.yaml
├── service.yaml
├── Jenkinsfile
├── package.json
├── vite.config.js
└── README.md
```

---

# 🔄 CI/CD Workflow

The Jenkins Pipeline consists of the following stages:

### 1️⃣ Checkout Source Code

Jenkins pulls the latest source code from GitHub.

---

### 2️⃣ Install Dependencies

```
npm install
```

---

### 3️⃣ Build React Application

```
npm run build
```

---

### 4️⃣ Build Docker Image

```
docker build -t react-vite-app:latest .
```

---

### 5️⃣ Push Image to Amazon ECR

- Authenticate with Amazon ECR
- Tag Docker image
- Push latest image

---

### 6️⃣ Deploy to Amazon EKS

```
kubectl rollout restart deployment/react-vite-app
```

---

### 7️⃣ Verify Deployment

```
kubectl rollout status deployment/react-vite-app
```

---

# ☁️ AWS Services Used

- EC2
- EKS
- ECR
- IAM
- Elastic Load Balancer (ELB)

---

# 🔐 Authentication

## GitHub

GitHub Personal Access Token

## AWS

IAM Role attached to the Jenkins EC2 instance

No AWS Access Keys are stored inside Jenkins.

---

# 📦 Docker

Docker image is automatically built and pushed to Amazon ECR on every successful build.

---

# ☸️ Kubernetes

Resources used:

- Deployment
- Service (LoadBalancer)

Features:

- Rolling Updates
- Zero Downtime Deployment
- Multiple Replicas

---

# 🤖 Jenkins Automation

The pipeline is automatically triggered whenever code is pushed to GitHub using GitHub Webhooks.

Workflow:

```
Git Push
      │
      ▼
GitHub Webhook
      │
      ▼
 Jenkins Pipeline
      │
      ▼
 Docker Build
      │
      ▼
 Push to ECR
      │
      ▼
 Deploy to EKS
```

---

# 📸 Project Screenshots

Include screenshots of:

- Jenkins Dashboard
- Successful Pipeline
- Amazon EC2
- Amazon EKS Cluster
- Amazon ECR Repository
- Running Pods
- Deployment
- Kubernetes Service
- Application Running in Browser

---

# 🎯 Key Features

- Fully Automated CI/CD Pipeline
- GitHub Webhook Integration
- Dockerized React Application
- Amazon ECR Integration
- Amazon EKS Deployment
- Rolling Updates
- Zero Downtime Deployment
- Infrastructure hosted on AWS
- Secure IAM Role Authentication

---

# 📚 Learning Outcomes

Through this project, I gained practical experience with:

- Jenkins Pipelines
- Docker
- Kubernetes
- Amazon EKS
- Amazon ECR
- AWS IAM Roles
- GitHub Webhooks
- CI/CD Best Practices
- Rolling Deployments
- DevOps Automation

---

# 🚀 Future Improvements

- HTTPS using Nginx Reverse Proxy
- Kubernetes Ingress
- Helm Charts
- Jenkins Shared Libraries
- Slack Notifications
- Prometheus & Grafana Monitoring
- ArgoCD for GitOps
- SonarQube Integration
- Trivy Security Scanning

---

# 👨‍💻 Author

**Chetan Prasad Sahoo**

B.Tech Computer Science & Engineering

Silicon University, Bhubaneswar

---

# ⭐ If you found this project useful, feel free to star the repository!
