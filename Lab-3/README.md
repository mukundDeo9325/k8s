# Kubernetes Lab 3 — Ingress + Nginx Ingress Controller

## 📝 Overview
- Install Nginx Ingress Controller
- Create sample applications
- Create Ingress rules for path-based routing
- Access apps through a single external IP
- Understand how Ingress works internally

---

## 📌 Prerequisites
- Kubernetes cluster (Minikube / Kind / EKS)
- kubectl installed
- Completed Labs 1–2 (recommended)
- **Minikube is preferred** for beginners

---

# 🚀 Lab Tasks

---

## **Task 1: Enable Ingress Controller (Minikube)**

If using Minikube:
```bash
minikube addons enable ingress
```
varify 
```bash
kubectl get pods -n ingress-nginx
```
You should see pods like:
```bash
ingress-nginx-controller-xxxxx
```

