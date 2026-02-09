🚀 DevSecOps CI/CD Pipeline on AWS EKS
📌 Project Overview

This project demonstrates an end-to-end DevSecOps CI/CD pipeline deployed on AWS EKS.
It automates application build, security scanning, containerization, and Kubernetes deployment with monitoring.

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/829c2ca8-0db9-4f42-8965-c33f45d6e91c" />


🧰 Tools & Technologies Used

Cloud: AWS (EC2, EKS, ECR, ELB, IAM, VPC)

CI/CD: Jenkins

Containers: Docker

Orchestration: Kubernetes (kubectl)

Security: SonarQube, Trivy

Monitoring: Prometheus, Grafana

Version Control: Git, GitHub

OS: Linux (Ubuntu)

Package Manager: Helm

Application: Node.js, Express.js, HTML, CSS

🔄 CI/CD Pipeline Stages

Code commit to GitHub

Jenkins pipeline trigger

Static code analysis using SonarQube

Vulnerability scanning using Trivy

Docker image build and tagging

Push image to AWS ECR

Deploy application to AWS EKS

Expose application using Kubernetes LoadBalancer

Monitor cluster and application using Prometheus & Grafana

📊 Monitoring

Kubernetes cluster metrics

Node and Pod-level monitoring

Dashboards configured in Grafana


🚀 Deployment Highlights

Application deployed on AWS EKS

Exposed publicly via AWS Elastic Load Balancer

Secure access using IAM roles and security groups

🧠 Key Learnings

End-to-end DevSecOps pipeline implementation

Kubernetes service exposure and networking

Secure container image handling

Real-world troubleshooting of CI/CD and cloud infrastructure

AWS cost awareness and cleanup practices

🧹 Cost Optimization

All AWS resources were properly terminated after project completion to avoid unnecessary billing.

👤 Author
AjayKumar Ramesh
