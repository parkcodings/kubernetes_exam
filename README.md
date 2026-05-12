# Kubernetes Exam Project

## 구성

- `docker-compose.yml`: PostgreSQL, Nginx, Spring Boot 3개 서비스
- `spring-app/`: Spring Boot 애플리케이션
- `nginx/default.conf`: Nginx 설정
- `k8s/nginx-deployment.yaml`: Kubernetes Deployment 예제

## 실행

### Docker Compose

```powershell
docker compose up --build -d
docker ps --filter name=exam- --format "table {{.Names}}\t{{.Status}}\t{{.Ports}}"
docker compose logs app
```

중지:

```powershell
docker compose down -v
```

### Kubernetes

현재 컨텍스트 확인:

```powershell
kubectl config current-context
```

배포:

```powershell
kubectl apply -f k8s/nginx-deployment.yaml
kubectl rollout status deployment/nginx-rolling-update
kubectl get deployment,pods
```

정리:

```powershell
kubectl delete -f k8s/nginx-deployment.yaml
```

## 제출 체크

- `docker ps` 결과 캡처
- `kubectl rollout status` 결과 캡처
- 소스 코드 GitHub 업로드

## 결과 캡처

### Docker Compose

![docker ps result](images/docker%20ps.png)

### Kubernetes Rollout

![kubectl rollout status result](images/kubectl%20rollout%20status.png)
