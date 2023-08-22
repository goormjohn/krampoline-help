# 크램폴린IDE를 활용한 DKOS 배포 플로우

크램폴린IDE를 통해 카카오 클라우드 자원을 활용하여 서비스를 배포하는 전체 플로우는 아래와 같습니다.

<figure><img src="https://lh4.googleusercontent.com/n95J16b1ui1J2Wp-_N5RPE2XUsXdL93wrntWk-10PyyB_4W4aMI824Qncu_hW4XrUDzpnELaA1Wa2tiRdeZWmbzQdFZgKdZeMpedj25ErRX9BT-WKYHA2hhBqoy6FpWe7Q2qT0HpPjMSwoltkCvnd8w" alt=""><figcaption><p>크램폴린IDE 배포 플로우 와 시스템 연동기능 관계도</p></figcaption></figure>

* **D2Hub 이미지 빌드** : github 소스 저장소의 코드를 이용하여 D2Hub repository에 이미지를 빌드합니다.
* **Kargo App 배포** : Kargo를 통해 사용자가 할당받은 DKOS Cluster에 D2Hub 이미지를 배포합니다.
* **외부실행 URL 등록 및 확인** : DKOS Cluster의 배포된 앱에 접속할 수 있는 외부 실행 URL을 발급합니다.
