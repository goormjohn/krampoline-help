# Pod

Pod는 쿠버네티스의  기본 배포 단위입니다.\
개발한 어플리케이션이 도커 이미지로 빌드 되면, 해당 이미지를 이용해서 Pod라는 실행 단위를 구성하게 됩니다.\
예를 들어 만약 Spring Server를 도커 이미지로 빌드했다면, 해당 Spring 이미지를 감싼 Pod라는 실행 단위를 구성하게 됩니다.\
해당 Pod를 실행시키면 내부의 이미지를 컨테이너로 실행하게 되어, Spring Server를 구동하게 됩니다.

<figure><img src="https://lh5.googleusercontent.com/ATQnHDLHJFI3xyr77bU3dWgxDI2wE49rJWbMW-jHKI03MzaYr6eRrxeWbG4LywY2azPUTJvhyD1gM6x_RkijD4eJ9pQvc1K8M1scrOZGBzv0or_aPf8C5CMo5-ZIqlXon0lnKLLjW1rFi52lVxYoFjM" alt=""><figcaption></figcaption></figure>
