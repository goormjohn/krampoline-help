# Kargo를 활용한 App 배포

이제 빌드한 이미지를 Kargo를 통해 배포해보도록 하겠습니다. 다시 카카오 클라우드 패널로 돌아와 이번에는 상단에서 Kargo 탭을 선택합니다. 애플리케이션을 배포하기 위해서는 먼저 Kargo 앱을 등록해야 합니다.

### **Kargo App 생성**

<figure><img src="../../.gitbook/assets/image (113).png" alt=""><figcaption></figcaption></figure>

화면에 보이는 앱 등록하기 버튼을 클릭하여 새로운 앱을 생성합니다.

### **Kargo App 배포**

<figure><img src="../../.gitbook/assets/image (134).png" alt=""><figcaption></figcaption></figure>

앱을 생성하면 화면과 같이 앱의 이름과 네임스페이스를 확인할 수 있습니다.

이제 앱을 배포할 준비가 완료되었습니다. 패널에서 배포할 앱을 선택합니다.

<figure><img src="../../.gitbook/assets/image (136).png" alt=""><figcaption></figcaption></figure>

* 그러면 해당 앱의 상세 정보를 확인할 수 있는 패널로 넘어갑니다. 여기에서 상단에 위치한 배포 버튼을 클릭합니다.

<figure><img src="../../.gitbook/assets/image (104).png" alt=""><figcaption></figcaption></figure>

그러면 배포할 D2Hub Repository와 태그를 선택할 수 있는 창이 나타납니다. 배포할 Repository와 태그를 선택하고 배포 버튼을 클릭하면 배포가 시작됩니다.

<figure><img src="../../.gitbook/assets/image (133).png" alt=""><figcaption></figcaption></figure>

* 이미지 빌드와 마찬가지로 화면의 우측 상단에 표시되는 메시지를 통해 배포 결과를 확인할 수 있고, 배포 작업이 끝나면 패널 하단의 배포 정보에서 배포 상태를 확인할 수 있습니다.

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

* 배포에 대한 manifest 내용은 배포 파일 정보에서 YAML 형식으로 확인할 수 있습니다. 이 파일을 수정할 수는 없지만 현재 애플리케이션이 어떤 정보로 배포되는지 확인할 수 있습니다.

<figure><img src="../../.gitbook/assets/image (154).png" alt=""><figcaption></figcaption></figure>
