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

## 📁 Project Structure
