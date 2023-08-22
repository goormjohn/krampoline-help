# DKOS에 배포된 풀스택 어플리케이션 구조

### 배포가 완료된 풀스택 어플리케이션의 예시 구조

#### DKOS Cluster에 배포하는 풀스택 앱의 예시 구조 입니다.

<figure><img src="https://lh5.googleusercontent.com/-EZvuULkHEcMBtSLhOaqE8EaPokRMuclYhuWPXKC_kPw5AD832gSpRV5ViYzALAHRqYG0O5cjjJz0gQzSTm9B-6dZkw6w4ehy6UlomgjFt9O4XHFPs4AwXeWTM8PO-At5MuL5Mrhdmq0d9wQxR0Gxrg" alt=""><figcaption><p>풀스택 앱의 예시 구조</p></figcaption></figure>

기본 제공된 쿠버네티스 배포 구성 파일을 활용하여 풀스택 어플리케이션을 배포할 경우, 위와 같은 구조로 어플리케이션이 배포됩니다.

총 3개의 Pod로 구성되며, 각각의 Pod의 역할 및 구성은 아래와 같습니다.

* FrontEnd Pod : Nginx, Frontend App
* BackEnd Pod : Backend API Server
* Database Pod : MariaDB

배포 시 팀원이 개발한 Frontend, Backend 레포지토리를 D2Hub를 통해 빌드하고, Kargo를 통해 이를 전체 풀스택 어플리케이션 구성에 포함시켜서 배포하게 됩니다.

Database는 기본 제공되는 MariaDB 이미지를 이용합니다.

기본 제공된 배포 구성 파일을 활용할 경우, 간단하게 이미지 경로와 subpath 등만 변경하면 풀스택 어플리케이션 구조로 배포하는 것이 가능합니다.

\
