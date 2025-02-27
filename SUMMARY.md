# Table of contents

* [크램폴린IDE](README.md)
  * [크램폴린IDE란?](ide/krampolineide.md)
  * [컨테이너 콘솔 사용법](ide/container-console/README.md)
    * [컨테이너 생성](ide/container-console/create.md)
    * [컨테이너 설정](ide/container-console/setting.md)
    * [실행 URL 설정](ide/container-console/shared-url.md)
    * [컨테이너 공유 설정과 멤버 설정](ide/container-console/undefined.md)
  * [크램폴린IDE 사용법](ide/krampolineide-1/README.md)
    * [코드 편집과 저장](ide/krampolineide-1/edit-save.md)
    * [파일](ide/krampolineide-1/file/README.md)
      * [새로 만들기](ide/krampolineide-1/file/new.md)
      * [열기 / 닫기](ide/krampolineide-1/file/open-close.md)
      * [복사 / 붙여넣기](ide/krampolineide-1/file/copy-paste.md)
      * [복제](ide/krampolineide-1/file/clone.md)
      * [이동](ide/krampolineide-1/file/move.md)
      * [이름 변경](ide/krampolineide-1/file/change-name.md)
      * [삭제](ide/krampolineide-1/file/delete.md)
      * [인쇄](ide/krampolineide-1/file/print.md)
      * [파일 관리](ide/krampolineide-1/file/manage.md)
      * [속성](ide/krampolineide-1/file/properties.md)
    * [에디터](ide/krampolineide-1/editor/README.md)
      * [설정](ide/krampolineide-1/editor/edit.md)
      * [텍스트](ide/krampolineide-1/editor/text.md)
      * [줄](ide/krampolineide-1/editor/line.md)
      * [선택](ide/krampolineide-1/editor/select.md)
      * [코드 접기](ide/krampolineide-1/editor/fold-code.md)
      * [이동](ide/krampolineide-1/editor/move.md)
      * [에디터에서 찾기](ide/krampolineide-1/editor/find.md)
      * [에디터에서 바꾸기](ide/krampolineide-1/editor/replace.md)
      * [프로젝트 / 디렉토리에서 찾기](ide/krampolineide-1/editor/find-projects.md)
      * [정렬](ide/krampolineide-1/editor/align.md)
      * [주석](ide/krampolineide-1/editor/comment.md)
      * [코드 병합](ide/krampolineide-1/editor/merge.md)
    * [터미널](ide/krampolineide-1/terminal/README.md)
      * [기본 사용법](ide/krampolineide-1/terminal/basic-how-to.md)
      * [설정](ide/krampolineide-1/terminal/edit.md)
    * [기타](ide/krampolineide-1/etc/README.md)
      * [단축키](ide/krampolineide-1/etc/shortcut.md)
      * [해당 영역을 쉘에서 실행하기](ide/krampolineide-1/etc/execute.md)
      * [정의된 곳으로 이동하기](ide/krampolineide-1/etc/go-to-definition.md)
    * [팀프로젝트](ide/krampolineide-1/undefined.md)
  * [Git 연동 사용법](ide/git/README.md)
    * [Github 설정](ide/git/github/README.md)
      * [새 컨테이너 Git 설정](ide/git/github/git.md)
      * [생성된 컨테이너에서 Git 설정](ide/git/github/git-1.md)
    * [Git](ide/git/git/README.md)
      * [Git](ide/git/git/git.md)
      * [Status](ide/git/git/status.md)
      * [Add](ide/git/git/add.md)
      * [Commit](ide/git/git/commit.md)
      * [Push](ide/git/git/push.md)
      * [Pull](ide/git/git/pull.md)
      * [Ignore](ide/git/git/ignore.md)
      * [Branch](ide/git/git/branch.md)
      * [History](ide/git/git/history.md)
      * [Event tab](ide/git/git/event-tab.md)
  * [명령어](ide/command/README.md)
    * [명령어](ide/command/basic-how-to.md)
    * [실행](ide/command/run.md)
    * [빌드](ide/command/build.md)
    * [실행 URL 설정](ide/command/url.md)
  * [Kakao Cloud 배포 사용법](ide/kakao-cloud/README.md)
    * [Kakao Cloud를 활용한 배포](ide/kakao-cloud/basic-how-to.md)
    * [D2Hub를 활용한 이미지 빌드](ide/kakao-cloud/d2hub-repository/README.md)
      * [1. Dockerfile 생성](ide/kakao-cloud/d2hub/1.-dockerfile.md)
      * [2. github 소스 저장소 추가 연동](ide/kakao-cloud/d2hub/2.-github.md)
      * [3. D2Hub Repository 생성](ide/kakao-cloud/d2hub/3.-d2hub-repository.md)
      * [4. D2hub 이미지 빌드](ide/kakao-cloud/d2hub/4.-d2hub.md)
    * [Kargo App 배포](ide/kakao-cloud/kargo-app/README.md)
      * [1. Kargo 배포 구성 파일 작성](ide/kakao-cloud/kargo-app/1.-kargo.md)
      * [2. Kargo App 생성](ide/kakao-cloud/kargo-app/2.-kargo-app.md)
      * [3. 쿠버네티스 구성 파일의 유효성 확인](ide/kakao-cloud/kargo-app/3..md)
      * [4. DKOS 클러스터 배포](ide/kakao-cloud/kargo-app/4.-dkos.md)
    * [DKOS 배포 APP의 외부 접속 URL 등록](ide/kakao-cloud/dkos-app-url/README.md)
      * [1. Ingress IP 확인 및 URL 발급](ide/kakao-cloud/dkos-app-url/1.-ingress-ip-url.md)
    * [DKOS 배포시 주의 사항](ide/kakao-cloud/dkos/README.md)
      * [D2hub 이미지 재빌드 및 재배포 방법](ide/kakao-cloud/dkos/d2hub.md)
      * [Proxy 적용 방법](ide/kakao-cloud/dkos/proxy.md)
      * [크램폴린IDE ConfigMap, Secret 사용하기](ide/kakao-cloud/dkos/ide-configmap-secret.md)
      * [크램폴린IDE - D2Hub 에서 사용가능한 Docker Image URL](ide/kakao-cloud/dkos/ide-d2hub-docker-image-url.md)
    * [Fullstack Application 배포를 위한 추가 가이드](ide/kakao-cloud/fullstack-application/README.md)
      * [DKOS에 배포된 풀스택 어플리케이션 구조](ide/kakao-cloud/fullstack-application/dkos.md)
      * [기본 구성에 포함된 쿠버네티스 구조](ide/kakao-cloud/fullstack-application/undefined/README.md)
        * [Pod](ide/kakao-cloud/fullstack-application/undefined/pod.md)
        * [Deployment](ide/kakao-cloud/fullstack-application/undefined/deployment.md)
        * [Service](ide/kakao-cloud/fullstack-application/undefined/service.md)
        * [Ingress](ide/kakao-cloud/fullstack-application/undefined/ingress.md)
      * [기본 배포 구성을 사용한 배포 방법](ide/kakao-cloud/fullstack-application/undefined-1/README.md)
        * [Frontend 구성](ide/kakao-cloud/fullstack-application/undefined-1/frontend.md)
        * [Backend 구성](ide/kakao-cloud/fullstack-application/undefined-1/backend.md)
        * [쿠버네티스 yaml 파일을 수정하는 방법](ide/kakao-cloud/fullstack-application/undefined-1/yaml.md)
      * [참고 사항](ide/kakao-cloud/fullstack-application/undefined-2/README.md)
        * [배포한 앱의 로그 확인](ide/kakao-cloud/fullstack-application/undefined-2/undefined.md)
        * [배포한 DB - SQL문을 실행](ide/kakao-cloud/fullstack-application/undefined-2/db-sql.md)
