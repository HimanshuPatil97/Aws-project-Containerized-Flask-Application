# Containerized Flask Application using AWS ECS

## 📌 Project Overview

This project demonstrates how to containerize a Python Flask application using Docker and deploy it on AWS ECS using Amazon ECR.

The Flask application was packaged into a Docker container, pushed to Amazon ECR, and deployed using ECS Fargate.

---

## 🧰 AWS Services Used

- Amazon ECS
- Amazon ECR
- Docker
- AWS Fargate
- IAM

---

## 🚀 Implementation Steps

### 1. Create Flask Application

Created a simple Flask application:

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return "Hello from Flask ECS App!"

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```

---

### 2. Create Dockerfile

Containerized the application using Docker.

```dockerfile
FROM python:3.9

WORKDIR /app

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY . .

CMD ["python", "app.py"]
```

---

### 3. Build Docker Image

```bash
docker build -t flask-app .
```

---

### 4. Create Amazon ECR Repository

Created an ECR repository to store Docker images.

Repository Name:
- flask-app

---

### 5. Push Docker Image to ECR

Authenticated Docker with ECR and pushed the image.

```bash
docker push <ECR-URI>
```

---

### 6. Create ECS Cluster

Created an ECS Fargate cluster:
- flask-cluster

---

### 7. Create Task Definition

Configured:
- Container Image
- CPU and Memory
- Port Mapping (5000)

---

### 8. Create ECS Service

Created ECS service with:
- Fargate launch type
- Public IP enabled
- Desired task count = 1

---

### 9. Test Application

Accessed the application using the ECS task public IP:

```text
http://<PUBLIC-IP>:5000
```

Output:

```text
Hello from Flask ECS App!
```

---

## 🎯 Features

- Docker Containerization
- Serverless Container Deployment
- Scalable Architecture
- Cloud-based Application Hosting

---

## 📸 Output

The Flask application was successfully containerized and deployed on AWS ECS using Docker and Amazon ECR.

---

## 🎓 Learning Outcomes

- Docker containerization
- Amazon ECS deployment
- Amazon ECR usage
- Container orchestration
- Cloud-native application deployment

---

## ✅ Conclusion

This project successfully demonstrated the deployment of a containerized Flask application using Docker, Amazon ECR, and AWS ECS Fargate for scalable cloud hosting.
