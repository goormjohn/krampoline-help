# Event tab

**"이벤트"** 탭에서는 크램폴린IDE의 **Git GUI**를 사용하여 작업한 내용들을 확인할 수 있습니다.

<figure><img src="../../../.gitbook/assets/image (122).png" alt=""><figcaption></figcaption></figure>

또한 Git에 익숙하지 않은 초보자도 쉽게 사용할 수 있도록 장애 원인을보다 자세히 알려주고 문제에 대한 해결책을 제시하는 안내 기능이 추가되었습니다.

**에러 상황 예시**

**Commit**

<figure><img src="../../../.gitbook/assets/image (105).png" alt=""><figcaption></figcaption></figure>

이유 : 커밋 메시지를 입력하지 않은 경우 해결방법 : 커밋하기 버튼을 누른 후, 커밋 메세지를 채우고 다시 커밋 해주세요.

**Checkout**

<figure><img src="../../../.gitbook/assets/image (106).png" alt=""><figcaption></figcaption></figure>

이유 : 변경사항을 저장하지 않고 브랜치 변경을 하는 경우 다음과 같은 에러가 발생합니다. 해결방법 : 3가지의 해결방법이 있습니다.

1. 변경사항을 직접 현재 브랜치에 커밋 후 브랜치를 변경 합니다.
2. 강제 체크아웃을 누르면 저장되지 않은 변경사항을 삭제 후 브랜치를 변경 합니다.
3. 스마트 체크아웃을 누르면 현재 변경사항을 이동하는 브랜치에 합치는 작업을 동반합니다.

**Push**

<figure><img src="../../../.gitbook/assets/image (83).png" alt=""><figcaption></figcaption></figure>

이유 : Git origin repository에 권한이 없는 경우 다음과 같은 에러가 발생합니다. 해결방법 : 권한등록하기 버튼을 누른 후, id, pw를 입력 후 다시 push를 진행해 주세요.

**Pull**

<figure><img src="../../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

이유 : Git pull을 받은 후 자동병합에 실패하면 발생합니다. 해결방법 : 충돌파일 보기를 누르면 충돌이 생긴 파일 리스트가 열립니다. 열린 파일들의 충돌을 해결 후 커밋해주세요,
