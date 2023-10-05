# 2. 이미지 재빌드 및 재배포 방법

만약 배포 과정에서 수정 사항이 발생한다면 D2hub Repository를 재빌드하고, Kargo App을 재배포하여 수정 사항을 반영할 수 있습니다.

다만 **D2hub Repository, Kargo App은 모두 Krampoline IDE의 실습 환경이 아닌 github 소스 저장소와 연결되어 있다는 점을 주의**해야 합니다.\
Krapoline IDE 내에서 파일을 수정한다고 해서, 해당 사항이 D2hub Repository나 Kargo App에 반영되지는 않습니다.\
반드시 **수정사항을 main 브랜치에 commit 하고 push 해야만, 배포 프로세스에 수정된 사항을 반영할 수 있습니다**.



크램폴린 IDE 내에서 파일을 수정했을 경우, IDE 내의 Git 기능을 이용하거나 터미널을 이용해서 commit - push 할 수 있습니다.\
현재 프로젝트 내에서 파일의 변경사항이 존재할 경우 ‘스테이지에서 제외된 파일’ 목록에 변경사항이 표시됩니다.\
commit 하고자 하는 변경사항에 대해서 + 버튼을 클릭해서 ‘스테이지에 추가된 파일’ 목록으로 옮길 수 있습니다.

<figure><img src="../../../.gitbook/assets/image (244).png" alt=""><figcaption></figcaption></figure>

‘스테이지에 추가된 파일’ 목록을 기반으로 커밋을 만들기 위해서 하단의 칸에 커밋 메시지를 작성한 후 ‘커밋하기’ 버튼을 클릭합니다.

<figure><img src="../../../.gitbook/assets/image (245).png" alt=""><figcaption></figcaption></figure>

커밋이 완료된 후에는 탭 상단의 ‘Push’ 버튼을 통해 원격의 github 소스 저장소에 커밋 내역을 push 할 수 있습니다.\
(해당 버튼이 정상 작동하지 않는 경우에는 터미널 창에서 git push를 입력하여 푸시를 진행합니다.)

<figure><img src="../../../.gitbook/assets/image (246).png" alt=""><figcaption></figcaption></figure>

사이드탭의 GIT 탭은 실습 환경 내에 git clone 되어 있는 프로젝트 중 하나와 연결되어 있습니다.\
만약 파일이 변경되었는데도 사이드탭에 변경사항이 보이지 않는다면 현재 GIT 탭이 다른 프로젝트에 연결되어 있을 수 있습니다.

GIT 설정 화면에서 GIT 탭이 바라보고 있는 프로젝트를 변경할 수 있습니다.\
먼저 상단의 설정 버튼을 통해 GIT 설정 페이지로 진입합니다.\


<figure><img src="../../../.gitbook/assets/image (247).png" alt=""><figcaption></figcaption></figure>

‘**폴더 설정**’ 탭에서 GIT 탭에 연결할 프로젝트를 선택할 수 있습니다.\
현재 연결된 프로젝트에는 체크 표시가 보이고, 프로젝트를 클릭한 뒤 ‘**Change**’ 버튼을 누르면 해당 프로젝트로 연결 대상을 변경합니다.

<figure><img src="../../../.gitbook/assets/image (248).png" alt=""><figcaption></figcaption></figure>

D2Hub Repository의 경우 ‘빌드하기’를 클릭해서 재빌드를 시도하면 자동으로 github 소스 저장소에서 새롭게 코드 내용을 읽어와서 이미지 빌드를 진행합니다.

이와 달리, Kargo App의 경우 ‘GIT 불러오기’ 버튼을 통해 배포 구성 파일 내용을 갱신해야만 변경사항을 새롭게 반영할 수 있습니다.

<figure><img src="https://lh5.googleusercontent.com/LwaXaODlcQ79FTHeN70pPGaDCVbzn9ewLKJoU6_4Ax9zukcwC-gsIP9HRZLp2XFy0z0pRF_Kx-wI4vPzZcVMyDDon6kMF6jSCUIx-bMIspWO1WAe5t4-ArqAf_LdzPxJ7gFQsX7uPsSk0pufboNLtMA" alt=""><figcaption></figcaption></figure>
