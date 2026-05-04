# 🚀 Blue-Green Deployment using DevOps Tools

---
## 📌 Project Overview
This project demonstrates the implementation of a **Blue-Green Deployment strategy** using modern DevOps tools on a cloud-based infrastructure.

The setup was deployed on an AWS EC2 instance using:
- Docker
- Kubernetes (Minikube)
- Git & GitHub

---

## 🎯 Objective
To implement a **zero-downtime deployment strategy** where:
- **Blue Environment** → Current live version
- **Green Environment** → New version
- Traffic can be switched seamlessly between versions

---

## 🧠 Architecture
User → NodePort Service → Kubernetes Cluster (Minikube)
↓
Blue / Green Pods


---

## 🛠️ Tools & Technologies Used

- ☁️ AWS EC2 (Ubuntu 24.04)
- 🐳 Docker
- ☸️ Kubernetes (Minikube)
- 🔧 kubectl
- 🧾 YAML (Deployment & Service configs)
- 🧑‍💻 Git & GitHub

---

## 📂 Project Structure
bluegreen/
│── deployment-blue.yaml
│── service.yaml
│── Dockerfile
│── index.html


---

## ⚙️ Implementation Steps

### 1. Launch EC2 Instance
- Ubuntu 24.04 instance on AWS
- Configure security groups (ports 22, 80, 30000–32767)

---

### 2. Setup Kubernetes Cluster
```bash
minikube start --driver=docker
kubectl get nodes
```
### 3. Deploy Blue Version
```bash
kubectl apply -f deployment-blue.yaml
kubectl get pods
```

### 4. Expose Service
```bash
kubectl apply -f service.yaml
kubectl get svc
```

### Service runs on:

```bash
http://<EC2-Public-IP>:30007
```
---

### 🔁 Blue-Green Deployment Concept
# Environment  	Description
Blue          	Current running version
Green          	New version to be deployed
Switch        	Update service to point to Green

---

### 📊 Verification
```bash
kubectl get pods
kubectl get svc
kubectl describe service myapp-service
```

---

### ⚠️ Challenges Faced
Minikube memory constraints on EC2
Docker disk space warnings
NodePort not accessible initially (network/security configs)
Git nested repository issue during upload

---

### ✅ Outcome
Successfully deployed application using Kubernetes
Implemented Blue-Green deployment strategy
Verified service exposure via NodePort
Uploaded project to GitHub

---

### 📌 Future Improvements
Add Green deployment YAML
Automate deployment using Jenkins CI/CD
Use LoadBalancer instead of NodePort
Integrate monitoring (Prometheus + Grafana)
