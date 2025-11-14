# Kubernetes Lab 2 — ConfigMaps & Secrets

## 📝 Overview
- Create and use ConfigMaps  
- Create and use Secrets  
- Inject ConfigMap & Secret values into Pods  
- Use environment variables and mounted files  
- Understand security considerations for Secrets  

---

## 📌 Prerequisites
- Kubernetes cluster (Minikube / Kind / EKS)
- kubectl installed
- Completion of Lab 1 (recommended)

---

# 🚀 Lab Tasks

---

## Task 1: Create a ConfigMap**

### Create a ConfigMap from a Literal Value
```bash
kubectl create configmap app-config --from-literal=APP_MODE=production
```
### Create a ConfigMap from a File
```bash 
echo "APP_COLOR=blue" > config.properties
```

### Create ConfigMap:
```bash
kubectl create configmap color-config --from-file=config.properties
```
### View ConfigMaps
```bash
kubectl get configmaps
kubectl describe configmap app-config
kubectl describe configmap color-config
```
## Task 2: Use ConfigMap in a Pod
```bash
nano cm-pod.yaml
```
### Create Pod
```bash
kubectl apply -f cm-pod.yaml
kubectl get pods
```
### Verify Values
```bash
kubectl exec -it configmap-demo-pod -- printenv | grep MODE
kubectl exec -it configmap-demo-pod -- ls /etc/app-config
kubectl exec -it configmap-demo-pod -- cat /etc/app-config/config.properties
```

## Task 3: Create a Secret
```bash
kubectl create secret generic db-secret \
  --from-literal=username=admin \
  --from-literal=password=admin123
```
### Create Secret from File
```bash
echo -n "superkey" > api-key.txt
```
```bash
kubectl create secret generic api-secret --from-file=api-key.txt
```
### View secrets (encoded)
```bash
kubectl get secrets
kubectl describe secret db-secret
```

## Task 4: Use Secret in a Pod
```bash
nano secret-pod.yaml
```

### Create pod
```bash
kubectl apply -f secret-pod.yaml
```

### Verify Secrets
```bash
kubectl exec -it secret-demo-pod -- printenv | grep DB_
```

### Check mounted secret file:
```bash
kubectl exec -it secret-demo-pod -- ls /etc/secret-data
kubectl exec -it secret-demo-pod -- cat /etc/secret-data/api-key.txt
```


