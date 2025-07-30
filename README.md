# Save the README content into a .txt file for easy copying
readme_content = """
# 🚀 Java Spring Boot CI/CD Pipeline with Jenkins, Docker, SonarQube, ArgoCD, Helm & Kubernetes

## 📚 Overview

This project demonstrates a complete CI/CD pipeline for a **Java Spring Boot** application using modern DevOps tools:

- **Jenkins** for Continuous Integration  
- **SonarQube** for Code Quality Analysis  
- **Docker** for containerization  
- **Helm** for Kubernetes deployment templating  
- **ArgoCD** for GitOps-based Continuous Deployment  
- **Minikube** for a local Kubernetes cluster  
- **GitHub** for source control and manifest storage

The goal is to simulate a real-world DevOps pipeline from code commit to automated deployment on Kubernetes.

---

## ⚙️ Tools & Technologies

| Tool       | Purpose                            |
|------------|-------------------------------------|
| Jenkins    | Build, test, and push Docker image  |
| SonarQube  | Analyze code quality                |
| Docker     | Build & push container image        |
| GitHub     | Store source code & K8s manifests   |
| Helm       | Package and template K8s resources  |
| ArgoCD     | Deploy app to Kubernetes (GitOps)   |

---

## 🧱 Pipeline Architecture

Developer --> GitHub --> Jenkins --> SonarQube --> DockerHub --> GitHub (manifests) --> ArgoCD --> Kubernetes

---

## 🛠️ Project Structure

java-maven-sonar-argocd-helm-k8s/
├── spring-boot-app/   # Java source code
    ├── Jenkinsfile      # CI steps
├── spring-boot-app-manifests/    # K8s YAML/Deployment and Services              
└── README.md

---

## ✅ CI/CD Flow

1. **Code Commit**  
   Developer pushes code to GitHub.

2. **Jenkins CI**
   - Pulls code
   - Performs Maven build & test
   - Runs SonarQube code analysis
   - Builds Docker image
   - Pushes image to Docker Hub
   - Updates Kubernetes manifest (`values.yaml` or deployment YAML)
   - Pushes manifest changes to GitHub

3. **ArgoCD CD**
   - Watches GitHub repo for manifest changes
   - Syncs changes and deploys app to Minikube cluster

---

## 🔄 ArgoCD Sync

After Jenkins updates the manifest (like image tag), ArgoCD auto-syncs and applies changes to the cluster. You can force sync from UI or CLI:

argocd app sync springboot-app

---

## 📈 Dashboard Access

| Tool       | URL                                   |
|------------|---------------------------------------|
| Jenkins    | http://localhost:<port #mentioned>    |
| SonarQube  | http://localhost:<port #mentioned>    |
| ArgoCD     | http://localhost:<port #mentioned>    |  
| App        | http://localhost:<#NodePort>          |

---

## 🌟 What We Learn

- Real-world Jenkins pipeline scripting  
- Automating code quality checks (SonarQube)  
- Docker image handling & tagging  
- ArgoCD GitOps approach to CD  
- K8s deployments  
- End-to-end CI/CD lifecycle

---

## 🧠 Tips

- Make sure ArgoCD has access to the GitHub manifest repo.
- Use `Always` imagePullPolicy to always pull new images.
- Keep Jenkins and ArgoCD on separate ports in Minikube to avoid clashes.
- Make sure all the credentials are correct, including docker ID, API keys
- If there's a problem with ArgoCD service, like changes are reverting back to clusterIP from Nodeport , try changing the ArgoCD service file itself(clusterIP to NodePort) and restart the pod.

