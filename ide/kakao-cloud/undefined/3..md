# 3. 프록시 적용 방법

기본적으로 DKOS 상에 배포된 앱과 Krampoline IDE의 개발환경에서는 외부의 API를 호출하는 것이 불가능합니다.

만약 외부 API 호출이 필요하다면, 프록시를 적용해서 API를 호출해야 합니다.

프록시 서버의 도메인 및 포트는 아래와 같습니다.

`http://krmp-proxy.9rum.cc:3128`

> proxy 서버의 경우 https가 아닌 http 프로토콜로 적용해야 합니다.

curl 요청을 보낼 때 프록시를 적용하는 예시는 아래와 같습니다.

<pre><code>curl -x http://krmp-proxy.9rum.cc:3128 \
<strong>     -L https://api.github.com/users
</strong></code></pre>

만약 배포한 어플리케이션 상에서 외부 API에 요청을 보내야 한다면, 자신이 사용하는 라이브러리에 맞게 프록시를 적용해야 합니다.

Node.js 스택의 Backend Server에서 외부 API에 요청을 보내야 하는 상황에서, Axios 라이브러리에 프록시를 적용하는 예시는 다음과 같습니다.



```javascript
const axios = require('axios');
const HttpsProxyAgent = require('https-proxy-agent');

const httpsAgent = new HttpsProxyAgent({
	host: 'krmp-proxy.9rum.cc',
	port: 3128,
});
const axiosUsingProxy = axios.create({ httpsAgent });

const accessToken = await axiosUsingProxy.get(
	'https://api.github.com/users',
);
```

> Frontend App에서 외부 API를 호출하는 경우에는 브라우저 단에서 요청이 이루어지기 때문에, 프록시를 적용할 필요가 없습니다.
>
> DKOS 내에서 실행되는 Backend Server 등에서 외부 API를 호출하는 경우에 프록시를 적용해야 합니다.
