# Deployment

**Deployment에는 Pod를 관리하는 정책을 정의**합니다.\
쿠버네티스에서는 컨테이너에 장애 상황이 발생했을 때 자동 복구(self-healing)하는 기능을 제공합니다.\
이를 위해 Pod의 복제본(레플리카)을 미리 만들어두고, 컨테이너 장애 상황에서는 미리 만들어 둔 복제본으로 파드를 대체하는 편의 기능을 제공합니다.\
어플리케이션의 새로운 버전을 배포할 때에도 이러한 방식을 활용하여 무중단 배포를 구성할 수 있습니다.\
이 때 **파드의 복제본들을 관리 및 업데이트 하는 정책을 정의하는 곳이 Deployment** 입니다.\
Deployment에는 미리 만들어 둘 복제본의 수를 지정하거나, Pod에 대한 모니터링 정책을 정의할 수 있습니다.

<figure><img src="../../../../.gitbook/assets/Deployment Image.svg" alt=""><figcaption></figcaption></figure>
