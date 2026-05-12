# Kubernetes 컨테이너 오케스트레이션 실습 시험 가이드

본 시험은 Docker Compose 기반 멀티 컨테이너 서비스 구성과 Kubernetes Deployment 운영(Rolling Update 전략 포함) 능력 평가를 목적으로 합니다.

## 평가 목표

- Docker Compose를 활용한 멀티 컨테이너 서비스 구성 능력
- 컨테이너 간 네트워크 설정 및 서비스 연동 (PostgreSQL ↔ Spring Boot)
- Kubernetes Deployment 작성 및 Rolling Update 전략 이해
- kubectl CLI를 활용한 배포 검증 및 결과 확인 능력

## 시험 문제

제시된 2가지 문제에 대해 다음 사항을 구현하고 결과를 제출합니다.

### Docker Compose 멀티 서비스 구성

1. PostgreSQL, Nginx, Spring Boot 애플리케이션 서버 3개 서비스를 하나의 docker-compose.yml 파일로 정의합니다.
2. 3개 서비스를 동일한 네트워크에 배치하여 상호 통신이 가능하도록 구성합니다.
3. Spring Boot 서버가 PostgreSQL에 정상 연결되도록 환경변수 및 의존성을 설정합니다.
4. docker-compose up 실행 후 모든 컨테이너가 정상 기동되었음을 docker ps 결과와 함께 제출합니다.

### Kubernetes Deployment & Rolling Update

1. nginx 이미지를 사용하는 Deployment를 작성합니다. replicas는 3으로 설정합니다.
2. Rolling Update 전략을 maxSurge: 1, maxUnavailable: 0으로 명시적으로 지정합니다.
3. 작성한 YAML을 클러스터에 적용한 후 kubectl rollout status 명령으로 배포 완료를 확인합니다.
4. 배포 결과 스크린샷 또는 GitHub 링크를 함께 제출합니다.

## 제출 안내

- 구현된 소스 코드(GitHub 레포지토리 링크)와 실행 결과 스크린샷, 간략한 보고서를 제출합니다.
- 보고서에는 각 문제에 대한 구현 설명, 설계 결정 사항(네트워크 구성, Rolling Update 파라미터 선택 근거 등), 실행 결과를 포함해야 합니다.

## 유의사항

- YAML 문법 오류가 없도록 정확히 작성해야 합니다.
- 컨테이너 환경변수, 포트 매핑, 볼륨 설정에 특히 유의해야 합니다.
- Rolling Update 파라미터(maxSurge, maxUnavailable) 의미를 정확히 이해하고 적용해야 합니다.
- docker-compose up 후 모든 컨테이너가 Up 상태인지, kubectl rollout status가 정상 완료되는지 반드시 확인하고 제출하십시오.

## 과제 문항

1. Docker Compose를 사용하여 PostgreSQL 데이터베이스, Nginx 웹서버, Spring Boot 애플리케이션 서버를 하나의 docker-compose.yml 파일로 정의하고 실행하시오. 각 서비스는 동일한 네트워크에서 통신할 수 있어야 하며, Spring Boot 서버는 PostgreSQL에 정상 연결되어야 한다. docker-compose up 실행 후 모든 컨테이너가 정상 기동되었음을 docker ps 결과와 함께 제출하시오.

2. Kubernetes에서 nginx 이미지를 사용하는 Deployment를 작성하시오. replicas는 3으로 설정하고, Rolling Update 전략(maxSurge: 1, maxUnavailable: 0)을 적용하시오. 작성한 YAML을 클러스터에 적용하고, kubectl rollout status 명령으로 배포 완료를 확인한 후 결과 스크린샷 또는 GitHub 링크를 제출하시오.
