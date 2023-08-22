# 코드 병합

두 소스 코드를 하나의 코드로 병합합니다. \
버전 관리시 충돌이 일어났을 때, 직접 충돌을 해결하기 위해 이용할 수 있습니다. \
병합을 하지 않아도 두 소스 코드의 다른 점을 쉽게 파악할 수 있습니다.\
\
**\[편집] > \[코드 병합]**의 하위 메뉴를 통해 사용하세요. 단축키를 이용하면 편리하게 기능을 이용할 수 있습니다.

* **코드 병합 창 보기(`Alt + Shift + M (Mac: ⌥⇧M)`)**: \
  실행하면 먼저 병합하고자 하는 두 파일을 선택합니다. \
  **`확인`** 버튼을 누르면 두 소스 코드간의 차이점이 표시된 에디터가 열립니다.\

* **다음 차이점(`Alt + Shift + = (Mac: ⌥⇧=)`)**: \
  현재 커서로부터 가장 가까운 다음 차이점으로 이동합니다. \
  차이점이 선택되면 배경색이 바뀝니다.\

* **이전 차이점(`Alt + Shift + - (Mac: ⌥⇧-)`)**: \
  현재 커서로부터 가장 가까운 이전 차이점으로 이동합니다. \
  차이점이 선택되면 배경색이 바뀝니다.\

* **차이점 병합(`Alt + Shift + / (Mac: ⌥⇧/)`)**: \
  현재 선택된 차이점을 오른쪽 에디터로부터 왼쪽 에디터에 덮어씌웁니다. \
  병합 에디터 중앙의 화살표 아이콘(**`<~`**)을 눌러서도 병합할 수 있습니다. \
  차이점이 선택되지 않았다면 제일 첫 번째 차이점을 병합합니다.

<figure><img src="../../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

병합 에디터 하단 중앙의 **`=><=`** 아이콘을 누르면 양쪽 에디터의 스크롤을 묶거나 풀 수 있습니다. \
기본 상태는 양쪽 에디터의 스크롤이 같이 움직이는 상태입니다. \
스크롤을 풀면, 양쪽 에디터의 스크롤이 각자 움직입니다.\
\
병합 후, 저장하면 왼쪽 에디터 원본에 병합된 내용이 저장됩니다. \
오른쪽 에디터는 수정이 불가합니다. \
코드 병합 창은 새로고침했을 경우 유지되지 않습니다.