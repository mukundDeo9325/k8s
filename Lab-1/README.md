# Kubernetes Lab 1 — Basic Pod, Deployment & Service

## 📝 Overview
- Create a Pod  
- Deploy an application using a Deployment & ReplicaSet  
- Expose an application using a Service  
- Scale a Deployment  
- Perform rolling updates and rollbacks  

---

## 📌 Prerequisites
- Kubernetes cluster (Minikube / Kind / EKS)
- kubectl installed
- Basic Docker understanding

---

# 🚀 Lab Tasks

---

## **Task 1: Create a Pod**

### 1.1 Create a Pod YAML file
```bash
nano nginx-pod.yaml
```
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
spec:
  containers:
    - name: nginx
      image: nginx:latest
      ports:
        - containerPort: 80
```
## Apply the Pod
```bash
kubectl apply -f nginx-pod.yaml
kubectl get pods
```

