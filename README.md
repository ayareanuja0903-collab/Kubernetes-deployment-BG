# 🚀 Kubernetes Blue-Green Deployment

![Kubernetes](https://img.shields.io/badge/Kubernetes-Blue--Green-blue?style=for-the-badge&logo=kubernetes)
![NGINX](https://img.shields.io/badge/NGINX-Blue-green?style=for-the-badge&logo=nginx)
![Apache](https://img.shields.io/badge/Apache-Green-red?style=for-the-badge&logo=apache)

---

## 📌 Project Overview
This project demonstrates a **Blue-Green Deployment strategy using Kubernetes** to achieve **zero-downtime deployments** and seamless traffic switching between application versions.

---

## 🧠 What is Blue-Green Deployment?<br/>
Blue-Green Deployment is a release management strategy where:<br/>
🔵 **Blue Environment** → Current production version<br/>
🟢 **Green Environment** → New version (testing/upgrade)<br/>

Once Green is validated, traffic is switched instantly from Blue → Green.

---

## 🛠️ Tech Stack
* Kubernetes (EKS)
* AWS (EC2, EKS, ELB)
* kubectl
* eksctl
* ConfigMap

---

📂 Project Structure
```bash
Kubernetes-deployment-BG/
│── blue-deployment.yml
│── green-deployment.yml
│── service.yml
│── index.html
│── green.html
│── README.md
```

## 🚀 Setup & Installation
🔹 1. Create EKS Cluster
```bash
eksctl create cluster --name my-eks-cluster --region ap-south-1
```
🔹 2. Configure kubectl
```bash
aws eks update-kubeconfig --region ap-south-1 --name my-eks-cluster
```
🔹 3. Verify Cluster
```bash
kubectl get nodes
```

🔵 Deploy Blue Version

🔹 Create ConfigMap
```bash
kubectl create configmap blue-html --from-file=blue.html
```
🔹 Deploy Blue
```bash
kubectl apply -f blue-deployment.yml
```
🔹 Expose Service
```bash
kubectl apply -f service.yml
```
🔹 Get URL
```bash
kubectl get svc
```
👉 Open in browser:
<img width="1920" height="1080" alt="image" src="https://github.com/ayareanuja0903-collab/Kubernetes-deployment-BG/blob/main/screenshots/Blue-deployment.png" />

🟢 Deploy Green Version
🔹 Create ConfigMap
```bash
kubectl create configmap green-html --from-file=green.html
```
🔹 Deploy Green
```bash
kubectl apply -f green-deployment.yml
```
🔄 Switch Traffic (Blue → Green)
```bash
kubectl edit svc blue-service
```
Change: service.yml
```bash
selector:
  app: myapp
  version: blue
```
👉 TO:
```bash
selector:
  app: myapp
  version: green
```
🔁 Rollback (Green → Blue)
```bash
kubectl edit svc blue-service
```
Change back:
```bash
version: green → blue
```
🔍 Verification
Check Pods
```bash
kubectl get pods
```
Check Service
```bash
kubectl get svc
```
Check Endpoints
```bash
kubectl get endpoints service
```
Output: 
🟢 Green Deployment Running
<img width="1920" height="1080" alt="image" src="https://github.com/ayareanuja0903-collab/Kubernetes-deployment-BG/blob/main/screenshots/green-deployment.png" />

🔄 Traffic Switching

---

## 🎯 Key Learnings

* Kubernetes Service acts as traffic controller
* ConfigMaps are critical for dynamic content
* LoadBalancer integrates with AWS ELB
* Blue-Green deployment ensures zero downtime
---

## 🧹 Cleanup (Avoid AWS Charges)
```bash
eksctl delete cluster --name my-eks-cluster --region ap-south-1
```
---

## 👨‍💻 Author

* DevOps Learning Project
* Kubernetes Blue-Green Deployment 🚀

--
