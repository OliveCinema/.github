# 🎟️ 실시간 영화 예매 플랫폼

본 프로젝트는 CJ OliveNetworks의 CloudWave 3기 인턴십의 일환으로 제작된 안정적이고 확장 가능한 영화 예매 플랫폼입니다. 인기 영화 개봉 및 특정 시간대에 급증하는 트래픽을 안정적으로 처리하는 것을 목표로 합니다.

## 🌐 아키텍처 개요

본 플랫폼은 두 개의 AWS 리전(서울, 싱가포르)에 걸쳐 세 가지 주요 VPC로 구성되어 있습니다.

- **Dev VPC (서울 리전)**: 개발 환경 및 CI/CD 구축
- **Prod VPC (서울 리전)**: 운영 서비스 제공, 오토스케일링 및 트래픽 관리
- **DR VPC (싱가포르 리전)**: 고가용성 재해복구(Hot Standby) 환경 구성

## ⚙️ 주요 기능

### ✅ CI/CD 파이프라인

- GitHub Actions를 사용한 코드 빌드 및 보안 취약점 검사
- Amazon ECR에 Docker 이미지 푸시
- ArgoCD를 통한 Amazon EKS 배포 자동화 (GitOps 방식)
- main 및 argocd 브랜치 변경 시 자동 배포 트리거

### ✅ 확장성 및 안정성

- Amazon EKS를 활용한 컨테이너 기반 마이크로서비스 구축
- Karpenter를 통한 노드 수준 자동 확장
- HPA (Horizontal Pod Autoscaler)를 통한 파드 수준 자동 확장
- 싱가포르 리전의 Hot Standby 기반 DR 구축

### ✅ 비동기 및 동시성 처리

- Redis를 이용한 고동시성 예약 요청 처리 및 레이스 컨디션 방지
- RabbitMQ를 활용한 결제 확인 및 이메일 알림 등 비동기 작업 처리

## 💸 비용 최적화 전략

- Savings Plan 활용하여 EC2 인스턴스 비용 최대 49% 절감
- CI/CD 과정 중 SonarQube를 Spot 인스턴스로 운영하여 최대 70% 비용 절감

---

# 🎟️ Real-Time Movie Ticketing Platform

This project was developed as part of the CJ OliveNetworks CloudWave 3rd Cohort Internship, aiming to provide a robust and scalable movie ticketing platform capable of handling high volumes of traffic during movie releases and special events.

## 🌐 Architecture Overview

The platform consists of three primary VPCs across two AWS regions:

- **Dev VPC (Seoul Region)**: Development environment and CI/CD setup
- **Prod VPC (Seoul Region)**: Production-grade services with auto-scaling and traffic management
- **DR VPC (Singapore Region)**: High availability disaster recovery (Hot Standby)

## ⚙️ Key Features

### ✅ CI/CD Pipeline

- Automated build and security vulnerability scanning with GitHub Actions
- Docker image push to Amazon ECR
- GitOps-based automated deployments to Amazon EKS via ArgoCD
- Automatic deployment triggered by changes in `main` and `argocd` branches

### ✅ Scalability & Reliability

- Containerized microservices deployed on Amazon EKS
- Node-level auto-scaling with Karpenter
- Pod-level auto-scaling via Horizontal Pod Autoscaler (HPA)
- Cross-region Hot Standby disaster recovery setup in Singapore

### ✅ Asynchronous & Concurrent Processing

- Redis utilized for handling high concurrency reservation requests and preventing race conditions
- RabbitMQ employed for asynchronous processing such as payment handling and email notifications

## 💸 Cost Optimization

- Savings Plan to reduce EC2 instance costs by up to 49%
- Deploying SonarQube on Spot Instances to reduce CI/CD costs by up to 70%
