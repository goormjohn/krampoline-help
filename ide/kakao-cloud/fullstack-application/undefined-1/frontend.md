# Frontend 구성

#### Frontend 구성

가장 먼저, Frontend 앱의 경우 static 파일 경로에 대한 설정이 반드시 필요합니다.\
크램폴린 배포 가이드에서 관련된 안내를 반드시 확인하고 설정해야 합니다.

두번째로 리액트 앱의 경우 3000번 포트로 앱이 실행되도록 설정되어야 합니다.\
기본으로 제공된 쿠버네티스 yaml에서 Frontend Service의 경우 3000번 포트로 실행된 앱을 노출시키는 것으로 정의해두었습니다.

따라서 3000번 포트로 앱이 실행되도록 설정해야 합니다.\
(React의 경우 추가적인 설정을 하지 않으면 자동으로 3000번 포트로 실행됩니다.)

또한 FrontEnd 레포지토리 내에는 nginx 관련 설정 파일(default.conf)이 위치해 있어야 합니다.&#x20;

기본 제공된 Frontend의 Dockerfile의 경우, 다음과 같이 nginx 관련 설정 파일을 세팅하고 실행하는 부분이 포함되어 있습니다.

nginx를 도커 이미지 내에 설치하고, 프로젝트 루트 위치에  작성한 nginx 설정 파일을 필요 위치에 이동시킨 다음, nginx를 실행시키는 코드입니다.

```docker
*** FrontEnd Dockerfile에서 nginx 설정 부분을 추출 내용입니다.***
RUN apt-get update && \
    apt-get install -y nginx && \
    rm -rf /var/lib/apt/lists/* && \
    rm /etc/nginx/sites-enabled/default
COPY default.conf /etc/nginx/conf.d/

CMD service nginx start
```

따라서 FrontEnd 소스코드 내에 nginx 설정 파일이 함께 포함되어 있어야 합니다.\
프로젝트 루트 디렉토리에 default.conf 파일을 생성하고 다음의 내용을 입력합니다.

**default.conf 파일 내용입니다. 잊지 않고 추가가 필요합니다.**

```nginx
server {
    server_name _;

    location / {
        proxy_pass http://localhost:3000;
    }
   
    location /api/ {
    
```

해당 설정파일의 경우 /api 로 시작하는 http 요청의 경우 BackEnd 앱으로 요청을 보내고, 그 외의 요청은 FrontEnd 앱으로 보내는 방식으로 작동합니다.

이를 통해 단일한 URL 도메인에서 프론트엔드, 백엔드 요청을 모두 받을 수 있게 구성되어 있고, 덕분에 프론트엔드에서는 CORS에 대한 걱정 없이 어플리케이션을 개발할 수 있습니다.
