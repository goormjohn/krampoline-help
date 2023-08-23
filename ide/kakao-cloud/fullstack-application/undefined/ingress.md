# Ingress

**Ingress는 외부의 http/https 요청을 서비스에 전달하는 정책을 정의**합니다.\
특정 api 주소로 http 요청이 들어왔을 때, 정의한 라우팅 규칙에 따라 적절한 서비스로 요청을 포워딩합니다.\
nginx 등의 controller를 이용하여 작동합니다.

크램폴린 IDE에서는 사용자별로 외부 URL을 발급하고, 이를 사용자가 배포한 Ingress 객체의 포트에 연결 시켜서 앱을 외부에 노출시킵니다.

<figure><img src="https://lh6.googleusercontent.com/wspnal1h0LtB7rRwC4ZI63FDazHdn1vjkcrG0EvBlAi7DIM1X1GWUuiAXizUdioSYlMi_qxi3yR3x2SSUH-JQoGRGMdm84E3MWqZNvBWsywWCGpZtLDaXzVo-r3D7jOmpncmfjDS7EJpDRub95_nGCU" alt=""><figcaption></figcaption></figure>

