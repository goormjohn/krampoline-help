# Kakao Cloud를 활용한 배포

크램폴린IDE와 카카오 D2Hub, Kargo 시스템의 연동을 통해 애플리케이션의 이미지를 간편하게 빌드하고 배포할 수 있습니다. D2Hub와 Kargo에 대한 자세한 설명은 카카오 클라우드 강의에서 확인하실 수 있고, 본 도움말에서는 크램폴린IDE 내에서 카카오 클라우드 서비스를 통해 애플리케이션을 빌드하고 배포하는 방법에 대해서 살펴보도록 하겠습니다.

## 크램폴린IDE를 활용한 DKOS 배포 플로우

크램폴린IDE를 통해 카카오 클라우드 자원을 활용하여 서비스를 배포하는 전체 플로우는 아래와 같습니다.

<figure><img src="../../.gitbook/assets/image (249).png" alt=""><figcaption></figcaption></figure>

* **D2Hub 이미지 빌드** : github 소스 저장소의 코드를 이용하여 D2Hub repository에 이미지를 빌드합니다.
* **Kargo App 배포** : Kargo를 통해 사용자가 할당받은 DKOS Cluster에 D2Hub 이미지를 배포합니다.
* **외부실행 URL 등록 및 확인** : DKOS Cluster의 배포된 앱에 접속할 수 있는 외부 실행 URL을 발급합니다.
