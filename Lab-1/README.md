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

### Create a Pod YAML file
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



## Task 2: Create a Deployment
```bash
nano nginx-deploy.yaml
```
### Apply Deployment 
```bash
kubectl apply -f nginx-deploy.yaml
kubectl get deployments
kubectl get pods -o wide
```

### Task 3: Expose Deployment using a Service
Create a NodePort service
```bash
kubectl expose deployment nginx-deployment --type=NodePort --port=80
```

### Check service
```bash
kubectl get svc
```

### Access application
```bash
http://<Node-IP>:<NodePort>
```

### Task 4: Scale Deployment
#### Scale up to 5 replicas:
```bash
kubectl scale deployment nginx-deployment --replicas=5
kubectl get pods   # check pods
```
#### Scale down to 2 replicas:
```bash
kubectl scale deployment nginx-deployment --replicas=2
```
check pods 
```bash
kubectl get pods
```



