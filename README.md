# DevOps CI/CD Pipeline Project using Jenkins, Docker, Ansible, and AWS

## 🚀 Project Overview

This project demonstrates a complete CI/CD pipeline setup for a Python Flask web application using Jenkins, Docker, Ansible, and AWS EC2. It includes automated build, push, and deployment stages along with monitoring using AWS CloudWatch.

---

## 🧰 Tech Stack

- **Cloud:** AWS EC2  
- **CI/CD:** Jenkins  
- **Containerization:** Docker  
- **Configuration Management:** Ansible  
- **Source Control:** Git, GitHub  
- **Monitoring:** AWS CloudWatch  
- **Application:** Python Flask  

---

## 🔄 Pipeline Flow

1. **Code pushed** to GitHub  
2. **Jenkins Pipeline** triggered:
   - Clones the repository  
   - Builds Docker image  
   - Pushes to DockerHub  
   - Deploys container using Ansible  
3. **Ansible** stops old container and runs the new one  
4. **CloudWatch** monitors EC2 instance and Docker container  

---

## 📁 Project Structure
flask-app/
├── app.py
├── requirements.txt
├── Dockerfile
├── ansible/
│ └── deploy.yml
├── jenkins/
│ └── Jenkinsfile
└── README.md


---

## ⚙️ Setup Instructions

### 1. Launch EC2 Instance
- OS: Amazon Linux 2  
- Open Security Group Ports: `22`, `8080`, `8081`

---

### 2. Install Required Packages

```bash
sudo yum update -y
sudo amazon-linux-extras install epel -y
sudo amazon-linux-extras install java-openjdk11 -y
sudo yum install git docker ansible python3 -y

**### 3. Install Jenkins**
apt update -y
apt install default-jdk -y
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
   https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
    https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
    /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update -y
sudo apt install jenkins -y
systemctl enable jenkins
systemctl start jenkins

**4. Start and Enable Docker**
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ec2-user

**5. Jenkins Setup**
Access Jenkins at: http://<EC2_PUBLIC_IP>:8080
Install Plugins: Git, Docker Pipeline, Pipeline, Credentials

**6. Jenkins Credentials **
Go to Manage Jenkins → Credentials
Add new credentials:
  |__ID: dockerhub-creds
  |__Type: Username & Password (your DockerHub login)

🛠️ Build and Deploy Pipeline
Create a GitHub repository and push your Flask project with Dockerfile, Jenkinsfile, and ansible/deploy.yml.

Create a Jenkins pipeline job and link it to your GitHub repo.
Add and use the Jenkinsfile for pipeline steps:
|--Clone repo
|--Build Docker image
|--Push image to DockerHub
|--Deploy using Ansible
