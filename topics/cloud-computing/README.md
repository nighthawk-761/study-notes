# Cloud Computing

가상화에서 출발해 AWS의 Compute, Network, Storage, Database, Messaging과 클라우드 보안을 연결해 정리한 노트입니다.

> 공개용 노트에는 CloudGoat 시나리오의 정답, 실제 자격 증명, 계정 식별자와 실습 스크린샷을 포함하지 않았습니다. 실습에서 확인한 내용은 재사용 가능한 방어 개념으로 일반화했습니다.

## 1. 클라우드 기반 기술

- [Virtualization Foundations](virtualization-foundations.md) — Hypervisor, vCPU, 메모리·I/O 가상화, VM과 Container
- [Control Plane, Data Plane과 Management Plane](control-data-management-planes.md) — 정책 결정, 실제 요청 처리, 운영 접점의 차이

## 2. AWS 핵심 서비스

- [EC2와 VPC](aws-ec2-and-vpc.md) — Instance, EBS, ENI, Subnet, Route, Security Group
- [S3 Object Storage](aws-s3-object-storage.md) — Bucket, Object, Key, 요청 흐름과 접근 제어
- [RDS Managed Database](aws-rds-managed-databases.md) — DB Instance, Multi-AZ, Read Replica, Backup
- [SQS Message Queue](aws-sqs-message-queues.md) — Decoupling, Visibility Timeout, 재처리, FIFO와 DLQ
- [Serverless와 Managed Platform](aws-serverless-and-managed-services.md) — Lambda, Elastic Beanstalk, SNS, API Gateway의 역할

## 3. Identity와 Security

- [IAM과 Temporary Credentials](aws-identity-and-temporary-credentials.md) — Principal, Policy, Role, STS와 Workload Identity
- [Cloud Security Misconfigurations](cloud-security-misconfigurations.md) — 과도한 권한, 비밀정보 저장, 공개 리소스와 공격 경로
- [Cloud Security Assessment](cloud-security-assessment.md) — CSPM, 자동 점검, 우선순위와 컴플라이언스

## 읽는 순서

처음이라면 `Virtualization → EC2/VPC → S3/RDS/SQS → IAM → Security` 순서를 권장합니다. 이미 AWS 서비스를 사용해봤다면 각 서비스 문서를 먼저 읽고 Plane과 IAM 문서로 공통 구조를 연결해도 됩니다.

## 외부 참고 자료

- [AWS Architecture Center](https://aws.amazon.com/architecture/)
- [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)
- [AWS Shared Responsibility Model](https://aws.amazon.com/compliance/shared-responsibility-model/)
- [CloudGoat](https://github.com/RhinoSecurityLabs/cloudgoat) — 의도적으로 취약한 AWS 실습 환경
- [Prowler](https://github.com/prowler-cloud/prowler) — 클라우드 보안 설정 자동 점검 도구
