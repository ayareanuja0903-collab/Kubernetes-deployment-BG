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
- 🔵 **Blue Environment** → Current production version<br/>
- 🟢 **Green Environment** → New version (testing/upgrade)<br/>

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

🔵 Blue App → http://<node-ip>:30008
🟢 Green App → http://<node-ip>:8082

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
