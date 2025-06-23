실시간 영화 예매 플랫폼
이 저장소는 인기 영화 개봉이나 특별 이벤트 시 발생하는 트래픽 폭증 상황을 안정적으로 처리할 수 있도록 설계된 영화 예매 플랫폼의 구성 및 문서를 포함합니다.

본 플랫폼은 확장 가능한 마이크로서비스 아키텍처, 자동화된 배포, 비용 효율성에 중점을 두고 있으며, 이 문서는 프로필 README와 동일한 내용을 포함해 방문자가 전체 개요를 쉽게 확인할 수 있도록 구성되어 있습니다.

🏗️ 아키텍처 개요
이 서비스는 AWS 서울 리전과 싱가포르 리전에 걸쳐 다음과 같은 세 개의 주요 VPC에서 운영됩니다:

Dev VPC (서울) – 개발 환경 및 CI/CD 파이프라인

Prod VPC (서울) – 실서비스 트래픽 처리 및 오토스케일링 적용

DR VPC (싱가포르) – 장애 발생 시를 대비한 핫 스탠바이(Hot Standby) 이중화 환경

![Architecture Diagram](https://github.com/user-attachments/assets/6b1820cc-1b3d-4bd9-ab4a-f19f7d13f53c)

🚀 주요 기능
CI/CD 파이프라인
GitHub Actions를 활용한 자동 빌드 및 보안 스캔

Docker 이미지를 Amazon ECR에 푸시

ArgoCD(GitOps)를 통한 Amazon EKS 배포 자동화

main 및 argocd 브랜치에 푸시 시 자동 배포 트리거

확장성과 신뢰성
Amazon EKS 상에서 마이크로서비스 운영

Karpenter 기반 노드 자동 스케일링

HPA(Horizontal Pod Autoscaler)를 활용한 파드 스케일링

리전 간 핫 스탠바이 구성으로 고가용성 확보

비동기 및 동시성 처리
Redis를 활용한 실시간 좌석 예매 시 동시성 문제 해결

RabbitMQ를 통한 결제 확인 및 이메일 알림 비동기 처리

💸 비용 최적화
Savings Plan을 활용하여 EC2 비용 최대 49% 절감

SonarQube를 Spot 인스턴스에서 실행하여 CI/CD 비용 최대 70% 절감


