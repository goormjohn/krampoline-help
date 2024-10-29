# 실행 URL 설정

* 크램폴린IDE **컨테이너에서 실행한** 애플리케이션에 접속하기 위해 실행 URL을 설정하는 방법에 대해서 살펴보겠습니다.

<figure><img src="../../.gitbook/assets/image (101).png" alt=""><figcaption></figcaption></figure>

* 실행 URL은 컨테이너 내에서 실행 중인 애플리케이션의 포트와 연결되어 애플리케이션을 쿠버네티스에 배포하기 전에 개발 내용들을 직접 확인해 볼 수 있도록 도와주는 기능입니다. 기본적으로 HTTPS 프로토콜을 지원하기 때문에 애플리케이션 보안에 대해서는 걱정하지 않아도 됩니다.



<figure><img src="../../.gitbook/assets/image (124).png" alt=""><figcaption></figcaption></figure>

* 현재 보이는 패널에서 URL 설정 탭을 선택합니다. 컨테이너의 실행 URL을 관리할 수 있는 패널이 나타납니다. 여기에서 새로운 실행 URL을 등록할 수 있는 버튼과 컨테이너에 등록되어 있는 실행 URL의 목록을 확인할 수 있습니다. 기본적으로 80번 혹은 3000번 포트와 연결된 실행URL이 미리 등록되어 있어 이 포트를 사용할 경우 별도로 실행 URL을 새로 생성할 필요가 없습니다.

<figure><img src="../../.gitbook/assets/image (163).png" alt=""><figcaption></figcaption></figure>

* 목록에서 URL과 포트 정보를 확인할 수 있는데, 이 URL을 바로 브라우저에서 실행하려면 링크 바로가기 버튼을 클릭합니다. 브라우저로 바로 실행하지 않고 URL을 복사하려면 복사하기 버튼을 클릭합니다.

<figure><img src="../../.gitbook/assets/image (125).png" alt=""><figcaption></figcaption></figure>

* 이 라디오 버튼으로 선택된 URL은 미리보기 기능과 연결되며, 미리보기를 통해 애플리케이션을 별도 브라우저 탭에서 실행하지 않고 IDE 내에서 화면이 분할되어 바로 확인할 수 있습니다.

<figure><img src="../../.gitbook/assets/image (132).png" alt=""><figcaption></figcaption></figure>

* 이제 새 URL을 생성하도록 하겠습니다. 패널 상단에 위치한 Add 버튼을 선택합니다.

<figure><img src="../../.gitbook/assets/image (135).png" alt=""><figcaption></figcaption></figure>

* 그러면 새로운 실행 URL을 등록할 수 있는 창이 나타납니다. 여기에서 실행 URL에 사용할 원하는 prefix와 연결할 애플리케이션의 포트 번호를 입력하고 등록 버튼을 클릭합니다. 그러면 실행 URL이 간단하게 등록됩니다.

<figure><img src="../../.gitbook/assets/image (4) (1) (1).png" alt=""><figcaption></figcaption></figure>

* 실행 URL 등록 창에서도 실행 URL의 목록을 볼 수 있으며, 이 곳에서 등록된 실행 URL을 삭제하거나 포트 번호를 수정할 수 있습니다.
