# 🚀 Kubernetes Blue-Green Deployment

![Kubernetes](https://img.shields.io/badge/Kubernetes-Blue--Green-blue?style=for-the-badge&logo=kubernetes)
![Docker](https://img.shields.io/badge/Docker-Containerization-blue?style=for-the-badge&logo=docker)
![NGINX](https://img.shields.io/badge/NGINX-Blue-green?style=for-the-badge&logo=nginx)
![Apache](https://img.shields.io/badge/Apache-Green-red?style=for-the-badge&logo=apache)

---

## 📌 Project Overview
This project demonstrates a **Blue-Green Deployment strategy using Kubernetes** to achieve **zero-downtime deployments** and seamless traffic switching between application versions.

---

## 🧠 What is Blue-Green Deployment?
Blue-Green Deployment is a release management strategy where:
- 🔵 **Blue Environment** → Current production version
- 🟢 **Green Environment** → New version (testing/upgrade)

Once Green is validated, traffic is switched instantly from Blue → Green.

---

## 🛠️ Tech Stack
- Kubernetes ☸️
- Docker 🐳
- NGINX (Blue)
- Apache HTTPD (Green)
- kubectl CLI
- NodePort Services

---

## 🚀 Deployment Steps

kubectl apply -f k8s/blue-deployment.yml
kubectl apply -f k8s/green-deployment.yml
kubectl apply -f k8s/blue-service.yml
kubectl apply -f k8s/green-service.yml

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

🔵 Blue App → http://<node-ip>:30009
🟢 Green App → http://<node-ip>:30008

---

## 📸 Screenshots

🖥️ Blue Deployment Running
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/92b0fab9-eb12-42cc-91ae-bde71782aa5f" />

🟢 Green Deployment Running
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/102fd0d6-bcce-4d99-abde-2e5b9061a1f6" />

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
