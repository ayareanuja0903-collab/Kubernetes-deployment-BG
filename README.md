🚀 Kubernetes Blue-Green Deployment on AWS EKS

![EKS](https://img.shields.io/badge/AWS-EKS-orange?logo=amazonaws)
![Kubernetes](https://img.shields.io/badge/Kubernetes-Orchestration-blue?logo=kubernetes)
![CI/CD](https://img.shields.io/badge/Deployment-Zero%20Downtime-success)
![Strategy](https://img.shields.io/badge/Strategy-Blue--Green-purple)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)


📌 Project Overview

This project demonstrates Blue-Green Deployment strategy using Kubernetes on AWS EKS (Elastic Kubernetes Service).

It ensures:

✅ Zero downtime deployment
✅ Easy rollback
✅ Safe production releases

---

## 🏗️ Architecture
<p>
  <img src="">
</p>

## 🧠 What is Blue-Green Deployment?<br/>
Blue-Green Deployment is a release management strategy where:<br/>
🔵 **Blue Environment** → Current production version<br/>
🟢 **Green Environment** → New version (testing/upgrade)<br/>

Once Green is validated, traffic is switched instantly from Blue → Green.

---

## 🛠️ Tech Stack
- Kubernetes ☸️
- NGINX (Blue)
- Apache HTTPD (Green)
- kubectl CLI
- NodePort Services

---

## 🚀 Deployment Steps

- kubectl apply -f blue-deployment.yml
- kubectl apply -f green-deployment.yml
- kubectl apply -f blue-service.yml
- kubectl apply -f green-service.yml

---

## 🔄 Traffic Switching (Blue → Green)
👉 Switch to Green
kubectl patch service blue-service -p '{
  "spec": {
    "selector": {
      "app": "myapp",
      "version": "green"
    }
  }
}'

---

## 🔙 Switch back to Blue

kubectl patch service blue-service -p '{
  "spec": {
    "selector": {
      "app": "myapp",
      "version": "blue"
    }
  }
}'

---

## 🌍 Application Access

🔵 Blue App → http://<node-ip>:30008<br/>
🟢 Green App → http://<node-ip>:8082<br/>

---

## 📸 Screenshots

🖥️ Blue Deployment Running
<img width="1920" height="1080" alt="image" src="https://github.com/ayareanuja0903-collab/Kubernetes-deployment-BG/blob/main/screenshots/Blue-deployment.png" />


🟢 Green Deployment Running
<img width="1920" height="1080" alt="image" src="https://github.com/ayareanuja0903-collab/Kubernetes-deployment-BG/blob/main/screenshots/green-deployment.png" />

🔄 Traffic Switching

---

## 📊 Key Benefits

* Zero downtime deployments
* Easy rollback strategy
* Production-safe release process
* Real-world Kubernetes experience
---

## 🎯 Project Outcome

* Successfully deployed Blue-Green architecture
* Implemented traffic switching using Kubernetes services
* Learned production-grade deployment strategy
* Improved DevOps & Kubernetes skills
---

## 👨‍💻 Author

* DevOps Learning Project
* Kubernetes Blue-Green Deployment 🚀

--
