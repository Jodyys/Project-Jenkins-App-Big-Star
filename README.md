# CI/CD Pipeline for Dockerized Application with GitLab & AWS EC2

This project implements a CI/CD pipeline using **GitLab CI/CD** to automate testing, Docker image building, and deployment to **AWS EC2** (staging and production).  
The application source code is based on the course **“Docker: Your First Project”** from [LinkedIn Learning](https://www.linkedin.com/learning/docker-your-first-project/), but all DevOps-related setup and deployment are implemented independently in this repository.

📁 GitLab Repo: [app-big-stars-collectibles](https://gitlab.com/jodyys-group/app-big-stars-collectibles.git)

---

## 🔗 Source Attribution

**Original application source:**  
📚 LinkedIn Learning course: _Docker: Your First Project_  
🔗 GitHub repo: [linkedin/docker-your-first-project-4485003](https://github.com/LinkedInLearning/docker-your-first-project-4485003)

> The application used in this project is based on the above open-source educational material.  
> All CI/CD configurations, Dockerization, environment setup, and deployment are created by me for learning and demonstration purposes.

---

## 🔧 Tech Stack

- GitLab CI/CD  
- Docker & Docker Hub  
- AWS EC2  
- Bash scripting  
- SSH  
- Pytest (unit testing)

---

## ⚙️ CI/CD Workflow

1. **Test**  
   - Runs unit tests using `pytest` before Docker build.

2. **Build**  
   - Builds Docker image and pushes to Docker Hub using GitLab runner.

3. **Deploy (Staging)**  
   - SSH into EC2 instance  
   - Pulls latest image and restarts container.

4. **Deploy (Production)**  
   - Manual trigger via GitLab  
   - Similar steps as staging but for production environment.

---

## 🐳 Docker Commands

Build & run locally:
```bash
docker build -t my-app .
docker run -d -p 5000:5000 my-app

🚀 EC2 Setup (Manual)

Docker was manually installed on both staging and production EC2 instances using the following Bash commands:

sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker

SSH keys for remote access are managed via GitLab CI/CD variables.


🗂️ Repository Structure
├── app.py
├── test_app.py
├── Dockerfile
├── requirements.txt
├── .gitlab-ci.yml
└── README.md

✅ Status

✅ Working CI/CD pipeline with full flow: test → build → deploy (staging & production).