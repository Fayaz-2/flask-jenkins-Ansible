# 🐳 DevOps CI/CD Pipeline Project with Jenkins, Docker, Ansible, and AWS

This project demonstrates a complete DevOps workflow using **Jenkins**, **Docker**, **GitHub**, **Ansible**, and **AWS EC2**, with monitoring enabled via **CloudWatch**. The pipeline automatically builds, tests, and deploys a simple Python Flask application inside a Docker container.

---

## 🚀 Tech Stack

- **Cloud Platform**: AWS EC2  
- **CI/CD**: Jenkins  
- **Containerization**: Docker  
- **Automation**: Ansible  
- **Monitoring**: AWS CloudWatch  
- **Version Control**: Git & GitHub  
- **App**: Python Flask

---

## 📌 Project Workflow

1. **Source Code** pushed to GitHub
2. **Jenkins Pipeline**:
   - Clones the GitHub repo
   - Builds Docker image
   - Pushes image to DockerHub
   - Runs Ansible playbook to deploy container
3. **Ansible** stops any existing container and deploys the updated one
4. **Flask App** runs on EC2 at `http://<EC2-Public-IP>:8080`
5. **CloudWatch Agent** monitors EC2 metrics and container performance

---

## 📂 Project Structure
flask-jenkins-ansible/
│
├── app/
│   ├── app.py
│   ├── requirements.txt
│   └── Dockerfile
│
├── ansible/
│   └── deploy.yml
│
├── jenkins/
│   └── Jenkinsfile
│
└── README.md
