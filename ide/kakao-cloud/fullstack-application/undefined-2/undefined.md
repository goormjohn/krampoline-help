# 배포한 앱의 로그 확인

#### 배포한 앱의 로그를 확인하고 싶다면 kubectl 명령어를 통해 확인할 수 있습니다.

크램폴린 IDE의 실습환경은 사용자에게 할당된 DKOS 클러스터에 연결되어 있습니다.\
따라서 터미널 상에서 kubectl 명령어를 이용하여 쿠버네티스 리소스에 접근할 수 있습니다.

만약 클러스터에 배포한 앱의 로그를 확인하고 싶다면, pod 리소스에 대한 조회를 통해 확인이 가능합니다.\
먼저 kubectl get pods를 실행하여 배포된 pod의 목록을 조회합니다.

```bash
$ kubectl get pods
NAME                        READY   STATUS    RESTARTS   AGE
backend-6bf587cf67-kkgl4    1/1     Running   2          8d
frontend-5b88bb75f8-dtn6l   1/1     Running   0          8d
mariadb-0                   1/1     Running   0          8d
```

목록에서 확인되는 pod들 중 로그를 확인하고 싶은 pod의 이름을 복사해서, **kubectl logs \[pod 이름]**을 실행합니다.

```bash
ex)
$ kubectl logs frontend-5b88bb75f8-dtn6l
```

해당 명령어를 통해 배포된 앱의 로그를 확인할 수 있습니다.
