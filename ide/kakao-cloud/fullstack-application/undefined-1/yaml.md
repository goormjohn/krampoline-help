# 쿠버네티스 yaml 파일을 수정하는 방법

기본 제공해드린 yaml 파일에서 수정해야 하는 부분은 Deployment의 이미지 경로와 Ingress의 path 정보입니다.

먼저 Frontend, Backend에 대한 Deployment 객체 정의 부분에서 이미지 경로를 변경해야 합니다.\
원하는 이미지를 담고 있는 Pod를 만들고, 이를 Deployment 객체가 관리하도록 설정하기 위함입니다.

D2Hub 이미지의 경로를 복사해오는 방법은 [Kargo 배포 구성 파일 작성 가이드](../../kargo-app/1.-kargo.md)에서 확인 가능합니다.

[1.-kargo.md](../../kargo-app/1.-kargo.md "mention")\


아래는 frontend.yaml 파일에 위치한 Deployment 객체의 예시입니다.\
spec.template.spec.containers 중 해당하는 컨테이너의 image 경로를 변경합니다.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
    annotations:
        kargo.9rum.cc/phase: dev
    labels:
        app: frontend
        app.kubernetes.io/managed-by: kargocd
    name: frontend
    namespace: default
spec:
    replicas: 1
    selector:
        matchLabels:
            app: frontend
    template:
        metadata:
            labels:
                app: frontend
        spec:
            containers:
                - name: frontend
                  # 여러분의 image 주소를 입력해주세요.
                  image: krmp-d2hub-idock.9rum.cc/goorm/techcamp-frontend
                  ports:
                      - containerPort: 80
```

Backend의 Deployment 객체의 경우 backend.yaml에 위치해있고, 동일한 방식으로 이미지 경로만 변경하면 됩니다.&#x20;



또한 Ingress의 path 정보도 수정이 필요합니다.\
/\[uid]/subpath 형태로 들어온 요청을 서비스 객체에 포워딩 하기 위한 설정입니다.

아래는 nginx.yaml 파일에 위치한 Ingress 객체의 작성 예시입니다.\
spec.rules의 http.paths의 backend 항목에서 path 정보를 Kargo App에 연결된 uid로 수정해야 합니다.

**\*\*추후 업데이트 시 nginx.yaml 파일 수정 부분은 제거될 수 있습니다. 업데이트 후에는 조치하지 않아도 됩니다.\*\***

```yaml
apiVersion: networking.k8s.io/v1beta1
kind: Ingress
metadata:
    name: krampoline
    namespace: default
spec:
    rules:
        - http:
              paths:
                  - backend:
                        serviceName: frontend-service
                        servicePort: 80
                        # 여러분의 app path를 넣어주세요.
                        path: /kfed0910e2e37a(/|$)(.*)
```
