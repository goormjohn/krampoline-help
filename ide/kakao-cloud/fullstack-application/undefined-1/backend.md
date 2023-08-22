# Backend 구성

**Backend 구성**

Backend 서버의 경우 8080번 포트로 실행된 앱을 Service 상에 노출시키는 것으로 정의해두었습니다.\
따라서 8080번 포트로 앱이 실행되도록 설정해야 합니다.

또한 DB 연결 시 기본 설정 사항들을 반영해야 합니다.\
제공된 구성 파일에서는 mariadb를 사용하고 있으므로, 해당 db와 연결할 수 있는 드라이버를 설정해야 합니다.

또한 username은 root, password는 root, database 이름은 kakao로 설정되어 있으므로, 해당 database에 server가 연결되도록 설정해야 합니다.

아래는 Spring Server에서 db를 연결하는 application.properties 설정 예시입니다.

```yaml
server:
  port: 8080
spring:
  datasource:
    url: ?allowPublicKeyRetrieval=true&useSSL=false
    driver-class-name: org.mariadb.jdbc.Driver
    username: root
    password: root
```
