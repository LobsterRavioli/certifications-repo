# Killer Coda Exercises 🐳

This document contains a collection of exercises and solutions from Killer Coda to help you prepare for the Certified Kubernetes Administrator (CKA) exam.
Yaml file use in the exercises will be in the 'manifest' folder.

---
This is the template i will user for exercises.
```
## Exercise
### 🎯 Task
### ✅ Resolution
### 🛞 Doc link
```
---



## Exercise Create a pod and assign him to a specific node (kodecloud)
### 🎯 Task
- Create a nginx pod named nginx
- Assign him to the 'node01' node.
### ✅ Resolution
#### Use nodname property in the pod spec
k apply -f pod_scheduled.yml
### 🛞 Doc link

---
## Exercise create an user (killercoda)
### 🎯 Task
- Create an user called 'carlton'.
- Create namespace web
- Give carlton permission to read (get and list) pods.
### ✅ Resolution

#### Creating the namespace and the authorizations
```bash
# Create namespace
kubectl create ns web

# Create role with pod read permissions
kubectl -n web create role pod-reader \
  --verb=get,list \
  --resource=pods

# Bind the role to user 'carlton'
kubectl -n web create rolebinding pod-reader-binding \
  --role=pod-reader \
  --user=carlton

# Deploy a test pod
kubectl -n web run pod1 --image=nginx
```
#### Creating the user

```bash
# Generate private key
openssl genrsa -out carlton.key 2048

# Generate CSR
openssl req -new -key carlton.key \
  -subj "/CN=carlton" \
  -out carlton.csr

# Encode CSR in base64
export REQUEST=$(cat carlton.csr | base64 -w 0)

# Check existing CSRs
kubectl get csr

# Approve CSR
kubectl certificate approve carlton

# Retrieve and decode certificate
kubectl get csr carlton -o jsonpath='{.status.certificate}' \
  | base64 -d > carlton.crt

# Configure kubectl credentials
kubectl config set-credentials carlton \
  --client-key=carlton.key \
  --client-certificate=carlton.crt \
  --embed-certs

# View configuration
kubectl config view

# Set user context
kubectl config set-context carlton \
  --user=carlton \
  --cluster=kubernetes

```
#### Switch to user and check authorizations
```bash
# Switch context
kubectl config use-context carlton

# Verify permissions in namespace 'web'
kubectl -n web get po
```

### 🛞 Doc link
Usefull link:
- https://kubernetes.io/docs/tasks/tls/certificate-issue-client-csr/

---