# 🚀 Frontend CI/CD Pipeline – GitHub Actions, Docker & Kubernetes

This pipeline delivers a **secure, efficient, and production-ready** solution for automating the deployment of a frontend application from code to Kubernetes.

---

## 🧪 Overview

Triggered on every push to the `dev` branch, this pipeline builds a Docker image, pushes it to Docker Hub, and seamlessly updates the live deployment on Kubernetes.

- 🔐 End-to-end secured with encrypted secrets
- ⚡ Lightning-fast builds using Docker cache
- 🔄 Fully automated from commit to cluster

---

## 🛠️ Build Job – Steps Breakdown

| Step | Purpose |
|------|---------|
| 🧬 Git Checkout | Clones the latest code |
| 🔖 Commit Hash Tag | Generates short hash for versioning |
| 🔐 Docker Login | Uses GitHub Secrets for authentication |
| ⚙️ Buildx Setup | Enables advanced builds with cache |
| 🛠️ Docker Build & Push | Pushes image tagged by commit hash |
| 📦 Env Injection | Securely injects frontend variables via `build-args` |

### 🌟 Secured .env Handling for Frontend

Instead of relying on `.env` files inside the repo, this pipeline injects sensitive variables (like `VITE_API_URL`) at **build time only**, directly from GitHub secrets.  
This ensures:
- 🔐 No secrets exposed in the image
- ♻️ Clean separation between code and environment

---

## 🚀 Deploy Job – Steps Breakdown

| Step | Purpose |
|------|---------|
| 🔐 Load kubeconfig | Decoded securely from base64 GitHub secret |
| 🌐 Switch Context | Targets the desired Kubernetes cluster |
| 🔄 Image Update | Uses `kubectl set image` for safe rolling update |
| ✅ Rollout Verification | Waits for the deployment to finish successfully |

---

## 💎 What Makes This Pipeline Stand Out?

### ✅ 1. Security at the Core
- Secrets for Docker & K8s fully encrypted
- No hardcoded credentials or .env values

### ⚡ 2. Speed with Docker Cache
- Utilizes GitHub’s cache system for faster builds
- Buildx + caching = minimal build times

### 🔄 3. True Automation
- One commit = full deployment
- Manual trigger supported for staged rollouts

### 🧠 4. Real-World-Ready Solutions
- Solves the common `.env` + Docker injection issue cleanly
- Prevents multiple deployments using concurrency locks

---

> ✨ A modern frontend pipeline built for cloud-native delivery.
> From your laptop to the cluster, fully automated and secured.
