# Real-Time Movie Ticketing Platform

This repository contains configuration and documentation for a movie ticketing platform designed to handle sudden spikes in traffic during popular film releases and special events.

The platform focuses on scalable microservices, automated deployments, and cost efficiency. The contents here mirror the profile README so that visitors to the repository see an overview at a glance.

## Architecture Overview

The service runs across two AWS regions (Seoul and Singapore) with three main VPCs:

- **Dev VPC (Seoul)** – Development environment and CI/CD pipeline
- **Prod VPC (Seoul)** – Handles production traffic with auto‑scaling
- **DR VPC (Singapore)** – Hot standby disaster recovery setup

![Architecture Diagram](https://github.com/user-attachments/assets/6b1820cc-1b3d-4bd9-ab4a-f19f7d13f53c)

## Key Features

### CI/CD Pipeline
- Automated build and security scans via GitHub Actions
- Docker images pushed to Amazon ECR
- Deployments to Amazon EKS using ArgoCD (GitOps)
- Automatic deployments triggered from `main` and `argocd` branches

### Scalability & Reliability
- Microservices on Amazon EKS
- Node auto‑scaling with Karpenter
- Horizontal Pod Autoscaler (HPA) for pod scaling
- Cross‑region hot standby for high availability

### Asynchronous & Concurrent Processing
- Redis for handling high‑concurrency reservation requests
- RabbitMQ for payment confirmation and email notifications

## Cost Optimization
- Savings Plan reduces EC2 costs by up to 49%
- SonarQube runs on Spot Instances to reduce CI/CD costs by up to 70%

---

## 한국어 안내

이 저장소는 실시간 영화 예매 플랫폼에 대한 구성과 문서를 포함하고 있습니다. 갑작스러운 트래픽 증가에도 안정적으로 대응할 수 있도록 설계되었습니다.

### 주요 구성 요소
- GitHub Actions와 ArgoCD를 이용한 CI/CD
- Karpenter와 HPA를 통한 오토스케일링
- Redis와 RabbitMQ 기반의 비동기 처리

비용 절감을 위해 Savings Plan과 Spot 인스턴스를 적극 활용합니다.
