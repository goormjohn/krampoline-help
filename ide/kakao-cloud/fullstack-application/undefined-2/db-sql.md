# 배포한 DB - SQL문을 실행

#### 배포한 DB에 SQL문을 실행하고 싶다면 DB Pod에 접속해야 합니다.

DKOS 클러스터에 배포한 DB에 sql문을 실행하고 싶다면, 크램폴린 IDE 내의 터미널에서 해당 db가 배포되어 있는 Pod에 접속해야 합니다.&#x20;

다음 명령어를 통해 mariadb가 배포된 Pod에 접속할 수 있습니다.\
(mariadb-0는 db가 배포된 Pod의 이름입니다. 다른 db 유형을 사용할 경우 이름이 달라질 수 있습니다.)

```bash
$ kubectl exec -it mariadb-0 -- /bin/bash
```

Pod에 진입했다면, 다음 명령어를 통해 해당 db 인스턴스에 mysql로 접속합니다.\
아래는 root 사용자로 krampoline database에 접근하는 커맨드입니다.

```bash
$ mysql -h mariadb-0.mariadb -u root -p krampoline
Enter password: -> 비밀번호 입력
```

이제 커맨드 라인이 다음과 같이 변하며, sql을 실행할 수 있습니다.

```bash
MariaDB [krampoline]>
```
