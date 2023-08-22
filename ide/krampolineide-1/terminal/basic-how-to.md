# 기본 사용법

크램폴린IDE는 터미널을 그대로 제공하고 있어, 명령어에 익숙한 개발자들이 터미널을 이용해서 고급 작업을 진행할 수 있습니다.

\
기본적으로 터미널은 크램폴린IDE 인터페이스 하단 레이아웃의 터미널 탭으로 사용할 수 있습니다. \
새 창으로 열고 싶다면 **\[창] > \[새 터미널 창]**으로 가거나 기본 단축키 **`Alt + Shift + T (Mac: ⌥⇧T)`** 를 누르세요. \
워크스페이스에 새로운 터미널 창이 뜹니다. 터미널 창은 크램폴린IDE를 새로고침하면 유지되지 않습니다.\
\
프로젝트 탐색기에서 폴더에 우클릭을 하고 **\[해당 위치에서 터미널 열기]** 메뉴를 클릭하면, 자동으로 해당 폴더로 이동된 채로 터미널을 새 창으로 열 수 있습니다.

<figure><img src="../../../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>



※ 크램폴린IDE는 docker 컨테이너 기반 서비스로 보안 정책상 컨테이너에 시스템 권한을 지원하지 않습니다. 따라서 **`ufw`**, **`systemctl`**, **`docker`**(docker in docker)와 같이 시스템 자원에 접근하는 명령어들은 사용하실 수 없습니다.