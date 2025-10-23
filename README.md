# Python App Deployment on Amazon Linux EC2
*"From Virtual Environment to Gunicorn, Deploying My First Python App on the Cloud"*

---

## Overview
This project demonstrates how I deployed a **Python webapplication** on an **Amazon Lilnux EC2 instance**. It covrs installing Python, creatin a virtual environment, installing dependencies, running the app locally, and deploying it using **Gunicorn** as a production-ready server.

---

## Prerequisites
Before starting, make sure you have:
1. **AWS EC2 Instance**
  - Running Amazon Linux 2
  - Accessible via SSH with a valid key pair

2. **Security Group Setup**
   - Port **22 (SSH)** open for connecting
   - Port **5000 (or your Python app port)** open for serving the app

3. **GitHub Repository**
  - A Python app storedd in a public or private Git repository

---

## Steps Followed

### 1. Update Packages and Install Python3
```bash
sudo yum update -y
sudo yum install python3 -y
sudo yum install python3-pip -y
```
---

### 2.Install Git and Clone Aplication
```bash
git -v # check if git installed
sudo yum install git -y
sudo git clone <url>
ls
cd pythonapp/
```

---

### 3. Create and Activate Virtual Environment
```bash
python3 -m venv myenv
sudo python3 -m venv myenv
sudo bash myenv/bin/activate
```

---

### 4. Install Dependencies
```bash
sudo pip install -r requirements.txt
```

---

### 5. Run the App Locally
```bash
python3 app.py
```

---

### 6. Deploy with Gunicorn (Production Server)
```bash
sudo gunicorn --bind 0.0.0.0:5000 app:app --daemon
```

---
### 7. Test Locally
```bash
curl localhost
```

---

### 8. Access in Browser

copy your **EC2 public IP** and visit:
```
http://<your-ec2-public-ip>:5000
```

---

## Common Issues & Fixes

### 1. Port Not Accessible

* **Issue**: Application runs, but browser shows
*connetion refused*.
* **Fix**: Update your EC2 **Security Group** -> Add inbound rule for port '5000' (or the port your app uses) with source set to '0.0.0.0/0'.

---

### 2. Virtual Environment Not Activating

* **Issue**: Error like 'permission denied' while activating virtual environment.
* **Fix**: Ensure you'e using the correct path:

```
source myenv/bin/activate
```

If needed, run with 'sudo bash myenv/bin/activate'.

---

### Result
My Python web application is now running on Amazon Linux EC2. Using **Uunicorn**, the app stays actie as a production-grade WSGI server accessible over the public IP.

![alt text](image.png)

---

## Tech Sack

* **OS**: Amazon Linux 2
* **Language**: Python 3
* **Package Manager**: pip
* **Web Server Gateway**: Gunicorn
* **hosting**: AWS EC2

---

## Summary

In this project, I deployed a Python application on an AWS EC2 instance. After installling Python and Git, I cloned the repository, created a virtual environment, installed dependencies, and deployed the app with Gunicorn. This marks my first successful python web app deployment on the cloud.

---
