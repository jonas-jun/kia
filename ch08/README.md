# 애플리케이션에서 파드 메타데이터와 그 외의 리소스에 액세스하기

## 8장 내용
- 컨테이너에 정보를 전달하기 위해 Downward API 사용
- 쿠버네티스 REST API 살펴보기
- 인증과 서버 검증을 kubectl proxy에 맡기기
- 컨테이너 내 API 서버에 접근하기
- 앰배서더 컨테이너 패턴의 이해
- 쿠버네티스 클라이언트 라이브러리 사용

## 1. Downward API로 메타데이터 전달
파드 자체의 메타데이터를 해당 파드 내에서 실행 중인 프로세스에 노출할 수 있다.
- 파드 이름
- 파드 IP 주소
- 파드가 속한 네임스페이스
- 파드가 실행 중인 노드 이름
- 파드가 실행 중인 서비스 어카운트 이름
- 각 컨테이너의 CPU와 메모리 요청
- 각 컨테이너의 CPU와 메모리 제한
- 파드의 레이블
- 파드의 어노테이션

~~~bash
kubectl create -f downward-api-env.yaml
> kubectl exec downward env # 모든 환경변수 접근 가능
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
HOSTNAME=downward
POD_IP=172.17.0.5
NODE_NAME=minikube
SERVICE_ACCOUNT=default
CONTAINER_CPU_REQUEST_MILLICORES=15
CONTAINER_MEMORY_LIMIT_KIBIBYTES=10240
POD_NAME=downward
POD_NAMESPACE=default
KUBERNETES_PORT=tcp://10.96.0.1:443
KUBERNETES_PORT_443_TCP=tcp://10.96.0.1:443
KUBERNETES_PORT_443_TCP_PROTO=tcp
KUBERNETES_PORT_443_TCP_PORT=443
KUBERNETES_PORT_443_TCP_ADDR=10.96.0.1
KUBERNETES_SERVICE_HOST=10.96.0.1
KUBERNETES_SERVICE_PORT=443
KUBERNETES_SERVICE_PORT_HTTPS=443
HOME=/root
~~~
