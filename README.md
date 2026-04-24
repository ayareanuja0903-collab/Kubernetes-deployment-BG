🚀 Kubernetes Blue-Green Deployment on AWS EKS

![EKS](https://img.shields.io/badge/AWS-EKS-orange?logo=amazonaws)
![Kubernetes](https://img.shields.io/badge/Kubernetes-Orchestration-blue?logo=kubernetes)
![CI/CD](https://img.shields.io/badge/Deployment-Zero%20Downtime-success)
![Strategy](https://img.shields.io/badge/Strategy-Blue--Green-purple)0
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)


📌 Project Overview<br/>
This project demonstrates Blue-Green Deployment strategy using Kubernetes on AWS EKS (Elastic Kubernetes Service).

It ensures:<br/>
✅ Zero downtime deployment<br/>
✅ Easy rollback<br/>
✅ Safe production releases<br/>

## 🏗️ Architecture
<p>
  <img width="1000" height="600" alt="Architeture-Blue-Green-deployment" src="https://github.com/user-attachments/assets/dc21c726-f9a1-4660-b24b-ac46241fc561" />
</p>

## 🧠 What is Blue-Green Deployment?<br/>
Blue-Green Deployment is a release management strategy where:<br/>
🔵 **Blue Environment** → Current production version<br/>
🟢 **Green Environment** → New version (testing/upgrade)<br/>

Once Green is validated, traffic is switched instantly from Blue → Green.

## 🛠️ Tech Stack
* Kubernetes (EKS)<br/>
* AWS (EC2, EKS, ELB)<br/>
* kubectl<br/>
* eksctl<br/>
* ConfigMap<br/>

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
## 🔵 Deploy Blue Version
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
<img width="1000" height="600" alt="image" src="https://github.com/ayareanuja0903-collab/Kubernetes-deployment-BG/blob/main/screenshots/Blue-deployment.png" />

## 🟢 Deploy Green Version
🔹 Create ConfigMap
```bash
kubectl create configmap green-html --from-file=index.html
```
🔹 Deploy Green
```bash
kubectl apply -f green-deployment.yml
```
🔄 Switch Traffic (Blue → Green)
```bash
kubectl edit svc blue-service
```
👉 Change:
```bash
selector:
  app: myapp
  version: blue
```
👉 To:
```bash
selector:
  app: myapp
  version: green
```
👉 Output: 
<img width="1000" height="600" alt="image" src="https://github.com/ayareanuja0903-collab/Kubernetes-deployment-BG/blob/main/screenshots/green-deployment.png" />

🔁 Rollback (Green → Blue)

```bash
kubectl edit svc blue-service
```

Change back:
```bash
version: green → blue
```
## 🔍 Verification
🔹 Check Pods
```bash
kubectl get pods
```
🔹 Check Service
```bash
kubectl get svc
```
🔹 Check Endpoints
```bash
kubectl get endpoints service
```

## ⚠️ Challenges Faced & Solutions
```bash
┌──────────────────────────────┬──────────────────────────────────────────────┬──────────────────────────────────────────────┐
│ ⚠️ Issue                     |🔍 Problem                                   │ ✅ Solution                                 │
├──────────────────────────────┼──────────────────────────────────────────────┼──────────────────────────────────────────────┤
│ ConfigMap not found          │ Pods stuck in ContainerCreating              │ Created required ConfigMap                  │
│ 404 Not Found                │ Nginx could not find index.html              │ Corrected file name in ConfigMap            │
│ LoadBalancer not accessible  │ External URL not opening                     │ Updated AWS Security Group (Port 80)        │
└──────────────────────────────┴──────────────────────────────────────────────┴──────────────────────────────────────────────┘
```

## 🎯 Key Learnings
* Kubernetes Service acts as traffic controller
* ConfigMaps are critical for dynamic content
* LoadBalancer integrates with AWS ELB
* Blue-Green deployment ensures zero downtime

## 🧹 Cleanup (Avoid AWS Charges)
```bash
eksctl delete cluster --name my-eks-cluster --region ap-south-1
```

## 📊 Key Benefits

* Zero downtime deployments
* Easy rollback strategy
* Production-safe release process
* Real-world Kubernetes experience

## 🎯 Project Outcome

* Successfully deployed Blue-Green architecture
* Implemented traffic switching using Kubernetes services
* Learned production-grade deployment strategy
* Improved DevOps & Kubernetes skills

## 👨‍💻 Author
* Anuja Ayare
* DevOps Engineer
