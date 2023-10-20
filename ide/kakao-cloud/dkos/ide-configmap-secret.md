# 크램폴린IDE ConfigMap, Secret 사용하기

## 크램폴린IDE ConfigMap, Secret 사용하기

API를 개발하다보면 민감한 정보들이 필요합니다. 현재 크램폴린IDE는 보통 github 기반으로 하고 있는데요. 지금부터 github 에 올리지 않고, IDE 안에서 secret 키나, config 를 사용하는 방법을 가르쳐 드리려고 합니다.

**모든 예시는 file기반으로 작성하였는데요. 환경변수로도 넣을 수 있습니다.**



### 컨피그맵(ConfigMap)

컨피그맵은 키-값 쌍으로 기밀이 아닌 데이터를 저장하는 데 사용하는 API 오브젝트입니다.\
현재 크램폴린 IDE 에서 ConfigMap 을 만드는 방법은 두 가지 입니다.

<mark style="color:red;">**주의**</mark><mark style="color:red;">: 컨피그맵은 보안 또는 암호화를 제공하지 않습니다. 저장하는 데이터가 기밀인 경우, 컨피그맵 대신</mark> [<mark style="color:red;">시크릿(Secret)</mark>](https://kubernetes.io/ko/docs/concepts/configuration/secret/) <mark style="color:red;">또는 추가(써드 파티) 도구를 사용하여 데이터를 비공개로 유지해야 합니다.</mark>

#### **kustomization을 이용해서 만드는법**

크램폴린IDE의 쿠버네티스 파일을 구성할때 `k8s/kustomization.yaml` 를 사용합니다. 여러분에게 제공되는 예시에서도 이 방법을 사용하고 있는데요, 바로 kustomization 의 configMapGenerator 입니다.

크램폴린 krampoline\_step4 예시에 보시면 다음 파일을 보실 수 있습니다.

```yaml
namespace: default
resources:
  - nginx.yaml
  - mariadb.yaml
  - backend.yaml
  - frontend.yaml
configMapGenerator:
  - name: nginx
    files:
      - configs/default.conf
  - name: init-db
    files:
      - configs/init.sql
```

여기 내용에서 보시면 configMapGenerator 에 여러분의 설정 파일을 넣으시고 다시 배포를 하시면 해당 파일을 자동으로 ConfigMap 으로 만들어서 실행하도록 되어있습니다.&#x20;

현재 예시는 ConfigMap 의 이름(name) 파일의 위치 (files) 로 구성되어 있습니다. 여러분께 드린 예시에서는 nginx 설정과 sql 설정이 되어 있는 것으로 보시면 됩니다.



#### 오브젝트를 작성해서 이용하는 방법

여러분이 직접 ConfigMap 오브젝트를 만들어보고 싶으시면, nginx.yaml 나 mariadb.yaml 처럼 직접 작성해서 만드실 수 있습니다. 다음 예시처럼 만들어주세요.

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: game-demo
data:
  # 속성과 비슷한 키; 각 키는 간단한 값으로 매핑됨
  player_initial_lives: "3"
  ui_properties_file_name: "user-interface.properties"

  # 파일과 비슷한 키
  game.properties: |
    enemy.types=aliens,monsters
    player.maximum-lives=5    
  user-interface.properties: |
    color.good=purple
    color.bad=yellow
    allow.textmode=true
```

그리고 다음과 같이 `k8s/kustomization.yaml` 에서 불러와서 사용할 수 있습니다.

```yaml
namespace: default
resources:
     ...
  - configMap.yaml
```

혹은 명령어로 바로 적용할 수 있습니다.

```sh
kubectl apply -f <configMap>
```

#### deployment로 가져와서 사용하는 방법

이제 config 를 만들었다면, 사용하는 방법에 대해서도 알아볼까요?

krampoline\_step4 로 돌아와 보시면 다음과 같은 nginx 설정이 있습니다.

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
        volumeMounts:
        - name: nginx-config
                    # 실제로 마운트를 할 위치를 설정한다.
          mountPath: /etc/nginx/conf.d
      volumes:
            # 파드 레벨에서 볼륨을 설정한 다음, 해당 파드 내의 컨테이너에 마운트한다.
      - name: nginx-config
        configMap:
                    # 마운트하려는 컨피그맵의 이름을 제공한다.
          name: nginx
```

이런식으로 원하는 위치에 원하는 설정을 넣을 수 있습니다.

**ConfigMap 관련 명령어**

```sh
kubectl get configmap # 전체 configmap 가져오기

kubectl describe configmap <configmap 이름> # 해당 configmap 내용 가져오기

kubectl edit configmap <configmap 이름> # 해당 configmap 내용 수정하기

kubectl delete configmap <configmap 이름> # 해당 configmap 내용 삭제하기
```

### 시크릿(Secret)

시크릿은 암호, 토큰 또는 키와 같은 소량의 중요한 데이터를 포함하는 오브젝트입니다.

특히나 깃허브 기반으로 하고 있는 크램폴린IDE 에서 비밀키나 api키 부분에 걱정이 많으실텐데요.

깃허브에 올리지 않고, Secret을 이용해서 IDE 안에서 쿠버네티스에 적용 시킬 수 있습니다.

#### kustomization을 이용해서 만드는법

ConfigMapGenerator 와 비슷한 방법을 사용하고 있는데요. 바로 kustomization 의 secretGenerator 입니다.

```yaml
namespace: default
resources:
  - nginx.yaml
  - mariadb.yaml
  - backend.yaml
  - frontend.yaml
secretGenerator:
- name: database-creds
  files:
  - username.txt
  - password.txt
```

여러분에게 이해를 쉽게 하기 위해 file타입으로 넣는다면 다음과 같이 넣으시면 됩니다.

#### 오브젝트를 작성해서 이용하는 방법

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: my-secret
data:
  username: <base64-encoded-username>
  password: <base64-encoded-password>
```

이번에 조금 다르게 value 로 해봅시다. 해당 오브젝트를 작성하고, configMap에서 처럼 `k8s/kustomization.yaml` 에서 불러와서 사용하거나 명령어로도 사용할 수 있습니다.

#### deployment로 가져와서 사용하는 방법

이번에는 해당 내용을 환경 변수로 불러오는 예시와 file 로 불러오는 예시를 보여드리도록 하겠습니다.

```yaml
# Deployment를 생성하는 YAML 파일
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app-env
spec:
  replicas: 1
  selector:
    matchLabels:
      app: my-app-env
  template:
    metadata:
      labels:
        app: my-app-env
    spec:
      containers:
        - name: my-app-container-env
          image: my-app-image:latest
          env:
            - name: MY_USERNAME
              valueFrom:
                secretKeyRef:
                  name: my-secret-env
                  key: username
              # Secret의 "username" 필드를 환경 변수 MY_USERNAME으로 설정합니다.
            - name: MY_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: my-secret-env
                  key: password
              # Secret의 "password" 필드를 환경 변수 MY_PASSWORD로 설정합니다.
```

```yaml
# Deployment를 생성하는 YAML 파일
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app-env
spec:
  replicas: 1
  selector:
    matchLabels:
      app: my-app-env
  template:
    metadata:
      labels:
        app: my-app-env
    spec:
      containers:
        - name: my-app-container-env
          image: my-app-image:latest
          env:
            - name: MY_USERNAME
              valueFrom:
                secretKeyRef:
                  name: my-secret-env
                  key: username
              # Secret의 "username" 필드를 환경 변수 MY_USERNAME으로 설정합니다.
            - name: MY_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: my-secret-env
                  key: password
              # Secret의 "password" 필드를 환경 변수 MY_PASSWORD로 설정합니다.
```

이런식으로 secret을 환경변수로도, 파일로도 사용할 수 있답니다.



**Secret 관련 명령어**

```sh
kubectl get secret # 전체 secret 가져오기

kubectl describe secret <configmap 이름> # 해당 secret 내용 가져오기

kubectl edit secret <configmap 이름> # 해당 secret 내용 수정하기

kubectl delete secret <configmap 이름> # 해당 secret 내용 삭제하기
```
