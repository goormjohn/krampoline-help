# Frontend 구성

#### Frontend 구성

가장 먼저, Frontend 앱의 경우 static 파일 경로에 대한 설정이 반드시 필요합니다.\
[Static Path 관련 설정 가이드](../../dkos/static-path.md)를 반드시 확인하고 설정해야 합니다.\
\*\***추후 업데이트 시 static path 부분은 제거될 수 있습니다. 업데이트 후에는 조치하지 않아도 됩니다.\*\***

{% content-ref url="../../dkos/static-path.md" %}
[static-path.md](../../dkos/static-path.md)
{% endcontent-ref %}

두번째로 리액트 앱의 경우 3000번 포트로 앱이 실행되도록 설정되어야 합니다.\
기본으로 제공된 쿠버네티스 yaml에서 Frontend Service의 경우 3000번 포트로 실행된 앱을 노출시키는 것으로 정의해두었습니다.

따라서 3000번 포트로 앱이 실행되도록 설정해야 합니다.\
(React의 경우 추가적인 설정을 하지 않으면 자동으로 3000번 포트로 실행됩니다.)

