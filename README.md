# WordPress + MySQL on Kubernetes

## 📌 Overview

A Kubernetes project that deploys a WordPress application with a MySQL database using **Kind**.

The project demonstrates Kubernetes networking, Services, persistent storage, Pods, labels/selectors, and application-to-database communication.

## 🏗️ Architecture

```text
Browser
   |
   v
WordPress Service
   |
   v
WordPress Pod
   |
   | mysql-service:3306
   v
MySQL Service
   |
   v
MySQL Pod
   |
   v
PVC → PV → Host Storage
```
🛠️ Technologies
Kubernetes
Kind
Docker
kubectl
WordPress
MySQL
📂 Project Structure
wordpress-kubernetes/
├── README.md
├── k8s/
│   ├── mysql-pv.yaml
│   ├── mysql-pvc.yaml
│   ├── mysql-pod.yaml
│   ├── mysql-service.yaml
│   ├── wordpress-pod.yaml
│   └── wordpress-service.yaml
└── screenshots/
🚀 Deployment

Create Kind cluster:

kind create cluster --name devops-cluster

Deploy all Kubernetes resources:

kubectl apply -f k8s/

Check resources:

kubectl get pods
kubectl get svc
kubectl get pv
kubectl get pvc

Check Pod details:

kubectl describe pod <pod-name>

Check logs:

kubectl logs <pod-name>

Check Service endpoints:

kubectl get endpoints
🌐 Access WordPress
kubectl port-forward service/wordpress-service 8080:80 --address=0.0.0.0

Open:

http://localhost:8080
💾 Persistent Storage

MySQL data is stored using:

PVC → PV → hostPath

Configuration:

Storage: 5Gi
Access Mode: ReadWriteOnce
Reclaim Policy: Retain
🧠 Kubernetes Concepts Practiced
Pods
Services
ClusterIP
NodePort
Port Forwarding
Labels & Selectors
PersistentVolume
PersistentVolumeClaim
Access Modes
Reclaim Policy
Environment Variables
Kubernetes Networking
Troubleshooting
🧹 Cleanup
kubectl delete -f k8s/
kind delete cluster --name devops-cluster
