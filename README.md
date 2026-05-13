# CI/CD Pipeline Implementation: Node.js with Jenkins & Docker

This repository contains the implementation of an end-to-end CI/CD pipeline designed to automate the build and deployment of a Node.js application. By leveraging industry-standard DevOps tools, this project ensures a seamless workflow from code commit to a live containerized environment.

---

## 🚀 Pipeline Flow
The automation process follows a structured lifecycle:
**GitHub** ➔ **Jenkins** ➔ **Docker Build** ➔ **Docker Hub** ➔ **Container Deployment**

---

## 🛠 Technology Stack
* **Backend:** Node.js (Express)
* **CI/CD Tool:** Jenkins (Declarative Pipeline)
* **Containerization:** Docker
* **Version Control:** GitHub
* **Image Registry:** Docker Hub

---

## 🌟 Key Highlights
* **Source Code Management:** Version controlled in GitHub with automated triggers.
* **Pipeline as Code:** Utilized a `Jenkinsfile` for a consistent and repeatable build process.
* **Automated Image Management:** Streamlined Docker image creation, tagging, and secure pushes to Docker Hub.
* **Secure Authentication:** Integrated credential management for protected access to external registries.
* **Automated Deployment:** Final containerized application deployment executed via Docker.

---

## 📂 Project Components
* `app/`: Contains the Node.js application source code.
* `Dockerfile`: Defines the environment and steps to containerize the application.
* `Jenkinsfile`: The declarative script managing the pipeline stages.

---

## 📈 Learning Outcomes
This implementation strengthened my hands-on expertise in:
1.  **Jenkins Configuration:** Mastering pipeline stages for automated builds and deployment.
2.  **Docker Orchestration:** Managing container lifecycles and ensuring environment parity.
3.  **DevOps Automation:** Bridging the gap between development and operations through streamlined workflows.

---

### 🔗 Project Links
* **Repository:** [docker-task-1](https://github.com/nandhakumar04080408/docker-task-1)
* **Developer:** [Nandhakumar](https://github.com/nandhakumar04080408)
