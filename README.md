# 🌐 Simple Static Website Deployment (SWE645)

A Dockerized static website serving a single HTML page via Nginx, deployed using Kubernetes and automated via a Jenkins-based CI/CD pipeline.

---

## 🚀 Features

- Serve a static HTML page using Nginx inside a Docker container
- Dockerized for portable deployment
- Kubernetes deployment-ready
- CI/CD pipeline using Jenkins
- Cloud-friendly (AWS EC2 recommended)

---

## 🛠️ Tech Stack

- HTML
- Nginx (running inside Docker)
- Docker
- Kubernetes
- Jenkins (CI/CD)
- AWS EC2 (You can also use S3, that's better for hosting static websites)

---

## 📂 Project Structure

- `index.html` – Static website home page
- `Dockerfile` – Builds the Nginx container image
- `deployment.yaml` – Kubernetes Deployment descriptor
- `survey.yaml` – Kubernetes Service descriptor
- `survey_key.pem` – Backend key (ensure secure handling)
- `Jenkinsfile` – CI/CD pipeline definition

---

## ⚙️ Setup & Deployment

### 1️⃣ Build the Docker Image

```bash
docker build -t static-website-nginx .
```

### 2️⃣ Run Locally via Docker

```bash
docker run -p 80:80 static-website-nginx
```
Your static website will be accessible at: http://localhost/

### 3️⃣ ☸️ Kubernetes Deployment

```bash
kubectl apply -f deployment.yaml
kubectl apply -f survey.yaml
```
This deploys the Nginx container in a Kubernetes cluster and exposes it via a service.(can be NodePort or LoadBalancer)

---

## 📈 CI/CD Pipeline

Automated builds and deployments using the provided **Jenkinsfile**.

**Recommended Setup:**

- **Source Control:** GitHub or GitLab repository
- **CI/CD Server:** Jenkins configured to monitor your repository
- **Deployment Target:** AWS EC2 instance or Kubernetes cluster

**Pipeline Tasks:**

- Build Docker image
- Push Docker image to container registry (optional)
- Deploy to production environment automatically via Kubernetes

---

## 🏗️ Future Enhancements

- Add HTTPS support using TLS certificates
- Implement multi-page website structure
- Add monitoring and logging using ELK Stack or Prometheus + Grafana
- Enable automated SSL certificate management via Let's Encrypt
- Optimize HTML for performance and SEO

---

## 👨‍💻 Author

Developed by **Gautama Shastry** and **Maheedar Sai** as part of **SWE645** coursework.

---

## 📄 License

Licensed under the **MIT License**.
